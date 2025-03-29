## 225. How to find out which nodes are running the service?
A. docker service ps <service>  
B. docker service nodes <service>  
C. docker swarm service nodes <service>  
D. docker inspect service <service>  

The correct command to find out which nodes are running a service in Docker Swarm is:

**A. docker service ps <service>**

Explanation:
- **A**: `docker service ps <service>` lists the tasks associated with the service and shows which nodes are running them.

The other options are incorrect:
- **B**: `docker service nodes <service>` is not a valid Docker command.
- **C**: `docker swarm service nodes <service>` is also incorrect.
- **D**: `docker inspect service <service>` is not valid syntax and won't show the nodes running the service.

So, the correct answer is **A**.
