## 161. Is the net namespace disabled by default in Docker and must be activated to be used at Docker engine runtime?
A. Yes  
B. No  

The correct answer is:

**B. No**

Explanation:
The network namespace (`netns`) is **not** disabled by default in Docker. Docker automatically uses network namespaces to isolate containers' networking, allowing each container to have its own networking environment. By default, Docker containers are connected to a bridge network unless specified otherwise.

There's no need to explicitly enable the network namespace at Docker engine runtime, as it is a fundamental part of how containers are isolated by default.
