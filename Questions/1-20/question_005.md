## You want to ensure that a container does not use more memory than it should. To do this, which of the following will be used by default by Docker?

```sh
namespaces
selinux
cgroups
seccomp
```

### Correct Answer:
✅ **`cgroups` (Control Groups)**  

### Explanation:
- **cgroups (Control Groups)** are used by Docker to **limit and allocate system resources**, including **memory, CPU, and I/O bandwidth**, to containers.
- By default, Docker applies memory limits using **cgroups**, ensuring that a container does not exceed its allocated resources.

---

### Incorrect Options:
❌ **`namespaces`**  
- Namespaces provide **isolation** for processes, network, and filesystems but do **not** enforce resource limits.

❌ **`selinux` (Security-Enhanced Linux)**  
- SELinux is a **security module** that controls access policies, not resource limits.

❌ **`seccomp` (Secure Computing Mode)**  
- seccomp is used to **restrict system calls** that a container can execute, mainly for security, not for resource control.

---

### Example: Setting a Memory Limit with `cgroups`
To limit a container to **512MB of memory**, use:

```sh
docker run --memory=512m ubuntu
```

This enforces the limit using **cgroups**.



