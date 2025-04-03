## Which of the following claims about the WORKDIR directive is false?
A. Containers that run from the image are unaffected; only the build is affected.  
B. For subsequent build steps, it sets the working directory.  
C. It can employ paths that are both absolute and relative.  
D. It configures the container's working directory during runtime.

The false statement is:

**A. Containers that run from the image are unaffected; only the build is affected.**  

### Explanation:
- The **`WORKDIR`** directive in a Dockerfile sets the working directory for subsequent `RUN`, `CMD`, `ENTRYPOINT`, and other instructions **during both build and runtime**.
- **B (True)**: It indeed sets the working directory for subsequent build steps.
- **C (True)**: It can accept both absolute and relative paths (relative paths are resolved from the previous `WORKDIR` setting or root).
- **D (True)**: It sets the working directory for the container during runtime, meaning any command executed inside the container starts from this directory.

Thus, **A is false** because the `WORKDIR` directive **affects both the image build process and runtime behavior** of the container.
