## How can we provide custom certificates to the Universal Control Plane (UCP) and Docker Trusted Registry (DTR)?
```
1. We can push new certificates via the UCP web API.
2. docker ucp config --cert
3. We can upload certificates via the UCP and DTR web UIs.
4. We must supply the certificates during the UCP and DTR installation process.
```

The correct answer is:

**We can upload certificates via the UCP and DTR web UIs.**

### Explanation:

For **Docker Universal Control Plane (UCP)** and **Docker Trusted Registry (DTR)**, custom certificates can be provided to ensure secure communication, especially in production environments. The most common way to upload and configure these certificates is through the **web UIs** of both UCP and DTR.

#### Here's how each option works:

- **We can upload certificates via the UCP and DTR web UIs**: This is the correct method for managing and uploading custom certificates. The UCP and DTR web interfaces allow you to upload your custom certificates, ensuring that communications with these services are encrypted with your own trusted certificates. This process is straightforward and can be done via the UI.

- **We can push new certificates via the UCP web API**: While the UCP API can be used for various management tasks, uploading certificates specifically is more commonly done via the web UIs, not through the API. The API can interact with the system, but direct certificate management via the web UI is recommended.

- **`docker ucp config --cert`**: There is no such `--cert` option in the `docker ucp` command. Certificate configuration generally happens during installation or through the web UI as described above.

- **We must supply the certificates during the UCP and DTR installation process**: While you can specify custom certificates during the installation process of UCP and DTR, this is not the **only** way to provide custom certificates. After installation, you can still upload and manage certificates via the web UIs.

### Summary:
You can **upload custom certificates via the UCP and DTR web UIs** after installation, which is the most common and user-friendly approach for managing SSL/TLS certificates.
