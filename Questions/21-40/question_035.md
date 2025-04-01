## 35. Which of the following commands will attach the tasks of a new service to an existing overlay net work called my-overlay?
```sh
A. docker service create --network-driver overlay nginx
B. docker service create --n my-overlay nginx
C. docker service create --attach my-overlay nginx
D. docker service create --network my-overlay nginx
```

The correct answer is:  

**D. `docker service create --network my-overlay nginx`**  

### Explanation:  
- The `--network` option specifies which network the service should connect to.  
- `my-overlay` is the name of the existing overlay network.  
- `nginx` is the service being created.  

### Why not the others?  
- **A**: `--network-driver` is incorrect here; it is used when creating a network, not when attaching a service.  
- **B**: `--n` is not a valid option.  
- **C**: `--attach` is not used for networks in Docker Swarm.
