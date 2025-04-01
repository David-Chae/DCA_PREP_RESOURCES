## 70. Which Dockerfile directive would set up the base image that can serve as our starting point for establishing a new image?
```sh
A. BASE
B. FROM
C. ARG
D. START
```

The correct answer is:  

**B. FROM**  

### Explanation:  
The `FROM` directive in a **Dockerfile** is used to specify the base image that serves as the starting point for building a new Docker image. This is typically the first instruction in a Dockerfile, and it can point to an official image from Docker Hub or a custom image.

### Why not the others?  
- **A. BASE**: There is no `BASE` directive in Dockerfile syntax.  
- **C. ARG**: The `ARG` directive defines build-time variables but doesn't set a base image.  
- **D. START**: There is no `START` directive in Dockerfile syntax.
