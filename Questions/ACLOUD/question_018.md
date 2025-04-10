## What should we use if we need to run multiple copies of a single image in a swarm?
```
We should run the docker-compose command.
We should use a task.
We should use a service.
We should use a stack.
```

✅ **Correct answer: We should use a _service_.**

---

### 💡 Here's why:

In **Docker Swarm**, if you want to run **multiple copies of the same containerized application**, you define a **_service_** and scale it to the desired number of replicas.

---

### 🔧 `service` in Docker Swarm
- A **service** is the fundamental unit of deployment in a Swarm.
- When you create a service, you can specify:
  - The **image** to run
  - The **number of replicas**
  - **Ports**, **networks**, **constraints**, etc.

#### Example:
```bash
docker service create --name my-web --replicas 3 nginx
```
This creates **3 running instances** (replicas) of the `nginx` container across the swarm.

---

### What about the other options?

- ❌ **docker-compose command**: Used for multi-container local development; not directly for managing a Swarm unless used with `docker stack deploy`.

- ❌ **task**: A task is a low-level component—an instance of a container created by a service. You don’t directly manage tasks.

- ❌ **stack**: A stack is a collection of services defined in a `docker-compose.yml` file and deployed together using `docker stack deploy`. Useful, but **overhead** if you're only managing one service.

---

### ✅ So in summary:
> If you want to run **multiple copies of a single image** in a Docker Swarm, you should use a **service**.

Let me know if you want an example with `docker-compose.yml` or `stack` as well!
