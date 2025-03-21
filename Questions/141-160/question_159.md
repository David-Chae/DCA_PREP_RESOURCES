## 159. Bob installed docker from scratch on his new Linux server. He only installed docker packages from the official repository and has not played around with anything else. 
## Which logging driver will be used by the new container when launched using the command "docker run -d nginx"?
A. Logentries  
B. Jounald  
C. Syslog  
D. json-file  

The correct answer is:

**D. json-file**

Explanation:
By default, Docker uses the `json-file` logging driver for containers when they are launched. This driver logs container output in JSON format, and these logs are stored locally on the host machine. 

Here's a breakdown of the other options:
- **A. Logentries**: This is not the default logging driver in Docker. It is a third-party logging service that can be configured, but not used by default.
- **B. Journald**: This logging driver is specific to systems using `systemd`. It is not the default unless specifically configured.
- **C. Syslog**: This is another available logging driver in Docker, but it's not the default. It can be used if configured, but it's not the default logging driver. 

So, for a fresh Docker installation on a Linux server, **`json-file`** is the default.
