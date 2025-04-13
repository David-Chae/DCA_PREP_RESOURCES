Great question! The `--filter` (or `-f`) flag in Docker is super useful for **narrowing down results** when listing containers, images, volumes, networks, and more.

---

## 🔍 General Syntax

```bash
docker [command] --filter "key=value"
```

You can use multiple `--filter` flags for more specific filtering.

---

## 🔧 Examples by Docker Command

### 🔹 1. **Filter Containers**

```bash
docker ps --filter "status=exited"
```

Shows only **stopped** containers.

```bash
docker ps -a --filter "name=myapp"
```

Shows containers with names matching `myapp`.

---

### 🔹 2. **Filter Images**

```bash
docker images --filter "dangling=true"
```

Shows **dangling images** (unused layers).

```bash
docker images --filter "reference=redis:7*"
```

Shows images that match a specific tag pattern like `redis:7.0`, `redis:7.2`, etc.

---

### 🔹 3. **Filter Volumes**

```bash
docker volume ls --filter "dangling=true"
```

Lists unused volumes (not attached to any containers).

---

### 🔹 4. **Filter Networks**

```bash
docker network ls --filter "driver=bridge"
```

Shows networks using the bridge driver.

---

### 🔹 5. **Filter Services (Docker Swarm)**

```bash
docker service ls --filter "name=web"
```

Shows services named `web`.

---

### ✅ Common Filter Keys

| Docker Object | Filter Keys                  |
|---------------|------------------------------|
| `docker ps`   | `status`, `name`, `label`    |
| `images`      | `dangling`, `reference`      |
| `volume ls`   | `dangling`, `name`           |
| `network ls`  | `driver`, `name`, `label`    |
| `service ls`  | `name`, `label`, `mode`      |

---

Let me know if you want to filter by labels, or build a cleanup script using filters!
