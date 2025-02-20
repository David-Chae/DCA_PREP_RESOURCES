# Verifying That a Docker Image Passes a Security Scan

## Introduction
Security scanning in Docker ensures that container images do not contain vulnerabilities before deployment. Docker provides built-in tools and integrations, such as **Docker Trusted Registry (DTR) security scanning**, to assess and verify images.

## 1. Why Perform a Security Scan?
- Detect **known vulnerabilities** in system libraries and dependencies.
- Maintain **compliance** with security policies.
- Reduce the risk of deploying **compromised images**.
- Improve overall **container security posture**.

## 2. Running a Security Scan on an Image
Docker provides **Docker Scout** (previously Docker Security Scanning) for scanning public and private images. 

### a. Prerequisites
Ensure you have:
- **Docker Desktop** installed (with Docker Scout enabled) or access to **Docker Trusted Registry (DTR)**.
- A local or remote Docker image to scan.

### b. Running a Security Scan Using Docker Scout
1. **Enable Docker Scout:**
   ```sh
   docker scout quickview <image_name>
   ```
2. **Run a detailed security scan:**
   ```sh
   docker scout cves <image_name>
   ```
3. **Example Output:**
   ```sh
   NAME           SEVERITY   PACKAGE         CVE
   libc-bin       High       libc6 2.31      CVE-2021-33574
   openssl       Critical    1.1.1g          CVE-2021-3450
   ```
4. **Ensure No Vulnerabilities Exist**
   - If vulnerabilities exist, update the base image and dependencies.
   - Re-run the scan until no high or critical vulnerabilities are found.

### c. Running a Security Scan on Docker Trusted Registry (DTR)
If using **DTR security scanning**:
1. **Enable Security Scanning** in DTR settings.
2. **Push an Image to DTR:**
   ```sh
   docker push <dtr_url>/<repository>:latest
   ```
3. **Trigger Scan in DTR UI or CLI**:
   ```sh
   curl -X POST -H "Authorization: Bearer <token>" \
     "https://<dtr_url>/api/v0/repositories/<repository>/tags/latest/scan"
   ```
4. **Check Scan Results**:
   ```sh
   curl -H "Authorization: Bearer <token>" \
     "https://<dtr_url>/api/v0/repositories/<repository>/tags/latest/scan-results"
   ```

## 3. Official Documentation
- [Docker Scout Documentation](https://docs.docker.com/scout/)
- [DTR Security Scanning](https://docs.mirantis.com/containers/v2.1/dockeree-products/dtr/dtr-user/manage-images/scan-images-for-vulnerabilities.html)

## Conclusion
Regularly scanning Docker images helps maintain a secure software supply chain. Using **Docker Scout** or **DTR Security Scanning**, you can verify that an image passes security checks before deployment.
