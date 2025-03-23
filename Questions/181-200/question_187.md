## 187. According to a company's security policy development and production containers must run on separate nodes in a Swarm cluster
## Can "label contraints" be used to schedule containers by security policy?
A. Yes  
B. No  

**A. Yes**  

### Explanation:  
**Label constraints** can be used in **Docker Swarm** to ensure that containers are scheduled on specific nodes that meet certain criteria. In this case, you can assign labels to nodes (e.g., `environment=production` or `environment=development`) and then use constraints in **service definitions** to ensure that development and production containers run on separate nodes.  

### How It Works:  
1. **Label the Nodes**  
   ```bash
   docker node update --label-add environment=production node1
   docker node update --label-add environment=development node2
   ```

2. **Use Constraints in the Service Definition**  
   ```bash
   docker service create --name app --constraint 'node.labels.environment == production' my-app
   ```

3. **Result**  
   - Production containers run only on nodes labeled **`environment=production`**  
   - Development containers run only on nodes labeled **`environment=development`**  

This ensures compliance with security policies by **isolating workloads** on designated nodes.
