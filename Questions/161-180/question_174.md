## 174. As a stack, the following Docker Compose file is deployed:
```yaml
version: "3.1'  
services:  
  app:  
    image: app :1.0  
    healthcheck  
      test:"curl --fail https://localhost/health || exit 1"  
      interval: 10s  
      timeout: 5s  
      retries: 3  
```

Is the given solution remark about the definition of a health check correct?  
Solution. App health checks should be done every ten seconds. Three failed health checks put the container in the "unhealthy" category  
A. Yes  
B. No  

✅ **Correct Answer: A. Yes**

---

### 📘 **Explanation:**

Let's break down the `healthcheck` section of the given Docker Compose YAML:

```yaml
healthcheck:
  test: "curl --fail https://localhost/health || exit 1"
  interval: 10s
  timeout: 5s
  retries: 3
```

---

### 🔍 What each directive means:

- **`test:`**  
  → Runs the command: `curl --fail https://localhost/health || exit 1`  
  If the curl fails, the container exits with non-zero status → indicating a failed health check.

- **`interval: 10s`**  
  → Docker runs the health check **every 10 seconds**.

- **`timeout: 5s`**  
  → Docker gives each health check **5 seconds** to complete.

- **`retries: 3`**  
  → If the check **fails 3 times in a row**, the container status becomes **"unhealthy"**.

---

### 🟢 So the solution statement is:

> "**App health checks should be done every ten seconds. Three failed health checks put the container in the 'unhealthy' category.**"

This is **accurate** based on the health check configuration.

---

### ✅ Therefore, the answer is: **A. Yes**

Let me know if you want help tweaking or testing health checks!


175. Could the failure of a user’s attempts to set the system time from within a Docker container constitute a hindrance to the operation of the container? A. Yes B. No   176. Will the given command return a list of volumes for a given container? docker container inspect nginx A. Yes B. No   177. How to remove the label from the node?
