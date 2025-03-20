## 127. Which of the following mounts the secret into the service container?
A. tmpfs Mount  
B. npipe Mount  
C. Volume Mount  
D. Bind Mount  

The correct answer is:  

**A. tmpfs Mount**  

- **tmpfs Mount** is used to store sensitive data, such as **secrets**, in memory instead of writing them to disk.  
- It ensures that secrets do not persist after the container stops, enhancing security.  
- This is particularly useful in **Docker Swarm** when using **Docker secrets**.
