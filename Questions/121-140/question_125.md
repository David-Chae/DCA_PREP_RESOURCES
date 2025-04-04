## 125. Which of the following acts as a block-level rather than a file-level?
A. Docker Stack  
B. Registry  
C. Devicemapper  
D. Docker Swarm  

The correct answer is:  

**C. Devicemapper**  

- **Devicemapper** is a **block-level storage driver** used by Docker to manage container storage.  
- Unlike file-level storage, it operates at the block level, providing efficient storage management for containerized environments.



Great! Let's break down **DOMC Question 125** in the required format — **True or False for each option with reasoning**.

---

### **Question 125:**
**Which of the following acts as a block-level rather than a file-level?**

---

### **A. Docker Stack**  
- **False**  
- **Reason**:  
  Docker Stack is a tool for deploying and managing multi-container Docker applications using a `docker-compose.yml` file in a Swarm. It has **nothing to do with storage levels** (block or file). It operates at the orchestration/application level.

---

### **B. Registry**  
- **False**  
- **Reason**:  
  A Docker Registry (like Docker Hub) is where Docker images are stored and distributed. It deals with **image management**, not with how container data is stored (block or file level). Therefore, it's unrelated to storage drivers or block-level operations.

---

### **C. Devicemapper**  
- **True**  
- **Reason**:  
  `devicemapper` is a **Docker storage driver** that works at the **block level**, managing data using thin provisioning and snapshotting. Unlike file-level storage (like with the overlay2 driver), devicemapper handles storage at a **lower level**, which makes it the correct answer here.

---

### **D. Docker Swarm**  
- **False**  
- **Reason**:  
  Docker Swarm is a **container orchestration tool**. It schedules and manages containers in a clustered environment but does not handle **storage operations directly**—especially not block-level ones.

---

### ✅ Final Answer:  
- **C. Devicemapper** is **True**.  
- All other options (**A, B, D**) are **False** because they don't relate to block-level storage.

Let me know if you'd like to rephrase this question or turn it into a more solid test item!
