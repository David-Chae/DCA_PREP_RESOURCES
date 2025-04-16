# Configure Backups for UCP and DTR
The **correct backup order** when you're running Docker Enterprise components (UCP, DTR, Swarm) is:
---

## ✅ **Backup Order:**

1. **Swarm**  
   - Backup `/var/lib/docker/swarm`  
   - Swarm contains the Raft data (cluster state, services, secrets, etc.)

2. **UCP** (Universal Control Plane)  
   - UCP stores cluster config, RBAC, certificates, etc.  
   - Use the `docker container run ... backup` command provided in UCP docs.

3. **DTR** (Docker Trusted Registry)  
   - Backup DTR metadata, images, config  
   - Use the `docker container run ... backup` command for DTR as well.

---

## 📌 Why this Order?

- Swarm is the **foundation**, and both UCP and DTR rely on it.
- UCP is deployed **on top of Swarm**, and DTR is often integrated with UCP.
- So you want to **restore in the reverse order**:
  
  > **Restore Order: Swarm → UCP → DTR**

---

Would you like a quick command cheat sheet for each backup step?
## Official Documentation
- Mirantis Doc Swarm Backup : [https://docs.mirantis.com/mke/3.8/ops/disaster-recovery/back-up-swarm.html]
- Mirantis Doc Swarm Restore : [https://docs.mirantis.com/mke/3.8/ops/disaster-recovery/restore-swarm.html]
- MKE UCP Backup and Restore: [MKE UCP Backup procedure](https://docs.mirantis.com/mke/3.8/ops/disaster-recovery/back-up-mke/backup-procedure.html)
- MSR DTR Backup : [Create an MSR backup](https://docs.mirantis.com/msr/3.1/ops/disaster-recovery/create-a-backup.html)
- MSR DTR Restore : [Restore from an MSR backup](https://docs.mirantis.com/msr/3.1/ops/disaster-recovery/restore-from-backup.html)
