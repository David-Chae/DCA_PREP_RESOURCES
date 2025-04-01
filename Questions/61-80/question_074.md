## 74. Which of the following network drivers is the standard for establishing connections between containers on the same host?
```sh
A. macvlan
B. Bridge
C. host
D. overlay
```

The correct answer is:  

**B. Bridge**  

### Explanation:  
The **bridge** network driver is the default and standard network driver used for establishing connections between containers on the same host. When containers are attached to a bridge network, they can communicate with each other through the bridge and are isolated from other networks unless explicitly configured to communicate with them.

### Why not the others?  
- **A. macvlan**: The `macvlan` driver is used to assign a unique MAC address to a container and allows it to appear as a physical device on the network, which is typically used for scenarios where containers need to be directly reachable on the network.
- **C. host**: The `host` driver allows containers to share the host’s network stack, but this is not the default method for connecting containers. It is typically used when you want to avoid network isolation between the container and the host.
- **D. overlay**: The `overlay` driver is used for communication between containers across multiple hosts in a Docker Swarm or other clustered environment, not for containers on the same host.
