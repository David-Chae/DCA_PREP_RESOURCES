## What does the EXPOSE directive do?
```
1. It documents ports intended for publishing at the time of running a container.
2. It automatically publishes ports when running a container.
3. It makes a container's port accessible externally.
4. It causes the container to listen on a port.
```

✅ **Correct Answer:**  
**It documents ports intended for publishing at the time of running a container.**

---

### 🧠 Explanation:

The `EXPOSE` directive in a Dockerfile:

- **Does not publish ports** — it just **documents** which ports the container is expected to use.
- **Does not make ports accessible externally** by itself.
- It's primarily **informational**, helping others (or tools) understand what ports the application inside the container is likely to need when published.

---

### ❌ Misconceptions:

- **"It automatically publishes ports…"** → ❌ You still need to use `-p` or `--publish` with `docker run`.
- **"It makes a container's port accessible externally…"** → ❌ Only `-p` does that.
- **"It causes the container to listen…"** → ❌ The containerized application itself (e.g., nginx, node app) must be configured to listen — `EXPOSE` doesn’t do this.

Let me know if you'd like a quick example Dockerfile using `EXPOSE`.
