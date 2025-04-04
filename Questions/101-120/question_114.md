## 114. How many publishing modes are available for services in Docker Swarm?
A. Four  
B. Three  
C. Only one  
D. TwO  

The correct answer is:

**D. Two**

**Explanation:**
In Docker Swarm mode, when you publish ports for services, there are two main publishing modes:

1. **Host mode**: In this mode, the port is published directly on the host machine. The container's port is mapped to a specific host port, and traffic is routed directly to that host port.
   
2. **Ingress mode**: In this mode, the published port is available across all nodes in the Docker Swarm cluster. Docker Swarm uses an internal routing mechanism to distribute incoming traffic to the appropriate container, even if it’s running on different nodes in the cluster.

So, indeed, Docker Swarm supports **two** publishing modes for ports: **host** and **ingress**.

Thank you for catching that, and apologies for the confusion!
