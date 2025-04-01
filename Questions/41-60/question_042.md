## 42. What would a container generated from the following Dockerfile's runtime working directory be?

```dockerfile
FROM alpine  
WORKDIR /x  
WORKDIR /y  
WORKDIR z  
CMD pwd  
```  

```sh
A. /y/z
B. /Z
C. /x
D. /
```

The correct answer is:  

**A. `./y/z`**  

### Explanation:  
In the given `Dockerfile`:  
```dockerfile
FROM alpine  
WORKDIR /x  
WORKDIR /y  
WORKDIR z  
CMD pwd  
```  

- `WORKDIR /x` → Sets the working directory to `/x`.  
- `WORKDIR /y` → Changes the working directory to `/y`, replacing `/x`.  
- `WORKDIR z` → Since `z` is a relative path, it appends to the current working directory (`/y`), making it `/y/z`.  
- `CMD pwd` → Runs `pwd` in the container, which prints `/y/z`.  

Thus, the runtime working directory is **`/y/z`**, making **A** the correct answer.
