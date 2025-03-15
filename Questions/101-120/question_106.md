## 106. Which of the following allows you to communicate with the server?
A. Docker object  
B. Docker client  
C. Docker daemon  
D. None of the above  

The correct answer is:

**B. Docker client**

### **Explanation:**

- **Docker client**: The Docker client is the primary way users communicate with the Docker server (daemon). It can be accessed via the command line or Docker API. When you run a command like `docker run` or `docker ps`, you're interacting with the Docker client, which sends requests to the Docker daemon to perform actions.

- **Docker object**: Docker objects (such as containers, images, volumes, and networks) represent resources managed by Docker, but they don't facilitate communication with the server.

- **Docker daemon**: The Docker daemon is responsible for managing containers and resources. However, communication with it is typically handled through the Docker client.

- **None of the above**: This is incorrect because the Docker client is the correct answer for communication with the server.

### **Final Answer:**
**B. Docker client**
