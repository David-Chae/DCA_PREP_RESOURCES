## How would we back up the metadata for Docker Swarm? 
1. We can back up the contents of /etc/docker/swarm. 
2. We can run the swarm image with the backup command. 
3. While the Docker daemon stops, we can back up the contents of /var/lib/docker/swarm on a Swarm manager. 
4. We can back up the contents of /usr/local/swarm.

The correct answer is:  

✅ **"While the Docker daemon stops, we can back up the contents of `/var/lib/docker/swarm` on a Swarm manager."**  

---

### Explanation:  
In Docker Swarm, the **Raft database** stores the cluster metadata, including service definitions, node memberships, and cryptographic keys. This data is located at:  
**`/var/lib/docker/swarm`** (on a Swarm **manager** node).  

To **safely back up Swarm metadata**, follow these steps:  
1. **Stop the Docker daemon** on the Swarm **manager** node:  
   ```sh
   systemctl stop docker
   ```
2. **Create a backup** of the Swarm metadata directory:  
   ```sh
   tar -czf swarm-backup.tar.gz /var/lib/docker/swarm
   ```
3. **Restart Docker** after the backup:  
   ```sh
   systemctl start docker
   ```

This ensures that the backup is **consistent** and **not corrupted**, since the Raft database must not be modified during the backup process.

---

### Why the Other Options Are Incorrect:  

❌ **"We can back up the contents of `/etc/docker/swarm`."**  
- The Swarm metadata **is not stored** in `/etc/docker/swarm`. This is not a valid path for backup.  

❌ **"We can run the swarm image with the backup command."**  
- There is **no official `swarm` image** or built-in **backup command** for Docker Swarm metadata.  

❌ **"We can back up the contents of `/usr/local/swarm`."**  
- This is **not a default directory** used by Docker Swarm for storing metadata.  

---

### Summary:  
To back up **Docker Swarm metadata**, you must back up **`/var/lib/docker/swarm`** **on a manager node**, and the **Docker daemon must be stopped** to ensure data integrity.

https://docs.docker.com/engine/swarm/admin_guide/
