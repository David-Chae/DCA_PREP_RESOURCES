## Which flag in Docker Inspect enables us to return particular fields?
A. --filter  
B.--field-limit  
C.--pretty  
D.--format  

The correct answer is:  

✔ **A. `--filter`**

---

### **Explanation:**

#### **1️⃣ Option A (`--filter`)**  
- The **`--filter`** flag is used to return particular fields or filter out certain information when using `docker inspect`.  
- This flag is typically used to filter results based on specific criteria (e.g., filtering containers by status, image, etc.).  
- **Example usage:**  
  ```bash
  docker inspect --filter "status=running" container_name_or_id
  ```

---

#### **2️⃣ Option D (`--format`)**  
- The **`--format`** flag allows you to format the output using Go templating to display specific fields in a custom format.  
- It is used to display selected fields rather than filtering, which is more flexible in extracting data from the inspection output.  
- **Example usage:**  
  ```bash
  docker inspect --format '{{.Config.Image}}' container_name_or_id
  ```

---

#### **Why the other options are incorrect?**

- **❌ Option B (`--field-limit`)**  
  - This is **not a valid flag** in `docker inspect`.

- **❌ Option C (`--pretty`)**  
  - **`--pretty`** is **not a valid flag** in `docker inspect`.

---

### **Final Answer:**  
✔ **A. `--filter`**
