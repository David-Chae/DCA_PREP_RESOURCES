## 235. Is the ingress network created when you initialize or join a swarm?
A. Yes, the ingress network is created when you initialize or join a swarm.  
B. No, when configuring a swarm, the ingress network must be manually setup.  
C. The ingress network is only created when the swarm manager is installed.  
D. Ingress network creation depends on the specific configuration of the swarm.  

The correct answer is:

**A. Yes, the ingress network is created when you initialize or join a swarm.**

### Explanation:
- **A** is correct because when you initialize or join a swarm, Docker automatically creates the **ingress network**. This network is used for routing traffic to services in the swarm and supports load balancing.
  
- **B** is incorrect because the ingress network is automatically created by Docker when the swarm is initialized or a node joins the swarm.
  
- **C** is incorrect because the ingress network is created for the entire swarm, not just when the swarm manager is installed.
  
- **D** is incorrect because the ingress network is automatically created as part of the swarm setup and does not require manual configuration.

Therefore, **A** is the correct choice.
