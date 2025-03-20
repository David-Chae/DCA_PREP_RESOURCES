## 126. Which of the following can communicate between the Docker host and container?
A. Volume Mount  
B. npipe Mount  
C. tmps Mount  
D. Bind Mount  

The correct answer is:  

**D. Bind Mount**  

- **Bind Mounts** allow communication between the Docker **host** and **container** by mounting a directory from the host into the container.  
- Changes made in the mounted directory on either the host or the container are reflected in both.  
- This is useful for sharing configurations, logs, or application files.  
