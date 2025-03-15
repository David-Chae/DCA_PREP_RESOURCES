## You have a background maintenance and cleanup application that must run on each Kubernetes cluster Node. Which Kubernetes object would allow you to deploy one replica of this application to each Node? 
1. ReplicaSet 
2. DaemonSet 
3. Deployment 
4. Service

The correct answer is:  

✅ **DaemonSet**  

### **Explanation:**  
- A **DaemonSet** ensures that **one copy** of a pod runs **on every node** in a Kubernetes cluster.  
- This is **ideal for background maintenance and cleanup tasks** that must be executed on **each node** (e.g., log collection, monitoring agents, node cleanup, etc.).  

### **Why the Other Options Are Incorrect:**  
❌ **ReplicaSet**  
- A **ReplicaSet** ensures that a specified **number of pod replicas** are running, but **does not guarantee** one per node.  
- Pods could be scheduled on some nodes but not others.  

❌ **Deployment**  
- A **Deployment** manages ReplicaSets and rolling updates, but **does not ensure** that one pod runs on each node.  
- It is meant for **scaling applications**, not for ensuring per-node execution.  

❌ **Service**  
- A **Service** provides networking and load balancing for a group of pods, but **does not deploy pods**.  
- It is used for **exposing applications**, not for running background tasks.  

### **Final Answer:**  
✅ **DaemonSet**
