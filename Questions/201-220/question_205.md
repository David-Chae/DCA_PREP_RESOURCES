## 205. Which command do you use to create a new swarm?  
A. docker swarm init --advertise-addr <MANAGER-IP>  
B. docker swarm init  
C. docker swarm init --advertise-addr <MANAGER-IP> --listen-addr <LISTEN-ADDR>  
D. docker swarm init --autolock  

**C. `docker swarm init --advertise-addr <MANAGER-IP> --listen-addr <LISTEN-ADDR>`**  

This command initializes a new Docker Swarm with a specific manager IP address for advertisement and a listening address for cluster communication, ensuring proper network configuration.  
