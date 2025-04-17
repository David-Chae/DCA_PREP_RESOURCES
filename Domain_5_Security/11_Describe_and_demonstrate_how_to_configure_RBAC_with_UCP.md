# Describe and demonstrate how to configure RBAC with UCP

Configuring Role-Based Access Control (RBAC) in Universal Control Plane (UCP) allows you to manage permissions and ensure that only authorized users can access and modify resources in your Docker cluster.  
Here’s a step-by-step guide on how to configure RBAC in UCP:  

## Step-by-Step Guide
### 1. Access UCP Web UI:
- Log in to the UCP web interface using your administrator credentials.

### 2. Navigate to Access Control:
- Go to the "Access Control" section in the UCP dashboard.

### 3. Create Roles:
- Navigate to the "Roles" page.
- Click on "Create Role".
- Define the role by specifying the permissions required. For example, you might create roles like "Developer," "Operator," and "Viewer."

### 4. Create Collections:
- Collections are groups of resources that you can apply access controls to.
- Go to the "Collections" page.
- Click on "Create Collection" and define the resources that belong to this collection.

### 5. Assign Roles to Collections:
- Navigate to the "Grants" page.
- Click on "Create Grant".
- Select the role, the collection, and the subject (user or team) to assign the role to the collection.

### 6. Add Users and Teams:
- Go to the "Users" or "Teams" page.
- Add new users or teams and assign them to the appropriate roles.

## Example Commands
1. Create a Role:

```
docker role create --name developer --description "Developer role with limited access"
```

2. Create a Collection:
```
docker collection create --name dev-collection --description "Collection for development resources"
```

3. Assign a Role to a Collection:
```
docker grant create --role developer --collection dev-collection --subject user1
```

Relevant Mirantis Documentation
For detailed information, you can refer to the following official Mirantis documentation:

[Mirantis Documentation: Access Control Model3](https://docs.mirantis.com/containers/v2.1/dockeree-products/ucp/authorization/access-control-model.html)
Below is from above documentation. 

# Access Control Model

Universal Control Plane (UCP) lets you authorize users to view, edit, and use cluster resources by granting role-based permissions against resource sets.

To authorize access to cluster resources across your organization, UCP administrators might take the following high-level steps:

1. Add and configure subjects (users, teams, and service accounts).
2. Define custom roles (or use defaults) by adding permitted operations per type of resource.
3. Group cluster resources into resource sets of Swarm collections or Kubernetes namespaces.
4. Create grants by combining subject + role + resource set.

## Subjects

A subject represents a user, team, organization, or a service account. A subject can be granted a role that defines permitted operations against one or more resource sets.

- **User**: A person authenticated by the authentication backend. Users can belong to one or more teams and one or more organizations.
- **Team**: A group of users that share permissions defined at the team level. A team can be in one organization only.
- **Organization**: A group of teams that share a specific set of permissions, defined by the roles of the organization.
- **Service account**: A Kubernetes object that enables a workload to access cluster resources which are assigned to a namespace.

## Roles

Roles define what operations can be done by whom. A role is a set of permitted operations against a type of resource, like a container or volume, which is assigned to a user or a team with a grant.

For example, the built-in role, Restricted Control, includes permissions to view and schedule nodes but not to update nodes. A custom DBA role might include permissions to r-w-x (read, write, and execute) volumes and execute) volumes and secrets.

Most organizations use multiple roles to fine-tune the appropriate access. A given team or user may have different roles provided to them depending on what resource they are accessing.

## Resource Sets

To control user access, cluster resources are grouped into Docker Swarm collections or Kubernetes namespaces.

- **Swarm collections**: A collection has a directory-like structure that holds Swarm resources. You can create collections in UCP by defining a directory path and moving resources into it. Also, you can create the path in UCP and use labels in your YAML file to assign application resources to the path. Resource types that users can access in a Swarm collection include containers, networks, nodes, services, secrets, and volumes.
- **Kubernetes namespaces**: A namespace is a logical area for a Kubernetes cluster. Kubernetes comes with a default namespace for your cluster objects, plus two more namespaces for system and public resources. You can create custom namespaces, but unlike Swarm collections, namespaces cannot be nested. Resource types that users can access in a Kubernetes namespace include pods, deployments, network policies, nodes, services, secrets, and many more.

Together, collections and namespaces are named resource sets.

## Grants

A grant is made up of a subject, a role, and a resource set.

Grants define which users can access what resources in what way. Grants are effectively Access Control Lists (ACLs) which provide comprehensive access policies for an entire organization when grouped together.

Only an administrator can manage grants, subjects, roles, and access to resources.
