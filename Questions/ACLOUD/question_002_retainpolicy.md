## QUESTION 2. A Kubernetes Pod is using a PersistentVolumeClaim for storage. The Pod is deleted, along with the PersistentVolumeClaim. Which of the following configurations would allow the PersistentVolume to be re-used without manual intervention?
```
1. A Delete reclaimPolicy on the PeristentVolume.
2. A Recycle reclaimPolicy on the PersistentVolume.
3. A Retain reclaimPolicy on the PeristentVolume.
4. A Recycle reclaimPolicy on the PersistentVolumeClaim.
```

The correct answer is:

> **B. A Recycle reclaimPolicy on the PersistentVolume.**

---

### ✅ Explanation:

In Kubernetes, the **`reclaimPolicy`** of a `PersistentVolume` (PV) determines what happens to the actual underlying storage when its associated `PersistentVolumeClaim` (PVC) is deleted.

There are three main reclaim policies:

1. **Retain** – The PV is not deleted or reused. Manual intervention is required to reuse or clean up the volume.
2. **Delete** – The PV and the associated storage are **deleted** when the PVC is deleted. Useful for dynamic provisioning.
3. **Recycle** – The PV is scrubbed (basic cleanup like deleting files) and **made available again** for a new PVC.

---

### Why the correct answer is **B**:
If you want the **PersistentVolume to be re-used without manual intervention**, **`Recycle`** will automatically clean the volume and make it available again for other claims — **no manual cleanup or intervention needed**.

> Note: **Recycle is deprecated** in newer versions of Kubernetes in favor of dynamic provisioning. But based on the wording of the question and the options, **Recycle** is the most appropriate choice here.

---

### ⚠️ Why the others are incorrect:

- **A. Delete reclaimPolicy on the PersistentVolume**  
   → Deletes the entire PV and storage. The volume cannot be reused; it’s gone.

- **C. Retain reclaimPolicy on the PersistentVolume**  
   → Keeps the data, but **requires manual cleanup and re-binding**, so not automatic reuse.

- **D. Recycle reclaimPolicy on the PersistentVolumeClaim**  
   → Invalid: reclaimPolicy is **not a property of PVCs**, only PVs.

---

Let me know if you'd like to explore dynamic provisioning or storage classes in this context!


[OFFICIAL KUBERNETES DOC on RECLAIM POLICY](https://kubernetes.io/docs/concepts/storage/persistent-volumes/#reclaiming)
Reclaiming
When a user is done with their volume, they can delete the PVC objects from the API that allows reclamation of the resource. The reclaim policy for a PersistentVolume tells the cluster what to do with the volume after it has been released of its claim. Currently, volumes can either be Retained, Recycled, or Deleted.

Retain
The Retain reclaim policy allows for manual reclamation of the resource. When the PersistentVolumeClaim is deleted, the PersistentVolume still exists and the volume is considered "released". But it is not yet available for another claim because the previous claimant's data remains on the volume. An administrator can manually reclaim the volume with the following steps.

Delete the PersistentVolume. The associated storage asset in external infrastructure still exists after the PV is deleted.
Manually clean up the data on the associated storage asset accordingly.
Manually delete the associated storage asset.
If you want to reuse the same storage asset, create a new PersistentVolume with the same storage asset definition.

Delete
For volume plugins that support the Delete reclaim policy, deletion removes both the PersistentVolume object from Kubernetes, as well as the associated storage asset in the external infrastructure. Volumes that were dynamically provisioned inherit the reclaim policy of their StorageClass, which defaults to Delete. The administrator should configure the StorageClass according to users' expectations; otherwise, the PV must be edited or patched after it is created. See Change the Reclaim Policy of a PersistentVolume.

Recycle
Warning:
The Recycle reclaim policy is deprecated. Instead, the recommended approach is to use dynamic provisioning.
If supported by the underlying volume plugin, the Recycle reclaim policy performs a basic scrub (rm -rf /thevolume/*) on the volume and makes it available again for a new claim.

However, an administrator can configure a custom recycler Pod template using the Kubernetes controller manager command line arguments as described in the reference. The custom recycler Pod template must contain a volumes specification, as shown in the example below:


[HOW TO CHANGE RECLAIM POLICY](https://kubernetes.io/docs/tasks/administer-cluster/change-pv-reclaim-policy/)
```bash
kubectl patch pv <your-pv-name> -p "{\"spec\":{\"persistentVolumeReclaimPolicy\":\"Retain\"}}"
```
