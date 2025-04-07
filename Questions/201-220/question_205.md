## 205. Which command do you use to create a new swarm?  
A. docker swarm init --advertise-addr <MANAGER-IP>  
B. docker swarm init  
C. docker swarm init --advertise-addr <MANAGER-IP> --listen-addr <LISTEN-ADDR>  
D. docker swarm init --autolock  

The correct answers are:  

✅ **A. `docker swarm init --advertise-addr`**  

### Explanation: The docker swarm init command initializes a new Docker swarm
The --advertise-addr lag is used to specify the manager node's address, which is crucial for other nodes in the swarm to reach and join the manager.

Reference:
https://docs.docker.com/engine/reference/commandline/swarm_init/
