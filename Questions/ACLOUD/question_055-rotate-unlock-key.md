## How would we rotate a docker swarm unlock-key and ensure that all nodes receive the new key?
```
1. We would generate a new key and save it in a file located at /etc/docker/swarm/unlock.key.
2. We would run the docker swarm unlock-key --rotate command on all manager nodes.
3. We can use the docker swarm unlock command.
4. We would run the docker swarm unlock-key --rotate command on one manager node.
```

✅ **Correct Answer:**  
**We would run the `docker swarm unlock-key --rotate` command on one manager node.**

---

### 🧠 Explanation:

In a Docker Swarm, the **unlock key** is used to encrypt the **Raft data store**, which stores the state of the swarm. To **rotate the unlock key**, you only need to run the command on **one manager node**:

```bash
docker swarm unlock-key --rotate
```

- This **generates a new unlock key**.
- Docker **automatically propagates the new key** to all other manager nodes in the swarm.
- After rotation, you can view the new key using:

```bash
docker swarm unlock-key
```

Make sure to **securely store** the new key in case you need to unlock the swarm after a restart.

---

### ❌ Why the other options are incorrect:

- **“Generate a new key and save it in a file…”** → Unlock keys aren’t manually stored or managed that way.
- **“Run the command on all manager nodes”** → It only needs to be run **once** on **one** manager.
- **“docker swarm unlock”** → That command is used to **unlock** an encrypted swarm, not rotate the key.

Let me know if you'd like help with a script to automate backing up the unlock key after rotation!
