# Manipulating a Running Stack of Services in Docker Swarm

## Introduction
Once a stack of services is deployed in Docker Swarm mode, you may need to update, scale, or troubleshoot services. This guide covers essential commands for manipulating a running stack.  
A running stack of services on Docker Swarm can be manipulated in different ways: docker stack ls shows an overview of all existing stacks.  
docker stack ps STACK lists all tasks in a stack, while docker stack services STACK gives an overview over the running services. docker stack rm STACK removes said stack.  

---

## 1. Listing Running Stacks and Services
To view all running stacks:
```sh
docker stack ls
```
To list services within a specific stack:
```sh
docker stack services <stack_name>
```
To see tasks (containers) running in a stack:
```sh
docker stack ps <stack_name>
```

---

## 2. Scaling Services
To scale a service within a stack:
```sh
docker service scale <stack_name>_<service_name>=<replica_count>
```
Example:
```sh
docker service scale my_stack_web=5
```

---

## 3. Updating a Service in a Stack
To update an existing service (e.g., changing the image version):
```sh
docker service update --image <new_image> <stack_name>_<service_name>
```
Example:
```sh
docker service update --image nginx:latest my_stack_web
```
Additional update options include:
- `--replicas <num>`: Change the number of replicas
- `--env-add VAR=value`: Add an environment variable
- `--limit-cpu <value>`: Set CPU limits

---

## 4. Rolling Back a Service
If an update fails, rollback to the previous version:
```sh
docker service rollback <stack_name>_<service_name>
```

---

## 5. Restarting a Service
To force a restart of all tasks in a service:
```sh
docker service update --force <stack_name>_<service_name>
```

---

## 6. Removing a Service from a Stack
To remove a specific service:
```sh
docker service rm <stack_name>_<service_name>
```

---

## 7. Removing the Entire Stack
To stop and remove a running stack:
```sh
docker stack rm <stack_name>
```

---

## 8. Inspecting a Running Stack
To inspect the details of a running stack:
```sh
docker stack ps <stack_name> --no-trunc
```
To inspect a specific service:
```sh
docker service inspect <stack_name>_<service_name>
```

---

## 9. Relevant Official Documentation
- [docker stack services](https://docs.docker.com/reference/cli/docker/stack/services/#related-commands)
- [Managing Services in Docker Swarm](https://docs.docker.com/engine/swarm/manage-services/)
- [Docker Stack Deploy](https://docs.docker.com/engine/swarm/stack-deploy/)
- [Docker Service Update](https://docs.docker.com/engine/reference/commandline/service_update/)

## Asciinema Examples
- [Manipulate a running stack of services](https://asciinema.org/a/224533)

By using these commands, you can efficiently manage and manipulate running services within a Docker Swarm stack. ??
