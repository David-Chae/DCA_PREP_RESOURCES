## In the Universal Control Plane, people require comparable permissions (UCP). Instead of providing unique access to each person individually, how can we manage their permissions as a group? 
1. Apply the users to a team and then assign grants to the entire team, granting them the necessary permissions.
2. Create a shared role with several permissions, and then assign each user to that role.
3. Grants are added to one person to provide them the access they require. Subsequently, those users' permissions are transferred to others.
5. Create a GrantBundle for each user and assign it to them.

The correct answer is:  

**"Apply the users to a team and then assign grants to the entire team, granting them the necessary permissions."**  

### **Explanation:**
- In **Docker Universal Control Plane (UCP)**, **Teams** are used to manage permissions efficiently.
- Instead of assigning permissions to each user individually, you can create a **team**, add users to it, and then apply **grants** (permissions) to the entire team.
- This method simplifies **access control**, ensures **consistency**, and makes it easier to manage permissions as team members change.

### **Why the Other Options Are Incorrect:**
1. **"Create a shared role with several permissions, and then assign each user to that role."**  
   - UCP does not use **roles** in this way. Instead, permissions (grants) are applied to teams or individual users.

2. **"Grants are added to one person to provide them the access they require. Subsequently, those users' permissions are transferred to others."**  
   - Permissions in UCP are **not transferred** between users. Each user needs to be explicitly assigned to a team or given specific grants.

3. **"Create a GrantBundle for each user and assign it to them."**  
   - **GrantBundles** are not a UCP concept for managing user permissions. Instead, **teams and grants** are the correct approach.

By using **teams** to manage user permissions, UCP ensures a scalable and organized approach to access control.
