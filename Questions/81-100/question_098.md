## Which of the following is not included in a Docker Trusted Registry (DTR) metadata backup? 
A. Role-Based Access Control (RBAC) Settings  
B. Repository metadata  
C. DTR Configurations  
D. Docker images  

The correct answer is:

**D. Docker images**

### **Explanation:**

A **Docker Trusted Registry (DTR)** metadata backup includes critical configuration and access-related information about the registry, but it **does not** include the actual Docker images stored in the registry.

Here’s a breakdown of the options:

1. **A. Role-Based Access Control (RBAC) Settings**: This is part of the metadata backup, as it involves access control configurations for the registry.

2. **B. Repository metadata**: This includes metadata about the repositories within DTR, such as tags, access logs, and settings. It is included in the metadata backup.

3. **C. DTR Configurations**: This involves configuration settings related to how DTR is set up and managed. It’s part of the backup.

4. **D. Docker images**: Docker images themselves (the actual data) are **not** part of the metadata backup. Images are stored separately, and to back them up, you would typically need to push them to a different registry or store them elsewhere.

---

### **Final Answer:**
**D. Docker images**
