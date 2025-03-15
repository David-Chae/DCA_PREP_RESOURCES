## Which of the following claims about the ENV directive is correct? 
1. It sets environment variables that are only visible during later build steps.
2. While executing the container, it establishes an environment variable on the host.
3. It sets environment variables available in subsequent build steps and to containers at the runtime.
4. It sets environment variables that are only visible at the container runtime.

The correct claim about the `ENV` directive is:

✅ **It sets environment variables available in subsequent build steps and to containers at the runtime.**

### **Explanation:**
- The `ENV` directive in a Dockerfile sets environment variables that are available both during **subsequent build steps** and at **runtime** when the container is running. This makes the environment variable accessible to any running container that is built from that Docker image.

### **Other Options:**

❌ **It sets environment variables that are only visible during later build steps.**  
- This is incorrect. The `ENV` directive also makes the environment variable available at runtime, not just during the build.

❌ **While executing the container, it establishes an environment variable on the host.**  
- This is incorrect. The `ENV` directive sets environment variables **inside the container**, not on the host machine.

❌ **It sets environment variables that are only visible at the container runtime.**  
- This is also incorrect. The `ENV` directive makes the environment variable available both at build time (for later build steps) and at runtime (when the container is running).

### **Final Answer:**
The `ENV` directive **sets environment variables available in subsequent build steps and to containers at the runtime**.
