## Question 7: What is a system administrator's correct order to create a Docker Enterprise Edition backup policy?
### Correct Order for Creating a Docker Enterprise Edition Backup Policy


1. swarm, ucp, dtr  
2. dtr, ucp, swarm  
3. ucp, dtr, swarm  
4. swarm, dtr, ucp  


The correct answer is:  

**1. swarm, ucp, dtr**  

### Explanation:  
According to best practices for **Mirantis Kubernetes Engine (formerly Docker Enterprise)**, the **recommended recovery order** is:

1. **Swarm**
2. **UCP (Universal Control Plane)**
3. **DTR (Docker Trusted Registry)**

This order ensures that the foundational components (Swarm being the orchestrator, followed by UCP as the control plane, and then DTR as the registry) are restored in the correct dependency chain.

### So, should backup be taken in the same order?

**Yes, ideally the backup should be taken in the same order** — **Swarm → UCP → DTR** — to ensure consistency across the stack. Here's why:

- **Swarm**: You want a consistent state of the swarm cluster, including node membership and certificates.
- **UCP**: Depends on the swarm; backing it up after swarm ensures UCP is capturing the current swarm state.
- **DTR**: Depends on UCP for authentication and orchestration context, so it should be backed up last.

### Summary:

| Action | Recommended Order |
|--------|--------------------|
| Backup | Swarm → UCP → DTR |
| Restore | Swarm → UCP → DTR |

If you’re automating backups, try to ensure that each backup is completed successfully before moving to the next component, and avoid long delays between steps to maintain state consistency.

Want help writing a backup script for these?


[OFFICIAL MIRANTIS DOCUMENTATION](https://docs.mirantis.com/containers/v2.1/dockeree-products/ucp/admin/disaster-recovery/disaster-recovery-ucp.html)
