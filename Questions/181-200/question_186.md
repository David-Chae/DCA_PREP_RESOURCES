## 186. Which algorithm does the docker engine use when it is in swarm mode to manage the global cluster state?
A. Raft Consensus Algorithm  
B. Paxos Consensus Algorithm  
C. Round Robin Algorithm  
D. Random Consensus Algorithm  

**A. Raft Consensus Algorithm**  

### Explanation:  
When Docker Engine operates in **Swarm mode**, it uses the **Raft Consensus Algorithm** to manage the global cluster state. This ensures that all manager nodes in the swarm agree on the current state of services, tasks, and nodes, even in case of failures.

### Why Raft?  
- **Consistency & Fault Tolerance**: Raft ensures that data remains consistent across all manager nodes.  
- **Leader Election**: One manager node acts as a **leader**, while others serve as **followers**.  
- **High Availability**: If the leader fails, a new leader is elected automatically.  

### Why Not the Others?  
- **B. Paxos Consensus Algorithm** → Paxos is another consensus algorithm, but it is more complex and not used by Docker Swarm.  
- **C. Round Robin Algorithm** → Used for load balancing, not for managing cluster state.  
- **D. Random Consensus Algorithm** → No such algorithm exists for managing distributed systems.
