## 232. How to increase the number of replicas?
A. To increase the number of replicas, you can use the docker service scale SERVICE=REPLICAS, for example, docker service scale frontend=50. You can also scale multiple services with this command  
B. You can increase the number of replicas using docker service update --replicas=50 frontend  
C. Increasing the number of replicas is only possible during the initial service deployment and cannot be modified afterward  
D. Use docker scale service=50 to adjust the number of replicas in a service  

The correct answer is:

**B. You can increase the number of replicas using `docker service update --replicas=50 frontend`.**

### Explanation:
- **B** is correct because `docker service update --replicas=50` is the proper way to modify the number of replicas for an existing service.
- **A** is also technically correct (`docker service scale`) but is deprecated in favor of `docker service update --replicas`.
- **C** is incorrect because the number of replicas can be modified after the initial deployment using `docker service update`.
- **D** is incorrect because `docker scale service=50` is not a valid Docker command.

So, **B** is the most accurate and current method.
