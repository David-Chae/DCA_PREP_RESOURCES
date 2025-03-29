## 207. How do you know the current status of the swarm?
A. docker info //You can find the info under the swarm section  
B. docker status  
C. docker swarm status  
D. docker check swarm  

The correct answer is:  

✅ **A. `docker info //You can find the info under the swarm section`**  

### Explanation:  
- **`docker info`** provides detailed information about your Docker setup, including the current Swarm status under the "Swarm" section. This will indicate whether the Docker daemon is part of a swarm and the state of the swarm (e.g., whether it's active, inactive, or in a specific mode).  

### Eliminations:  
❌ **B. `docker status`**  
- Incorrect. `docker status` is not a valid Docker command. It doesn't exist in the Docker CLI.  

❌ **C. `docker swarm status`**  
- Incorrect. There's no `docker swarm status` command. To check Swarm status, you would use `docker info` or other swarm-specific commands like `docker node ls` for more specific details.  

❌ **D. `docker check swarm`**  
- Incorrect. `docker check swarm` is not a valid Docker command.  

Would you like to see this in a structured DOMC format for clarity? 😊
