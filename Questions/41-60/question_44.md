## Which of the claims concerning the overlay network driver is correct? 
1. Each node must manually configure the network.
2. Only containers running on the same host can communicate with each other using the overlay driver.
3. As soon as the network is created, it is set up on every node in the cluster.
4. When jobs are scheduled on a node, networking components are built dynamically.

The correct claim is:  

✅ **"When jobs are scheduled on a node, networking components are built dynamically."**  

### **Explanation:**  
- **Overlay networks** are designed for multi-host communication within a **Docker Swarm** cluster.  
- The overlay network **does not exist on every node immediately upon creation**. Instead, it is **dynamically configured** when a service task (container) is scheduled on a node.  
- This ensures that only nodes that **need** to participate in the network get the required networking components.

### **Why the Other Options Are Incorrect:**  
❌ **"Each node must manually configure the network."**  
- Overlay networks are **automatically configured** by Docker Swarm, so no manual setup is required on each node.  

❌ **"Only containers running on the same host can communicate with each other using the overlay driver."**  
- Overlay networks **allow communication across multiple nodes**, enabling containers on different hosts to talk to each other.  

❌ **"As soon as the network is created, it is set up on every node in the cluster."**  
- The network is **not immediately set up on all nodes**. Instead, it is configured **on-demand**, only on nodes where a service needs it.  

### **Final Answer:**  
✅ **"When jobs are scheduled on a node, networking components are built dynamically."**
