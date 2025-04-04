## 126. Which of the following can communicate between the Docker host and container?
A. Volume Mount  
B. npipe Mount  
C. tmps Mount  
D. Bind Mount  

The correct answer is:  

**B. npipe Mount**  

- For communication between the Docker host and a container, a npipe mount can be utilized. A common use case is to run a third-party tool within a container and use a named pipe to connect to the Docker Engine API.

### Docker Documentation 
**Named pipes**
Named pipes can be used for communication between the Docker host and a container. Common use case is to run a third-party tool inside of a container and connect to the Docker Engine API using a named pipe. (REF: https://docs.docker.com/engine/storage/)
