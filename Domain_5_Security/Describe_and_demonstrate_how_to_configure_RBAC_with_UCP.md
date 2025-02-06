# Describe and demonstrate how to configure RBAC with UCP

Configuring Role-Based Access Control (RBAC) in Universal Control Plane (UCP) allows you to manage permissions and ensure that only authorized users can access and modify resources in your Docker cluster.  
Here’s a step-by-step guide on how to configure RBAC in UCP:  

## Step-by-Step Guide
1. Access UCP Web UI:
- Log in to the UCP web interface using your administrator credentials.

2. Navigate to Access Control:
- Go to the "Access Control" section in the UCP dashboard.

3. Create Roles:
- Navigate to the "Roles" page.
- Click on "Create Role".
- Define the role by specifying the permissions required. For example, you might create roles like "Developer," "Operator," and "Viewer."

4. Create Collections:
- Collections are groups of resources that you can apply access controls to.
- Go to the "Collections" page.
- Click on "Create Collection" and define the resources that belong to this collection.

5. Assign Roles to Collections:
- Navigate to the "Grants" page.
- Click on "Create Grant".
- Select the role, the collection, and the subject (user or team) to assign the role to the collection.

6. Add Users and Teams:
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
For detailed, step-by-step instructions and more information, you can refer to the following official Mirantis documentation:

[Mirantis Documentation: UCP Architecture1](https://docs.mirantis.com/containers/v2.1/dockeree-products/ucp/ucp-architecture.html)
[Mirantis Documentation: Authorize Role-Based Access2](https://docs.mirantis.com/containers/v2.1/dockeree-products/ucp/authorization.html)
[Mirantis Documentation: Access Control Model3](https://docs.mirantis.com/containers/v2.1/dockeree-products/ucp/authorization/access-control-model.html)
These resources provide comprehensive guidance on setting up and managing RBAC in UCP.
