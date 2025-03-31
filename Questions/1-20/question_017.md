## What is the difference between a manager and a worker in a Docker swarm? 
1. Managers handle networking, while workers handle containers. 
2. Managers never execute containers; workers do. 
3. Managers control the cluster, while workers only execute workloads. 
4. Managers create new workers. 

The correct statement is:  

✅ **"Managers control the cluster, while workers only execute workloads."**  

### Explanation:  
In a **Docker Swarm**, the roles of **manager** and **worker** nodes differ in terms of responsibilities:

1. **Manager Nodes**:  
   - **Control the cluster**: They manage the overall state of the swarm and are responsible for the **orchestration** and **scheduling** of services and tasks.  
   - **Maintain swarm state**: They store the cluster's metadata and configurations (via the Raft consensus algorithm).  
   - **Handle management tasks**: Managers are responsible for accepting and distributing work assignments to worker nodes. They also handle **swarm configuration**, **service scaling**, and **networking** setup.  

2. **Worker Nodes**:  
   - **Execute workloads**: Worker nodes run the containers or tasks that have been scheduled by the manager.  
   - **Do not control the cluster**: They do not have the authority to manage the cluster state or service definitions.  
   - **Receive tasks from managers**: They report to managers and only execute the tasks assigned to them.

### Why Other Options Are Incorrect:  
❌ **"Managers handle networking, while workers handle containers."**  
   - Networking tasks are distributed across the entire swarm, and both managers and workers participate in container networking. The key distinction is that **managers control the cluster**, while **workers execute tasks**.

❌ **"Managers never execute containers; workers do."**  
   - While it's true that workers execute containers, **managers can also run containers** if required, but their primary role is **cluster management**.

❌ **"Managers create new workers."**  
   - **Managers do not create new worker nodes**. Worker nodes are added to the swarm by an admin, and managers simply maintain the cluster's state, including the list of worker nodes.

### Summary:
- **Managers** control and manage the Docker Swarm, including scheduling tasks and handling the cluster's state.  
- **Workers** execute the tasks (containers) assigned to them by the manager.
