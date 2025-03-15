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
