
# Provisioning Persistent Storage to a Kubernetes Pod Using PersistentVolumes (PVs)

## Overview

In Kubernetes, Persistent Volumes (PVs) are an abstraction for managing storage resources in a cluster. They allow you to provide persistent storage that exists independently of the lifecycle of individual pods. This ensures that data is not lost when a pod is deleted or rescheduled. PVs are created by an administrator and can be dynamically or statically provisioned.

This guide covers how to provision persistent storage to a Kubernetes pod using PersistentVolumes (PVs), including the creation of PersistentVolumeClaims (PVCs) that bind to PVs for storage usage.

## Steps for Provisioning Persistent Storage with PVs

### 1. Understanding PersistentVolumes (PVs) and PersistentVolumeClaims (PVCs)

- **PersistentVolume (PV)**: A PV is a piece of storage in the Kubernetes cluster, provisioned by an administrator or dynamically based on storage class.
- **PersistentVolumeClaim (PVC)**: A PVC is a request for storage by a user, specifying size, access modes, and other attributes. It is used to bind to a PV.

### 2. Static Provisioning of Persistent Volumes

In static provisioning, the administrator manually creates a PV that corresponds to a specific storage backend (e.g., NFS, Ceph, or AWS EBS).

#### Step 1: Create a PersistentVolume (PV)

Create a YAML file that defines the PersistentVolume (PV). The following is an example that provisions a PV backed by a directory on a node:

```yaml
apiVersion: v1
kind: PersistentVolume
metadata:
  name: my-pv
spec:
  capacity:
    storage: 1Gi
  accessModes:
    - ReadWriteOnce
  persistentVolumeReclaimPolicy: Retain
  hostPath:
    path: /mnt/data
```

This PV uses a `hostPath` to store data on a specific directory (`/mnt/data`) on the node. The storage is 1Gi, and it supports the `ReadWriteOnce` access mode, meaning only one node can mount the volume at a time.

#### Step 2: Apply the PV

```bash
kubectl apply -f pv-definition.yaml
```

### 3. Create a PersistentVolumeClaim (PVC)

A PersistentVolumeClaim (PVC) allows a pod to request storage. Here’s how to create a PVC that matches the PV created earlier:

```yaml
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: my-pvc
spec:
  accessModes:
    - ReadWriteOnce
  resources:
    requests:
      storage: 1Gi
```

This PVC is requesting 1Gi of storage with the `ReadWriteOnce` access mode.

#### Step 1: Apply the PVC

```bash
kubectl apply -f pvc-definition.yaml
```

### 4. Verify the PVC and PV Binding

After creating the PVC, Kubernetes will automatically bind it to an appropriate PV if the request matches the available PV. You can verify the status of the binding:

```bash
kubectl get pvc my-pvc
```

The `STATUS` should be `Bound`, indicating that the PVC has successfully been bound to a PV.

### 5. Use the PVC in a Pod

Once the PVC is bound to a PV, you can use it in a pod. Here’s an example of a pod specification that mounts the PVC as a volume:

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: my-app
spec:
  containers:
  - name: my-app-container
    image: my-image
    volumeMounts:
    - name: my-storage
      mountPath: /data
  volumes:
  - name: my-storage
    persistentVolumeClaim:
      claimName: my-pvc
```

This pod mounts the PVC `my-pvc` into the `/data` directory inside the container.

#### Step 1: Apply the Pod

```bash
kubectl apply -f pod-definition.yaml
```

### 6. Dynamic Provisioning of Persistent Volumes

Dynamic provisioning automatically creates PVs based on PVC requests if a storage class is configured. This is ideal when you don't want to manually create PVs.

#### Step 1: Define a StorageClass

You first need to create a `StorageClass` that defines the dynamic provisioning parameters. Here is an example for AWS EBS:

```yaml
apiVersion: storage.k8s.io/v1
kind: StorageClass
metadata:
  name: ebs-sc
provisioner: kubernetes.io/aws-ebs
parameters:
  type: gp2
```

This `StorageClass` uses AWS EBS to dynamically provision persistent volumes.

#### Step 2: Create a PVC with the StorageClass

Now create a PVC that uses the `StorageClass` for dynamic provisioning:

```yaml
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: my-dynamic-pvc
spec:
  accessModes:
    - ReadWriteOnce
  resources:
    requests:
      storage: 1Gi
  storageClassName: ebs-sc
```

When you apply this PVC, Kubernetes will automatically provision a PV using the `ebs-sc` storage class.

#### Step 3: Apply the PVC

```bash
kubectl apply -f dynamic-pvc-definition.yaml
```

### 7. Cleanup

After you no longer need the persistent storage, you can delete the resources.

#### Delete the Pod

```bash
kubectl delete pod my-app
```

#### Delete the PVC

```bash
kubectl delete pvc my-pvc
```

#### Delete the PV (if manually created)

```bash
kubectl delete pv my-pv
```

For dynamically provisioned volumes, the PV and associated storage resource will be automatically cleaned up when the PVC is deleted.

## Official Documentation

For more in-depth information, refer to the following official Kubernetes documentation:

- [Persistent Volumes](https://kubernetes.io/docs/concepts/storage/persistent-volumes/)
- [PersistentVolumeClaims](https://kubernetes.io/docs/concepts/storage/persistent-volumes/#persistentvolumeclaims)
- [Storage Classes](https://kubernetes.io/docs/concepts/storage/storage-classes/)
- [Dynamic Provisioning](https://kubernetes.io/docs/concepts/storage/persistent-volumes/#dynamic-provisioning)

## Conclusion

By using PersistentVolumes (PVs) and PersistentVolumeClaims (PVCs), Kubernetes provides a robust mechanism for managing persistent storage. Whether using static or dynamic provisioning, these resources allow you to attach storage to pods in a consistent, reliable way, ensuring that your applications have access to the data they need even as pods are rescheduled or restarted. 
Good luck with your DCA exam preparation!
