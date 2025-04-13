# Converting an Application Deployment into a Stack File

## Introduction
Deploying applications using Docker can be simplified by defining services in a **YAML-based compose file**. When using **Docker Swarm mode**, you can deploy these services as a **stack** using `docker stack deploy`.

---

## 1. Create a `docker-compose.yml` File
A `docker-compose.yml` file defines the services, networks, and volumes for your application. Below is an example:

### Example `docker-compose.yml`
```yaml
version: '3.8'

services:
  web:
    image: nginx:latest
    ports:
      - "80:80"
    deploy:
      replicas: 3
      restart_policy:
        condition: on-failure

  db:
    image: mysql:5.7
    environment:
      MYSQL_ROOT_PASSWORD: example
```

---

## 2. Initialize Docker Swarm (If Not Already Active)
Ensure your system is in Swarm mode:
```sh
docker swarm init
```

---

## 3. Deploy the Stack
Use `docker stack deploy` to deploy the services as a stack:
```sh
docker stack deploy -c docker-compose.yml my_stack
```

- `-c docker-compose.yml` specifies the compose file.
- `my_stack` is the stack name.

To verify the deployment:
```sh
docker stack ls            # List deployed stacks
docker stack services my_stack  # List services in the stack
docker stack ps my_stack       # List running containers in the stack
```

---

## 4. Removing the Stack
If you need to remove the deployed stack, run:
```sh
docker stack rm my_stack
```

---

## 5. Relevant Official Documentation
- [Docker Compose File Reference](https://docs.docker.com/compose/compose-file/)
- [Docker Stack Deploy](https://docs.docker.com/engine/swarm/stack-deploy/)
- [Docker Swarm Mode](https://docs.docker.com/engine/swarm/)

## 6. Asciinema Examples
- [Convert an application deployment into a stack file using a YAML compose file with docker stack deploy](https://asciinema.org/a/224532)

By using `docker stack deploy`, you can efficiently manage multi-container applications in a scalable and reliable manner. ??
