## 137. Which of the following allows you to specify how many jobs you want to run for each service?
```sh
A. Service model
B. Service discovering
C. Multi-host networking
D. Scaling
```

The correct answer is:  

**D. Scaling**  

### Explanation:  
**Scaling** in Docker allows you to specify how many instances (or replicas) of a service you want to run. You can scale services up or down based on demand, and Docker Swarm ensures that the specified number of tasks (containers) for each service are running.

### Why not the others?  
- **A. Service model**: The service model defines how services are structured in Docker (e.g., replicated services, global services), but it doesn't directly deal with specifying the number of jobs to run.
- **B. Service discovering**: Service discovery is a feature that helps containers discover and communicate with each other, but it doesn't define the number of tasks or jobs for a service.
- **C. Multi-host networking**: Multi-host networking refers to the ability to connect containers across different Docker hosts, but it does not manage the number of jobs or tasks for a service.
