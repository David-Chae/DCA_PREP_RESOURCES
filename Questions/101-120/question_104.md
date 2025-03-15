## 104. Which steps are required to secure the Docker daemon HTTP socket?
A. Create a CA  
B. Create server and client certificates  
C. Configure the daemon on the server  
D. Configure the client to connect securely using the client certificate  
E. All of the Above  

The correct answer is:

**E. All of the Above**

### **Explanation:**

To secure the Docker daemon HTTP socket, the following steps are required:

1. **A. Create a CA (Certificate Authority)**: You need to create a Certificate Authority (CA) to sign the server and client certificates that will be used for secure communication.

2. **B. Create server and client certificates**: After creating the CA, you need to generate the server certificate for the Docker daemon and the client certificate for the Docker client. These certificates are necessary for mutual authentication (MTLS) between the client and server.

3. **C. Configure the daemon on the server**: You need to configure the Docker daemon to listen for secure connections by specifying the server certificates and enabling the TLS options in the daemon configuration.

4. **D. Configure the client to connect securely using the client certificate**: The Docker client needs to be configured with the client certificate so that it can securely communicate with the Docker daemon.

Thus, **all the steps** (A, B, C, D) are necessary to ensure the Docker daemon HTTP socket is secured properly.

### **Final Answer:**
**E. All of the Above**
