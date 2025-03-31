## Which of the following statements is correct? Choose two statements at random. 
1. A container is a running instance of an image, whereas an image is a collection of immutable layers. 
2. The image can exist without the container, but the container cannot exist without the image. 
3. Only one container can be made from a given image at any moment. 
4. When several containers are created from the same image, they all use the same memory copy of the image.

## Correct Statements About Docker Containers and Images

### The correct statements are:

✅ **"A container is a running instance of an image, whereas an image is a collection of immutable layers."**  
✅ **"The image can exist without the container, but the container cannot exist without the image."**  

---

### Explanation:
- **A container is a running instance of an image**:  
  A **container** is created by running an image, which is a template or blueprint for the container. The **image** itself consists of immutable layers, which are stacked together to create the final image.

- **An image can exist without the container, but the container cannot exist without the image**:  
  **Images** are stored as read-only files, and containers are created from images. A **container** cannot exist without being instantiated from an image, but an **image** can exist independently of any running container.

---

### Why the Other Statements Are Incorrect:

❌ **"Only one container can be made from a given image at any moment."**  
   - This is incorrect because multiple **containers** can be created from the same image simultaneously. Each container is a separate instance, but they all share the same image.

❌ **"When several containers are created from the same image, they all use the same memory copy of the image."**  
   - This is incorrect in terms of memory usage. While **containers** share the same image layers (which are read-only), each **container** has its own separate **runtime memory** for its writable layer. This means they do not share the same memory copy of the image in terms of their **running state**.

---

### Final Summary:
- Containers are instances of images, and an image can exist without a container, but the container cannot exist without the image.  
- Multiple containers can be created from the same image.
