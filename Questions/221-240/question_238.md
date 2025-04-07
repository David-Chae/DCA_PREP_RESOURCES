## 238. How to inspect the network?
A. To inspect a network, use the docker network inspect my-network command  
B. You can inspect a network using docker network show my-network  
C. Use docker inspect network my-network to view network details  
D. Inspecting a network requires the docker network view command  

The correct answer is:

**A. To inspect a network, use the docker network inspect my-network command**

### Explanation:
- **A** is correct because the `docker network inspect` command allows you to view detailed information about a specific Docker network, such as its configuration, containers connected to it, and other properties.
  
- **B** is incorrect because `docker network show` is not a valid command in Docker for inspecting networks.

- **C** is incorrect because the `docker inspect network` command is not valid; `docker network inspect` is the correct command. Docker will output "Error: No such object: network".

- **D** is incorrect because `docker network view` is not a valid command in Docker.

Therefore, **A** is the correct choice.
