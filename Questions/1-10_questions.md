## 1. Which command is valid for running a global service in Docker Swarm?

```sh
docker service create --mode global 
docker swarm create --mode global 
docker service create --global 
docker swarm create --global
```

The correct command for running a global service in Docker Swarm is:

```sh
docker service create --mode global
```

### Explanation:
- `docker service create`: This command is used to create a service in Docker Swarm.
- `--mode global`: This ensures that the service runs on every node in the Swarm.

### Incorrect Commands:
1. `docker swarm create --mode global` ❌  
   - `docker swarm create` is not a valid command. To initialize a Swarm, you use `docker swarm init`.

2. `docker service create --global` ❌  
   - The `--global` flag does not exist. Instead, you must use `--mode global`.

3. `docker swarm create --global` ❌  
   - Again, `docker swarm create` is not a valid command.

### Example Usage:
To create a global service that runs on all nodes, use:

```sh
docker service create --name my_global_service --mode global nginx
```

This will deploy an Nginx container on every node in the Swarm.
