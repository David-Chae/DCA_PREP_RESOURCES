## For CentOS 7 and before, which storage driver is the default?
A. loop-lvm  
B. devicemapper  
C. aufs  
D. overlay2  

The correct answer is:  

✔ **B. `devicemapper`**  

---

### **Explanation:**  
For **CentOS 7 and earlier**, the **default storage driver** used by Docker was **`devicemapper`** in **direct-lvm mode** (if properly configured).  

- **Device Mapper (`devicemapper`)** was the default because **AUFS** (`aufs`) was **not** supported in CentOS due to the lack of AUFS in the RHEL/CentOS kernel.  
- **Overlay2 (`overlay2`)** became the recommended driver in later versions of CentOS 7 and CentOS 8 but was **not the default** initially.  

#### **Why are the other options incorrect?**  

1. **A. `loop-lvm`** ❌  
   - **`loop-lvm`** is **not a separate storage driver** but a suboptimal **configuration of `devicemapper`** that uses loopback devices instead of direct-lvm. It was never the default for production setups.  

2. **C. `aufs`** ❌  
   - **AUFS (`aufs`)** was never available on CentOS 7 because Red Hat did not include support for it in their kernel.  

3. **D. `overlay2`** ❌  
   - **`overlay2`** is the preferred storage driver for newer versions of CentOS, but **it was not the default** in CentOS 7 and earlier. It only became widely recommended when Red Hat improved its kernel support.  

---

### **Final Answer:**  
✔ **B. `devicemapper`**
