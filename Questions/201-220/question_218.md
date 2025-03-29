## 218. How to rotate the unlock key?
A. docker swarm unlock-key --rotate  
B. docker swarm rotate-key  
C. docker swarm update --rotate-key  
D. docker swarm change-key  

The correct answer is:

**A. docker swarm unlock-key --rotate**

### Explanation:
- The command `docker swarm unlock-key --rotate` is used to **rotate the unlock key** for the Docker Swarm, which is part of managing security when autolock is enabled. 

### Why the other options are incorrect:
- **B. docker swarm rotate-key**: This is not a valid command in Docker.
- **C. docker swarm update --rotate-key**: This is not a valid command in Docker.
- **D. docker swarm change-key**: This is not a valid command in Docker.

The correct command is `docker swarm unlock-key --rotate`, which will generate a new unlock key and rotate it for use.
