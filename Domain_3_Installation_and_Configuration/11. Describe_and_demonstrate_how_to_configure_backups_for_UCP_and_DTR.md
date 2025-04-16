# Configure Backups for UCP and DTR
The **correct backup order** when you're running Docker Enterprise components (UCP, DTR, Swarm) is:
---

## ✅ **Backup Order:**

1. **Swarm**  
   - Backup `/var/lib/docker/swarm`  
   - Swarm contains the Raft data (cluster state, services, secrets, etc.)

 **Swarm Backup Contents**

| **Data**            | **Backed Up** | **Description**                                                                 |
|---------------------|---------------|---------------------------------------------------------------------------------|
| **Raft keys**       | Yes           | Keys used to encrypt communication between Swarm nodes and to encrypt and decrypt raft logs |
| **Membership**      | Yes           | List of the nodes in the cluster                                               |
| **Services**        | Yes           | Stacks and services stored in Swarm mode                                       |
| **Overlay networks**| Yes           | Overlay networks created on the cluster                                        |
| **Configs**         | Yes           | Configs created in the cluster                                                 |
| **Secrets**         | Yes           | Secrets saved in the cluster                                                   |
| **Swarm unlock key**| No            | Secret key needed to unlock a manager after its Docker daemon restarts         |



2. **UCP** (Universal Control Plane)  
   - UCP stores cluster config, RBAC, certificates, etc.  
   - Use the `docker container run ... backup` command provided in UCP docs.

```markdown
# 📦 MKE Backup Contents

> The following backup contents are stored in a `.tar` file.  
> Backups contain MKE configuration metadata for recreating configurations such as **LDAP**, **SAML**, and **RBAC**.

---

## ✅ Backed Up

| **Data**              | **Backed up** | **Description**                                                                 |
|-----------------------|---------------|---------------------------------------------------------------------------------|
| **Configurations**    | Yes           | MKE configurations, including MCR license, Swarm, and client CAs.              |
| **Access control**    | Yes           | Swarm resource permissions for teams, including collections, grants, and roles.|
| **Certificates/Keys** | Yes           | Certificates, public and private keys used for authentication and mTLS.        |
| **Metrics data**      | Yes           | Monitoring data gathered by MKE.                                               |
| **Organizations**     | Yes           | Users, teams, and organizations.                                               |
| **Volumes**           | Yes           | All MKE-named volumes including component certs and data.                      |

---

## ❌ Not Backed Up

| **Data**               | **Backed up** | **Description**                                                                 |
|------------------------|---------------|---------------------------------------------------------------------------------|
| **Overlay networks**   | No            | Swarm mode overlay network definitions, including port info.                   |
| **Configs, secrets**   | No            | MKE configs and secrets — use a **Swarm backup** to save these.                |
| **Services**           | No            | MKE stacks/services are in Swarm or SCM.                                       |
| **ucp-metrics-data**   | No            | Metrics server data.                                                           |
| **ucp-node-certs**     | No            | Certs for locking down MKE system components.                                  |
| **Routing mesh**       | No            | Interlock layer 7 ingress config. Manual backup/restore process is required.   |
```

Let me know if you'd like to download it or include links/document references!


3. **DTR** (Docker Trusted Registry)  
   - Backup DTR metadata, images, config  
   - Use the `docker container run ... backup` command for DTR as well.

The following table describes the various data types that **Mirantis Secure Registry (MSR)** manages, and indicates which data types are backed up during **automatic** or **manual** backup operations.

