# Default Engine Security in Docker

## Introduction
Docker Engine has built-in security features that help protect containers, images, and the host system. Understanding these default security mechanisms is crucial for the Docker Certified Associate (DCA) exam.

## 1. Namespace Isolation
Docker uses Linux namespaces to isolate processes, ensuring that containers do not interfere with each other or the host system.
- Process IDs (PID) are isolated.
- Network and mount namespaces provide separate environments for containers.
- [Official Documentation](https://docs.docker.com/engine/security/security/)

## 2. Control Groups (cgroups)
Docker leverages cgroups to limit resource usage per container.
- CPU, memory, and I/O bandwidth can be restricted.
- Prevents a single container from consuming all system resources.
- [Official Documentation](https://docs.docker.com/config/containers/resource_constraints/)

## 3. Seccomp Security Profiles
Seccomp (Secure Computing Mode) restricts the system calls available to a container.
- By default, Docker applies a Seccomp profile to mitigate risks.
- Blocks over 40 syscalls that could be exploited.
- [Official Documentation](https://docs.docker.com/engine/security/seccomp/)

## 4. AppArmor and SELinux
Docker supports Mandatory Access Control (MAC) policies:
- **AppArmor** (on Ubuntu/Debian) restricts what actions a container can perform.
- **SELinux** (on RHEL/Fedora) enforces security policies.
- [Official Documentation](https://docs.docker.com/engine/security/apparmor/)

## 5. Read-Only Root Filesystem
By default, Docker containers have a writable layer, but it is recommended to run them with a read-only filesystem:
- Prevents accidental modifications to the base image.
- Enhances security by restricting write access.
- [Official Documentation](https://docs.docker.com/develop/develop-images/dockerfile_best-practices/)

## 6. Kernel Capabilities
Docker containers run with a restricted set of Linux capabilities:
- Limits what a containerized process can do.
- Allows dropping capabilities that are not required.
- [Official Documentation](https://docs.docker.com/engine/security/capabilities/)

## 7. User Namespaces
Docker can map container users to non-root users on the host:
- Helps avoid privilege escalation risks.
- Prevents root inside the container from having host-level root access.
- [Official Documentation](https://docs.docker.com/engine/security/userns-remap/)

## 8. Image Signing and Verification
Docker supports Content Trust (DCT) to ensure only signed images are pulled and run.
- Protects against tampered or untrusted images.
- Uses cryptographic signing for integrity verification.
- [Official Documentation](https://docs.docker.com/engine/security/trust/)

## 9. Logging and Auditing
Docker provides logging mechanisms to monitor container activity:
- Multiple logging drivers (`json-file`, `syslog`, `fluentd`, etc.).
- Helps with security auditing and compliance.
- [Official Documentation](https://docs.docker.com/config/containers/logging/)

## Conclusion
Docker Engine incorporates several default security features to ensure safe containerized environments. It is essential to understand these mechanisms and apply best practices for enhanced security.
