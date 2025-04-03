## 93. Nancy wants to use the foo image to run a container. She desires to publish port 3001 from the container to port 5050 on the host. Which of the subsequent commands will make this happen?
A. docker run --port 5050:3001 foo  
B. docker run -d-p 3001:5050 foo  
C. docker run -d-p 5050:3001 foo  
D. docker run foo-p 5050:3001  

The correct answer is:

**C. docker run -d -p 5050:3001 foo**

---

### **Explanation:**

- The `-p` flag in Docker is used to publish a container's port to the host. The correct format for using the `-p` flag is `host_port:container_port`.
  
- **In this case:**
  - **5050** is the port on the **host**.
  - **3001** is the port inside the **container**.
  
  Thus, `-p 5050:3001` will publish the container's port 3001 to the host's port 5050.

- **-d** stands for **detached mode**, which means the container will run in the background.

---

### **Why the other options are incorrect:**

- **A. docker run --port 5050:3001 foo**
  - The correct flag to publish ports is `-p`, not `--port`.

- **B. docker run -d -p 3001:5050 foo**
  - This reverses the order of the ports. It would publish container port 5050 to host port 3001, but Nancy wanted to publish container port 3001 to host port 5050, so this is not the right command.

- **D. docker run foo -p 5050:3001**
  - This is incorrect syntax. The correct form is to place `-p 5050:3001` immediately after `docker run` rather than at the end.

---

### **Final Answer:**
**C. docker run -d -p 5050:3001 foo**
