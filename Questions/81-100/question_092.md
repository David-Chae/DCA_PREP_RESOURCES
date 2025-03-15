## What Linux feature does Docker employ to restrict the amount of memory containers used?
A. cgroups  
B. Capabilities  
C. The mem namespace  
D. Namespace  


The correct answer is:

**A. cgroups**

---

### **Explanation:**

- **cgroups (Control Groups)** is a Linux kernel feature that Docker uses to **limit, account for, and isolate resource usage**, including CPU, memory, disk I/O, and network. Docker uses cgroups to enforce memory limits on containers, ensuring they don't exceed a specified amount of memory.

    - For example, you can limit the memory a container can use with the `--memory` flag when running a container:
      ```bash
      docker run --memory="512m" my_container
      ```
    - This ensures that the container does not use more than 512MB of memory.

---

### **Why the other options are incorrect:**

- **B. Capabilities**:
  - Linux capabilities allow containers to have a more granular set of privileges, restricting access to certain system operations, but they do not directly limit resource usage like memory.

- **C. The mem namespace**:
  - The **memory namespace** is responsible for isolating the memory usage of containers, so that each container has its own memory. However, it is **cgroups** that enforce the actual limits on memory.

- **D. Namespace**:
  - Linux namespaces (e.g., process, user, network, mount) are used to isolate containers from each other. While namespaces do contribute to isolation, **cgroups** is the mechanism responsible for limiting resource usage like memory.

---

### **Final Answer:**
**A. cgroups**
