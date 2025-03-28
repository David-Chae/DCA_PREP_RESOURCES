## 206. What is this flag --advertise-addr for?
A. --advertise-addr sets the maximum number of nodes in a Docker swarm.  
B. --advertise-addr is a flag specifying the network driver for Docker containers.  
C. --advertise-addr defines the DNS server for Docker containers  
D. --advertise-addr configures the IP address for the manager node in a Docker swarm, ensuring that other nodes can access the manager at that IP address.  


The correct answer is:  

**D. --advertise-addr configures the IP address for the manager node in a Docker swarm, ensuring that other nodes can access the manager at that IP address.**  

### Explanation:  
- The `--advertise-addr` flag is used when initializing a Swarm (`docker swarm init --advertise-addr <MANAGER-IP>`).  
- It sets the IP address that worker and manager nodes should use to communicate with the Swarm manager.  
- This is especially useful in multi-network environments where the node has multiple interfaces.  
- It ensures that Swarm nodes connect to the correct manager IP address.
