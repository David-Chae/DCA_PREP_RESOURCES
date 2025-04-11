The correct answer is:
## Amanda wants to execute a one-time job using a Docker container. However, occasionally, this job fails and needs to restart. Amanda doesn't want to restart it manually if it fails. Which command should she use to make sure that the container executes the one-time job successfully?
```
1. docker run --restart on-failure cleanup-job 
2. docker run --restart unless-stopped cleanup-job 
3. docker run --restart failure-only cleanup-job 
4. docker run --recover-failure cleanup-job
```

> **✅ 1. `docker run --restart on-failure cleanup-job`**

---

### ✅ Explanation:

- `--restart on-failure`  
  This policy **restarts the container only if it exits with a non-zero exit code**, which is ideal for Amanda's case where the job **sometimes fails**.
  - It’s commonly used for **one-time jobs** or scripts that might fail due to transient errors.

---

### ❌ Option 2: `--restart unless-stopped`  
- This keeps the container running **regardless of exit code**, even after a reboot, **until it’s manually stopped** — not ideal for one-time jobs.

### ❌ Option 3: `--restart failure-only`  
- 🔴 **Invalid option** — not a real Docker flag.

### ❌ Option 4: `--recover-failure`  
- 🔴 **Also invalid** — not a valid Docker CLI flag.

---

### 🔁 Summary:

| Option | Valid? | Description | Appropriate for Amanda? |
|--------|--------|-------------|--------------------------|
| `--restart on-failure` | ✅ Yes | Restarts only on non-zero exit code | ✔️ Yes |
| `--restart unless-stopped` | ✅ Yes | Restarts always unless manually stopped | ❌ No |
| `--restart failure-only` | ❌ No | Not a valid flag | ❌ No |
| `--recover-failure` | ❌ No | Not a valid flag | ❌ No |

Let me know if you’d like a full command example using `docker run` for Amanda's use case!
