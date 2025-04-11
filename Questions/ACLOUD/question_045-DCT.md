## Which of the following statements about Docker Content Trust (DCT) is accurate?
```
1. Only images stored on Docker Hub can be signed.
2. When Docker Content Trust is enabled, unsigned images will not be allowed to run on the system.
3. Docker Content Trust requires a Docker Enterprise Edition (EE) license.
4. We need to implement a trusted Public Key Infrastructure (PKI) to sign images.
```

The correct answer is:

> ✅ **When Docker Content Trust is enabled, unsigned images will not be allowed to run on the system.**

---

### ✅ Explanation:

**Docker Content Trust (DCT)** ensures the **integrity and publisher** of Docker images by enabling **image signing and verification**. When DCT is enabled (by setting the environment variable `DOCKER_CONTENT_TRUST=1`), **Docker will only allow operations with signed images**.

---

### ❌ Why the other options are incorrect:

- **"Only images stored on Docker Hub can be signed"**  
  ❌ Incorrect. DCT supports other registries as long as they support Notary (which is used by DCT).

- **"Docker Content Trust requires a Docker Enterprise Edition (EE) license"**  
  ❌ False. DCT is available in the **open-source Docker Engine**.

- **"We need to implement a trusted Public Key Infrastructure (PKI) to sign images"**  
  ❌ Not required. Docker uses **Notary**, which manages keys and signatures without requiring a full PKI setup.

---

Let me know if you want to see how to sign and verify images using DCT in practice!
