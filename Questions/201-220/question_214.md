214. How to unlock the swarm?
```
A. docker swarm unlock
B. 'docker swarm open'
C. 'docker swarm access'
D. 'docker swarm unseal'
```

The correct answer is: **A. `docker swarm unlock`**

---

### ✅ Explanation:

When Docker Swarm **autolock** is enabled and a **manager node** restarts, it becomes locked to protect sensitive data.  
To unlock the swarm and allow the manager to resume its duties, use:

```bash
docker swarm unlock
```

You’ll then be prompted to enter the **unlock key**, which you can retrieve (if needed) using:

```bash
docker swarm unlock-key
```

---

### ❌ Incorrect options:
- **B. `docker swarm open`** – Not a real Docker command.
- **C. `docker swarm access`** – Invalid CLI command.
- **D. `docker swarm unseal`** – This is from **HashiCorp Vault**, not Docker.

---

Let me know if you want to see an example of the unlock process!
