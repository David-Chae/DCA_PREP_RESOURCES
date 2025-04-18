# Configuring DeviceMapper Storage Driver in Docker

## Introduction
`devicemapper` is a storage driver that uses the **Linux Device Mapper** framework to manage snapshots and thin provisioning. It is commonly used on **Red Hat Enterprise Linux (RHEL)** and **CentOS**.

## 1. Checking the Current Storage Driver
To determine the current storage driver in use, run:
```sh
docker info | grep "Storage Driver"
```

## 2. Configuring Docker to Use `devicemapper`

### a. Stop Docker Service
```sh
systemctl stop docker
```

### b. Edit Docker Daemon Configuration
Modify `/etc/docker/daemon.json` to set `devicemapper` as the storage driver:
```json
{
    "storage-driver": "devicemapper",
    "storage-opts": [
        "dm.directlvm_device=/dev/sdX", 
        "dm.thinpooldev=/dev/mapper/docker-thinpool"
    ]
}
```
> Replace `/dev/sdX` with the correct block device.

### c. Set Up Direct-LVM Mode
1. Create a physical volume:
   ```sh
   pvcreate /dev/sdX
   ```
2. Create a volume group:
   ```sh
   vgcreate docker /dev/sdX
   ```
3. Create a thin pool:
   ```sh
   lvcreate --wipesignatures y -n thinpool docker -L 95%VG
   lvcreate --wipesignatures y -n thinpoolmeta docker -L 5%VG
   lvconvert -y --zero n -c 512K --thinpool docker/thinpool --poolmetadata docker/thinpoolmeta
   ```
4. Configure automatic pool resizing:
   ```sh
   cat > /etc/lvm/profile/docker-thinpool.profile <<EOF
   activation {
       thin_pool_autoextend_threshold=80
       thin_pool_autoextend_percent=20
   }
   EOF
   lvchange --metadataprofile docker-thinpool docker/thinpool
   ```
5. Restart Docker:
   ```sh
   systemctl start docker
   ```

## 3. Verifying the Configuration
Run:
```sh
docker info | grep "Storage Driver"
docker info | grep "Pool Name"
```
It should display `devicemapper` as the storage driver and `docker-thinpool` as the pool name.

## 4. Official Documentation
- [Docker DeviceMapper Storage Driver](https://docs.docker.com/storage/storagedriver/device-mapper-driver/)
- [Configuring Direct-LVM](https://docs.docker.com/storage/storagedriver/device-mapper-driver/#configure-direct-lvm-mode)

## Conclusion
`devicemapper` provides **thin provisioning and snapshot capabilities** for Docker storage. Proper configuration with **direct-lvm mode** ensures optimal performance and stability.
