## What port needs to be open for workers and managers to be able to communicate with each other in a swarm? Can you find the official documentation on this?

​To enable proper communication between manager and worker nodes in a Docker Swarm cluster, certain ports must be open on all participating nodes.

### 🔐 Required Ports for Docker Swarm Communication
| Port | Protocol | Purpose                                                                 |
|------|----------|-------------------------------------------------------------------------|
| 2377 | TCP      | Cluster management communications between manager nodes and for worker nodes to join the swarm |
| 7946 | TCP/UDP  | Communication among nodes for container network discovery and cluster management |
| 4789 | UDP      | Overlay network traffic (VXLAN) for container-to-container networking   
If you plan to use encrypted overlay networks (`--opt encrypted`), ensure that IP protocol 50 (ESP) is allowed for IPsec traffic
These requirements are detailed in the [Docker Swarm tutorial](https://docs.docker.com/engine/swarm/swarm-tutorial/#open-protocols-and-ports) and the [Swarm networking documentation](https://docs.docker.com/engine/swarm/networking/#firewall-considerations)

### 🔧 Firewall Configuration Tips

- **Internal Firewalls** Ensure that these ports are open between all nodes in the swar.
- **External Firewalls** Only expose necessary service ports to the public interne.
- **VXLAN Port (4789)** Since VXLAN does not provide authentication, restrict access to this port to trusted networks onl.
Properly configuring these ports ensures seamless operation of your Docker Swarm cluste. 
