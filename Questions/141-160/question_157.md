## 157. Which of the following is NOT true when Bob launches a container with -net=host? On the host, some containers are already active
A. The container will use the host's network namespace, network interfaces, and IP stack.  
B. On the host interfaces, every container in the host network can talk to every other container.  
C. Two containers can bind to the same TCP port since they share the host networking namespace.  
D. This is the networking equivalent of running several processes on a host without containers.  

The correct answer is:

**C. Two containers can bind to the same TCP port since they share the host networking namespace.**

Explanation:
When a container is launched with the `--net=host` option, it uses the host's network namespace. This means that the container shares the host's network interfaces and IP addresses. Because the container shares the same network namespace, **only one process (container) can bind to a specific TCP port** at a time. Therefore, **two containers cannot bind to the same TCP port** when using the host network.

Let's break down the other options:
- **A.** This is true. The container uses the host's network namespace, network interfaces, and IP stack.
- **B.** This is true. Since containers are using the host's network namespace, all containers on the host network can communicate with each other.
- **D.** This is true. Running a container with `--net=host` is similar to running multiple processes directly on the host without containers, as they share the same network namespace.

