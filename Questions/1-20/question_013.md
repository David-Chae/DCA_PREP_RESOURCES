## 13. Global service runs task/tasks on every node that meets the placement and resource constraints.
A. many  
B. one  
C. more than one  
D. none  




The correct answer is:  

**B. one**  

### Explanation:  
In Docker Swarm, a **global service** ensures that **one task runs on every node** that meets the placement and resource constraints. Unlike replicated services, which run a specific number of tasks across the cluster, a **global service** automatically schedules exactly one task per eligible node.  

### Example:  
If you create a global service:  
```sh
docker service create --mode global --name my_global_service alpine top
```  
This service will run **one instance per node** in the Swarm.  

### Why the other options are incorrect:  
- **A. many** → **False** (A global service runs exactly **one** task per node, not multiple.)  
- **C. more than one** → **False** (Each node gets exactly **one** task, not more.)  
- **D. none** → **False** (As long as the node meets constraints, at least **one** task will run.)  

Thus, **B. one** is the correct answer.
