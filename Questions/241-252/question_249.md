## 249. How to create a service with a volume driver?
A. To create a service with a volume driver, you can use the docker service create command with the --mount flag, specifying the volume type, source, target, volume driver, and driver-specific options.  
For example: docker service create -d --name nfs-service --mount 'type=volume,source=nfsvolume,target=/app,volume-driver-local,volume-opt=type=nfs,volume-opt=device=:/var/docker-nfs,volume-opt=o=addr=10.0.0.10' nginx:latest.  
B. Services cannot be created with volume drivers; they are limited to using named volumes.  
C. To create a service with a volume driver, you should use the docker service create command and specify the driver and driver-specific options without using the --mount flag  
D. Volume drivers are automatically applied when creating a service; there's no need to specify them in the docker service create command.  

The correct answer is:

**A. To create a service with a volume driver, you can use the docker service create command with the --mount flag, specifying the volume type, source, target, volume driver, and driver-specific options. For example: docker service create -d --name nfs-service --mount 'type=volume,source=nfsvolume,target=/app,volume-driver-local,volume-opt=type=nfs,volume-opt=device=:/var/docker-nfs,volume-opt=o=addr=10.0.0.10' nginx:latest.**

### Explanation:
- **A** is correct because when creating a service with a volume driver in Docker, you use the `--mount` flag and specify the volume type (`volume`), the source (`nfsvolume`), the target path, and then define the volume driver with its options (`volume-driver`, `volume-opt`). This is the correct syntax for using volume drivers in services.

- **B** is incorrect because services can be created with volume drivers, and they are not limited to named volumes. You can specify custom drivers when creating a service.

- **C** is incorrect because the `docker service create` command must use the `--mount` flag to specify the volume driver and options. Without it, you cannot attach a volume with a custom driver.

- **D** is incorrect because you must explicitly specify the volume driver when creating a service. Docker does not automatically apply volume drivers unless specified in the command.

Thus, **A** is the correct choice.
