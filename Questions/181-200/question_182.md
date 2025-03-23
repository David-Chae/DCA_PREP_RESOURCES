## 182. Is PID namespace disabled by default and must be activated to be used at Docker engine runtime?
A. Yes  
B. No  

**B. No**  

Explanation:  
By default, Docker uses its own PID namespace for each container, meaning that processes inside a container are isolated from those outside. However, you can enable PID namespace sharing using the `--pid` flag when running a container. For example:  

```
docker run --pid=host my_container
```

This allows the container to share the host’s PID namespace, but it is **not disabled by default**—it is simply isolated unless explicitly configured otherwise.