| **Data**                        | **Automatic Backup** | **Manual Backup** | **Description**                                                                 |
|----------------------------------|----------------------|-------------------|---------------------------------------------------------------------------------|
| **Configurations**               | Yes                  | Yes               | MSR settings.                                                                  |
| **Repository metadata**          | Yes                  | Yes               | Metadata about repositories, charts, and images (e.g., architecture, size).    |
| **Access control to repos/images** | Yes               | Yes               | Permissions for teams and repositories.                                        |
| **Notary data**                  | Yes                  | Yes               | Signatures and digests for signed images.                                      |
| **Scan results**                 | Yes                  | Yes               | Information about security vulnerabilities in images.                          |
| **Image and chart content**      | Yes (when `fullBackup` is `true`) | No     | Images and charts stored in MSR; must be backed up separately if needed.       |
| **Users, orgs, teams**           | Yes                  | Yes               | Data related to users, organizations, and teams.                               |
| **Vulnerability database**       | No                   | No                | Can be re-downloaded after restore; not included in backup.                    |


---

## 📌 Why this Order?

- Swarm is the **foundation**, and both UCP and DTR rely on it.
- UCP is deployed **on top of Swarm**, and DTR is often integrated with UCP.
- So you want to **restore in the reverse order**:
  
  > **Restore Order: Swarm → UCP → DTR**

---

## Quick command cheat sheet for each backup step

### To back up Swarm:

1. Stop Docker on the manager node before backing up the data, so that no data is changed during the backup:
```bash
systemctl stop docker
```

2. Back up the /var/lib/docker/swarm directory:
```bash
tar cvzf "/tmp/swarm-$(hostname -s)-$(date +%s%z).tgz" /var/lib/docker/swarm/
```

3. If auto-lock is enabled, unlock the swarm:
```bash
docker swarm unlock
```

4. Restart Docker on the manager node:
```
systemctl start docker
```


### To backup UCP (MKE)

1. "Run the mirantis/ucp:3.8.4 backup command on a single MKE manager node, including the --file and --include-logs options.
This creates a .tar archive with the contents of all volumes used by MKE and streams it to stdout. Replace 3.8.4 with the version you are currently running."
```bash
docker container run \
  --rm \
  --log-driver none \
  --name ucp \
  --volume /var/run/docker.sock:/var/run/docker.sock \
  --volume /tmp:/backup \
  mirantis/ucp:3.8.4 backup \
  --file mybackup.tar \
  --passphrase "secret12chars" \
  --include-logs=false
```

If you are running MKE with Security-Enhanced Linux (SELinux) enabled, which is typical for RHEL hosts, include --security-opt label=disable in the docker command, replacing 3.8.4 with the version you are currently running:

```bash
docker container run \
  --rm \
  --log-driver none \
  --security-opt label=disable \
  --name ucp \
  --volume /var/run/docker.sock:/var/run/docker.sock \
  mirantis/ucp:3.8.4 backup \
  --passphrase "secret12chars" > /tmp/mybackup.tar
```

#### Create a backup using the MKE web UI¶

Log in to the MKE web UI.
In the left-side navigation panel, navigate to Admin Settings.
Click Backup.
Initiate an immediate backup by clicking Backup Now.
The MKE web UI also provides the following options:
Display the status of a running backup
Display backup history
Display backup outcome

#### Create, list, and retrieve backups using the MKE API
The MKE API provides three endpoints for managing MKE backups:
/api/ucp/backup
/api/ucp/backups
/api/ucp/backup/{backup_id}
You must be an MKE administrator to access these API endpoints.


Here’s your content formatted as a Markdown (`.md`) file:


#### 📦 Creating a Backup Using the MKE API

You can create a backup using the `POST: /api/ucp/backup` endpoint.

This JSON endpoint accepts the following arguments:

| **Field Name** | **JSON Data Type** | **Description**                                           |
|----------------|--------------------|-----------------------------------------------------------|
| `passphrase`   | String             | Encryption passphrase                                     |
| `noPassphrase` | Boolean            | Whether a passphrase is used (`true` to disable)          |
| `fileName`     | String             | Backup file name                                          |
| `includeLogs`  | Boolean            | Whether to include a log file in the backup               |
| `hostPath`     | String             | File system location for storing the backup               |

---

**✅ Response Codes**

- `200`: Success
- `400`: Malformed request (payload fails validation)
- `500`: Internal server error

