## 169. Will a DTR security scan pick up private keys copied to a Docker image?
A. Yes  
B. No  

The correct answer is:

**B. No**

Explanation:
Private keys transferred to the image are not detected by a DTR security scan. A DTR security scan is a capability that searches images for known vulnerabilities in software packages or dependencies installed in the image. A DTR security scan does not look for private keys or other sensitive data that may have been copied to the image by accident or on purpose. To avoid copying private keys to the image, you should manage your credentials using Docker secrets or other safe means.
