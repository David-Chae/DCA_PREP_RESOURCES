## Which of the following commands will only broadcast the service port on nodes performing a task for that service? \
1. docker service create -p mode=ingress,published=8082,target=80 nginx
2. docker service create -p 8080:80 --mode host nginx
3. docker service create -p 8080:80 nginx
4. docker service create -p mode=host,published=8082,target=80 nginx ce

The correct command that will only broadcast the service port on nodes performing a task for that service is:

**`docker service create -p mode=host,published=8082,target=80 nginx`**

### **Explanation:**
- **`mode=host`**: This mode binds the port directly to the host's network interface, ensuring that the service port is only exposed on nodes that are running a task for that service.
  - The port `8082` will be exposed on the node's interface where the service is running. It will not be routed across the swarm network (as it would be in `mode=ingress`), and it only affects the nodes with active tasks for that service.

### **Other options:**

1. **`docker service create -p mode=ingress,published=8082,target=80 nginx`**  
   - **`mode=ingress`**: This mode publishes the service port across the swarm cluster, meaning it broadcasts the service port on all nodes, not just the ones running the service tasks.

2. **`docker service create -p 8080:80 --mode host nginx`**  
   - This command is missing the `mode` option (it should be part of `-p`), and also it’s an incorrect syntax. The correct format should be `-p mode=host,published=8080,target=80`.

3. **`docker service create -p 8080:80 nginx`**  
   - This exposes the service port on all nodes in the swarm, regardless of whether the node is running the task or not. This is equivalent to using `mode=ingress`.

### **Final Answer:**
**`docker service create -p mode=host,published=8082,target=80 nginx`** will only broadcast the service port on nodes performing a task for that service.
