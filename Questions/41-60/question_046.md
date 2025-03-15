## Anastasia has created a container with a volume called shared-data. She wants to create a new container to access the same data as the first. However, she wants this new container only to be able to read the data, not modify it. How can she accomplish this? 
1. Anastasia can create a bind mount for the new container that points to the physical location of the shared volume on the host.
2. Anastasia can use docker run --name new-container -v shared-data:/tmp nginx.
3. This task is impossible for Anastasia to complete because we cannot mount the same volume to two containers.
4. Anastasia can use docker run --name new-container -v shared-data:/tmp:ro nginx.

The correct way for Anastasia to accomplish this is:

✅ **Anastasia can use docker run --name new-container -v shared-data:/tmp:ro nginx.**

### **Explanation:**

- The `-v shared-data:/tmp:ro` option allows Anastasia to mount the `shared-data` volume into the new container, but with **read-only** (`ro`) access. This means the new container will be able to read data from the volume but not modify it.
  
### **Other Options:**

❌ **Anastasia can create a bind mount for the new container that points to the physical location of the shared volume on the host.**  
- This approach would allow read/write access to the volume unless explicitly specified. It's not the recommended solution if you want to control access permissions as the bind mount gives direct access to the host filesystem.

❌ **This task is impossible for Anastasia to complete because we cannot mount the same volume to two containers.**  
- This is incorrect. Docker allows you to mount the same volume to multiple containers with proper access control like the `:ro` option.

### **Final Answer:**
To give the new container **read-only** access to the `shared-data` volume, Anastasia should use:

```
docker run --name new-container -v shared-data:/tmp:ro nginx
```
