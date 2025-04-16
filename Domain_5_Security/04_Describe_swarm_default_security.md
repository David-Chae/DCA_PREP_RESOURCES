# Swarm Default Security in Docker

## Introduction
Docker Swarm Mode provides built-in security mechanisms to protect clusters, nodes, and services. Understanding these security features is crucial for the Docker Certified Associate (DCA) exam.

## 1. Mutual TLS (mTLS) for Node Communication
Swarm mode uses **mutual TLS (mTLS)** to authenticate and encrypt all communication between nodes.
- Each node in the swarm has a TLS certificate issued by the cluster’s Certificate Authority (CA).
- Certificates are automatically rotated to enhance security.
- [Official Documentation](https://docs.docker.com/engine/swarm/how-swarm-mode-works/pki/)

## 2. Role-Based Access Control (RBAC)
Swarm has role-based access control to limit privileges:
- **Managers** handle orchestration, scheduling, and security operations.
- **Workers** only run containers but cannot make administrative changes.
- [Official Documentation](https://docs.docker.com/engine/swarm/)

## 3. Encrypted Network Traffic
Swarm enables encryption for overlay networks:
- Data traffic between services in the same overlay network is **AES-GCM encrypted**.
- Encryption is configurable using `--opt encrypted` when creating a network.
- [Official Documentation](https://docs.docker.com/network/overlay/#enable-encryption)

## 4. Automatic Certificate Rotation
Swarm automatically rotates certificates to minimize security risks:
- Node certificates have a **90-day expiration** by default.
- Managers handle **automatic renewal** and distribution.
- [Official Documentation](https://docs.docker.com/engine/swarm/how-swarm-mode-works/pki/#certificate-rotation)

## 5. Secret Management
Swarm provides built-in secret management for storing sensitive data:
- Secrets are **encrypted at rest and in transit**.
- Access to secrets is **restricted to specific services**.
- [Official Documentation](https://docs.docker.com/engine/swarm/secrets/)

## 6. Service-Level Security Policies
Swarm allows security options for services:
- **Service constraints** restrict tasks to specific nodes.
- **Node labels** enforce scheduling policies.
- [Official Documentation](https://docs.docker.com/engine/swarm/services/#placement-constraints)

## 7. Node Join Security
New nodes must be explicitly allowed to join the swarm:
- `docker swarm join-token` generates unique tokens for new managers and workers.
- Tokens can be **rotated** to invalidate old ones.
- [Official Documentation](https://docs.docker.com/engine/swarm/join-nodes/)

## 8. Logging and Auditing
Swarm supports centralized logging and monitoring:
- **Docker logs** and **Swarm events** track activities.
- Integration with **ELK Stack, Fluentd, and Splunk**.
- [Official Documentation](https://docs.docker.com/config/containers/logging/)

## Conclusion
Docker Swarm mode enforces security through encryption, RBAC, automatic certificate rotation, and secret management. These built-in features help protect distributed applications and ensure secure cluster operations.
