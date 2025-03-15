## What distinguishes a worker from a manager in a Docker swarm?
A. Workers merely carry out workloads while managers manage the cluster  
B. Workers handle containers, while managers take care of networking.  
C. Managers create workers  
D. Workers always run containers; managers never do.

The correct answer is:

**A. Workers merely carry out workloads while managers manage the cluster.**

---

### **Explanation:**

In a Docker Swarm cluster:
- **Managers** are responsible for maintaining the state of the cluster, making decisions about task scheduling, managing the overall Swarm, and handling the orchestration of services. Managers also manage the Raft consensus to ensure the cluster state is consistent and can manage the cluster's settings.
- **Workers** are the nodes that execute tasks (containers) that are assigned to them by managers. They run the actual containers that are part of the services in the Swarm but do not participate in the management of the cluster.

---

### **Why the other options are incorrect:**

- **B. Workers handle containers, while managers take care of networking.**
  - While workers do handle running containers, **managers** are also involved in the networking setup of the cluster, not just workers.

- **C. Managers create workers.**
  - This is not accurate. Workers are simply nodes that join the cluster and run tasks; they are not "created" by managers but are added to the Swarm cluster through the join process. Managers are the ones that control and schedule tasks but do not create worker nodes.

- **D. Workers always run containers; managers never do.**
  - This is not true. Managers run containers too.
---

### **Final Answer:**
**A. Workers merely carry out workloads while managers manage the cluster.**
