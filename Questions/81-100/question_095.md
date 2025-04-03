## What distinguishes a worker from a manager in a Docker swarm?
A. Workers merely carry out workloads while managers manage the cluster  
B. Workers handle containers, while managers take care of networking.  
C. Managers create workers  
D. Workers always run containers; managers never do.

The correct answer is:  

✅ **A. Workers merely carry out workloads while managers manage the cluster**  

---

### Explanation:

In a **Docker Swarm**, nodes are categorized as **managers** and **workers**:

- **Managers:**  
  - Manage the cluster and orchestrate services.  
  - Make scheduling decisions.  
  - Maintain the swarm’s state.  
  - Can also run containers, but it's optional.  

- **Workers:**  
  - Execute tasks assigned by the manager.  
  - Do **not** participate in cluster management.  
  - Always run workloads (containers).  

#### Breakdown of the options:

| Option | Explanation | Correct? |
|---------|------------------------------------------------|------------|
| **A** | ✅ **Correct**: Managers handle cluster management, while workers execute workloads. | ✅ **Yes** |
| **B** | ❌ **Incorrect**: Both managers and workers handle networking; networking is not exclusive to managers. | ❌ No |
| **C** | ❌ **Incorrect**: Managers **do not create workers**—workers must be manually joined to the swarm. | ❌ No |
| **D** | ❌ **Incorrect**: Managers **can also run containers**, though it's not their primary role. | ❌ No |

Thus, **option A is the most accurate description of the difference between a worker and a manager in Docker Swarm.** ✅
