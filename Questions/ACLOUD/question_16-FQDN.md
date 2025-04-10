## A Kubernetes ClusterIP service called user-db exists in the auth-gateway namespace. The user-db Service's cluster IP is 10.23.254.63. Which of the following addresses could be used to communicate with this service from a pod located in the default namespace?

**ANS: user-db.auth-gateway.svc.cluster.local**

To communicate with a Kubernetes service (`user-db`) in the `auth-gateway` namespace **from a different namespace** (like `default`), you need to use the **fully qualified domain name (FQDN)**:

```
user-db.auth-gateway.svc.cluster.local
```

---

### 🔍 Why it works:

Kubernetes DNS follows this format for service discovery:

```
<service-name>.<namespace>.svc.cluster.local
```

So for your case:
- **Service name**: `user-db`
- **Namespace**: `auth-gateway`

The correct FQDN is:
```
user-db.auth-gateway.svc.cluster.local
```

This resolves to the service's ClusterIP internally (`10.23.254.63` in your case).

---

### Bonus 🧠: Shorter Forms (if inside same namespace)
If a pod were in the same namespace (`auth-gateway`), it could use:
- `user-db`
- `user-db.auth-gateway`
- `user-db.auth-gateway.svc`

But since you're in the `default` namespace, only the **fully qualified name** works reliably.

## How to test it from a pod or write a quick `curl`/`wget` example!

Awesome! Here’s how you can **test access to `user-db.auth-gateway.svc.cluster.local`** from a pod in the **default namespace**, using `curl` or `wget`.

---

### ✅ Step 1: Run a test pod in the `default` namespace

You can start a simple Alpine-based pod with networking tools:

```bash
kubectl run curl-test \
  --image=alpine \
  --restart=Never \
  --rm -i -t \
  --namespace=default \
  -- sh
```

Once inside the pod, install `curl` or `wget` if they’re not already there:

```sh
apk add --no-cache curl
```

---

### ✅ Step 2: Use curl to test the service

Now try:

```sh
curl http://user-db.auth-gateway.svc.cluster.local
```

Or if it's using a port other than 80 (e.g., 5432 for Postgres):

```sh
curl http://user-db.auth-gateway.svc.cluster.local:5432
```

Or for `wget`:

```sh
wget http://user-db.auth-gateway.svc.cluster.local
```

---

### 🔎 Bonus: DNS resolution check

You can also verify DNS resolution with:

```sh
nslookup user-db.auth-gateway.svc.cluster.local
```

Or with `dig` if available:

```sh
apk add --no-cache bind-tools
dig user-db.auth-gateway.svc.cluster.local
```

---

Let me know the service type (`http`, `postgres`, `mongo`, etc.) if you want to go deeper with specific client commands.

