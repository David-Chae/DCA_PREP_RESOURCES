## 66. You have a web application front-end that will need to be accessed by users and a backend database that the front-end Pods will access. Both of these components are running within your Kubernetes cluster. Which Service types should you use to expose the web front-end and the backend database, respectively?
```sh
A. NodePort, ClusterIP
B. ClusterIp for both.
C. NodePort for both.
D. None of the above
```


The correct answer is:  

**A. NodePort, ClusterIP**  

### Explanation:  
- **NodePort** should be used for the **web front-end** because it needs to be accessible externally by users. The `NodePort` service exposes the application on a static port across all nodes in the cluster, making it accessible from outside the cluster.
  
- **ClusterIP** should be used for the **backend database** because it doesn't need to be accessed directly from outside the cluster. The `ClusterIP` service is only accessible within the Kubernetes cluster, which is ideal for internal services like a database that the front-end Pods can access.

### Why not the others?  
- **B. ClusterIP for both**: While this would work for internal communication, it would not expose the web front-end to external users.  
- **C. NodePort for both**: While a `NodePort` service would expose both services externally, it is not necessary to expose the backend database in this way, as it only needs to be accessed internally within the cluster.  
- **D. None of the above**: Since option A is correct, this option is incorrect.
