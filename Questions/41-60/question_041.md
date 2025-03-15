## Which of the following commands will run a busybox container and automatically delete it once it exits? 
1. docker run --rm busybox
2. docker container rm busybox
3. docker run --rm --restart on-failure busybox
4. docker run --restart no busybox

The correct command is:  

✅ **`docker run --rm busybox`**  

### **Explanation:**  
- The `--rm` flag ensures that the container is **automatically removed** when it stops.  
- This means **no manual cleanup** is needed after the container exits.  

### **Why the Other Options Are Incorrect:**  
❌ **`docker container rm busybox`**  
- This command **removes an existing container**, but **it does not run** one.  
- Also, it does **not ensure automatic deletion upon exit**—it requires manual execution.  

❌ **`docker run --rm --restart on-failure busybox`**  
- The `--rm` flag **conflicts with** `--restart on-failure`.  
- Containers with `--rm` **cannot** have a restart policy because they are deleted upon exit.  

❌ **`docker run --restart no busybox`**  
- This command runs the container **without an automatic restart**, but it **does not delete** the container upon exit.  

### **Final Answer:**  
✅ **`docker run --rm busybox`**
