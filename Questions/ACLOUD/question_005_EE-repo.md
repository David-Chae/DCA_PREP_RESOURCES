## Where can we find a repository URL for installing the Docker Enterprise Edition (EE)?

Docker Hub. (https://docs.mirantis.com/mke/3.8/install/install-mke-image.html)
 
To install MKE:

Log in to the target host using Secure Shell (SSH).

Pull the latest version of MKE:
```
docker image pull mirantis/ucp:3.8.4
```
Install MKE:
```
docker container run --rm -it --name ucp \
-v /var/run/docker.sock:/var/run/docker.sock \
mirantis/ucp:3.8.4 install \
--host-address <node-ip-address> \
--interactive
```

The ucp install command runs in interactive mode, prompting you for the necessary configuration values. For more information about the ucp install command, including how to install MKE on a system with SELinux enabled, refer to the MKE Operations Guide: mirantis/ucp install.

---

## SAMPLE QUESTION : Where can we find a repository URL for installing the Docker Enterprise Edition (EE)?
```
1. Docker Trusted Registry
2. Docker Marketplace
3. Docker Hub
4. Docker Enterprise Hub
```

The correct answer is:

> ✅ **3. DockerHub**

---

### 🔍 Explanation:

Let’s break down each option:

#### 1. **Docker Trusted Registry**
- ❌ Incorrect.  
  This is a **private image registry** used to **store and manage container images securely**, but **not for installing Docker EE** itself.

#### 2. **Docker Marketplace**
- ❌ Incorrect.  
  Docker Marketplace is for **browsing and acquiring containerized apps**, not the Docker EE installation packages or repository URLs.

#### 3. **Docker Hub**
- ✅ **Correct.**  
  Docker Hub has mirantis/ucp repository with tag 3.8.4 which can be pulled.

#### 4. **Docker Enterprise Hub**
❌ Incorrect.  
  There is no such as thing as Docker Enterprise Hub.
 
