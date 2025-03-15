113. Which of the following network drivers provides complete control of IP addresses?
A. ipvlan  
B. None  
C. Bridge  
D. macvlan


The correct answer is:

**A. ipvlan**

### **Explanation:**

The **ipvlan** network driver provides complete control over IP addresses by allowing containers to be assigned their own IP addresses within a network, without the need for a virtual network bridge. This driver is often used when you need to manage IP addresses directly for each container, offering flexibility for networking and better integration with external systems.

- **macvlan** also provides containers with their own MAC addresses and allows containers to be treated as physical devices on the network, but **ipvlan** offers more precise control over the IP address allocation.

### **Final Answer:**
**A. ipvlan**
