## 210. How to add another worker node to the swarm?
A. docker swarm join-token worker  
B. docker swarm add-worker  
C. docker swarm create-worker  
D. docker worker add  

The correct answer is:  

✅ **A. `docker swarm join-token worker`**  

### Explanation:  
- **`docker swarm join-token worker`** generates a command that can be used on another node to add it as a worker node to the existing Swarm. The generated command includes a token that allows the new node to join the Swarm as a worker.  
- You then run the generated command on the new node to add it as a worker in the Swarm.

### Eliminations:  
❌ **B. `docker swarm add-worker`**  
- Incorrect. This is not a valid Docker command.  

❌ **C. `docker swarm create-worker`**  
- Incorrect. There is no `docker swarm create-worker` command. The process for adding a worker is done through the `join-token` command.  

❌ **D. `docker worker add`**  
- Incorrect. This is not a valid Docker command. The proper way to add a worker node is by using the `docker swarm join-token worker` command.

Feel free to ask if you'd like further clarification!
