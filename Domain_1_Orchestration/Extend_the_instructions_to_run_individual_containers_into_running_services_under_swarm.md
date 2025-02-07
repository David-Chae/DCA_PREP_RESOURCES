# Running Services Under Docker Swarm

## 1. Initialize a Swarm Cluster
If you haven’t already, initialize a Swarm cluster on your manager node:

```sh
docker swarm init
```

If you have multiple nodes, join worker nodes to the Swarm using the token from:

```sh
docker swarm join-token worker
```

## 2. Deploy Services in Swarm
Instead of running standalone containers with `docker run`, deploy services using `docker service create`:

```sh
docker service create --name my-service --replicas 3 -p 80:80 nginx
```

This command runs an Nginx service with three replicas, exposing port 80.

## 3. Managing Services
- List services:
  
  ```sh
  docker service ls
  ```

- Scale a service:
  
  ```sh
  docker service scale my-service=5
  ```

- Update a service:
  
  ```sh
  docker service update --image nginx:latest my-service
  ```

## 4. Deploy Multi-Service Applications with Stacks
For complex applications, use **Docker Compose with Swarm mode**:

1. Define `docker-compose.yml`:
    
    ```yaml
    version: "3.8"
    services:
      web:
        image: nginx
        ports:
          - "80:80"
      redis:
        image: redis:alpine
    ```
    
2. Deploy it as a stack:
    
    ```sh
    docker stack deploy -c docker-compose.yml my-stack
    ```

## 5. Monitoring and Troubleshooting
- Check service logs:
  
  ```sh
  docker service logs my-service
  ```

- Inspect service details:
  
  ```sh
  docker service inspect my-service
  ```

## Relevant Official Documentations
- [Deploy a service to the swarm](https://docs.docker.com/engine/swarm/swarm-tutorial/deploy-service/)
- [Swarm Mode Overview](https://docs.docker.com/engine/swarm/)
- [Deploying Services](https://docs.docker.com/engine/swarm/services/)
- [Docker Stack Deploy](https://docs.docker.com/engine/reference/commandline/stack_deploy/)
- [Managing Nodes in Swarm](https://docs.docker.com/engine/swarm/manage-nodes/)
