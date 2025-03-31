## What volume driver allows you to use SSH to create and access external storage shared across a Docker Swarm cluster? 
A. overlay 
B. vieux/sshfs 
C. overlay2 
D. devicemapper 

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







## How should we permit users to interact with the Docker daemon on a machine without giving them unnecessary additional access? 
A. Give the user the root user credentials to run the docker commands as root. 
B. Give the user the ability to run docker commands with sudo. 
C. Add the user to the docker group. 
D. Have them log in as the docker user. 

The correct answer is:  

✅ **"Add the user to the docker group."**  

---

### **Explanation:**  
In Docker, the **Docker daemon (`dockerd`)** runs as **root**, but allowing every user to run commands as root is a security risk. The best way to **grant controlled access** to Docker is by **adding the user to the `docker` group**.  

#### **Steps to Add a User to the Docker Group:**  
1. **Check if the `docker` group exists:**  
   ```sh
   cat /etc/group | grep docker
   ```
   If it doesn't exist, create it:  
   ```sh
   sudo groupadd docker
   ```

2. **Add the user to the `docker` group:**  
   ```sh
   sudo usermod -aG docker username
   ```

3. **Apply the group change (log out and log back in, or run):**  
   ```sh
   newgrp docker
   ```

4. **Verify that the user can run Docker commands without `sudo`:**  
   ```sh
   docker ps
   ```

---

### **Why the Other Options Are Incorrect?**  

❌ **"Give the user the root user credentials to run the docker commands as root."**  
- **Bad practice!** Giving out **root credentials** exposes the entire system to security risks.  

❌ **"Give the user the ability to run docker commands with sudo."**  
- While using **`sudo`** works, it **requires entering a password** each time, which is inconvenient.  

❌ **"Have them log in as the docker user."**  
- There is **no default `docker` user** in Linux. Docker runs as a **daemon**, not as a separate user account.  

---

### **Summary:**  
To safely grant users access to Docker **without giving them unnecessary privileges**, **add them to the `docker` group**.






## Which approach is the most secure for a Docker client to authenticate with a registry that employs a self-signed certificate? 
1. We add the registry to the insecure-registries list in /etc/docker/daemon.json. 
2. docker login --accept-cert 
3. docker login --trust-ca 
4. Under /etc/docker/certs.d/, we add the self-signed certificate as a trusted registry certificate.

The most secure approach is:

✅ **"Under /etc/docker/certs.d/, we add the self-signed certificate as a trusted registry certificate."**

---

### **Explanation:**  
To securely authenticate with a Docker registry that uses a self-signed certificate, the most secure approach is to **explicitly add the self-signed certificate** to the list of trusted certificates. This ensures that Docker clients can securely communicate with the registry while avoiding insecure communication or bypassing SSL verification.

1. **Add the self-signed certificate** to the **`/etc/docker/certs.d/`** directory:
   - Place the self-signed certificate (e.g., `myregistry.crt`) in the `/etc/docker/certs.d/` directory on the Docker client.
   - The path should be `/etc/docker/certs.d/<registry-domain>/ca.crt`, where `<registry-domain>` is the domain of your registry.
   
   Example:
   ```sh
   sudo mkdir -p /etc/docker/certs.d/myregistry.com
   sudo cp myregistry.crt /etc/docker/certs.d/myregistry.com/ca.crt
   ```

2. **Restart Docker** to apply the changes:
   ```sh
   sudo systemctl restart docker
   ```

This method ensures that Docker treats the self-signed certificate as **trusted** and establishes secure communication without bypassing security.

---

### **Why the Other Options Are Not Recommended:**  

❌ **"We add the registry to the insecure-registries list in /etc/docker/daemon.json."**  
- Adding a registry to the **`insecure-registries`** list allows Docker to communicate with the registry **without certificate validation**, which is **insecure** and should be avoided, especially with self-signed certificates.

❌ **"docker login --accept-cert"**  
- Docker doesn't have an `--accept-cert` flag, and this approach is **not a standard or secure way** of accepting certificates.

❌ **"docker login --trust-ca"**  
- Similarly, there is **no `--trust-ca` flag** for the `docker login` command. This is not a valid or recommended option.

---

### **Summary:**  
The most secure method for Docker to authenticate with a registry using a self-signed certificate is to **add the certificate as a trusted certificate** under `/etc/docker/certs.d/`.










