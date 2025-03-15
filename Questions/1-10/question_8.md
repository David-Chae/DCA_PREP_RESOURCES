##  Overlay networks cannot be created if the docker engine is not a manager node in the docker swarm. True False

The correct answer is:  

✅ **True**  

### Explanation:
In Docker Swarm, **overlay networks** are used for **multi-host communication** between containers. Overlay networks require the Docker engine to be part of a **Swarm cluster** and specifically a **manager node** in the swarm to create and manage them. 

- **Manager nodes** in Docker Swarm are responsible for maintaining the **Swarm state**, including network configurations like overlay networks.
- **Worker nodes** can join the swarm and participate in the network but cannot create overlay networks.

Thus, **overlay networks cannot be created** unless the Docker engine is part of a **Swarm manager node**.

---

### Summary:
To create an overlay network, the Docker engine must be a **manager node** in the Docker Swarm. If it's not a manager node, it **cannot create overlay networks**.
