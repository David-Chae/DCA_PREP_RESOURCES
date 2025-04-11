## We have a group of people who need similar permissions in Universal Control Plane (UCP). How can we manage their permissions as a group without having to assign individual permissions to each user manually?
```
1. Create a GrantBundle and assign it to each user.
2. Assign the users to a team, and then assign grants to the entire team, giving them the permissions they need.
3. Create a role with several permissions assigned, and then assign each user to that shared role.
4. Add grants to one user to give them the permissions they need, and then copy that user's permissions to the other users.
```

✅ **Correct Answer:**  
**Assign the users to a team, and then assign grants to the entire team, giving them the permissions they need.**

---

### 🧠 Explanation:

In **Docker Universal Control Plane (UCP)**, the best way to manage permissions for multiple users efficiently is by using **teams**:

- **Teams** allow you to group users together.
- You can then **assign grants** (which define access to resources via roles) to the **entire team**.
- This avoids the need to assign individual permissions to each user, making management **scalable and consistent**.

---

### ❌ Why the others are incorrect:

- **"Create a GrantBundle..."** → There's no such object as "GrantBundle" in UCP terminology.
- **"Create a role..."** → Roles define *what* permissions are granted, but you must still assign those roles via grants, typically to users or teams.
- **"Copy that user's permissions..."** → UCP doesn’t support a copy-permissions feature natively.

Let me know if you’d like a walkthrough of how to assign a role to a team in UCP!
