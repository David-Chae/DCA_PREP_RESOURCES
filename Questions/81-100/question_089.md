## What accomplishes the CMD directive?
A. When the container starts, it executes a command on the host.  
B. During the building process, it runs a command.  
C, If no additional command is supplied it establishes the default command for the image to run.  
D. It executes a command inside the image and adds the output to the result.  


The correct answer is:

✔ **C. If no additional command is supplied, it establishes the default command for the image to run.**

---

### **Explanation:**

- **Option C** is correct because the **CMD** directive in a Dockerfile is used to specify the default command that should be executed when a container is started from the image. If no command is provided at runtime (i.e., when running `docker run`), this default command is executed. However, if a command is provided at runtime, it overrides the CMD directive.

---

### **Why the other options are incorrect:**

- **❌ Option A (`When the container starts, it executes a command on the host.`)**:
  - This is incorrect. The **CMD** directive specifies the command that should run **inside** the container, not on the host machine.

- **❌ Option B (`During the building process, it runs a command.`)**:
  - This is incorrect. The **CMD** directive is not run during the build process; it defines the default command for when the container is started, after the image is built.

- **❌ Option D (`It executes a command inside the image and adds the output to the result.`)**:
  - This is incorrect. The **CMD** directive does not execute a command inside the image and capture its output. Instead, it defines the default executable that will be run when the container starts.

---

### **Final Answer:**
✔ **C. If no additional command is supplied, it establishes the default command for the image to run.**
