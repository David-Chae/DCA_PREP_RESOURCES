## 3. Bob has configured his docker daemon to use the syslog log driver by default; how can he run a container which uses the json-file log driver?
A. By using "--log-opt json-file" along with docker run  
B. By using "--log-driver json-file" along with docker run  
C. By using "--logger json-file" along with docker run  
D. Not possible  

The correct answer is:  

**B. By using "--log-driver json-file" along with docker run**  

Explanation:  
Docker allows you to override the default log driver configured in the daemon settings by specifying a different log driver when running a container. The correct option for specifying the log driver is `--log-driver json-file`.  

Example command:  
```sh
docker run --log-driver json-file -d my-container-image
```  
