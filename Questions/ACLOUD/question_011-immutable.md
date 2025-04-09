## Tracy has a Docker Trusted Registry (DTR), and her development team has been mistakenly overwriting images in a repository by pushing a different image with an existing tag. How can she prevent this from happening?

To prevent images from being overwritten in a **Docker Trusted Registry (DTR)**, Tracy can implement the following solution:

### ✅ **Enforce tag immutability in DTR.**

In **Docker Trusted Registry (DTR)**, she can **enable tag immutability** to ensure that once an image with a certain tag is pushed, it cannot be overwritten with another image.

### Steps Tracy can take:
1. **Log in to the DTR web UI** using her admin credentials.
2. **Navigate to the repository** where the images are stored.
3. Go to the **Settings** for that repository.
4. **Enable tag immutability** for the repository.
   - This setting ensures that once an image with a specific tag is pushed to the repository, the tag cannot be reused or overwritten by another image.

### Why is this important?
- This prevents accidental overwriting of images with the same tag, which could lead to confusion or deployment of the wrong image version.
- Immutability ensures that tags remain consistent and reflect the exact image pushed at the time.

---

If Tracy's team needs to update or modify an image, they would need to **use a new tag** (for example, `v2`, `latest`, etc.) rather than overwriting the existing tagged image.

Let me know if you'd like help with any specific steps or further details!
