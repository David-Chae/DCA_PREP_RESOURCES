213. How to lock the swarm?
```
A. docker swarm init --autolock
B. docker swarm lock
C. docker swarm secure
D. docker swarm protect
```

The correct answer is: **A. `docker swarm init --autolock`**

---

### ✅ Explanation:

To **lock a Docker Swarm**, you enable the **autolock** feature **at the time of initializing the swarm** using the following command:

```
docker swarm init --autolock
```

This ensures that **manager nodes require an unlock key** after restarting, protecting the encryption keys for swarm data (like secrets and Raft logs).

---

### ❌ The other options are incorrect:
- **B. `docker swarm lock`** – No such command exists.
- **C. `docker swarm secure`** – Invalid command.
- **D. `docker swarm protect`** – Also not a valid Docker CLI command.

---

Read on if you'd like to see how to **rotate or unlock** a swarm as well!


Great! Here's a clear and complete guide on how to **lock** and **unlock** a Docker Swarm using the **autolock** feature:

---

## 🔐 **How to Lock a Docker Swarm**

### 🟢 When creating a new swarm:
Use the `--autolock` flag during swarm initialization:
```bash
docker swarm init --autolock
```

### 🔁 Enable autolock on an existing swarm:
If your swarm is already initialized, you can enable autolock like this:
```bash
docker swarm update --autolock=true
```

Once enabled, the Docker engine will **require a manual unlock** with a key each time a **manager node** restarts.

---

## 🔓 **How to Unlock a Docker Swarm**

### 1. **After restart, to unlock a manager node:**

Docker will prompt:
```
Manager node is locked. Unlock key needed to decrypt storage.
```

Use the unlock key:
```bash
docker swarm unlock
```

You'll be prompted to enter the unlock key.

---

### 2. **View the unlock key:**
In case you didn’t save it (you should!), you can retrieve it **from any manager node**:
```bash
docker swarm unlock-key
```

It will show something like:
```
SWMKEY-1-abc123def456...
```

---

### 3. **Rotate the unlock key (for security):**
You can rotate the key like this:
```bash
docker swarm unlock-key --rotate
```

This gives you a **new key**, and you must update all manager nodes with the new key after they restart.

---

Let me know if you want a quick script or best practices for managing these keys securely.
