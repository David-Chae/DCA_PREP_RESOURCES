## 149. which of the following improves content security?
A. Docker Client Customization  
B. Docker Deamon Security  
C. Linux Security Modules  
D. Docker Content Trust  

The correct answer is:

**D. Docker Content Trust**

Docker Content Trust (DCT) helps improve content security by ensuring that only signed images are pulled and run. This feature verifies the authenticity and integrity of the images, ensuring that they have not been tampered with, and allowing users to trust the content they are using.

Here's a breakdown of the options:
- **Docker Client Customization**: Refers to configuring the Docker client but does not specifically relate to security.
- **Docker Daemon Security**: While important, this focuses on securing the Docker daemon, not content specifically.
- **Linux Security Modules**: Provide security features at the OS level but do not directly focus on the content security of Docker images.

Therefore, **Docker Content Trust** is the correct choice to improve content security.

REF: https://docs.docker.com/engine/security/trust/
