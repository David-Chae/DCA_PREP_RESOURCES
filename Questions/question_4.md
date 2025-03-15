## Question 4: What is a system administrator's correct order to create a Docker Enterprise Edition backup policy?
### Correct Order for Creating a Docker Enterprise Edition Backup Policy

```sh
1. swarm, ucp, dtr
2. dtr, ucp, swarm
3. ucp, dtr, swarm
4. swarm, dtr, ucp
```

### Correct Answer:
✅ **`3. ucp, dtr, swarm`**  

### Explanation:
A **Docker EE backup** should follow a structured approach to ensure consistency and restore capability:

1️⃣ **UCP (Universal Control Plane)**  
   - UCP manages the **Swarm cluster, RBAC, and container orchestration**.  
   - Backing it up first ensures that access control and cluster state are preserved.

2️⃣ **DTR (Docker Trusted Registry)**  
   - DTR is responsible for **storing and managing container images**.  
   - It should be backed up after UCP since **it relies on UCP for authentication and access control**.

3️⃣ **Swarm**  
   - Swarm mode is the foundation, but its state (such as services and nodes) is already included in the UCP backup.  
   - Backing it up last ensures that it is consistent with UCP and DTR.

### Summary of Backup Order:
1. **UCP first** (to preserve cluster management and authentication).  
2. **DTR second** (to save registry data after UCP is backed up).  
3. **Swarm last** (as UCP already includes necessary Swarm data).