## What would be the best way to start a new swarm cluster? 
1. Run docker cluster create. 
2. Start dockerd with the swarm=true flag. 
3. Run docker swarm init. 
4. Use a Docker compose file that defines a new cluster.

The correct answer is:

✅ **"Run docker swarm init."**

---

### **Explanation:**  
To **initialize** a new Docker Swarm cluster, the command **`docker swarm init`** is used on the **manager node**. This command sets up the current machine as a **Swarm manager** and prepares it to start managing the swarm cluster.

#### **Steps:**
1. On the manager node, run:
   ```sh
   docker swarm init
   ```
2. This will output a **join token** that worker nodes can use to join the swarm.
   
3. To join worker nodes to the swarm, run the **join command** on each worker node:
   ```sh
   docker swarm join --token <SWARM_JOIN_TOKEN> <MANAGER_NODE_IP>:2377
   ```

After these steps, your Docker Swarm cluster is ready to use!

---

### **Why the Other Options Are Incorrect:**

❌ **"Run docker cluster create."**  
- There is no `docker cluster create` command. Swarm initialization is done with `docker swarm init`.

❌ **"Start dockerd with the swarm=true flag."**  
- Docker does not







## Sally wants to prevent Docker Swarm encryption keys from storing insecurely on her swarm managers. How can she tackle enforcing a lock on the swarm cluster? 
1. Sally cannot do this because Docker does not offer this functionality. 
2. Sally can use the --autolock=true flag with the docker swarm update command. 
3. Sally can locate the critical files after the installation and delete them. 
4. The autolock feature must be turned on when the cluster is initialized and cannot be enabled after the fact.

The correct answer is:

✅ **"Sally can use the --autolock=true flag with the docker swarm update command."**

---

### **Explanation:**

In Docker Swarm, **autolock** is a feature that encrypts the swarm's **manager node encryption keys**, ensuring that they are not stored insecurely on the swarm managers. The **autolock** feature prevents unauthorized access to the keys and ensures they are only accessible with the proper unlocking mechanism.

1. **To enable autolock** after initializing the swarm:
   - Sally can use the `docker swarm update --autolock=true` command to enforce autolock on her swarm cluster, ensuring the encryption keys are locked.

   Example:
   ```sh
   docker swarm update --autolock=true
   ```

2. **To unlock the swarm** when needed:
   - The `docker swarm unlock` command is required to unlock the swarm, and it will prompt for the unlock key when performing any operation on the swarm that requires access to the keys.

---

### **Why the Other Options Are Incorrect:**

❌ **"Sally cannot do this because Docker does not offer this functionality."**  
- This is incorrect because Docker **does** offer the `--autolock` feature to secure the swarm encryption keys.

❌ **"Sally can locate the critical files after the installation and delete them."**  
- Simply deleting files is not a secure or recommended method. It would not ensure the proper encryption or safety of the swarm keys. Docker provides a more secure mechanism with **autolock**.

❌ **"The autolock feature must be turned on when the cluster is initialized and cannot be enabled after the fact."**  
- This is **incorrect**. The **autolock feature can be enabled at any time** after the swarm has been initialized, using the `docker swarm update --autolock=true` command. It is **not limited to initialization**.

---

### **Summary:**

To ensure Docker Swarm encryption keys are stored securely and locked on the managers, Sally should use the `docker swarm update --autolock=true` command.







## In Kubernetes, which of the following is needed to expand a PersistentVolumeClaim? 
1. A StorageClass with allowVolumeExpansion=true.
2. A StorageClass with expandable=true.
3. A PersistentVolume with allowVolumeExpansion=true.
4. A Storage driver that supports volume expansion. 

The correct answer is:

✅ **"A StorageClass with allowVolumeExpansion=true."**

---

### **Explanation:**

In Kubernetes, **expanding a PersistentVolumeClaim (PVC)** requires the **StorageClass** associated with the PVC to have **`allowVolumeExpansion: true`**. This allows the PVC to request a larger volume if the underlying **PersistentVolume (PV)** supports expansion.

#### **Steps to enable volume expansion:**
1. **Ensure the StorageClass supports expansion**:
   - The **StorageClass** used by the PVC must have the `allowVolumeExpansion` field set to `true`.
   - Example of a StorageClass that allows expansion:
     ```yaml
     kind: StorageClass
     apiVersion: storage.k8s.io/v1
     metadata:
       name: standard
     provisioner: kubernetes.io/aws-ebs
     allowVolumeExpansion: true
     ```

