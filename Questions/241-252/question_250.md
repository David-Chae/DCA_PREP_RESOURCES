## 250. You created a deployment that runs exactly one task on every node. which type of service deployment is this?
A. "global"  
B. "replicated"  
C. "constraint-based"  
D. "swarm-wide"  

The correct answer is:

**A. "global"**

### Explanation:
- **A (Global)**: A **global** service ensures that exactly one task (container) runs on each node in the swarm. This is typically used for tasks that need to run on all nodes, such as monitoring agents or logging services. The number of replicas is not specified explicitly; instead, Docker schedules one instance per node automatically.

- **B (Replicated)**: A **replicated** service allows you to specify the exact number of replicas you want for the service, but it does not ensure that there is one task on each node. Instead, it distributes tasks according to available resources and the replica count.

- **C (Constraint-based)**: **Constraint-based** services allow you to define rules about where tasks should be deployed based on node attributes. This is more about placement rules, but it doesn't define a service that runs one task per node.

- **D (Swarm-wide)**: This is not a recognized deployment type in Docker Swarm. The term "swarm-wide" isn't used to describe a service deployment mode.

Therefore, **A (global)** is the correct answer.
