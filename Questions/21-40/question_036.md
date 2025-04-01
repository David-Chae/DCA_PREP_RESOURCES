## Which of the following is true of filesystem storage models? (Choose two) 
1. They use an external, object-based store. 
2. They are used by overlay2 and aufs. 
3. They store data in regular files on the host machine. 
4. They are efficient with write-heavy workloads.

The correct answers are:

✅ **They are used by overlay2 and aufs.**

✅ **They store data in regular files on the host machine.**

---

### **Explanation:**

1. **They are used by overlay2 and aufs:**
   - **overlay2** and **aufs** are examples of **storage drivers** in Docker that are part of the **filesystem storage model**.
   - These drivers manage container filesystems by layering and providing an efficient method to handle container image layers. They store data in the underlying filesystem and manage writes and reads by using the overlay file system model.

2. **They store data in regular files on the host machine:**
   - The **filesystem storage model** (used by storage drivers like **overlay2** and **aufs**) stores data in regular files on the host machine. These files represent container layers and other data stored in the container filesystem.

---

### **Why the Other Options Are Incorrect:**

❌ **They use an external, object-based store:**
   - This statement is not true of **filesystem storage models** like **overlay2** or **aufs**. These storage models use the host machine's local filesystem, not an external, object-based store. Object storage is typically associated with other types of storage, such as cloud storage systems (e.g., AWS S3), but not Docker filesystem storage models.

❌ **They are efficient with write-heavy workloads:**
   - Filesystem storage models like **overlay2** and **aufs** are generally more efficient for **read-heavy** workloads, as they are designed to efficiently layer files and minimize redundant data. Write-heavy workloads can lead to inefficiencies in these models due to the nature of how data is layered and managed, especially when multiple layers are involved.

---

### **Summary:**
Filesystem storage models like **overlay2** and **aufs** are used in Docker to manage container filesystems by storing data in regular files on the host machine and utilizing layered filesystems. They are not optimized for external object stores or write-heavy workloads.
