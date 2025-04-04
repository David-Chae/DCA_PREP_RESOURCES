## 113. Which of the following network drivers provides complete control of IP addresses?
A. ipvlan  
B. None  
C. Bridge  
D. macvlan


The correct answer is:

**A. ipvlan**

**Explanation:**

- **ipvlan** provides complete control of IP addresses within a network. It is a network driver that allows for multiple containers or virtual interfaces to share the same MAC address but have different IP addresses. This gives greater control over IP address management in a containerized environment.

The other options:

- **B. None** is not correct because **ipvlan** does indeed provide control over IP addresses.
  
- **C. Bridge** is a common network driver but does not provide as much control over IP addresses. It typically uses the host's network stack to manage IP addresses, relying more on Docker’s or the system's default network settings.
  
- **D. macvlan** creates virtual network interfaces with unique MAC addresses but does not directly control IP addresses in the way **ipvlan** does. It typically allows devices to appear on the network as if they are physical devices but does not provide the same level of IP management control as **ipvlan**.

Therefore, **ipvlan** is the correct choice as it allows for precise control over IP addresses in containerized environments.