---

**📋 Example API Call**

```bash
curl -sk -H "Authorization: Bearer $AUTHTOKEN" https://$UCP_HOSTNAME/api/ucp/backup \
  -X POST \
  -H "Content-Type: application/json" \
  --data '{"passphrase": "secret12chars", "includeLogs": true, "fileName": "backup1.tar", "logFileName": "backup1.log", "hostPath": "/tmp"}'
```

Replace `$AUTHTOKEN` and `$UCP_HOSTNAME` with your actual UCP authentication token and host name.

### To backup DTR (MSR)

#### Back up MSR metadata
Use the msr backup command to create a backup of the MSR metadata. The command is present in any API Pod and can be run using the kubectl exec command.
An example follows of how to create a backup for an MSR installation named mymsr. The backup contents are streamed to standard output, which is redirected locally to the file backup.tar.
```
kubectl exec -i deployment/mymsr-api -- msr backup - > backup.tar

# Optionally, you can exclude scanned images and layers from the backup by adding the --ignore-scan-data flag to the command:

kubectl exec -i deployment/msr-api -- msr backup --ignore-scan-data - > backup.tar
```

#### Back up MSR image content

**Backing Up MSR Images and Charts (PersistentVolume Example)**
As you can configure **MSR** (Mirantis Secure Registry) for several types of storage backends, the method for backing up images and charts will vary. The example below is specific to the **PersistentVolume** storage backend. 
> If you are using a different storage backend (e.g., AWS EBS, GCP Persistent Disk, etc.), you should follow the backup practices recommended for that system.
---
Where Are Images and Charts Stored?
When MSR is configured with a `PersistentVolume`, images and charts are stored on the **local file system** or on **mounted network storage**.
---
**Steps to Back Up MSR Image and Chart Data**
1. Get the PersistentVolumeClaim (PVC)
```bash
kubectl get persistentvolumeclaim msr
```
Example output:
```
NAME   STATUS   VOLUME                                     CAPACITY   ACCESS MODES   STORAGECLASS   AGE
msr    Bound    pvc-36c236cb-d5f2-431d-aeb7-76c0de49b17b   10Gi       RWX            standard        17h
```
---
2. Get the Host Path of the Volume
```bash
kubectl get persistentvolume pvc-36c236cb-d5f2-431d-aeb7-76c0de49b17b -o jsonpath='{.spec.hostPath.path}'
```
This returns:
```bash
/tmp/hostpath-provisioner/myns0/msr
```
---
3. Create a Tar Archive of the MSR Data
```bash
sudo tar -cvf /tmp/msr-backup.tar /tmp/hostpath-provisioner/myns0/msr
```
> Replace `/tmp/msr-backup.tar` and the path based on your actual environment.
This command creates a `.tar` archive that can be stored for backup or transferred elsewhere.
---

**Notes**

- Ensure you have **sufficient disk space** for the archive.
- You may want to **stop MSR temporarily** during backup to avoid changes while archiving (not mandatory for all environments).
- This is for **image and chart content only** ??use `dtr backup` to get metadata and config.



## Official Documentation
- Mirantis Doc Swarm Backup : [https://docs.mirantis.com/mke/3.8/ops/disaster-recovery/back-up-swarm.html]
- Mirantis Doc Swarm Restore : [https://docs.mirantis.com/mke/3.8/ops/disaster-recovery/restore-swarm.html]
- MKE UCP Backup and Restore: [MKE UCP Backup procedure](https://docs.mirantis.com/mke/3.8/ops/disaster-recovery/back-up-mke/backup-procedure.html)
- MSR DTR Backup : [Create an MSR backup](https://docs.mirantis.com/msr/3.1/ops/disaster-recovery/create-a-backup.html)
- MSR DTR Restore : [Restore from an MSR backup](https://docs.mirantis.com/msr/3.1/ops/disaster-recovery/restore-from-backup.html)
