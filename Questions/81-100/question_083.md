## Our nginx service has replicas that are failing. Which of the following commands can list every replica that makes up a service?
```sh
A. docker service ps nginx  
B. docker service get nginx  
C. docker container ls  
D. docker ps  
```

The correct answer is:

✔ **A. `docker service ps nginx`**

---

### **Explanation:**

#### **1️⃣ Option A (`docker service ps nginx`)**  
- The **`docker service ps`** command shows the status of tasks (replicas) that are part of a service.  
- It lists all the tasks associated with the service, including their current state (running, failed, etc.) and on which nodes they are located.  
- **Example usage:**  
  ```bash
  docker service ps nginx
  ```

---

#### **Why the other options are incorrect?**

- **❌ Option B (`docker service get nginx`)**  
  - **`docker service get`** is **not a valid Docker command**. You would use `docker service ps` to list replicas, not `docker service get`.

- **❌ Option C (`docker container ls`)**  
  - **`docker container ls`** shows a list of all running containers but does not specifically list the replicas of a service. It shows individual containers, regardless of whether they're part of a service or not.

- **❌ Option D (`docker ps`)**  
  - **`docker ps`** is similar to `docker container ls` and shows all running containers but doesn't provide information specific to service replicas.

---

### **Final Answer:**  
✔ **A. `docker service ps nginx`**
