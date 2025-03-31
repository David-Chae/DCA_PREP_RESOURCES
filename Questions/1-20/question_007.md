## Question 7: What is a system administrator's correct order to create a Docker Enterprise Edition backup policy?
### Correct Order for Creating a Docker Enterprise Edition Backup Policy


1. swarm, ucp, dtr  
2. dtr, ucp, swarm  
3. ucp, dtr, swarm  
4. swarm, dtr, ucp  


The correct answer is:  

**C. ucp, dtr, swarm**  

### Explanation:  
When creating a **Docker Enterprise Edition (EE)** backup policy, the correct order is:  

1. **UCP (Universal Control Plane)** – UCP manages users, access control, and orchestration. Since it contains critical cluster and security configurations, it should be backed up first.  
2. **DTR (Docker Trusted Registry)** – DTR stores and manages container images. Since it depends on UCP for access control, it should be backed up after UCP.  
3. **Swarm** – The Swarm state can be rebuilt from UCP, so it is backed up last.  

### Backup Commands:  
- **UCP Backup:**  
  ```sh
  docker container run --rm -i \
  --name ucp-backup \
  -v /var/run/docker.sock:/var/run/docker.sock \
  -v $(pwd):/backup \
  docker/ucp backup --file /backup/ucp_backup.tar
  ```  
- **DTR Backup:**  
  ```sh
  docker run --rm docker/dtr backup \
  --ucp-username admin --ucp-password password \
  --ucp-url https://ucp.example.com \
  --output dtr_backup.tar
  ```  
- **Swarm Backup:**  
  ```sh
  docker swarm leave --force
  docker swarm init
  ```  
This order ensures that the most critical configurations and dependencies are backed up properly.
