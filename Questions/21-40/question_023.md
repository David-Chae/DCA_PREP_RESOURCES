## Tracy has a Docker Trusted Registry (DTR), and her development team mistakenly overwrote images in a repository by pushing a different image with an existing tag. How can she prevent this from happening? 
1. Tracy can back up the registry.
2. Tracy can make the repository private.
3. Tracy can remove the team's access to the registry.
4. Tracy can mark the repository as immutable.

The correct answer is:  

✅ **"Tracy can mark the repository as immutable."**  

---

### **Explanation:**  
In **Docker Trusted Registry (DTR)**, an **immutable repository** prevents images from being **overwritten** if they have the same tag. This ensures that once an image is pushed, it remains unchanged, avoiding accidental overwrites.  

To mark a repository as **immutable** in DTR:  
1. **Go to the DTR web UI**  
2. **Select the repository**  
3. **Enable the "Immutable tags" setting**  

Once enabled, any attempt to push an image **with an existing tag** will be **blocked**.

---

### **Why the Other Options Are Incorrect?**  

❌ **"Tracy can back up the registry."**  
- Backups help restore data but **do not prevent accidental overwrites** from happening in the first place.  

❌ **"Tracy can make the repository private."**  
- A private repository only **restricts access**, but it does **not** prevent overwriting existing tags.  

❌ **"Tracy can remove the team's access to the registry."**  
- This would **block all access**, preventing the team from pushing any images, not just overwrites.  

---

### **Summary:**  
To prevent accidental overwrites in Docker Trusted Registry, **Tracy should mark the repository as immutable.**
