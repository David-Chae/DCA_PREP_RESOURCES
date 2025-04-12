# Differences Between Running a Container vs. Running a Service

| Feature               | Running a Container                      | Running a Service (in Docker Swarm or Kubernetes) |
|----------------------|--------------------------------|----------------------------------------|
| **Scope**            | Runs a single container instance. | Manages multiple instances (replicas) of containers. |
| **Scaling**          | Manual; requires running multiple instances manually. | Supports automatic scaling and load balancing. |
| **Networking**       | Uses Docker’s default bridge network unless configured otherwise. | Uses an overlay network for communication between service replicas. |
| **Persistence**      | Persistent storage must be explicitly configured. | Typically integrated with persistent storage solutions. |
| **Fault Tolerance**  | No built-in recovery; container stops if it crashes. | Automatically restarts failed instances. |
| **Orchestration**    | No orchestration; runs independently. | Managed by an orchestrator like Docker Swarm or Kubernetes. |
| **Deployment**       | `docker run` is used to start a single container. | `docker service create` (Swarm) or `kubectl apply` (Kubernetes) is used to deploy services. |
| **Load Balancing**   | No built-in load balancing; requires additional configuration. | Built-in load balancing across replicas. |

---

## Relevant Official Documentation:

- **Running a Single Container (Docker Run)**
  - [Docker Run Reference](https://docs.docker.com/engine/reference/run/)
- **Running a Service in Docker Swarm**
  - [Docker Swarm Services](https://docs.docker.com/engine/swarm/how-swarm-mode-works/)
  - [Docker Service Create Command](https://docs.docker.com/engine/reference/commandline/service_create/)
- **Running a Service in Kubernetes**
  - [Kubernetes Services](https://kubernetes.io/docs/concepts/services-networking/service/)
  - [Kubernetes Deployment](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/)
- **Third Party Resources**
  - [What is the difference between Docker Service and Docker Container?](https://stackoverflow.com/questions/43408493/what-is-the-difference-between-docker-service-and-docker-container/43408904#43408904)
- **Asciinema Examples**
  - [State the differences between running a container vs running a service](https://github.com/DevOps-Academy-Org/dca-prep-guide/blob/master/Domain_1_Orchestration/State_the_differences_between_running_a_container_vs_running_a_service.md)
