## In a Kubernetes, what happens when you perform a rolling update using a Deployment?  
1. A new ReplicaSet is created, which gradually increases its replica count. Meanwhile, the old ReplicaSet gradually decreases its replica count as new Pods spin up. 
2. The Deployment's ReplicaSet deletes its existing Pods gradually, replacing them with new ones. 
3. The Deployment creates a new Service, which gradually replaces the old Service. 
4. The old Pods are removed, and new ones are created once fully terminated.

The correct description of how a **Kubernetes Deployment** updates its Pods is:  

✅ **"A new ReplicaSet is created, which gradually increases its replica count. Meanwhile, the old ReplicaSet gradually decreases its replica count as new Pods spin up."**  

### **Explanation:**  
- **Kubernetes Deployments** use a **rolling update** strategy by default.  
- When a new Deployment version is applied:  
  1. A **new ReplicaSet** is created.  
  2. The new ReplicaSet **gradually increases** its Pod count.  
  3. The old ReplicaSet **gradually decreases** its Pod count.  
  4. This continues until all old Pods are replaced by new Pods.  

### **Why the Other Statements Are Incorrect:**  
❌ **"The Deployment's ReplicaSet deletes its existing Pods gradually, replacing them with new ones."**  
- The **ReplicaSet itself** does not delete its Pods one by one. Instead, Kubernetes **creates a new ReplicaSet** and scales the old one down.  

❌ **"The Deployment creates a new Service, which gradually replaces the old Service."**  
- **Deployments do not create Services.** Services remain unchanged during updates and continue routing traffic to available Pods.  

❌ **"The old Pods are removed, and new ones are created once fully terminated."**  
- This describes a **Recreate strategy**, where old Pods are **terminated first** before new ones start.  
- The default **RollingUpdate strategy** works **incrementally**, so old and new Pods **coexist** during the update.  

### **Final Answer:**  
✅ **"A new ReplicaSet is created, which gradually increases its replica count. Meanwhile, the old ReplicaSet gradually decreases its replica count as new Pods spin up."**
