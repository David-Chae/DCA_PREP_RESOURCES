## 112. How many native network drivers are there?
A. Three  
B. Five  
C. Four  
D. TWo  


The correct answer is:

**B. Five**

### **Explanation:**

Docker provides five **native network drivers**:

1. **Bridge**: The default network driver. Containers connected to the bridge network can communicate with each other, but they are isolated from the external network unless specifically configured.

2. **Host**: This driver allows containers to share the network stack of the host machine. The container will use the host's IP address for communication.

3. **Overlay**: Used in Docker Swarm mode, the overlay network allows containers across different host machines to communicate securely.

4. **Macvlan**: Allows containers to appear as physical devices on the network with their own MAC addresses. This is useful for integrating containers with physical network infrastructure.

5. **None**: This driver disables all networking for the container. The container does not get an IP address and cannot communicate with other containers or external networks.

### **Final Answer:**
**B. Five**
