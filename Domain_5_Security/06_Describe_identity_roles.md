# Identity Roles in Docker

## Introduction
Identity roles define access and permissions for different entities within Docker environments, including Docker Swarm. Understanding these roles is essential for managing security and governance.

## 1. Identity Roles in Docker Swarm
Docker Swarm uses **Role-Based Access Control (RBAC)** to manage access based on identity roles:

### a. **Manager Nodes**
- Responsible for orchestration and cluster management.
- Can **create, update, and remove** services.
- Maintain the **internal CA** and issue mTLS certificates.
- Manage node membership and scheduling.
- Execute **docker swarm** and **docker node** commands.

### b. **Worker Nodes**
- Execute tasks assigned by the manager nodes.
- Cannot make administrative changes.
- Only run assigned service containers.

[Official Documentation](https://docs.docker.com/engine/swarm/)

## 2. Identity Roles in Docker Enterprise
In Docker Enterprise, access management is enforced via **Docker Universal Control Plane (UCP)**, which uses RBAC to define identity roles:

### a. **Full Administrator**
- Has full control over Docker UCP.
- Can manage users, nodes, and all resources.

### b. **Restricted Control Plane Administrator**
- Can manage specific resources but lacks full administrative privileges.

### c. **Scheduler**
- Can deploy and manage workloads but cannot alter system-wide settings.

### d. **Security Administrator**
- Manages security policies, role-based access, and secrets.

[Official Documentation](https://docs.mirantis.com/mke/3.8/ref-arch/rbac.html#rbac)

## 3. User Authentication and Authorization
Docker Enterprise integrates with authentication providers to manage identities:
- LDAP
- Active Directory (AD)
- OAuth and OpenID Connect

These integrations help enforce access policies and manage security efficiently.

[Official Documentation](https://docs.mirantis.com/mke/3.8/ops/administer-cluster/integrate-with-LDAP-directory/configure-ldap-integration.html)

## Conclusion
Identity roles in Docker, particularly in **Swarm and Docker Enterprise**, define access control and security policies. Understanding these roles ensures a secure and well-managed containerized environment.
