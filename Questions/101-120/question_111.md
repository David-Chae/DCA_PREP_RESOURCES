## 111.Which of the following network drivers allows swarm services to communicate with each other?
A. Host
B. None
C. Bridge
D. Overlay

The correct answer is:

**D. Overlay**

### **Explanation:**

- **Overlay Network**: In Docker Swarm, the **overlay network** allows services running on different nodes to communicate with each other. It is the primary network driver used in a Docker Swarm to enable communication between containers across different host machines in the cluster.

- **Host**: The **host** network driver allows containers to share the network stack of the host machine. It does not allow communication across multiple nodes in a swarm.

- **Bridge**: The **bridge** network driver is used for communication between containers on the same host but not for swarm services spread across multiple nodes.

- **None**: The **none** network driver disables networking for a container, meaning it cannot communicate with any other container or service.

### **Final Answer:**
**D. Overlay**
