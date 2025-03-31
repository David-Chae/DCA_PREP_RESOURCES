## 9. Which of the following options would enable SSH into a running Docker container named 'nginx'?
A. docker exec -it nginx /bin/sh  
B. docker inspect webserver  
C. docker run -it nginx /bin/sh  
D. docker ssh-it nginx /bin/sh


The correct answer is:  

**A. `docker exec -it nginx /bin/sh`**  

### Explanation:  
To "SSH" into a running Docker container (i.e., open an interactive shell inside it), you can use:  
```sh
docker exec -it nginx /bin/sh
```  
- **`docker exec`** runs a command inside an existing container.  
- **`-it`** allows interactive mode with a TTY session.  
- **`/bin/sh`** starts a shell session (use `/bin/bash` if the container has it).  

### Why the other options are incorrect:  
- **B. `docker inspect webserver`** → **False**  
  - This only shows metadata about a container but does not provide shell access.  

- **C. `docker run -it nginx /bin/sh`** → **False**  
  - This creates and runs a **new** container instead of connecting to the existing `nginx` container.  

- **D. `docker ssh-it nginx /bin/sh`** → **False**  
  - `docker ssh` is not a valid Docker command. SSH is not built into Docker, but you can install an SSH server inside the container if needed.  

Thus, **A** is the correct option.
