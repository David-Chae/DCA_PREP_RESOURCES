## How would we back up Docker Swarm? 
1. On a Swarm manager, make a backup of the contents of /etc/docker. 
2. On a Swarm manager, make a backup of the contents of /var/lib/docker/swarm. 
3. Back up all of the containers in the swarm's tiered file systems. 
4. On a Swarm manager, make a backup of the contents of /etc/docker/swarm.

The correct answer is:  

✅ **"On a Swarm manager, make a backup of the contents of `/var/lib/docker/swarm`."**  

---

### Explanation:  
Docker Swarm stores its **Raft database** and **cluster metadata** in the directory:  
**`/var/lib/docker/swarm`** (on a Swarm **manager** node).  

To safely back up the Swarm state, follow these steps:  

1. **Stop the Docker daemon** on the Swarm **manager** node to ensure data consistency:  
   ```sh
   systemctl stop docker
   ```
2. **Create a backup of the Swarm metadata directory**:  
   ```sh
   tar -czf swarm-backup.tar.gz /var/lib/docker/swarm
   ```
3. **Restart Docker after the backup**:  
   ```sh
   systemctl start docker
   ```

This ensures a **consistent and uncorrupted** backup of the Swarm cluster's configuration.

---

### Why the Other Options Are Incorrect:  

❌ **"On a Swarm manager, make a backup of the contents of `/etc/docker`."**  
- **`/etc/docker`** contains **configuration files**, but it does **not** store Swarm metadata or Raft logs.  

❌ **"Back up all of the containers in the swarm's tiered file systems."**  
- Swarm metadata **does not** include container file systems. While backing up containers is important, it is **not sufficient** for a Swarm backup.  

❌ **"On a Swarm manager, make a backup of the contents of `/etc/docker/swarm`."**  
- **`/etc/docker/swarm` does not exist**; this is an incorrect directory path.  

---

### **Summary:**  
To properly back up Docker Swarm, back up **`/var/lib/docker/swarm`** from a Swarm **manager node** while the Docker daemon is stopped.
