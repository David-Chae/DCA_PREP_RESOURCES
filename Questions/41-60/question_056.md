## 56. In terms of establishing a high level of availability, what is the benefit of having more manager nodes present in a swarm?
```sh
A. It would allow for more worker nodes to be present.
B. It would help bolster fault-tolerance
C. The cluster would be easier to set up
D. It would result in being more efficient with resources.
```

The correct answer is:  

**B. It would help bolster fault-tolerance**  

### Explanation:  
In Docker Swarm, manager nodes are responsible for the orchestration and decision-making of the cluster. Having **more manager nodes** improves **fault tolerance** because the swarm can tolerate the failure of one or more manager nodes without losing the ability to manage the cluster. With an odd number of managers, the swarm can also ensure a quorum for making decisions (i.e., maintaining cluster consistency and avoiding split-brain scenarios).

### Why not the others?  
- **A**: More manager nodes do not directly affect the ability to add more worker nodes. Worker nodes are typically added based on capacity, not the number of manager nodes.  
- **C**: Adding more manager nodes actually makes the cluster more complex to set up, not easier.  
- **D**: Having more manager nodes doesn't necessarily make the system more efficient with resources. It actually consumes more resources because of the overhead of running multiple manager nodes.
