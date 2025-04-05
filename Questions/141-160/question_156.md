## 156. Which of the following describes grants under the UCP?
A. images, containers, and nodes  
B. subject, role, and containers  
C. nodes, role, and containers  
D. subject, node, and container  
E. subject, role, and resource set  

The correct answer is:

**E. subject, role, and resource set**

Explanation:
In Docker Universal Control Plane (UCP), grants consist of three key components:
1. **Subject**: The user or entity to which the grant is being assigned.
2. **Role**: The permissions that define what actions the subject can perform (e.g., admin, read-only).
3. **Resource Set**: The resources the role applies to, such as containers, nodes, or services.

These three components together define access control and permissions in UCP.



Docker EE administrators can create grants to control how users and organizations access resource sets.

A grant defines who has how much access to what resources. Each grant is a 1:1:1 mapping of subject, role, and resource set. For example, you can grant the “Prod Team” “Restricted Control” over services in the “/Production” collection.

A common workflow for creating grants has four steps:

Add and configure subjects (users, teams, and service accounts).
Define custom roles (or use defaults) by adding permitted API operations per type of resource.
Group cluster resources into Swarm collections or Kubernetes namespaces.
Create grants by combining subject + role + resource set

https://docs.mirantis.com/containers/v2.1/dockeree-products/ucp/authorization/grant-permissions.html
