## Which of the following are insecure ways to allow a Docker client to authenticate against a registry that uses a self-signed certificate? (Choose two)
```
1. We pass the --insecure-registry flag to the Docker daemon.
2. We use the --skip-tls flag with docker login.
3. We add the self-signed certificate as a trusted registry certificate under /etc/docker/certs.d/.
4. We add the registry to insecure-registries in /etc/docker/daemon.json.
```

✅ **Correct answers:**  
1. **We pass the `--insecure-registry` flag to the Docker daemon.**  
2. **We add the registry to `insecure-registries` in `/etc/docker/daemon.json`.**

---

### 🔍 Explanation:

Both options above **explicitly mark a registry as "insecure"**, allowing communication **without proper certificate verification**. This makes it easier to use a **self-signed certificate**, but it's **not secure**, especially in production environments.

---

### ❌ Why the other options are incorrect (i.e., they are secure or don't exist):

- **We use the `--skip-tls` flag with `docker login`.**  
  ❌ `--skip-tls` is **not a valid flag** for `docker login`. This is not a real or supported option.

- **We add the self-signed certificate as a trusted registry certificate under `/etc/docker/certs.d/`.**  
  ✅ This is the **secure and recommended way** to use self-signed certs:  
  Place the self-signed cert in:  
  ```bash
  /etc/docker/certs.d/<registry-hostname>/ca.crt
  ```
  This way, the Docker client can verify the cert **without disabling security**.

---

Would you like a step-by-step guide for securely trusting a self-signed cert?
