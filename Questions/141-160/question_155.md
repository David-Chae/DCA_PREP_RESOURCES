## 155. Bob wants to update a secret that one of his employees is using. What steps does he need to do in the right order?
```sh
A. Using docker secret update, update the current secret.
B. Restart all services using this secret after updating the existing one
C. Update the service to utilize the new secret create a new secret, and destroy the previous secret.
D. Create a new secret, use that secret to create a new Service, and then remove the prior secret and service.
```

The correct answer is:

**D. Create a new secret, use that secret to create a new Service, and then remove the prior secret and service.**

Explanation:
1. **Create a new secret**: First, Bob needs to create a new secret with the updated values.
2. **Use that secret to create a new Service**: Then, Bob should update the service to use the new secret. This involves creating a new service or updating the service definition to reference the new secret.
3. **Remove the prior secret and service**: After the service is updated to use the new secret, Bob should delete the old secret and any services that were using the outdated secret.

This approach ensures that the service is using the updated secret and avoids potential disruptions during the update process.

Secrets in a docker swarm are unchangeable. They cannot be changed, thus. Therefore, you must create a new secret file to modify a secret. Despite this, the current procedure for updating a secret is first to create a new one (since we cannot update an existing one) and attach the new secret to the service by updating the service (this would necessitate the service's restart; docker swarm would handle that), and then delete the old secret. Reference: https://docs.docker.com/engine/swarm/secrets/
