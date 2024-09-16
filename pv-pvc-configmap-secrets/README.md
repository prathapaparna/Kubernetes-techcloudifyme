## types of volumes
  - statically provisioned volume
  - dynamically provisioned volume

 static pv:
 ---------
 Provisioning: In static provisioning, the administrator manually creates PV objects before they are claimed by PersistentVolumeClaims (PVCs).
 The administrator must pre-allocate and configure the storage resources, 
 including specifying the capacity, access modes, and other details.
 
 dynamic pv:
 -----------
 Provisioning: In dynamic provisioning, PVs are created automatically by a StorageClass when a PVC is created.
 The administrator defines a StorageClass with specific provisioning parameters, 
 and when a PVC requests storage using that StorageClass, a PV is dynamically created to fulfill the request.

 storage class:
 -------------
 A Kubernetes StorageClass is a Kubernetes storage mechanism that lets you
 dynamically provision persistent volumes (PV) in a Kubernetes cluster. 
 Kubernetes administrators define classes of storage, 
and then pods can dynamically request the specific type of storage they need
```
apiVersion: storage.k8s.io/v1
kind: StorageClass
metadata:
  name: local-storage
provisioner: kubernetes.io/no-provisioner
volumeBindingMode: WaitForFirstConsumer
```
**volumeBindingMode:**

- **Immediate:** Volume binding happens as soon as the PVC is created, regardless of pod scheduling. 
  
- **WaitForFirstConsumer:** Volume binding is delayed until the pod is scheduled.
