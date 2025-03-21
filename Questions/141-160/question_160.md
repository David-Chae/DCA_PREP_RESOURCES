## 160. You are now in a directory that contains the Dockerfile-app file. 
## Without renaming it to "Dockerfile," you can use this "Dockerfile-app" file to create a Docker image. 
## Which of the subsequent responses is true?
A. docker build -f Dockerfile-app  
B. docker build -from-file Dockerfile-app  
C. docker build -dockerfile Dockerfile-app  
D. docker build-d Dockerfile-app  

The correct answer is:

**A. docker build -f Dockerfile-app**

Explanation:
When you want to specify a Dockerfile with a custom name (like `Dockerfile-app` instead of the default `Dockerfile`), you use the `-f` flag followed by the file name. The command would look like this:

```bash
docker build -f Dockerfile-app .
```

Where:
- `-f` specifies the path to the Dockerfile.
- `Dockerfile-app` is the custom Dockerfile name.
- The `.` indicates the current directory as the build context.

The other options are incorrect:
- **B.** There is no `-from-file` option in Docker build.
- **C.** `-dockerfile` is not a valid option for the `docker build` command.
- **D.** `-d` is used for detached mode in `docker run`, not for specifying a Dockerfile.

So, the correct way to build an image with a Dockerfile named `Dockerfile-app` is **A**.
