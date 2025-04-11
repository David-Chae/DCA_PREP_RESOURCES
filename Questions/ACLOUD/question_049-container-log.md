## Which of the following commands would we use to view a container's logs?
```
1. sudo journalctl -u docker
2. docker service logs <service>
3. docker logs <container>
4. docker container get-log
```

✅ **Correct answer:**  
**`docker logs <container>`**

---

### 🔍 Explanation of each option:

1. **`sudo journalctl -u docker`**  
   🔸 **False** – This shows the logs of the **Docker daemon itself**, not the logs of individual containers.

2. **`docker service logs <service>`**  
   🔸 **True but limited** – This is valid **only for services in Docker Swarm mode**, not for standalone containers.

3. **✅ `docker logs <container>`**  
   ✔️ **True** – This is the **standard and correct way** to view logs from a specific container.

4. **`docker container get-log`**  
   ❌ **False** – This is **not a valid Docker command**.

---

Would you like examples of how to tail logs, follow logs in real time, or filter them by time?
