To enable full communication between Docker Swarm nodes (especially in **AWS EC2 instances**), you need to open specific **ports** in your **Security Groups** and **Network ACLs**. These are essential for cluster management, service discovery, and ingress routing.

Here are the **required ports** for **Docker Swarm mode** to work properly:

---

### Docker Swarm Required Ports

| **Port(s)**           | **Description**                                                                 |
|-----------------------|---------------------------------------------------------------------------------|
| `2377/tcp`            | The default **Swarm control plane** port. Configurable with `docker swarm join --listen-addr`. |
| `4789/udp`            | The default port for **overlay network traffic**. Configurable with `docker swarm init --data-path-addr`. |
| `7946/tcp`, `7946/udp`| Used for **communication among nodes** (gossip protocol). **Not configurable**. |




### ✅ **Required Ports for Docker Swarm Communication**

| Purpose                         | Protocol | Port  | Direction | Description |
|---------------------------------|----------|-------|-----------|-------------|
| **Cluster management**         | TCP      | 2377  | Inbound   | Only between **manager nodes**. Used for control plane traffic (e.g., raft, swarm join). |
| **Node discovery (gossip)**    | UDP      | 7946  | Inbound/Outbound | Between all nodes (managers and workers). Used for communication about services, nodes, etc. |
| **Overlay network traffic**    | TCP/UDP  | 4789  | Inbound/Outbound | VXLAN tunnel for overlay networks (inter-container traffic). |
| **Ingress load balancing**     | TCP/UDP  | 30000–32767 | Inbound | Ports used by Swarm's routing mesh (default published port range). |
| **App-specific published ports** | TCP/UDP | Any app ports you expose | Inbound | Allow these to access services from outside. |

---

### 🔐 AWS Security Group Rules Example

| Type | Protocol | Port Range | Source (CIDR or SG) |
|------|----------|------------|----------------------|
| Custom TCP | TCP | 2377 | SG of other Swarm nodes or your CIDR |
| Custom UDP | UDP | 7946 | SG of other Swarm nodes or your CIDR |
| Custom TCP | TCP | 7946 | SG of other Swarm nodes or your CIDR |
| Custom UDP | UDP | 4789 | SG of other Swarm nodes or your CIDR |
| Custom TCP | TCP | 30000–32767 | 0.0.0.0/0 or your trusted CIDR |
| App Port | TCP | e.g., 80, 443 | 0.0.0.0/0 or your CIDR block |

---

### 🔄 Network ACL Rules

Ensure that your VPC’s **Network ACLs** also allow:

- **Inbound and outbound** traffic for the same ports listed above.
- **Stateless** rules—so you must allow both **inbound and outbound** for TCP/UDP as required.

---

### 🧠 Bonus Tips

- You can tighten security by scoping source IPs to the **private IP range of your VPC** (like `10.0.0.0/16`) instead of `0.0.0.0/0`.
- For overlay networks to work properly, **ICMP (ping)** is not required, but **MTU** consistency between nodes helps avoid hidden connectivity issues.
- If using **firewalls inside the instance** (e.g., `ufw` or `iptables`), allow the same ports there too.
