# Replicated vs Global Service in Docker Swarm

## Running a Replicated vs Global Service

Docker Swarm allows you to deploy services in two different modes:

1. **Replicated Service**: Runs a specified number of replicas across nodes.
2. **Global Service**: Runs one instance on every available node.

---

## Running a Replicated Service

A **replicated** service ensures that a specific number of instances run across the cluster.

```sh
# Create a replicated service with 3 replicas
docker service create --name my_replicated_service --replicas 3 nginx
```

- This deploys three instances of `nginx` across available nodes.
- If a node fails, Swarm reschedules the replicas on healthy nodes.

---

## Running a Global Service

A **global** service ensures that one instance runs on every node in the cluster.

```sh
# Create a global service
docker service create --name my_global_service --mode global nginx
```

- This guarantees that every worker node runs exactly one instance of `nginx`.
- If a new node joins, it automatically gets an instance.

---

## Visual Representation

| Service Mode  | Number of Instances | Behavior |
|--------------|------------------|----------|
| Replicated  | User-defined (e.g., 3) | Runs only on some nodes |
| Global      | One per node | Runs on all nodes |

---

## Official Documentation
- [Docker Swarm Services Documentation](https://docs.docker.com/engine/swarm/services/)

## Asciinema Examples
- [Illustrate running a replicated vs global service](https://asciinema.org/a/224928)
