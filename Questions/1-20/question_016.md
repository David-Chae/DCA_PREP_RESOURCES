## Which of the following is not a namespace used by Docker? 
1. net
2. pid
3. uts
4. mem

The correct answer is:  

✅ **mem**  

### Explanation:  
Docker uses several namespaces to **isolate** different aspects of containerized applications. The valid namespaces used by Docker include:

- **`net`** (Network Namespace)  
  - This isolates network resources, allowing containers to have their own network interfaces and IP addresses.

- **`pid`** (Process ID Namespace)  
  - This isolates process IDs, so processes in one container cannot see or interfere with processes in another container.

- **`uts`** (UTS Namespace)  
  - This isolates the hostname and domain name, allowing each container to have its own hostname.

However, there is **no `mem` namespace** in Docker. While **memory limits** can be set for containers, **memory** is not isolated by a specific namespace. Memory isolation is typically handled by **cgroups**, not namespaces.

### Summary:
- The **mem** namespace is not a valid namespace in Docker.

### What does UTS stand for in UTS names pace?

**UTS** stands for **Unix Timesharing System**.

### Explanation:
In the context of Docker and Linux namespaces, the **UTS namespace** isolates the hostname and domain name of a container. This means each container can have its own **hostname** and **domain name**, which is independent of the host system or other containers. This is particularly useful in multi-container environments where each container might need a unique identity.

### Summary:
**UTS** refers to the Unix Timesharing System, and the UTS namespace isolates the hostname and domain name within a containerized environment.
