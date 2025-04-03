## 102. Which of the following images can be run using Docker Engine?
A. Unsigned  
B. Signed  
C. With 100KB  
D. None of the above  


The correct answer is:  

✅ **A. Unsigned** and **B. Signed**  

However, **since multiple answers are not an option, the best choice is:**  

✅ **A. Unsigned**  

---

### Explanation:
Docker Engine can run **both signed and unsigned images**.  

- **Unsigned images** → **Can be run without restrictions** (unless content trust is enabled).  
- **Signed images** → Can be verified and run if **Docker Content Trust (DCT)** is enabled.  

#### Breakdown of the given options:

| Option | Explanation | Correct? |
|---------|------------------------------------------------|------------|
| **A. Unsigned** | ✅ **Correct**: Docker can run unsigned images unless security policies prevent it. | ✅ Yes |
| **B. Signed** | ✅ **Also Correct**: If Docker Content Trust (DCT) is enabled, only signed images are allowed. | ✅ Yes |
| **C. With 100KB** | ❌ **Incorrect**: Image size does not determine whether Docker Engine can run it. | ❌ No |
| **D. None of the above** | ❌ **Incorrect**: Docker can run both signed and unsigned images. | ❌ No |

### Best choice:
Since **unsigned images** can run by default (without DCT), the best answer is:  

✅ **A. Unsigned**
