## 1. Which command is valid for running a global service in Docker Swarm?

```sh
1. docker service create --mode global 
2. docker swarm create --mode global 
3. docker service create --global 
4. docker swarm create --global
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




## 2. Excluding Python Byte-Code Files During Docker Image Creation: Which patterns would exclude all Python byte-code files from being copied?

```sh
1. **.pyc
2. **/*.pyc
3. *.pyc
4. /*.pyc
```

To exclude all Python bytecode files (`.pyc`) from being copied during Docker image creation (when using `COPY` or `ADD` in a `Dockerfile`), the correct patterns to use in a `.dockerignore` file are:

### Correct Patterns:
1. `**/*.pyc` ✅  
   - This pattern ensures that **all** `.pyc` files, no matter where they are in the directory structure, are excluded.

2. `*.pyc` ✅  
   - This only excludes `.pyc` files in the root directory, **not** in subdirectories.

### Incorrect or Incomplete Patterns:
1. `**.pyc` ❌  
   - This is incorrect because `**` matches directories, but `**.pyc` is not a valid pattern in `.dockerignore`.

2. `/*.pyc` ❌  
   - This only excludes `.pyc` files **directly in the root directory**, not in subdirectories.

### Recommended `.dockerignore` Entry:
To exclude all Python bytecode files, use:

```
**/*.pyc
```

or

```
*.pyc
**/*.pyc
```

for full coverage.
