## 103. Which of the following is used by nodes in a swarm for authentication and authorization?
A. Docker compose  
B. Docker Volume  
C. MTLS  
D. Docker Trusted Registry  


The correct answer is:
**C. MTLS (Mutual TLS)**

### **Explanation:**

In a Docker Swarm, **MTLS (Mutual TLS)** is used for **authentication and authorization** between nodes in the swarm. This ensures that the communication between the manager and worker nodes is secure. With MTLS, both the client and the server authenticate each other by exchanging certificates, providing a secure and trusted connection.

- **Docker Compose**: This is a tool used to define and run multi-container Docker applications, but it's not directly involved in swarm authentication and authorization.
  
- **Docker Volume**: Docker volumes are used for persistent storage, but they are unrelated to swarm authentication and authorization.

- **Docker Trusted Registry (DTR)**: DTR is a private image registry that helps manage Docker images and can enforce security policies like image signing, but it's not directly involved in swarm node authentication and authorization.

### **Final Answer:**
**C. MTLS**
