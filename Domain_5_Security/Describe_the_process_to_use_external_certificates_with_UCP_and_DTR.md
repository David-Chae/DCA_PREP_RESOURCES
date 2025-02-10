# Using External Certificates with UCP and DTR

## Introduction
Docker Universal Control Plane (UCP) and Docker Trusted Registry (DTR) support the use of external TLS certificates for enhanced security. This ensures secure communication between users, nodes, and components.

## 1. Why Use External Certificates?
- Improve security with certificates from a **trusted Certificate Authority (CA)**.
- Ensure compliance with **enterprise security policies**.
- Avoid browser warnings when accessing UCP and DTR web interfaces.
- Facilitate **secure CLI access** for users and automation tools.

## 2. Steps to Use External Certificates

### a. Obtain the Required Certificates
For both UCP and DTR, you need:
- **TLS Certificate** (`cert.pem`) issued by a CA.
- **Private Key** (`key.pem`) corresponding to the certificate.
- **CA Bundle** (`ca.pem`) containing the full chain of trust.

### b. Applying Certificates to UCP
1. **Upload Certificates During Installation**
   ```sh
   docker container run --rm -it \
     -v /var/run/docker.sock:/var/run/docker.sock \
     docker/ucp install \
     --san <UCP_FQDN> \
     --external-ca-cert ca.pem \
     --external-ca-key key.pem \
     --external-ca-chain cert.pem
   ```
2. **Replace Certificates on an Existing UCP Cluster**
   ```sh
   docker cp cert.pem <ucp_container>:/certs/
   docker cp key.pem <ucp_container>:/certs/
   docker cp ca.pem <ucp_container>:/certs/
   docker restart <ucp_container>
   ```

### c. Applying Certificates to DTR
1. **Replace Default Certificates**
   ```sh
   docker run --rm docker/dtr reconfigure \
     --dtr-external-ca-cert ca.pem \
     --dtr-external-ca-key key.pem \
     --dtr-external-ca-chain cert.pem
   ```
2. **Restart DTR Components**
   ```sh
   docker ps | grep dtr | awk '{print $1}' | xargs docker restart
   ```

## 3. Verifying the Configuration
After applying the certificates:
- Ensure the web UI of **UCP and DTR load without SSL warnings**.
- Check with OpenSSL:
  ```sh
  openssl s_client -connect <UCP_FQDN>:443 -CAfile ca.pem
  ```
- Validate **CLI interactions**:
  ```sh
  docker login <DTR_FQDN>
  ```

## 4. Official Documentation
- [UCP TLS Certificates](https://docs.docker.com/ee/ucp/admin/configure/use-your-own-tls-certificates/)
- [DTR TLS Certificates](https://docs.docker.com/ee/dtr/admin/configure/use-your-own-tls-certificates/)

## Conclusion
Using external certificates enhances security and ensures compliance with enterprise policies. By following these steps, you can seamlessly configure UCP and DTR to use trusted TLS certificates.
