## 251. In Docker, what is the role of an ENTRYPOINT in a Dockerfile?
A. It defines environment variables for the container.  
B. It specifies the base image for the container.  
C. It sets the command to be executed when the container starts.  
D. It exposes container ports to the host system  

The correct answer is:  

**C. It sets the command to be executed when the container starts.**  

### Explanation:  
- **ENTRYPOINT** in a Dockerfile defines the default executable that runs when a container starts. It is often used when you want the container to function as a specific application or service.  
- Unlike `CMD`, which provides default arguments, `ENTRYPOINT` ensures that the container always runs as a specific executable, making it more suitable for containers designed to be used as commands.  

#### Why the other options are incorrect:  
- **A (Defines environment variables)** → Environment variables are set using the `ENV` instruction, not `ENTRYPOINT`.  
- **B (Specifies the base image)** → The base image is defined using the `FROM` instruction.  
- **D (Exposes container ports)** → Ports are exposed using the `EXPOSE` instruction, not `ENTRYPOINT`.  

Thus, **C is the correct answer** since `ENTRYPOINT` defines the command executed when the container starts.
