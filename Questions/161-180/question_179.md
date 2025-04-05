## 179. Can the given sequence of commands determine a container's published port(s)? docker container inspect, docker port
```
A. Yes
B. No
```

Answer: A  
Explanation: The sequence of commands 'docker container inspect' and 'docker port' can be used to determine a container's published port(s). 

Here's how it works:
1. You use 'docker container inspect' to gather detailed information about a running container, including its configuration, network settings, etc. This command provides a JSON-formatted output with all the container details.  
2. 'docker port' lists the port mappings for a container. It shows the ports exposed within the container and mapped to the host.  
  
Combining these two commands, you can inspect the container to find its ID or name and then use 'docker port' to see the published ports and their mappings. 
References:  
https://docs.docker.com/engine/reference/commandline/container_inspect/  
https://docs.docker.com/engine/reference/commandline/port/  
