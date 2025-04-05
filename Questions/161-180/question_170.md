## 170. Will the given sequence of commands determine a container's published port(s)? docker container inspect, docker port
A. Yes  
B. No  

The correct answer is:

**A. Yes**

Explanation:
The sequence of commands can indeed determine a container's published port(s). Here's how they work:

- `docker container inspect` provides detailed information about a container, including its network settings and port mappings.
- `docker port` shows which ports on the container are exposed to the host machine and their mappings.

Together, these commands can give you the published port information for a container.
