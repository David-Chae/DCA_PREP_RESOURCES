## 87. How can we guarantee that every node gets the updated unlock-key for a docker swarm?
A. Run the docker swarm unlock-key --rotate command on all manager nodes  
B. Generate a new key and save it at /etc/docker/swarm/unlock.key location  
C. Use the docker swarm unlock command  
D. Run the docker swarm unlock-key --rotate command on one manager node  

The correct answer is:

✔ **D. Run the docker swarm unlock-key --rotate command on one manager node**

---

### **Explanation:**

In Docker Swarm, **unlocking the swarm** is a crucial process to ensure the security of the swarm’s data. When the unlock key is rotated, all the manager nodes in the swarm will automatically receive the updated unlock key.

- The **`docker swarm unlock-key --rotate`** command is used to rotate the unlock key. Running this command on **one manager node** automatically propagates the new unlock key to all the manager nodes in the swarm.

---

### **Why the other options are incorrect:**

- **❌ Option A (`Run the docker swarm unlock-key --rotate command on all manager nodes`)**
  - It's unnecessary to run the command on **all** manager nodes. Running it on just **one manager node** is sufficient to update the key on all manager nodes.

- **❌ Option B (`Generate a new key and save it at /etc/docker/swarm/unlock.key location`)**
  - Docker does not expect you to manually generate or store the unlock key in a specific file location. Instead, the **`--rotate`** command automatically handles the management and distribution of the unlock key.

- **❌ Option C (`Use the docker swarm unlock command`)**
  - The **`docker swarm unlock`** command is used to unlock a swarm node but does not rotate or distribute the unlock key. To propagate the updated key, the **`--rotate`** command is necessary.

---

### **Final Answer:**
✔ **D. Run the docker swarm unlock-key --rotate command on one manager node**