2. **Ensure the underlying volume supports expansion**:
   - The **Storage driver** and the underlying **PersistentVolume** (e.g., an EBS volume) must support volume expansion.
   
3. **Update the PersistentVolumeClaim**:
   - Once the StorageClass is set up correctly, you can increase the size of the PVC by modifying the `spec.resources.requests.storage` field on the PVC, and Kubernetes will attempt to resize the volume if the underlying storage supports it.

---

### **Why the Other Options Are Incorrect:**

❌ **"A StorageClass with expandable=true."**  
- This is not a valid field in the Kubernetes StorageClass specification. The correct field is `allowVolumeExpansion`.

❌ **"A PersistentVolume with allowVolumeExpansion=true."**  
- The **PersistentVolume** itself does not have an `allowVolumeExpansion` field. The **StorageClass** is responsible for enabling volume expansion, not the PV.

❌ **"A Storage driver that supports volume expansion."**  
- While it is true that the underlying **storage driver** must support volume expansion, the **StorageClass** must specifically have `allowVolumeExpansion: true` for Kubernetes to allow expanding the PVC.

---

### **Summary:**
To expand a PersistentVolumeClaim in Kubernetes, you need a **StorageClass with `allowVolumeExpansion=true`** and an underlying storage driver that supports volume expansion.











## Which commands would we use to view a container's logs? 
1. sudo journalctl -u docker
2. docker logs <container>
3. docker service logs <service>
4. docker container get-log

The correct answers are:

✅ **`docker logs <container>`**

✅ **`docker service logs <service>`**

---

### **Explanation:**

1. **`docker logs <container>`**:
   - This command is used to view the logs of a **specific container**. You replace `<container>` with the container's name or ID.
   - Example:
     ```sh
     docker logs my-container
     ```

2. **`docker service logs <service>`**:
   - This command is used to view the logs for a **service** in Docker Swarm. It allows you to see logs for all the tasks that make up the service.
   - Example:
     ```sh
     docker service logs my-service
     ```

---

### **Why the Other Options Are Incorrect:**

❌ **`sudo journalctl -u docker`**:  
- This command is used to view **system logs** related to the Docker daemon, not the logs of a specific container or service. It's typically used for troubleshooting Docker daemon-related issues, not for container logs.

❌ **`docker container get-log`**:  
- This is **not a valid Docker command**. The correct command for viewing logs is `docker logs <container>`, not `docker container get-log`.

---

### **Summary:**

To view a container's logs, use `docker logs <container>`. For service logs in Docker Swarm, use `docker service logs <service>`.









## How would we keep track of changes made to an image in source control (i.e., git)? 
1. We would use Docker Trusted Registry (DTR) to handle this.
2. Maintain tags for each new version within the Docker registry.
3. We would push the image layers to a source control repository.
4. We would store the Dockerfile in source control.

The correct answer is:

✅ **We would store the Dockerfile in source control.**

---

### **Explanation:**

- **Storing the Dockerfile in source control (e.g., Git)** is the best practice for tracking changes made to an image. The Dockerfile contains the instructions for building the Docker image, so keeping it in source control allows you to track changes in the image's configuration, dependencies, and setup over time.

- By versioning the Dockerfile in a repository, you can trace the exact changes that have been made to the Docker image, ensuring a transparent and reproducible build process. This is particularly useful in collaboration and CI/CD (Continuous Integration/Continuous Delivery) workflows.

---

### **Why the Other Options Are Incorrect:**

❌ **"We would use Docker Trusted Registry (DTR) to handle this."**
- Docker Trusted Registry (DTR) is useful for storing and managing Docker images in a private registry, but it does not provide version tracking or history of changes like source control (e.g., Git) does for Dockerfiles.

❌ **"Maintain tags for each new version within the Docker registry."**
- While tags help identify different versions of an image, they do not give you a detailed history of the specific changes made to the image over time. Tags are useful for versioning but do not provide the full context of what has changed inside the image.

❌ **"We would push the image layers to a source control repository."**
- Pushing image layers (i.e., the binary data representing different parts of the Docker image) to source control is inefficient and unnecessary. Source control systems like Git are designed to handle text files (like the Dockerfile), not large binary files, and this would lead to bloated repositories.

---

### **Summary:**

To keep track of changes made to an image in source control, the best approach is to store the **Dockerfile** in a Git repository. This allows for effective versioning and tracking of changes in the image's build process.
