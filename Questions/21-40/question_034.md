## We have some containerized software that needs to reference the hostname of the node the software runs on. Which of the following commands will let us pass the node hostname as an environment variable into each task in a service? 
1. docker service create --env NODE_HOSTNAME="{{Hostname}}" nginx
2. docker service create -e NODE_HOSTNAME nginx
3. docker service create --env NODE_HOSTNAME="{{.Node.Hostname}}" nginx
4. docker service create --pass-node-hostname=true nginx

The correct answer is:  

✅ **`docker service create --env NODE_HOSTNAME="{{.Node.Hostname}}" nginx`**  

### **Explanation:**  
- The **`--env`** or **`-e`** flag in Docker is used to **set environment variables** when creating a service.  
- The **`{{.Node.Hostname}}`** is a **Docker Swarm template variable** that dynamically **retrieves the hostname** of the node where the task is running.  
- This allows each task in the service to **automatically receive** the correct node hostname as an environment variable.

### **Why the Other Options Are Incorrect:**
1. **`docker service create --env NODE_HOSTNAME="{{Hostname}}" nginx`**  
   ❌ **Incorrect**: **`{{Hostname}}`** is **not** a valid Swarm template variable. The correct syntax is **`{{.Node.Hostname}}`**.

2. **`docker service create -e NODE_HOSTNAME nginx`**  
   ❌ **Incorrect**:  
   - **`-e NODE_HOSTNAME`** sets an **empty environment variable** (i.e., `NODE_HOSTNAME=`).  
   - It **does not pass the node hostname dynamically**.

3. **`docker service create --pass-node-hostname=true nginx`**  
   ❌ **Incorrect**:  
   - **`--pass-node-hostname`** is **not** a valid Docker command option.

### **Final Answer:**  
✅ **`docker service create --env NODE_HOSTNAME="{{.Node.Hostname}}" nginx`**
