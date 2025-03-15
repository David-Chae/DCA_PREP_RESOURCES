## Sara wants to run a container using the busybox image and pass a custom command to the container: echo Docker is great! Which of the following commands will accomplish this? 
1. docker run busybox -cmd echo Docker is great! 
2. docker run busybox ["echo", "Docker is great!"] 
3. docker run busybox -c echo Docker is great! 
4. docker run busybox echo Docker is great!

The correct command is:

**`docker run busybox echo Docker is great!`**

### **Explanation:**
- In this command, `docker run busybox` starts a container using the `busybox` image.
- The `echo Docker is great!` part is the command that is passed to the container, and `echo` is the default executable for the `busybox` image. The rest of the text, `"Docker is great!"`, is the argument passed to the `echo` command.

### **Why the Other Options Are Incorrect:**
1. **`docker run busybox -cmd echo Docker is great!`**:
   - The `-cmd` flag is not a valid option for the `docker run` command. You should pass the command directly after the image name.

2. **`docker run busybox ["echo", "Docker is great!"]`**:
   - This syntax would be correct if the command were specified in the `CMD` or `ENTRYPOINT` instruction of a Dockerfile, but not for running it directly via `docker run`. The correct way to pass commands is to do it as arguments, not in array format.

3. **`docker run busybox -c echo Docker is great!`**:
   - The `-c` flag is used in shell commands (e.g., `sh -c`), but it's not necessary for this case. The `echo` command can be passed directly without the need for `-c`.

