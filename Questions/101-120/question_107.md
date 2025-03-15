## 107. Which of the following can connect services and containers to many networks?
A. Overlay networks  
B. Docker client  
C. Docker container  
D. None of the above  

The correct answer is:

**A. Overlay networks**

### **Explanation:**

- **Overlay networks**: These networks allow containers running on different Docker hosts (nodes) to communicate with each other, making them ideal for connecting services and containers across multiple networks. Overlay networks create a virtual network on top of the host network, enabling cross-host communication in a Docker Swarm or Docker standalone cluster.

- **Docker client**: The Docker client is used to interact with the Docker daemon, but it does not directly manage networks or connect services.

- **Docker container**: A Docker container is a lightweight, standalone, and executable package of software, but it doesn't directly manage networks or connect services to multiple networks.

- **None of the above**: This is incorrect because overlay networks do indeed connect services and containers to multiple networks.

### **Final Answer:**
**A. Overlay networks**
