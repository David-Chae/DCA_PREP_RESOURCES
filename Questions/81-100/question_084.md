## 84. How do you ensure that an existing worker node in a UCP cluster only executes containers managed by Kubernetes and not Docker Swarm?
```
A. Set Kubernetes as the default orchestrator.  
B. In the UCP UI, change the orchestrator type to Swarm.  
C. In the UCP UI, change the orchestrator type to Mixed.  
D. In the UCP UI, change the orchestrator type to Kubernetes.  
```

The correct answer is:

The correct answer is:

**D. In the UCP UI, change the orchestrator type to Kubernetes.**

### Explanation:

In Docker Universal Control Plane (UCP), you can configure **which orchestrator** a node uses:

- **Swarm**: The node will run only **Swarm services**.
- **Kubernetes**: The node will run only **Kubernetes workloads**.
- **Mixed**: The node can run **both Swarm and Kubernetes** workloads.

### To ensure the node **only executes Kubernetes-managed containers**, you should:

👉 **Change the orchestrator type to Kubernetes** in the UCP UI (or via CLI/API if needed).

This ensures that the node will **not participate in Swarm orchestration** and will be dedicated solely to Kubernetes workloads.

✅ **Correct Answer: D**  
Let me know if you'd like the steps to change this setting in the UCP UI!
### **Final Answer:**  
✔ **A. Set Kubernetes as the default orchestrator.**
