## 183.Is it feasible to group Kubernetes-specific resources, such as secrets, for each application by including all resources in the default namespace?
A. Yes  
B. No  

**B. No**  

### Explanation:  
While it is possible to place all Kubernetes resources (such as Secrets, ConfigMaps, Pods, and Services) in the **default** namespace, it is **not recommended** for organizational and security reasons.  

- **Namespaces help separate applications**: Using different namespaces for different applications or environments (e.g., `dev`, `staging`, `prod`) prevents conflicts and makes resource management easier.  
- **Access control & security**: Kubernetes RBAC (Role-Based Access Control) works better when resources are properly grouped into separate namespaces.  
- **Avoid cluttering the default namespace**: If all secrets and resources are in the `default` namespace, it becomes difficult to manage them efficiently.  

**Best Practice**:  
- Create a dedicated namespace for each application using:  
  ```sh
  kubectl create namespace my-app
  ```
- Apply resources to that namespace using `-n my-app` when deploying:  
  ```sh
  kubectl apply -f my-app-deployment.yaml -n my-app
  ```
