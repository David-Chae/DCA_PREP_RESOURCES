## In a UCP cluster, how can you ensure that an existing worker node only runs containers that are orchestrated with Kubernetes, not Docker Swarm?

To ensure that an existing worker node in a **Universal Control Plane (UCP)** cluster only runs containers orchestrated with **Kubernetes** and not **Docker Swarm**, you can **label the node** to ensure that it is exclusively used for Kubernetes workloads.

Here’s how you can do that:

### Steps to Ensure the Node Runs Only Kubernetes Workloads:

1. **Label the Node for Kubernetes Workloads:**
   You can label the worker node to ensure that only Kubernetes workloads are scheduled on it. This is done by adding a label that Kubernetes recognizes for node selection.

   ```bash
   docker node update --label-add kubernetes=true <node-name>
   ```

   This adds a custom label to the worker node that marks it as available for Kubernetes workloads.

2. **Configure Docker Swarm Not to Schedule Tasks on This Node:**
   You can also **drain the node** for Swarm to ensure that no Swarm services are scheduled on it. To do this, you can run the following command to **remove the node from the Swarm** and prevent it from scheduling Docker Swarm tasks:

   ```bash
   docker node update --availability drain <node-name>
   ```

   The `drain` availability status will remove the node from the Swarm scheduler and stop Swarm services from being assigned to it.

3. **Ensure that Kubernetes Can Use the Node:**
   Once the node is labeled for Kubernetes and drained from Swarm, **Kubernetes** will continue to schedule workloads on this node, as it will consider the label as part of its scheduling rules.

4. **(Optional) Enforce Kubernetes Scheduling via Taints and Tolerations:**
   If you want to make sure that only Kubernetes workloads are scheduled on this node, you can apply a **taint** to the node so that only workloads with the corresponding **toleration** can be scheduled on it.

   ```bash
   kubectl taint nodes <node-name> orchestrator=swarm:NoSchedule
   ```

   This will ensure that **Swarm** tasks are not scheduled on this node, and only Kubernetes workloads with the appropriate tolerations can run.

### Summary of Actions:
1. Label the node for Kubernetes using `docker node update --label-add kubernetes=true`.
2. Drain the node from Docker Swarm using `docker node update --availability drain <node-name>`.
3. Optionally, apply a taint to the node to prevent Swarm workloads from being scheduled using Kubernetes taints and tolerations.

This way, the node will only run Kubernetes-managed containers and will be excluded from running Docker Swarm services.

---

## SAMPLE QUESTION : In a UCP cluster, how can you ensure that an existing worker node only runs containers that are orchestrated with Kubernetes, not Docker Swarm?
```
1. Set the orchestrator type to Kubernetes in the UCP UI.
2. Set the orchestrator type to Mixed in the UCP UI.
3. Set the default orchestrator to Kubernetes.
4. Set the orchestrator type to Swarm in the UCP UI.
```
The correct answer is:

> ✅ **Set the orchestrator type to Kubernetes in the UCP UI.**

### Explanation:

In a **UCP (Universal Control Plane)** cluster, you can specify which orchestrator should be used for each node. By default, UCP allows you to run both **Docker Swarm** and **Kubernetes** workloads on the same cluster. However, to ensure that a worker node only runs containers orchestrated by **Kubernetes** (and not Docker Swarm), you need to configure the node's orchestrator to **Kubernetes**.

### Steps to Achieve This:

1. **Access the UCP UI**:
   - Log in to the UCP web interface with admin credentials.

2. **Select the Worker Node**:
   - Navigate to the "Nodes" section and select the worker node you want to configure.

3. **Set the Orchestrator Type**:
   - In the node details, find the option to set the orchestrator type.
   - Set the orchestrator type to **Kubernetes**. This configuration ensures that the worker node will only run containers managed by Kubernetes.

### Explanation of Other Options:

- **Set the orchestrator type to Mixed in the UCP UI**:
  - This would allow both **Swarm** and **Kubernetes** to orchestrate containers on the same node. It doesn't restrict the node to only Kubernetes workloads.
  
- **Set the default orchestrator to Kubernetes**:
  - While setting the default orchestrator to Kubernetes will influence newly added nodes, it doesn't apply to already existing nodes. You must explicitly change the orchestrator type for the specific node.

- **Set the orchestrator type to Swarm in the UCP UI**:
  - This would make the node run **Docker Swarm** workloads, which is the opposite of the desired configuration.

By setting the orchestrator type to **Kubernetes** on a worker node, you ensure that **only Kubernetes-managed containers** are scheduled on that node, excluding Docker Swarm workloads.

Let me know if you need additional help!
