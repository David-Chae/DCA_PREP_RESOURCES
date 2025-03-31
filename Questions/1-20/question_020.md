## 20. How would we back up the metadata for Docker Swarm?
```sh
A. We can back up the contents of /etc/docker/swarm.
B. We can run the swarm image with the backup command
C. While the Docker daemon stops, we can back up the contents of /var/lib/docker/swarm on a Swarm manager
D. We can back up the contents of /usr/local/swarm.
```


Let's evaluate each option for backing up Docker Swarm metadata:

**A. We can back up the contents of /etc/docker/swarm.**  
**True** – The configuration files related to Docker Swarm, including swarm-related metadata, are typically stored in `/etc/docker/swarm` on Swarm manager nodes. Backing this up is a good approach to ensure that you have the Swarm's current configuration.

**B. We can run the swarm image with the backup command.**  
**False** – Docker itself does not have a specific `swarm image` or `backup command` built into its standard functionality. Swarm-related backup typically involves manually backing up configurations or state files from the manager nodes, not running a specific image or command.

**C. While the Docker daemon stops, we can back up the contents of /var/lib/docker/swarm on a Swarm manager.**  
**True** – The state of a Docker Swarm is stored in `/var/lib/docker/swarm` on the manager node, which includes information like the state of services, tasks, and nodes. Backing up this directory while the Docker daemon is stopped ensures consistency and integrity of the metadata.

**D. We can back up the contents of /usr/local/swarm.**  
**False** – `/usr/local/swarm` is not a standard location for storing Docker Swarm metadata. Swarm-related files are not typically stored in this directory. The primary locations for Swarm metadata are `/etc/docker/swarm` and `/var/lib/docker/swarm`.

### Summary:
- **A**: True
- **B**: False
- **C**: True
- **D**: False
