## Which commands would we use to view a container's logs? 
1. sudo journalctl -u docker
2. docker logs <container>
3. docker service logs <service>
4. docker container get-log

The correct answers are:

✅ **`docker logs <container>`**

✅ **`docker service logs <service>`**

---

### **Explanation:**

1. **`docker logs <container>`**:
   - This command is used to view the logs of a **specific container**. You replace `<container>` with the container's name or ID.
   - Example:
     ```sh
     docker logs my-container
     ```

2. **`docker service logs <service>`**:
   - This command is used to view the logs for a **service** in Docker Swarm. It allows you to see logs for all the tasks that make up the service.
   - Example:
     ```sh
     docker service logs my-service
     ```

---

### **Why the Other Options Are Incorrect:**

❌ **`sudo journalctl -u docker`**:  
- This command is used to view **system logs** related to the Docker daemon, not the logs of a specific container or service. It's typically used for troubleshooting Docker daemon-related issues, not for container logs.

❌ **`docker container get-log`**:  
- This is **not a valid Docker command**. The correct command for viewing logs is `docker logs <container>`, not `docker container get-log`.

---

### **Summary:**

To view a container's logs, use `docker logs <container>`. For service logs in Docker Swarm, use `docker service logs <service>`.
