## 127. Which of the following mounts the secret into the service container?
A. tmpfs Mount  
B. npipe Mount  
C. Volume Mount  
D. Bind Mount  

The correct answer is:  

**A. tmpfs Mount**  

- **tmpfs Mount** is used to store sensitive data, such as **secrets**, in memory instead of writing them to disk.  
- It ensures that secrets do not persist after the container stops, enhancing security.  
- This is particularly useful in **Docker Swarm** when using **Docker secrets**.

### Docker Documentation
tmpfs mounts
A tmpfs mount stores files directly in the host machine's memory, ensuring the data is not written to disk. This storage is ephemeral: the data is lost when the container is stopped or restarted, or when the host is rebooted. tmpfs mounts do not persist data either on the Docker host or within the container's filesystem.

These mounts are suitable for scenarios requiring temporary, in-memory storage, such as caching intermediate data, handling sensitive information like credentials, or reducing disk I/O. Use tmpfs mounts only when the data does not need to persist beyond the current container session.
(REF: https://docs.docker.com/engine/storage/)
