## 191. Will the given command from the commandline list all nodes in a swarm cluster?
docker inspect nodes
A. Yes  
B. No  

**B. No**  

The correct command to list all nodes in a Docker Swarm cluster is:  

```sh
docker node ls
```

The command `docker inspect nodes` is incorrect because:  
- `docker inspect` is used to inspect details of a specific object (e.g., containers, images, volumes, networks, or nodes), but it does not list all nodes.  
- The correct syntax for inspecting a specific node is:  

  ```sh
  docker node inspect <node-name>
  ```  

To see all nodes, you must use `docker node ls`.
