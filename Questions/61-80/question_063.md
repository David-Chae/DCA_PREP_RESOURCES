## 63. How can you enable Docker Content Trust (DCT) in Docker Community Edition (CE)?
```sh
A. Set "content-trust": true in /etc/docker/daemon.json
B. Set the DOCKER_CONTENT_TRUST environment variable to 1.
C. Set the CONTENT_ TRUST environment variable to 1.
D. Pass the --content-trust flag to dockerd
```

The correct answer is:  

**B. Set the DOCKER_CONTENT_TRUST environment variable to 1.**  

### Explanation:  
To enable **Docker Content Trust (DCT)** in Docker Community Edition (CE), you can set the **`DOCKER_CONTENT_TRUST`** environment variable to `1`. This ensures that Docker only pulls and pushes signed images, enforcing the use of trusted content.

### Why not the others?  
- **A**: The `daemon.json` file is used for configuring Docker daemon settings, but enabling DCT is done through the environment variable, not in this file.  
- **C**: There is no `CONTENT_TRUST` environment variable in Docker; it must be `DOCKER_CONTENT_TRUST`.  
- **D**: The `--content-trust` flag is not used for the `dockerd` command (Docker daemon); it is used with `docker` commands like `docker pull` or `docker push` to enforce content trust for specific operations.
