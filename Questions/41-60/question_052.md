## A group of endpoints that can communicate with one another is referred to by what part of the Docker Container Networking Model (CNM)? 
A. Sandbox  
B. Network device  
C. Network  
D. IP Address Management (IPAM) driver  

The correct answer is:  

✔ **C. Network**  

### **Explanation:**  
In the **Docker Container Networking Model (CNM)**, a **Network** is a group of **endpoints** that can communicate with one another.  

- A **Network** connects multiple **endpoints**, allowing containers to communicate with each other.  
- It provides **isolation** and **connectivity** between containers using **network drivers** like **bridge, overlay, or macvlan**.  
- Multiple **containers** can be connected to the same **network**, enabling them to communicate **securely**.  

### **Why are the other options incorrect?**  

1. **A. Sandbox** ❌  
   - A **sandbox** is an **isolated environment** for a single container's networking **configuration** (e.g., IP address, routes). It does not define a group of communicating endpoints.

2. **B. Network device** ❌  
   - A **network device** is a low-level component that connects a container to a network, like a **veth pair** or **bridge interface**, but it does not define a group of endpoints.

3. **D. IP Address Management (IPAM) driver** ❌  
   - The **IPAM driver** assigns IP addresses to networks but does not define a group of communicating endpoints.  

### **Final Answer:**  
✔ **C. Network**
