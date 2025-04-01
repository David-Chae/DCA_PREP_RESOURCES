## What volume driver allows you to use SSH to create and access external storage shared across a Docker Swarm cluster? 
```sh
A. overlay 
B. vieux/sshfs 
C. overlay2 
D. devicemapper 
```
The correct answer is:  

✅ **B. vieux/sshfs**  

---

### **Explanation:**  
The **`vieux/sshfs`** volume driver allows Docker to use **SSHFS (SSH Filesystem)** for mounting external storage across a **Docker Swarm cluster**. This enables secure remote access to shared storage using SSH.  

#### **Key Features of `vieux/sshfs`:**  
- Uses **SSHFS** to mount remote directories as Docker volumes.  
- Allows containers to share storage **across multiple Swarm nodes**.  
- Securely connects to external storage via **SSH authentication**.  

#### **Example Usage:**
To create a volume using `vieux/sshfs`:  
```sh
docker volume create \
  --driver vieux/sshfs \
  -o sshcmd=user@remote-server:/path/to/data \
  -o password=mysecurepassword \
  my-ssh-volume
```
Then, use it in a container:  
```sh
docker run -v my-ssh-volume:/data my-container
```

---

### **Why the Other Options Are Incorrect?**  

❌ **A. overlay**  
- `overlay` is a **storage driver**, not a volume driver. It is used for Docker’s **union filesystem**, not for shared storage.  

❌ **C. overlay2**  
- `overlay2` is an **improved version** of `overlay`, but it is also a storage driver, not a volume driver.  

❌ **D. devicemapper**  
- `devicemapper` is a **storage driver** that manages container **layered storage** but does not provide external shared storage across a Swarm cluster.  

---

### **Summary:**  
To **use SSHFS for shared storage in Docker Swarm**, the correct **volume driver** is **`vieux/sshfs`**.
