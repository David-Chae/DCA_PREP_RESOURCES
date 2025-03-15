## How can you enable Docker Content Trust (DCT) in Docker Community Edition (CE)? 
1. Set "content-trust": true in /etc/docker/daemon.json.
2. Set the DOCKER_CONTENT_TRUST environment variable to 1.
3. Set the CONTENT_TRUST environment variable to 1.

The correct way to enable **Docker Content Trust (DCT)** in Docker Community Edition (CE) is:

✅ **Set the DOCKER_CONTENT_TRUST environment variable to 1.**

### **Explanation:**
- **Docker Content Trust (DCT)** ensures that images pulled from or pushed to a registry are signed, verifying their authenticity and integrity. 
- The `DOCKER_CONTENT_TRUST` environment variable controls whether content trust is enabled. When set to `1`, it enables DCT for operations like `docker pull` and `docker push`.

### **Other Options:**

❌ **"Set 'content-trust': true in /etc/docker/daemon.json."**  
- This setting is **not valid** in the `daemon.json` configuration file for Docker CE. DCT is controlled via the environment variable, not the daemon configuration.

❌ **"Set the CONTENT_TRUST environment variable to 1."**  
- The environment variable **should be `DOCKER_CONTENT_TRUST`**, not `CONTENT_TRUST`.

### **Final Answer:**
To enable Docker Content Trust, set:

```
DOCKER_CONTENT_TRUST=1
```
