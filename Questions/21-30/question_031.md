## Which of the following commands can create a new named volume? 
1. docker run --mount source=/my-vol,destination=/tmp nginx \ 
2. docker run -v /my-vol:/tmp nginx 
3. docker run -v my-vol:/tmp nginx 
4. docker run -v /my-vol:/tmp:create nginx

The correct answer is:  

**`docker run -v my-vol:/tmp nginx`**  

### **Explanation:**
- In Docker, a **named volume** is a persistent storage unit managed by Docker, which is separate from the container’s lifecycle.
- The **`-v` (or `--volume`)** option allows you to specify a volume.
- When you use **`-v my-vol:/tmp`**, Docker **creates a named volume** called **`my-vol`** (if it does not exist) and mounts it to **`/tmp`** in the container.

### **Why the Other Options Are Incorrect:**
1. **`docker run --mount source=/my-vol,destination=/tmp nginx`**  
   - The **`--mount`** option uses a different syntax.
   - For named volumes, the correct syntax should be:  
     **`--mount type=volume,source=my-vol,target=/tmp`**  
   - Also, **`source=/my-vol`** suggests a path, but named volumes don’t use absolute paths.

2. **`docker run -v /my-vol:/tmp nginx`**  
   - **Incorrect because `/my-vol` is an absolute path**, which creates a **bind mount** instead of a **named volume**.
   - A named volume should **not** start with `/`.

3. **`docker run -v /my-vol:/tmp:create nginx`**  
   - **Syntax is incorrect.**  
   - The `-v` option does **not** accept a `:create` argument.

### **Conclusion:**
The correct way to create a **new named volume** is:  
**`docker run -v my-vol:/tmp nginx`**
