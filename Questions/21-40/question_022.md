## 22. How would we back up Docker Swarm?
```sh
A. On a Swarm manager, make a backup of the contents of /etc/docker.
B. On a Swarm manager, make a backup of the contents of /var/lib/docker/swarm
C. Back up all of the containers in the swarm's tiered file systems.
D. On a Swarm manager, make a backup of the contents of /etc/docker/swarm.
```

The correct answer is **B. On a Swarm manager, make a backup of the contents of /var/lib/docker/swarm**.

Docker Swarm's state is stored in the `/var/lib/docker/swarm` directory on Swarm managers. This directory contains the data necessary for the Swarm cluster to operate, including cryptographic keys, certificates, and cluster configuration. Backing up this directory ensures that you can restore the cluster's state if needed.

### Suggested Documentation
For detailed information, you can refer to the official Docker documentation:
- [Docker Swarm Overview](https://docs.docker.com/engine/swarm/)
- [Backing Up and Restoring Docker Swarm](https://docs.docker.com/engine/swarm/admin_guide/)

These resources provide insights into managing and backing up Docker Swarm clusters effectively. Let me know if you'd like further assistance!
