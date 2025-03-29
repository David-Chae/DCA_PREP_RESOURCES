## 211. How to run the container?
A. docker run <image>  
B. docker start <image>  
C. docker create <image>  
D. docker launch <image>  

The correct answer is:  

**A. `docker run <image>`**  

### Explanation:  
- **`docker run <image>`** → **Creates and starts a new container from the image** (if the image is not available locally, Docker pulls it first).  
- **`docker start <image>`** → Incorrect. `start` is used to restart a stopped container, not to create a new one.  
- **`docker create <image>`** → Creates a container but **does not start it**.  
- **`docker launch <image>`** → Incorrect. This is **not a valid Docker command**.  

### Example:  
```bash
docker run nginx
```
This command **creates, starts, and runs** a container from the `nginx` image.
