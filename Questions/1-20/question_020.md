## Sally wants to prevent Docker Swarm encryption keys from storing insecurely on her swarm managers. How can she tackle enforcing a lock on the swarm cluster? 
1. Sally cannot do this because Docker does not offer this functionality. 
2. Sally can use the --autolock=true flag with the docker swarm update command. 
3. Sally can locate the critical files after the installation and delete them. 
4. The autolock feature must be turned on when the cluster is initialized and cannot be enabled after the fact.

The correct answer is:

✅ **"Sally can use the --autolock=true flag with the docker swarm update command."**

---

### **Explanation:**

In Docker Swarm, **autolock** is a feature that encrypts the swarm's **manager node encryption keys**, ensuring that they are not stored insecurely on the swarm managers. The **autolock** feature prevents unauthorized access to the keys and ensures they are only accessible with the proper unlocking mechanism.

1. **To enable autolock** after initializing the swarm:
   - Sally can use the `docker swarm update --autolock=true` command to enforce autolock on her swarm cluster, ensuring the encryption keys are locked.

   Example:
   ```sh
   docker swarm update --autolock=true
   ```

2. **To unlock the swarm** when needed:
   - The `docker swarm unlock` command is required to unlock the swarm, and it will prompt for the unlock key when performing any operation on the swarm that requires access to the keys.

---

### **Why the Other Options Are Incorrect:**

❌ **"Sally cannot do this because Docker does not offer this functionality."**  
- This is incorrect because Docker **does** offer the `--autolock` feature to secure the swarm encryption keys.

❌ **"Sally can locate the critical files after the installation and delete them."**  
- Simply deleting files is not a secure or recommended method. It would not ensure the proper encryption or safety of the swarm keys. Docker provides a more secure mechanism with **autolock**.

❌ **"The autolock feature must be turned on when the cluster is initialized and cannot be enabled after the fact."**  
- This is **incorrect**. The **autolock feature can be enabled at any time** after the swarm has been initialized, using the `docker swarm update --autolock=true` command. It is **not limited to initialization**.

---

### **Summary:**

To ensure Docker Swarm encryption keys are stored securely and locked on the managers, Sally should use the `docker swarm update --autolock=true` command.
