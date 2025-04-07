## 224. How to inspect the service on the swarm so that it will print limited information in an easily readable format?
A. docker service inspect <service> --pretty  
B. docker inspect service <service> --format="{{.Spec.Name}}"  
C. docker swarm service inspect <service> --format-="{{.Spec.Name}}" --pretty  
D. docker inspect <service> --format="{{.SpecName}}" -pretty  

The correct command to inspect a service on the swarm and print limited information in an easily readable format is:

**A. docker service inspect <service> --pretty**

Explanation:
- **A** uses the `--pretty` flag with `docker service inspect`, which provides a more human-readable format with limited and key information about the service. Reference: https://docs.docker.com/reference/cli/docker/service/inspect/

The other options are incorrect:
- **B**: `docker inspect service <service> --format="{{.Spec.Name}}"` is not a valid command as the `docker inspect` command does not use "service" in that context.
- **C**: `docker swarm service inspect <service> --format="{{.Spec.Name}}" --pretty` is incorrect as `docker swarm service inspect` is not a valid command.
- **D**: `docker inspect <service> --format="{{.Spec.Name}}" -pretty` is also incorrect due to improper formatting and the invalid use of `-pretty`.

So, the correct answer is **A**.
