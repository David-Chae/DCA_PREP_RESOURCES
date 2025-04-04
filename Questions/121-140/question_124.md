## 124. Which allows you to write files to an external storage system?
```sh
A. Docker Swarm  
B. Registry  
C. Container  
D. Volume driver  
```sh
The correct answer is:  

**D. Volume driver**  

- A **volume driver** allows Docker to write files to an external storage system by managing storage volumes.  
- It enables integration with various storage backends, such as NFS, AWS EBS, or cloud storage solutions.


Answer: D Explanation: Volume drivers in Docker allow you to write files to an external storage system. Docker volumes are a way to persist data generated or used by Docker containers. Using volume drivers, you can connect Docker containers to external storage systems or remote network-attached storage and write data to and read from these external storage systems. This is useful for scenarios where you need to store data outside of the container itself or share data between containers.  
  
  The other options listed do not directly provide a mechanism for writing files to an external storage system:  

Option A. Docker Swarm is a container orchestration platform that focuses on managing container deployments at scale but does not specifically provide external storage solutions.  

Option B. A Docker Registry is a service for storing and distributing Docker images, not writing data to external storage.  

Option C. Containers are isolated environments for running applications. While they can read and write data within their filesystem, it is not inherently for writing data to an external storage system. External storage can be connected to containers using volume drivers, as mentioned in option D.
