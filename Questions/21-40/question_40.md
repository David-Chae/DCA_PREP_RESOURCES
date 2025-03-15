## Which of the following are insecure ways to allow a Docker client to authenticate against a registry that uses a self-signed certificate? (Choose two) 
1. Under /etc/docker/certs.d/, we add the self-signed certificate as a trusted registry certificate. 
2. We add the registry to insecure-registries in /etc/docker/daemon.json. 
3. We pass the --insecure-registry flag to the Docker daemon. 
4. We use the --skip-tls flag with the docker login.

The **insecure** ways to allow a Docker client to authenticate against a registry that uses a self-signed certificate are:  

✅ **We add the registry to `insecure-registries` in `/etc/docker/daemon.json`**  
✅ **We pass the `--insecure-registry` flag to the Docker daemon**  

### **Explanation:**  
- **Adding the registry to `insecure-registries`** or using `--insecure-registry` tells Docker **to ignore certificate validation** entirely.  
- This means Docker will **accept any certificate, even if it is untrusted or compromised**, making it **vulnerable to MITM (Man-in-the-Middle) attacks**.  

### **Why the Other Options Are Secure:**  
❌ **Under `/etc/docker/certs.d/`, we add the self-signed certificate as a trusted registry certificate.**  
- This is the **correct and secure** way to handle a self-signed certificate.  
- It explicitly tells Docker to **trust the specific certificate** rather than disabling security altogether.  

❌ **We use the `--skip-tls` flag with `docker login`.**  
- No such flag exists in Docker.  
- If it did, it would be insecure, but this is a **wrong option** in this context.  

### **Final Answer (Insecure Methods):**  
✅ **Adding the registry to `insecure-registries` in `/etc/docker/daemon.json`**  
✅ **Using the `--insecure-registry` flag**
