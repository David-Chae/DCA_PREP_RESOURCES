## 171. Which Docker feature allows you to limit a container's CPU usage?
A. Docker Swarm  
B. Docker Compose  
C. Docker Hub  
D. Docker CPU constraint  

✅ **Correct Answer: D. Docker CPU constraint**

---

### 🧠 **Explanation:**

Docker allows you to **limit a container’s CPU usage** through **CPU constraints** — a set of runtime flags passed when starting a container.

Here’s how it works:

---

### ⚙️ **CPU Constraint Options in Docker:**

When you run a container, you can use:

- `--cpus`  
  → Limit the **total number of CPUs**. Example: `--cpus="1.5"`  

- `--cpu-shares`  
  → Set **relative CPU weight** (used when multiple containers compete for CPU).  

- `--cpu-quota` and `--cpu-period`  
  → Advanced controls for **fine-grained throttling**.  

---

### ❌ Why Not the Others?

- **A. Docker Swarm** → It's an orchestration tool, not for setting resource limits directly.
- **B. Docker Compose** → It can define CPU limits, but it's just a YAML wrapper around Docker run; the *feature* is still CPU constraints.
- **C. Docker Hub** → This is a cloud-based registry, not related to container runtime behavior.

---

### ✅ Summary:

The **feature** that enables CPU usage limits is **Docker CPU constraint** (option D), regardless of whether you apply it via CLI, Docker Compose, or Swarm templates.

Let me know if you'd like command examples or Compose syntax for CPU limits!
