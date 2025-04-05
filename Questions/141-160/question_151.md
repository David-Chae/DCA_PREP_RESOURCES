## 151. Bob wants to test a rogue Docker image with a problem that causes it to start consuming memory quickly, resulting in other apps on the system crashing due to memory exhaustion. Bob wants the container to run with a 512MB maximum memory limit. Which of the following may Bob utilize to solve this issue when operating a container?
A. docker run-m 512  
B. docker run -limit 5 12  
C. docker run -limit 5 12m  
D. docker run -m 512m  

The correct answer is:

**D. docker run -m 512m**

Explanation:
- The `-m` flag in the `docker run` command is used to set the memory limit for the container.
- The value `512m` specifies the maximum memory allocation of 512MB.

Here's a breakdown of the other options:
- **A. docker run -m 512**: This would work if the memory value is interpreted as bytes, but it's not the common practice to specify without units.
- **B. docker run -limit 512**: This option is incorrect because `-limit` is not a valid flag.
- **C. docker run -limit 512m**: This is incorrect because `-limit` is not a valid flag for limiting memory.

Therefore, **D. docker run -m 512m** is the correct command to set the memory limit to 512MB.
