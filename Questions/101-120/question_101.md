## 101. Which of the following is a Linux container?
A. Kernel capabilities  
B. Processes  
C. Daemon  
D. Control group  

The correct answer is:  

✅ **D. Control group**  

---

### Explanation:
A **Linux container** is a lightweight, portable, and isolated environment that runs applications using the **host machine’s Linux kernel**. Several Linux kernel features enable containers, including:  

- **Control Groups (cgroups) → (Correct Answer)**  
  - **cgroups** limit and allocate resources (CPU, memory, disk I/O, network) for containers.  
  - They ensure that one container does not consume excessive system resources.  

#### Breakdown of the other options:

| Option | Explanation | Correct? |
|---------|------------------------------------------------|------------|
| **A. Kernel capabilities** | ❌ **Incorrect**: Kernel capabilities define fine-grained privileges but do not define a container itself. | ❌ No |
| **B. Processes** | ❌ **Incorrect**: Containers run processes, but a process alone is not a container. | ❌ No |
| **C. Daemon** | ❌ **Incorrect**: The Docker daemon (`dockerd`) manages containers but is not itself a Linux container. | ❌ No |
| **D. Control group** | ✅ **Correct**: cgroups enforce resource constraints, which is a key part of containerization. | ✅ **Yes** |

Thus, the best answer is **D. Control group (cgroup)** ✅
