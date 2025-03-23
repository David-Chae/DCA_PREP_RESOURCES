## 184. Will the given command return a list of volumes for a given container?
## docker volume logs nginx -containers
A. Yes  
B. No  

**B. No**  

### Explanation:  
The given command **`docker volume logs nginx -containers`** is incorrect and will not return a list of volumes for the container.  

#### Correct way to list volumes for a given container:
To check the volumes attached to a specific container (`nginx` in this case), use:  
```sh
docker container inspect nginx
```
Then, look under the `"Mounts"` section in the JSON output to see the attached volumes.

Alternatively, to list all Docker volumes:
```sh
docker volume ls
```

#### Key Points:
- `docker volume logs` is **not a valid command**.
- `docker container inspect <container_name>` provides volume details.
- `docker volume ls` lists all available volumes.
