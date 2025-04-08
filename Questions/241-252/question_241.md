## 241. How to find which networks the service is connected to?

A. To find out which networks the service is connected to, you can use docker network inspect my-network. Alternatively, you can use docker service ls to find the service name and then docker service ps <SERVICE> to list the networks it is connected to.  
B. You can determine the service's connected networks by using the docker network list <SERVICE>  
C. Finding the networks a service is connected to is not possible through Docker commands  
D. Use docker service network <SERVICE> to list the networks to which a service is connected.  


---

### ❌ Why **Option A** is misleading:

You're spot on:

- `docker network inspect my-network`  
  → **Shows containers**, but not directly which **services** those containers are part of.
  
- `docker service ps <service>`  
  → Lists **tasks/containers** of the service, but **not their network details**.

- So while you could *infer* some connections through container inspection, it’s **indirect and incomplete**.

---

### ✅ **Correct approach (not in any listed option):**

The **most accurate** way to see which networks a service is connected to is:

```bash
docker service inspect <service-name> --format '{{json .Spec.Networks}}'
```

Or the more readable:

```bash
docker service inspect <service-name> --pretty
```

This will clearly show:

- Networks the service is connected to.
- Network names or IDs under the `Spec.Networks` section.

---

### Let's revisit the options:

#### A. ❌ *Incorrect / Misleading*
As discussed — it’s indirect, and doesn’t give you service-to-network mapping cleanly.

#### B. ❌ Incorrect  
`docker network list` only lists available networks, no relation to services.

#### C. ❌ Incorrect  
You **can** definitely find service-network connections via proper inspect commands.

#### D. ❌ Invalid command  
`docker service network` doesn’t exist.

---

### 🟩 So what's the right answer?

Technically, **none of the listed options are fully correct**.

> ✅ The most accurate answer should have been:  
> **"Use `docker service inspect <service-name>` to view which networks a service is connected to."**

---

If you’d like, I can help rewrite the question and answers to be technically precise.
