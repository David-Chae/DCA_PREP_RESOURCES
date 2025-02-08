# Mounting Volumes in Docker and Kubernetes

## Mounting Volumes in Docker

You can mount a volume in Docker using the `-v` or `--mount` flag:

```sh
# Using the -v flag (legacy method)
docker run -d -v my_volume:/app/data my_image

# Using --mount (recommended method)
docker run -d --mount source=my_volume,target=/app/data my_image
```

More details:
- [Docker Volumes Documentation](https://docs.docker.com/storage/volumes/).
- [Give a service access to volumes or bind mounts](https://docs.docker.com/engine/swarm/services/#give-a-service-access-to-volumes-or-bind-mounts)
- [Mount volumes](https://asciinema.org/a/224916)

## Mounting Volumes in Kubernetes

In Kubernetes, you can mount a volume in a Pod by defining it in a YAML file:

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: my-pod
spec:
  containers:
  - name: my-container
    image: my_image
    volumeMounts:
    - mountPath: "/app/data"
      name: my-volume
  volumes:
  - name: my-volume
    persistentVolumeClaim:
      claimName: my-pvc
```

More details: [Kubernetes Volumes Documentation](https://kubernetes.io/docs/concepts/storage/volumes/).
