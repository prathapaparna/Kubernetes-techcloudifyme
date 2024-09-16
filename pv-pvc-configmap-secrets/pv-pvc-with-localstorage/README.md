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
