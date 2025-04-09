## How would we back up Docker Swarm?

Backing up a **Docker Swarm** involves preserving the critical data required to **restore or migrate** your Swarm cluster in case of failure or disaster. The most important part of this is backing up the **Swarm manager state**, which includes:

- Service definitions
- Secrets
- Configs
- Networking
- Internal cluster state (Raft logs)

---

## ✅ Here’s How to Back Up Docker Swarm:

### 🔐 Step 1: Backup the Docker Swarm **Raft Data Directory**

> This only applies to **manager nodes** — worker nodes don’t hold Swarm state.

By default, the Swarm data is stored in:

```bash
/var/lib/docker/swarm
```

To safely back this up:

1. **Stop the Docker daemon** on the manager node:
   ```bash
   sudo systemctl stop docker
   ```

2. **Copy the Swarm directory** to a backup location:
   ```bash
   sudo cp -a /var/lib/docker/swarm /backup/swarm-backup-$(date +%F)
   ```

3. **Restart Docker**:
   ```bash
   sudo systemctl start docker
   ```

> 📝 Best practice: Only back up from a **single manager node**, preferably the **leader**.

---

### 🚨 Important Notes:
- Do **not** back up the Raft data while Docker is running — it can corrupt the snapshot.
- The Swarm state is stored in a **Raft log**, and backing it up while running can result in an inconsistent state.

---

## 🛠️ How to Restore

To restore:

1. Stop Docker on the node where you're restoring.
2. Replace `/var/lib/docker/swarm` with your backup copy.
3. Start Docker again:
   ```bash
   sudo systemctl start docker
   ```

> If you're restoring on a **different machine**, make sure it's **not part of an existing Swarm** and has a **matching Docker version**.

---

## 📦 What about volumes and images?

- **Volumes**: If you're using `local` volumes, these are stored in `/var/lib/docker/volumes`. You must back this up separately.
- **Images**: Either back up the image tarballs with `docker save`, or rely on your image registry.

---

## ✅ Summary Checklist for Full Swarm Backup:
- [x] `/var/lib/docker/swarm` (Swarm Raft data)
- [x] `/var/lib/docker/volumes` (if using local volumes)
- [x] Docker images (`docker save`, if not using registry)
- [x] Application config files (Compose files, CI/CD configs, etc.)

---

## SAMPLE QUESTION : How would we back up Docker Swarm?
```
1. Back up the layered file systems of all containers running within the swarm.
2. Back up the contents of /etc/docker/swarm on a Swarm manager.
3. Back up the contents of /var/lib/docker/swarm on a Swarm manager.
4. Back up the contents of /etc/docker on a Swarm manager.
```

