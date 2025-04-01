## 131. Which of the following commands returns the low-level information of the Docker objects?
```sh
A. docker swarm
B. docker stack
C. docker compose
D. docker inspect
```

The correct answer is:  

**D. docker inspect**  

### Explanation:  
The `docker inspect` command provides low-level details and metadata about Docker objects (such as containers, images, volumes, networks, and more). It returns information in JSON format, which includes detailed configuration and state information.

### Why not the others?  
- **A. docker swarm**: This command is used to manage Docker Swarm clusters but does not provide low-level information about Docker objects.  
- **B. docker stack**: This command is used to manage multi-container applications (stacks) in Docker Swarm, not for retrieving low-level object details.  
- **C. docker compose**: Docker Compose is used for defining and running multi-container Docker applications, but it does not provide low-level object information.
