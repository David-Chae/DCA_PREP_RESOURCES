What is the difference between a manager and a worker in Docker swarm?
```
1. Managers never execute containers, workers do.
2. Managers handle networking, while workers handle containers.
3. Managers create new workers.
4. Managers control the cluster, while workers only execute workloads.
```

The correct answer is:

**Managers control the cluster, while workers only execute workloads.**

### Explanation:

In Docker Swarm, the cluster is composed of two types of nodes: **managers** and **workers**.

- **Manager nodes**: These nodes are responsible for managing the swarm. They handle the control plane functions, such as maintaining the desired state of the cluster, scheduling tasks, and handling the Swarm's orchestration. They also manage service discovery, networking, and maintain the cluster's overall state. A manager node can also run containers, but it is primarily responsible for the coordination and management of the swarm.

- **Worker nodes**: Worker nodes are responsible for running the actual application workloads. They receive tasks from the manager nodes and execute them by running containers. Workers do not participate in managing the swarm; their role is purely to execute the containers assigned to them by the manager.

### Why the other options are incorrect:

- **Managers never execute containers, workers do**: While it is true that workers execute containers, manager nodes **can also run containers**. However, their primary responsibility is managing the swarm, not executing containers.

- **Managers handle networking, while workers handle containers**: While manager nodes are involved in orchestration and scheduling of containers, the **actual container execution is handled by both managers (if configured) and workers**. However, networking within the swarm is managed as part of the orchestration, so this statement is partially correct but misleading.

- **Managers create new workers**: Managers do not create new worker nodes. They can add or remove worker nodes to/from the swarm, but worker nodes are typically set up separately and joined to the swarm by the manager.

### Summary:
In a Docker Swarm, **manager nodes** control and manage the cluster, while **worker nodes** are responsible for executing the containers (workloads) that are scheduled by the managers.
