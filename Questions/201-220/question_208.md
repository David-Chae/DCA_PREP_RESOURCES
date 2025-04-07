## 208. Which command do you use to find the information about the nodes in the swarm?
A. docker node ls  
B. docker swarm nodes  
C. docker inspect node  
D. docker info nodes  

The correct answer is:  

✅ **A. `docker node ls`**  

### Explanation:  
- **`docker node ls`** lists all the nodes in the Swarm cluster, showing details like their ID, status, availability, and manager role. This command is specifically used to get information about the nodes in the Docker Swarm.  
Reference: https://docs.docker.com/engine/reference/commandline/node_ls/

### Eliminations:  
❌ **B. `docker swarm nodes`**  
- Incorrect. There is no command `docker swarm nodes`. The correct command is `docker node ls`.  

❌ **C. `docker inspect node`**  
- Incorrect. While `docker inspect` can be used to get detailed information about a specific Docker object (like a container, image, or volume), it does **not** directly apply to nodes in the Swarm.  

❌ **D. `docker info nodes`**  
- Incorrect. `docker info` provides general Docker system information, but it does **not** specifically list or provide detailed information about the nodes in a Swarm.  

Would you like further clarification or a structured DOMC format for this question?
