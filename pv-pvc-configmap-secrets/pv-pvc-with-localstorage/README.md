![image](https://github.com/user-attachments/assets/66c8db5f-ba06-4839-8288-4606f53dcff9)# pv-pvc-with-localstorage
## create storage class, pv and pvc
```
kubectl apply -f local-sc.yaml
kubectl apply -f pv.yaml
kubectl apply -f pvc.yaml
```

![image](https://github.com/user-attachments/assets/febe8f75-16b9-4b96-9cda-830c70338781)

**observation:** pvc is in pending state and no value at pv claim

## deploy an application and use pv and pvc
```
kubectl apply -f deployment.yaml
```
![image](https://github.com/user-attachments/assets/0249d9f6-8838-4320-8f51-f41f9aa4ee70)

**Observation:** pvc is bound and pv is claimed

**Note:** 
- Goto mysql pod and create table and employee info in that table
- delete and recreate the pod and observe previous employee info is exist or not
- if it exist you correctly configured pv and pvc



## create a table in mysql
```
  kubectl exec -it <pod-name>  /bin/bash  # enter to pod
  mysql -u root -p                       # enter mysql
  show databases;
  use mysql;                             # use my sql db
# create table <table-name>(values)
 create table employee(eno varchar(40), ename varchar(40));
 select * from employee;
# enter employee info in that table
 insert into employee(eno, ename) values(101, "appu");
# this employee information is available in /var/lib/mysql folder of inside container
```
## pv.yaml
```
apiVersion: v1
kind: PersistentVolume
metadata:
  name: mysql-pv
  labels:
    type: local
spec:
  storageClassName: local-storage
  capacity:
    storage: 250Mi
  accessModes:
    - ReadWriteOnce
  hostPath:
    path: "/mnt/data"
  persistentVolumeReclaimPolicy: Retain
```
The **persistentVolumeReclaimPolicy** in a Kubernetes PersistentVolume (PV) defines what happens to the PV after the PersistentVolumeClaim (PVC) that was using it is deleted. Essentially, it controls the behavior of the volume when it is no longer bound to a claim.

- **Retain:** Retain means the PV will remain exist after its associated PVC is deleted. The data will not be lost, and you will need to manually manage the volume if you want to reuse or delete it.
- **Recycle:** (Less common) Use when you need to clean the PV and make it available for reuse without keeping the data. Useful in basic scenarios where the PV can be used multiple times for different PVCs after being cleaned.(only for static pv not for dynamic)
- **Delete:** Used with dynamically provisioned storage where you don’t need to keep the data after the claim is deleted. Suitable for environments where the underlying storage can be easily deleted and recreated.
