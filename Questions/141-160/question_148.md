## 148. Which of the following daemon arguments is used for troubleshooting?
A. seccomp  
B. debug  
C. selinux  
D. bridge  

### Explanation:

- **B. debug**: The `--debug` flag is used to enable debug mode for the Docker daemon. This mode provides more detailed logging and information, which can be helpful for troubleshooting issues with the Docker daemon. When enabled, debug mode produces more verbose logs, allowing administrators to understand what might be going wrong and diagnose problems more effectively.

---

### Why the other options are incorrect:

- **A. seccomp**: `seccomp` is used for security purposes to apply security filters to containers. It restricts the system calls that a container can use, helping to secure the container environment. It is not related to troubleshooting.

- **C. selinux**: `selinux` refers to Security-Enhanced Linux, which is a security mechanism in the Linux kernel that helps control access to various resources. While it can be important for security management, it is not a daemon argument used for troubleshooting.

- **D. bridge**: `bridge` is related to Docker’s default network driver. It allows containers to communicate with each other on the same bridge network. While networking issues might require troubleshooting, the `--bridge` argument is not a debugging tool itself; it’s used for configuring the network.

---

### How the question could be better framed:
If the question is specifically targeting debugging or troubleshooting, it could be framed like this:

**"Which of the following Docker daemon arguments enables debug logging for troubleshooting purposes?"**

This clarification makes it clear that the goal is to identify the debugging option for troubleshooting.
