## Which of the following commands will publish a service's port, but only on nodes that are running a task for that service?
```
docker service create -p mode=ingress,published=8082,target=80 nginx
docker service create -p mode=host,published=8082,target=80 nginx
docker service create -p 8080:80 nginx
docker service create -p 8080:80 --mode host nginx
```

The correct command to **publish a service's port only on nodes that are running a task for that service** is:

### **`docker service create -p mode=host,published=8082,target=80 nginx`**

---

### Explanation:

- **`mode=host`**: This setting ensures that the port is published directly on the host node where the task is running, rather than using the default **ingress mode** which publishes the port on all nodes in the swarm. By using `mode=host`, the port is exposed only on the nodes that actually run tasks for the service.
  
- **`published=8082`**: This is the external port on the host that will be used to access the service.
  
- **`target=80`**: This is the internal port within the container.

### Why the other options are incorrect:

- **`docker service create -p mode=ingress,published=8082,target=80 nginx`**:  
  This would publish the port in **ingress mode**, which means that the port is exposed on **all nodes in the swarm**, not just on nodes running tasks for the service.

- **`docker service create -p 8080:80 nginx`**:  
  This would create a service with the port **8080** on the host mapped to **80** in the container, but it would publish it across all nodes (default behavior), which is not limited to only nodes running tasks.

- **`docker service create -p 8080:80 --mode host nginx`**:  
  The `--mode` flag here is incorrectly placed. The correct flag for specifying the mode is `mode=host`, but `--mode` is not a valid flag for this command syntax.

---

### Correct Answer:
```bash
docker service create -p mode=host,published=8082,target=80 nginx
```

This ensures the service's port is exposed **only on nodes running tasks** for that service.
REF: [docker service create](https://docs.docker.com/reference/cli/docker/service/create/#publish)
