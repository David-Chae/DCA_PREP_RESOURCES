## 200. You built a new service called 'http' and discovered it is not registering as healthy. Will the following command allow you to see a list of previous tasks for this service?
## docker service inspect http
A. Yes  
B. No  

**B. No**

The command `**docker service inspect http**` **does not** show a list of previous tasks for the service. Instead, it provides detailed information about the service's configuration and status (e.g., replicas, networks, update policy).

To see a list of tasks (including their current and previous states), you should use:

```
docker service ps http
```

This command lists all tasks (instances) of the service `http`, along with their state (e.g., running, failed, shutdown), node, and error messages if any.

**So the answer is:**  
**No**, `docker service inspect http` will not show a list of previous tasks. Use `docker service ps http` instead.
