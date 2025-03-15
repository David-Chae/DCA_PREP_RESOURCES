## 101. Which of the following is a Linux container?
A. Kernel capabilities  
B. Processes  
C. Daemon  
D. Control group  

The correct answer is:

**B. Processes**

### **Explanation:**

A **Linux container** is essentially a lightweight, isolated environment that runs processes. These processes share the same kernel but are isolated from each other. The main components that enable this isolation are:

- **Kernel capabilities**: These are a set of features in the Linux kernel that control and limit the actions that a process can perform.
- **Processes**: Containers are composed of processes that are isolated from the rest of the system using namespaces and cgroups. Each container runs its own process or set of processes.
- **Daemon**: The Docker daemon (`dockerd`) is responsible for managing containers, but it is not itself a container.
- **Control group (cgroup)**: These are used to limit, account for, and isolate resource usage for processes, but they are not containers themselves.

Thus, the processes running inside a container are the key element of what constitutes a Linux container.

---

### **Final Answer:**
**B. Processes**
