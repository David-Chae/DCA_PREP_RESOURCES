## 73. What is the name of the Docker feature that allows us to sign images and check the signatures on those images before running them?
```sh
A. Only files kept in Docker Hub's cloud can be signed.
B. A Docker Enterprise Edition (EE) license is necessary for Docker Content Trust.
C. We must place a reliable Public Key Infrastructure (PKI) to sign images.
D. The system cannot run unsigned images when Docker Content Trust is enabled.
```

The correct answer is:  

**D. The system cannot run unsigned images when Docker Content Trust is enabled.**  

### Explanation:  
When **Docker Content Trust (DCT)** is enabled, it ensures that only signed images can be pulled or pushed. If an image is not signed, Docker will not allow it to be used, helping to ensure that only trusted and verified images are run. This is a security feature that verifies the integrity and authenticity of images before use.

### Why not the others?  
- **A. Only files kept in Docker Hub's cloud can be signed**: This is incorrect. While Docker Hub supports signing images, Docker Content Trust can be used with any registry that supports image signing, not just Docker Hub.  
- **B. A Docker Enterprise Edition (EE) license is necessary for Docker Content Trust**: This is incorrect. Docker Content Trust is available in Docker Community Edition (CE) as well as Enterprise Edition (EE).  
- **C. We must place a reliable Public Key Infrastructure (PKI) to sign images**: While PKI can be used for signing, Docker Content Trust does not require you to set up your own PKI. Docker uses a built-in mechanism for signing images, which simplifies the process.
