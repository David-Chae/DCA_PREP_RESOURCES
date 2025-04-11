## When creating an overlay network, what flag can we use to allow containers to attach to the network after it is created?
```
1. --network-driver attachable
2. --attachable
3. --attach=true
4. --open true
```

✅ **Correct answer:**  
**`--attachable`**

---

### 🔍 Explanation of each option:

1. **`--network-driver attachable`**  
   ❌ **False** – `--network-driver` is not a valid flag, and `attachable` is not a driver name.

2. **✅ `--attachable`**  
   ✔️ **True** – This is the **correct flag** to make an **overlay network attachable**, allowing standalone containers (not part of services) to connect to it after creation.

3. **`--attach=true`**  
   ❌ **False** – This is **not a valid flag** for `docker network create`.

4. **`--open true`**  
   ❌ **False** – There is **no such flag** in Docker's network commands.

---

### 🧪 Example command:

```bash
docker network create --driver overlay --attachable my-overlay
```

Let me know if you’d like to see how to connect a running container to an attachable overlay network.
