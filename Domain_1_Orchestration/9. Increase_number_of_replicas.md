# Increasing the Number of Replicas in Docker Swarm

## Introduction
In Docker Swarm, **replicas** determine the number of instances of a service running within the cluster. You may need to scale your services up or down to handle load changes efficiently. This guide explains how to increase the number of replicas for a service.

---

## 1. Checking the Current Number of Replicas
Before scaling, check the current replica count:
```sh
docker service ls
```
This displays information about running services, including their replica counts.

To inspect a specific service:
```sh
docker service inspect <service_name> --format '{{.Spec.Mode.Replicated.Replicas}}'
```

---

## 2. Increasing Replicas
To scale a service, use:
```sh
docker service scale <stack_name>_<service_name>=<replica_count>
```
Example:
```sh
docker service scale my_stack_web=5
```
This increases the number of `web` service replicas to 5.

Alternatively, update the service:
```sh
docker service update --replicas <replica_count> <service_name>
```
Example:
```sh
docker service update --replicas 10 my_service
```

---

## 3. Verifying the Update
To confirm the changes:
```sh
docker service ps <service_name>
```
This lists the running tasks and their states.

---

## 4. Scaling via `docker-compose.yml`
If using a **stack file**, update the `deploy` section:
```yaml
services:
  web:
    image: nginx:latest
    deploy:
      replicas: 5
```
Then, apply the changes:
```sh
docker stack deploy -c docker-compose.yml my_stack
```

---

## 5. Relevant Official Documentation
- [Docker Service Scale](https://docs.docker.com/engine/reference/commandline/service_scale/)
- [Docker Service Update](https://docs.docker.com/engine/reference/commandline/service_update/)
- [Docker Swarm Mode](https://docs.docker.com/engine/swarm/)

## Asciinema Examples
- [Increase number of replicas](https://asciinema.org/a/224629)

By scaling replicas efficiently, you ensure high availability and optimal resource utilization in your Docker Swarm environment. ??
