## 198. Will the given command return a list of volumes for a given container?
## docker container logs nginx --volumes
A. Yes  
B. No  

**B. No**

The command `docker container logs nginx --volumes` is not valid for listing volumes. To list volumes associated with a container, you would need to use `docker container inspect nginx` and look for the `Mounts` section in the output.
