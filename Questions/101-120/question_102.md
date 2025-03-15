## 102. Which of the following images can be run using Docker Engine?
A. Unsigned  
B. Signed  
C. With 100KB  
D. None of the above  


The correct answer is:

**A. Unsigned**

### **Explanation:**

Docker Engine can run both signed and unsigned images. However, **unsigned images** are the default and can be run without any issues. Signed images are typically used when Docker Content Trust (DCT) is enabled to ensure the authenticity and integrity of the image. 

- **Unsigned images**: These images are the most common, and Docker Engine can run them without requiring any specific configuration.
  
- **Signed images**: Docker Content Trust (DCT) enables the use of signed images, which are verified before being used to ensure they haven't been tampered with. However, this is not a requirement for running an image in Docker Engine.

- **With 100KB**: Docker Engine doesn't impose a specific size requirement on the images, and it can run images of varying sizes, including those around 100KB.

### **Final Answer:**
**A. Unsigned**
