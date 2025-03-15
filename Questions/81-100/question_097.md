## 97. Amanda wants to use a Docker container to complete a one-time task. However, this task occasionally fails and needs to be redone. If it fails, Amanda does not want to restart it manually. Which command should she issue to guarantee the container completes theone-time job?
A. docker run --restart failure-only cleanup-job
B. docker run --recover-failure cleanup-job
C. docker run --restart unless-stopped cleanup-job
D. docker run --restart on-failure cleanup-job

The correct answer is:  

**D. `docker run --restart on-failure cleanup-job`**  

### Explanation:  
The `--restart` flag in Docker determines the restart policy for a container. The `on-failure` policy ensures that the container automatically restarts **only if it exits with a non-zero status (indicating failure)**. This is ideal for Amanda’s case, where the task sometimes fails and needs to be retried without manual intervention.

#### Why the other options are incorrect:
- **A. `docker run --restart failure-only cleanup-job`**  
  → This is **not a valid Docker restart policy**. The correct option is `on-failure`.  

- **B. `docker run --recover-failure cleanup-job`**  
  → This is **not a valid Docker option**. There is no `--recover-failure` flag in Docker.  

- **C. `docker run --restart unless-stopped cleanup-job`**  
  → This option makes the container restart **indefinitely**, even if it succeeds. Since Amanda wants the task to **complete once** and retry only on failure, this is not the best choice.  

### Correct usage example:
```bash
docker run --restart on-failure cleanup-job
```

This ensures the container automatically retries if it fails but stops once it succeeds. 🚀
