## 215. Can we enable the autolock feature only when we create a swarm for the first time?
A. "No. You can lock the existing swarm as well."  
B. "Yes, autolock can only be enabled during the initial creation of a swarm."  
C. "Autolock can be enabled after swarm creation but it is a complex and irreversible process."  
D. "Autolock is not a feature available in Docker swarm.'  

The correct answer is:  

**A. "No. You can lock the existing swarm as well."**  

### Explanation:  
- **Autolock can be enabled both during and after swarm creation.**  
- To enable autolock **after** swarm creation, you can use the command:  
  ```bash
  docker swarm update --autolock=true
  ```
- When autolock is enabled, the **manager nodes' encryption keys are locked**, and you need to manually unlock them after a restart using:  
  ```bash
  docker swarm unlock
  ```

### Why the other options are incorrect:  
- **B** is incorrect because autolock **can be enabled after swarm creation** using `docker swarm update --autolock=true`.  
- **C** is incorrect because enabling autolock **after swarm creation is straightforward** and not irreversible.  
- **D** is incorrect because **autolock is a real feature in Docker Swarm**.
