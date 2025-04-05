## 175. Could the failure of a user's attempts to set the system time from within a Docker container constitute a hindrance to the operation of the container?
A. Yes  
B. No  

**A. Yes**

Explanation:
Failure to set the system time within a Docker container could cause issues, particularly for applications that rely on accurate time synchronization, such as those dealing with scheduled tasks, logging, or time-sensitive transactions. While containers typically rely on the host system's time, certain applications inside the container may need to adjust or manage the system time themselves. If this is restricted or fails, it could disrupt operations.
  
This operation is being thwarted by Linux capabilities. Linux capabilities are a division of the powers usually associated with the superuser into different parts called capabilities that can be enabled and disabled independently. Docker uses capabilities to limit the tasks that a container can do on the host system. Docker disables all capabilities save those required for common activities, such as binding to ports less than 1024 or mounting filesystems. CAP_SYS_TIME, which allows you to set the system clock, is one of the capabilities that is disabled by default. As a result, unless this capability is expressly introduced, a user cannot set the system time from within a Docker container.   
  
References:   
https://docs.docker.com/engine/security/security/#linux-kernel-capabilities   
https://man7.org/linux/man-pages/man7/capabilities.7.html  
