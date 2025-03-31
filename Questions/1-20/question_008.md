## 8. Which commands can take a tar file as an argument and automatically add the extracted content into the image? Choose the possible options.
A. COPY  
B. ADD  
C. ADD and DELETE both  
D. None of these  

The correct answer is:  

**B. ADD**  

### Explanation:  
- **`ADD`** can take a `.tar` file as an argument and automatically extract its contents into the image.  
  Example:  
  ```dockerfile
  ADD archive.tar /app/
  ```
  This will extract `archive.tar` into `/app/`.  

- **`COPY`** does **not** extract `.tar` files automatically. It only copies files as-is.  
  Example:  
  ```dockerfile
  COPY archive.tar /app/
  ```
  This just copies `archive.tar` to `/app/` without extracting it.  

- **DELETE** is not a valid Dockerfile command.  

Thus, the correct answer is **B. ADD**.
