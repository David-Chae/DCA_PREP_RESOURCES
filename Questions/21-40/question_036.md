## Eric's application comprises many different containers that communicate with one another. In a Docker Swarm, how should he handle this application? 
1. Eric should use docker-compose.
2. Eric should use a service with multiple tasks.
3. Eric should use a task.
4. Eric should use a stack.

✅ **Eric should use a stack.**  

### **Explanation:**  
- In **Docker Swarm**, a **stack** is the best way to manage **multi-container applications** because it allows defining and deploying multiple **services** that work together.  
- A stack is managed using **Docker Compose files (`docker-compose.yml`)**, which define **services, networks, and volumes** needed for the application.  
- Running **`docker stack deploy`** in Swarm mode ensures that the application is orchestrated across multiple nodes.

### **Why the Other Options Are Incorrect:**
1. **`Eric should use docker-compose.`**  
   ❌ **Incorrect**:  
   - **`docker-compose`** is primarily for **single-host deployments**, not Swarm clusters.  
   - In Swarm mode, **`docker stack deploy`** (which uses Compose files) is the preferred method.

2. **`Eric should use a service with multiple tasks.`**  
   ❌ **Incorrect**:  
   - A **service** in Swarm represents **a single application component**, not the entire app.  
   - Since Eric’s app has **multiple containers** that need to communicate, using **only one service** is insufficient.

3. **`Eric should use a task.`**  
   ❌ **Incorrect**:  
   - A **task** is just an instance of a container running as part of a service.  
   - Tasks are **not used to manage applications** directly.

### **Final Answer:**  
✅ **Eric should use a stack.**
