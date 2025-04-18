## 10. On AWS, you are creating a new Docker Swarm. You must check that neither the Security Group Rules nor the Network Access Control List blocks traffic between hosts. Which statement best characterizes all ports that must be allowed between Docker hosts?
A. TCP/2377 and UDP/2377  
B. TCP/7946 and UDP/2377  
C. TCP/2377, TCP/7946, and UDP/7946  
D. TCP/2377 and TCP/4789  


The correct answer is:  

**C. TCP/2377, TCP/7946, and UDP/7946**  

### Explanation:  
When setting up a **Docker Swarm** on AWS, you need to allow the following ports for proper communication between Swarm nodes:  

1. **TCP/2377** → Swarm **control plane** (used for cluster management and leader election).  
2. **TCP/7946** → Used for **inter-node communication** (for exchanging control data).  
3. **UDP/7946** → Used for **node discovery** (helps nodes find each other).  
4. **UDP/4789** → Used for **container overlay network traffic** (but is not strictly required for Swarm to function).  

### Why the other options are incorrect:  
- **A. TCP/2377 and UDP/2377** → **Incorrect**  
  - `UDP/2377` is not needed. Swarm uses **TCP/2377** for control, but lacks `TCP/7946` and `UDP/7946` for node communication.  

- **B. TCP/7946 and UDP/2377** → **Incorrect**  
  - `UDP/2377` is unnecessary. Also, **TCP/2377 is missing**, which is required for cluster management.  

- **D. TCP/2377 and TCP/4789** → **Incorrect**  
  - `TCP/4789` is not used for cluster management (Swarm overlay networks use **UDP/4789**, not TCP).  
  - This option is missing **TCP/7946** and **UDP/7946**, which are required for inter-node communication.  

Thus, **C** is the best answer.
