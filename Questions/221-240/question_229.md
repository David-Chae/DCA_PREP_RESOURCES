## 229. How to update metadata about a node?
A. Labels provide a way to update metadata about a node  
B. Use the docker node update command with the --label-add option  
C. Metadata can only be updated during node initialization  
D. Docker does not support updating metadata about nodes  

The correct answer is:

**B. Use the docker node update command with the --label-add option**

Explanation:
- You can update metadata about a node in Docker by using the `docker node update` command along with options like `--label-add` to add labels. Labels are a way to associate metadata with Docker objects, including nodes. For example, you can add a label to a node to categorize it or give it specific attributes for scheduling or other purposes.

The other options are incorrect:
- **A. Labels provide a way to update metadata about a node**: While labels are used to store metadata, simply using labels does not directly update metadata. The update process requires the `docker node update` command.
- **C. Metadata can only be updated during node initialization**: This is not true. You can update metadata at any time, not just during initialization.
- **D. Docker does not support updating metadata about nodes**: This is incorrect because Docker does support updating metadata using commands like `docker node update`.

So, the correct method for updating metadata about a node is **B**.
