## Which of the following claims about the WORKDIR directive is false?
A. Containers that run from the image are unaffected; only the build is affected.  
B. For subsequent build steps, it sets the working directory.  
C. It can employ paths that are both absolute and relative.  
D. It configures the container's working directory during runtime.

The correct answer is:

❌ **D. It configures the container's working directory during runtime.**

---

### **Explanation:**

- **Option D** is false because the **WORKDIR** directive in a Dockerfile is used to set the working directory **during the build process** and **for subsequent instructions** in the Dockerfile. It does not affect the container's working directory during runtime. The container’s working directory during runtime is typically controlled by the command specified in the **CMD** or **ENTRYPOINT** directive, but **WORKDIR** itself only affects the build and the subsequent build steps.

---

### **Why the other options are correct:**

- **✔ Option A (`Containers that run from the image are unaffected; only the build is affected.`)**:
  - This is true because **WORKDIR** affects the build process. It sets the working directory for any subsequent build steps (like **RUN**, **COPY**, etc.) and does not affect the container’s runtime behavior. The **WORKDIR** path used during the build does not carry over to the container runtime unless explicitly used by the command run in the container.

- **✔ Option B (`For subsequent build steps, it sets the working directory.`)**:
  - This is true. After a **WORKDIR** directive is set in a Dockerfile, any subsequent build steps (such as **RUN**, **COPY**, etc.) are executed relative to that directory.

- **✔ Option C (`It can employ paths that are both absolute and relative.`)**:
  - This is true. The **WORKDIR** directive can accept both absolute and relative paths. If a relative path is specified, it is resolved relative to the current working directory.

---

### **Final Answer:**
❌ **D. It configures the container's working directory during runtime.**
