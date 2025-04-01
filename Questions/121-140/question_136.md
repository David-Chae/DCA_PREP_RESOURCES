## 136. Which of the following is responsible for receiving and completing tasks assigned by manager nodes?
```sh
A. Swarmkit
B. Worker Nodes
C. Service
D. Load Balancing
```

The correct answer is:  

**B. Worker Nodes**  

### Explanation:  
In Docker Swarm, **worker nodes** are responsible for receiving and completing tasks (i.e., running containers) that are assigned by the **manager nodes**. Worker nodes execute the tasks, maintain the desired state of the services, and report back to the manager nodes.

### Why not the others?  
- **A. Swarmkit**: Swarmkit is the underlying component that handles the orchestration of services and nodes within Docker Swarm, but it does not directly receive or complete tasks. It's the framework for Swarm's operation.
- **C. Service**: A **service** in Docker Swarm defines the desired state of the application, including the containers that should be running, but it is not responsible for completing tasks. It's a higher-level abstraction for managing containers.
- **D. Load Balancing**: Load balancing in Docker Swarm ensures that network traffic is evenly distributed among available tasks or services, but it does not receive or complete tasks.
