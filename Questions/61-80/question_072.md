## 72. What is the name of the Docker feature that allows us to sign images and check the signatures on those images before running them?
```sh
A. Docker Trusted Registry  
B. Docker Registry  
C. Docker Content Trust  
D. Docker Image Trust  
```

The correct answer is:  

**C. Docker Content Trust**  

### Explanation:  
**Docker Content Trust (DCT)** is the Docker feature that enables image signing and verification. When enabled, Docker Content Trust ensures that only signed images are pulled or pushed to the Docker registry. This adds an extra layer of security by ensuring the authenticity and integrity of images before they are used or deployed.

### Why not the others?  
- **A. Docker Trusted Registry**: This is a commercial product for managing private image repositories but does not specifically handle image signing and verification like Docker Content Trust.  
- **B. Docker Registry**: This is the default repository service for storing Docker images, but it does not inherently handle image signing.  
- **D. Docker Image Trust**: This is not a recognized feature or term within Docker’s official terminology. The correct term is **Docker Content Trust**.
