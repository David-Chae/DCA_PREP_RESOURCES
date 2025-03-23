## 181. Will the given command encrypt the overlay traffic between service tasks?
## docker network create -d overlay --secure
A. Yes  
B. No  

**B. No**

Explanation:
The `--secure` flag is not a valid option for the `docker network create` command. 

To encrypt overlay network traffic between service tasks in Docker Swarm, you need to use the `--opt encrypted` flag when creating an overlay network, like this:

```
docker network create -d overlay --opt encrypted my_overlay_network
```

This ensures that the traffic between containers in the overlay network is encrypted.
