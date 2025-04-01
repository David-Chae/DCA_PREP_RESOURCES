## 43. Which of the following statements about docker images is correct?
```sh
A. There can only be one FROM directive per Dockerfile.
B. Only those layers (and any subsequent layers) that have changed since the last build are built.
C. Docker Compose files are used to create Docker images.
D. Every time the docker build is run, every image layer is rebuilt,
```

The correct answer is:  

**B. Only those layers (and any subsequent layers) that have changed since the last build are built.**  

### Explanation:  
Docker uses a **layered caching mechanism** to optimize builds. When building an image, Docker checks if each layer has changed:  
- If a layer remains unchanged, Docker reuses the cached version.  
- If a layer changes, that layer and all subsequent layers must be rebuilt.  

### Why not the others?  
- **A**: Incorrect. A `Dockerfile` can have **multiple `FROM` directives**, especially in **multi-stage builds**.  
- **C**: Incorrect. **Docker Compose** is used for defining and running multi-container applications, but it does **not** build Docker images.  
- **D**: Incorrect. Docker **does not rebuild every layer** every time. It **uses caching** to avoid rebuilding unchanged layers.
