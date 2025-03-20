## 119. How many Docker storage options are there?
A. Three  
B. Four  
C. TwO  
D. Only one  

The correct answer is:

**B. Four**

### **Explanation:**
Docker provides **four** main storage options to manage data in containers:

1. **Volumes**: Managed by Docker and can be shared across containers. They are stored in a specific directory on the host filesystem.
2. **Bind mounts**: Link a container’s file or directory to a location on the host filesystem.
3. **tmpfs mounts**: Store data in the host system’s memory (not persistent).
4. **Container filesystem**: The filesystem of a running container, typically layered, and temporary.

### **Final Answer:**
**B. Four**
