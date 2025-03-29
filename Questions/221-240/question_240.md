## 240. Can service containers connected to the overlay network communicate with each other?
A. Yes, service containers connected to the overlay network can, in fact, communicate with one another.  
B. Service containers cannot communicate with each other when connected to an overlay network.  
C. Service containers can only communicate with other containers on the same node, not across nodes in the swarm.  
D. Communication across overlay network service containers is feasible but requires additional configuration.  

The correct answer is:

**A. Yes, service containers connected to the overlay network can, in fact, communicate with one another.**

### Explanation:
- **A** is correct because containers attached to the same overlay network, regardless of whether they are on the same node or different nodes, can communicate with each other. Overlay networks are designed to allow communication between containers across multiple Docker nodes in a swarm.

- **B** is incorrect because containers connected to the overlay network can communicate with each other by design, and the overlay network is specifically intended to enable this cross-node communication.

- **C** is incorrect because containers in the same overlay network can communicate across nodes in the swarm, not just within a single node.

- **D** is incorrect because no additional configuration is required for containers to communicate over an overlay network. The overlay network facilitates communication across nodes by default.

Thus, **A** is the correct choice.
