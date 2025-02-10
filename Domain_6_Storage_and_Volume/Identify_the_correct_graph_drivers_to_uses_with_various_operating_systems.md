# Identifying the Correct Graph Drivers for Various Operating Systems

## Introduction
Docker uses **storage drivers (graph drivers)** to manage container layer storage. The correct choice of graph driver depends on the **operating system** and **performance requirements**.

## 1. Default Graph Drivers by OS

| Operating System | Default Graph Driver | Alternative Options |
|-----------------|--------------------|--------------------|
| **Ubuntu (ext4, xfs)** | `overlay2` | `aufs`, `devicemapper`, `btrfs`, `zfs` |
| **Debian (ext4, xfs)** | `overlay2` | `aufs`, `btrfs`, `zfs` |
| **CentOS (xfs with ftype=1)** | `overlay2` | `devicemapper`, `btrfs` |
| **Red Hat Enterprise Linux (xfs with ftype=1)** | `overlay2` | `devicemapper`, `btrfs` |
| **Fedora (xfs with ftype=1)** | `overlay2` | `btrfs`, `zfs` |
| **Windows** | `windowsfilter` | `lcow` (for Linux containers on Windows) |

## 2. Recommended Graph Driver for Linux

The `overlay2` driver is the **default** and most **recommended** for modern Linux distributions because:
- It has better **performance** and **lower overhead** than `aufs`.
- It is supported by **all major Linux distributions**.
- It works well with **xfs** and **ext4** filesystems.

## 3. Recommended Graph Driver for Windows

For Windows containers:
- **Use `windowsfilter`** for **Windows-native** containers.
- **Use `lcow` (Linux Containers on Windows)** when running Linux containers on Windows.

## 4. Checking the Current Storage Driver
To check which storage driver Docker is using, run:
```sh
docker info | grep "Storage Driver"
```

## 5. Changing the Graph Driver
To change the storage driver:
1. Stop Docker:
   ```sh
   systemctl stop docker
   ```
2. Edit Docker daemon configuration (`/etc/docker/daemon.json`):
   ```json
   {
       "storage-driver": "overlay2"
   }
   ```
3. Restart Docker:
   ```sh
   systemctl start docker
   ```

## 6. Official Documentation
- [Docker Storage Drivers](https://docs.docker.com/storage/storagedriver/)
- [Configure OverlayFS](https://docs.docker.com/storage/storagedriver/overlayfs-driver/)
- [Docker on Windows Storage](https://docs.docker.com/docker-for-windows/)

## Conclusion
Choosing the correct graph driver is crucial for **performance**, **compatibility**, and **stability**. For Linux, `overlay2` is generally the best option, while Windows uses `windowsfilter` by default.
