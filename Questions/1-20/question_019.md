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
