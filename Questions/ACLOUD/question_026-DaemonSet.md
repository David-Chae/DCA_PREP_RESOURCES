## You have a background maintenance and cleanup application that needs to run on each Node a Kubernetes cluster. Which Kubernetes object would allow you to deploy one replica of this application to each Node?
```
Service
ReplicaSet
Deployment
DaemonSet
```

The correct answer is **DaemonSet**.

### Explanation:
- **DaemonSet** is a Kubernetes object that ensures a specified pod runs on all (or a subset of) nodes in a cluster. In your case, since you need one replica of the application to run on each node, a **DaemonSet** is the most suitable choice.
  
  - When you create a **DaemonSet**, Kubernetes automatically ensures that the application runs on each node in the cluster. If nodes are added or removed, the DaemonSet ensures that the application is scheduled and run on the new nodes or removed from the deleted nodes.
  
  - **DaemonSet** is commonly used for applications like log collectors, monitoring agents, or background maintenance tasks, which need to run on every node.

### Why the other options are incorrect:
- **Service**: A Kubernetes Service is used to expose a set of pods (typically replicas) within a cluster. It does not control the scheduling of pods to nodes.
  
- **ReplicaSet**: A ReplicaSet ensures that a specified number of pod replicas are running at any given time. However, it does not guarantee that the application will run on every node. It only ensures the number of pods (replicas) is maintained.

- **Deployment**: A Deployment is used to manage replicas of an application and ensures that a certain number of pods are running, but it does not guarantee that each node will have a pod. It is more suited for managing the scaling and rollout of pods rather than ensuring they run on every node.

### Summary:
To deploy one replica of an application to **each node** in a Kubernetes cluster, you would use a **DaemonSet**.
