216. How to enable or disable autolock on the existing swarm?
```
A. To enable autolock on an existing swarm, you can use docker swarm update --autolock=true. To disable autolock, use docker swarm update --autolock=false.
B. Autolock can only be enabled when creating a new swarm and cannot be modified for existing swarms.
C. Autolock is always enabled by default, and disabling it on an existing swarm is impossible.
D. To enable or disable autolock on an existing swarm, use the docker swarm autolock command with the enable or disable option.
```

The correct answer is:  
**A. To enable autolock on an existing swarm, you can use `docker swarm update --autolock=true`. To disable autolock, use `docker swarm update --autolock=false`.**

---

### ✅ Explanation:

Docker Swarm allows you to **enable or disable autolock** on an existing swarm with a simple command:

- **Enable autolock:**
  ```bash
  docker swarm update --autolock=true
  ```

- **Disable autolock:**
  ```bash
  docker swarm update --autolock=false
  ```

This gives you the flexibility to add or remove autolock as your security needs change.

---

### ❌ Why the others are incorrect:
- **B**: Incorrect – You can **enable or disable** autolock at any time.
- **C**: Incorrect – Autolock is **not enabled by default**.
- **D**: Incorrect – There is **no command** called `docker swarm autolock`.

---

Let me know if you'd like a quick command summary table for Swarm security options!
