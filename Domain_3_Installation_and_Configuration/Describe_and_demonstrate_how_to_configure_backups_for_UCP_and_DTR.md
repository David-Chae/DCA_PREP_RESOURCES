# Configure Backups for UCP and DTR

### Backup UCP
```sh
# Create a backup directory
mkdir -p ~/ucp-backup

# Backup UCP
docker container run --rm \
  --name ucp \
  -v /var/run/docker.sock:/var/run/docker.sock \
  -v ~/ucp-backup:/backup \
  docker/ucp backup --file /backup/ucp-backup.tar
```

### Restore UCP
```sh
# Restore UCP from backup
docker container run --rm \
  --name ucp \
  -v /var/run/docker.sock:/var/run/docker.sock \
  -v ~/ucp-backup:/backup \
  docker/ucp restore --file /backup/ucp-backup.tar
```

### Backup DTR
```sh
# Backup DTR
docker run --rm \
  -v /var/lib/docker:/var/lib/docker \
  -v ~/dtr-backup:/backup \
  docker/dtr backup --ucp-url https://<UCPManagerIP> --ucp-username admin --file /backup/dtr-backup.tar
```

### Restore DTR
```sh
# Restore DTR from backup
docker run --rm \
  -v /var/lib/docker:/var/lib/docker \
  -v ~/dtr-backup:/backup \
  docker/dtr restore --ucp-url https://<UCPManagerIP> --ucp-username admin --file /backup/dtr-backup.tar
```

## Official Documentation
- Mirantis Doc Swarm Backup : [https://docs.mirantis.com/mke/3.8/ops/disaster-recovery/back-up-swarm.html]
- Mirantis Doc Swarm Restore : [https://docs.mirantis.com/mke/3.8/ops/disaster-recovery/restore-swarm.html]
- MKE UCP Backup and Restore: [MKE UCP Backup procedure](https://docs.mirantis.com/mke/3.8/ops/disaster-recovery/back-up-mke/backup-procedure.html)
- MSR DTR Backup : [Create an MSR backup](https://docs.mirantis.com/msr/3.1/ops/disaster-recovery/create-a-backup.html)
- MSR DTR Restore : [Restore from an MSR backup](https://docs.mirantis.com/msr/3.1/ops/disaster-recovery/restore-from-backup.html)
