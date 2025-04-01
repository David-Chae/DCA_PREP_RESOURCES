## 135. Which of the following encrypts sensitive data by Docker Swarm?
```sh
A. Node Labels
B. Node Constraint
C. Autolock
D. Placement-pref
```

The correct answer is:  

**C. Autolock**  

### Explanation:  
**Autolock** is a feature in Docker Swarm that encrypts sensitive data, such as secrets, and ensures that the Docker Swarm manager's Raft data store is locked. It requires the use of a key to unlock the swarm and provides encryption for sensitive data stored in the swarm, protecting it from unauthorized access.

### Why not the others?  
- **A. Node Labels**: Node labels are used for organizing and selecting nodes based on key-value pairs, but they do not involve encryption of sensitive data.  
- **B. Node Constraint**: Node constraints are used to limit the scheduling of tasks to specific nodes based on labels or other conditions, but they do not encrypt sensitive data.  
- **D. Placement-pref**: Placement preferences are used to specify the preferred placement of services or tasks on specific nodes but do not involve encryption of sensitive data.
