What volume driver allows you to create and access external storage that can be shared across a Docker Swarm cluster using SSH?
```
devicemapper
overlay
overlay2
vieux/sshfs
```

The correct answer is **4. vieux/sshfs**.

### Explanation:
- **vieux/sshfs** is a volume driver that allows you to mount remote file systems over SSH. It can be used in a Docker Swarm cluster to create and access external storage that can be shared across multiple nodes. This is done by mounting an SSH-based file system (using SSHFS) and making it available as a Docker volume. 

- **devicemapper**, **overlay**, and **overlay2** are all storage drivers for managing container filesystem layers locally on nodes in the Docker engine. They are not used for accessing remote storage over SSH.

### To summarize:
- **vieux/sshfs** allows sharing external storage across nodes in a Docker Swarm cluster using SSH. It enables you to mount remote directories and use them as volumes for Docker containers.
