## 220. How to deploy a service in the docker swarm?
A. docker create service --replicas 3 --name nginx-web nginx  
B. docker deploy service --replicas 3 --name nginx-web nginx  
C. docker service deploy --replicas 3 --name nginx-web nginx  
D. docker stack deploy --replicas 3 --name nginx-web nginx  

The correct answer is:  
**None of the above options are exactly correct**, but the **most accurate and valid approach** would be:

### ✅ **To deploy a service in Docker Swarm**, use:
```bash
docker service create --replicas 3 --name nginx-web nginx
```

So, if **option A** had said `docker service create`, it would be correct.

---

### ❌ Let's review the options:

- **A. `docker create service`** – ❌ Invalid syntax. It should be `docker service create`.
- **B. `docker deploy service`** – ❌ Not a real Docker command.
- **C. `docker service deploy`** – ❌ Invalid command; `deploy` is not a subcommand of `docker service`.
- **D. `docker stack deploy --replicas 3`** – ❌ `--replicas` is not used here. With `stack deploy`, you use a **Compose file** to define replicas.

---

### ✅ Two valid ways to deploy in Docker Swarm:
1. **With CLI:**
   ```bash
   docker service create --replicas 3 --name nginx-web nginx
   ```

2. **With a Compose file:**
   ```bash
   docker stack deploy -c docker-compose.yml nginx-stack
   ```

Let me know if you'd like an example Compose file too!
