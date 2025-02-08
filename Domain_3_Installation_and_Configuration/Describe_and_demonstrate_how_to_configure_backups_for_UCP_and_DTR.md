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
- UCP Backup and Restore: [https://docs.mirantis.com/ucp/current/admin/backups/](https://docs.mirantis.com/ucp/current/admin/backups/)
- DTR Backup and Restore: [https://docs.mirantis.com/dtr/current/admin/backups/](https://docs.mirantis.com/dtr/current/admin/backups/)
