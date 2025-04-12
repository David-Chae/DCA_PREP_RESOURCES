To **self-test** this Docker Certified Associate (DCA) exam topic:

> **"Describe and demonstrate how to extend the instructions to run individual containers into running services under Swarm"**

You're basically being asked to **convert a standalone container** into a **Swarm service**, and know the differences, advantages, and syntax involved.

---

### ✅ Step-by-Step Self-Test Plan

---

#### 🧪 Step 1: Start With a Basic Container

Run a container as you normally would:

```bash
docker run -d --name web1 -p 8080:80 nginx
```

This runs a simple Nginx container.

Check it:

```bash
docker ps
curl localhost:8080
```

---

#### 🐝 Step 2: Initialize Docker Swarm (if not already)

```bash
docker swarm init
```

Note the **advertise address** if needed. You're now in Swarm mode.

---

#### 🔄 Step 3: Convert the Container to a Swarm Service

Run the equivalent **service** instead:

```bash
docker service create --name web-service -p 8080:80 nginx
```

Check it:

```bash
docker service ls
docker service ps web-service
curl localhost:8080
```

---

#### 🧠 Step 4: Understand Differences

| Feature | `docker run` | `docker service create` |
|--------|---------------|--------------------------|
| Container | Standalone | Managed by Swarm |
| Replicas | Not supported | `--replicas` flag |
| Restart | `--restart` policy | Built-in health and rescheduling |
| Networking | Bridge | Overlay (in Swarm) |
| Scaling | Manual | `docker service scale` |
| Deployment | One container | Declarative service definition |

---

#### 🧪 Step 5: Test Scaling

Scale your service up:

```bash
docker service scale web-service=3
```

Check:

```bash
docker service ps web-service
```

You'll see multiple **replicas** scheduled across the Swarm.

---

#### 📄 Step 6: Try a Compose File (Optional)

If you want to go further, define a simple `docker-compose.yml`:

```yaml
version: "3"
services:
  web:
    image: nginx
    ports:
      - "8080:80"
    deploy:
      replicas: 3
```

Deploy to Swarm:

```bash
docker stack deploy -c docker-compose.yml mystack
docker stack services mystack
```

---

### 📝 Practice Checklist

- [x] Ran a standalone container.
- [x] Initialized a Swarm.
- [x] Ran a service using `docker service create`.
- [x] Compared differences between `run` and `service create`.
- [x] Scaled the service.
- [ ] (Optional) Deployed a stack using `docker stack deploy`.

---

Want a short quiz-style self-test too?
