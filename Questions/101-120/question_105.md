## 105. Which of the following is responsible for Docker object actions?
A. Container Runtime  
B. Registry  
C. Docker client  
D. Docker daemon  


The correct answer is:

**D. Docker daemon**

### **Explanation:**

- **Docker daemon** is responsible for managing Docker objects such as containers, images, networks, and volumes. It is the core component of Docker that listens for Docker API requests and manages the container lifecycle (such as creation, running, stopping, and removing containers).

- **A. Container Runtime**: The container runtime is responsible for running containers, but it does not manage Docker objects directly. It is part of the Docker daemon.

- **B. Registry**: The registry is responsible for storing and distributing Docker images but not managing the actions of Docker objects like containers.

- **C. Docker client**: The Docker client is a command-line interface (CLI) that allows users to interact with the Docker daemon, but it doesn't manage Docker objects on its own; it sends commands to the Docker daemon.

### **Final Answer:**
**D. Docker daemon**
