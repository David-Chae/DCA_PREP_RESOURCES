## What type of data exists in a container's writable file system layer? 
1. A snapshot of the data in its current state would reside in the layer. 
2. It would be only the data from the base image. 
3. The data would consist of only container logs. 
4. The data would consist of only changes from the previous layer made by the container.

The correct answer is:

**The data would consist of only changes from the previous layer made by the container.**

### **Explanation:**
- In Docker, when a container is created from an image, it uses a **writable layer** on top of the read-only layers of the image. Any changes made to the container, such as modified files, newly created files, or removed files, are stored in this writable layer.
- The writable layer only contains the changes made by the container since it was created. This layer is distinct from the base image, which is read-only and provides the initial filesystem state.

### **Why the Other Options Are Incorrect:**
1. **A snapshot of the data in its current state would reside in the layer**:
   - This is incorrect because the writable layer only tracks changes (modifications, additions, deletions), not the entire state of the filesystem.

2. **It would be only the data from the base image**:
   - The base image provides the read-only layers that the container uses, but the writable layer contains the changes made after the container is started. The writable layer is not the same as the base image data.

3. **The data would consist of only container logs**:
   - This is not correct because the writable layer can contain more than just logs. It includes any file system changes made by the container, not just logs.
 
