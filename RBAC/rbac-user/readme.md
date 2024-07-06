# rbac-demo
**Assumption** : EKS cluster is ready 

# Steps:

1.	Deploy ngnix application
2.	Create rbac-user dev and devops
3.	MAP user to K8S
4.	Test new users
5.	Create role and binding
6.	Verify role and binding

# 1.Install ngnix application.

**# kubectl apply -f deployment.yaml** 
![image](https://github.com/prathapaparna/Kubernetes-techcloudifyme/assets/99127429/0bdb905f-05dc-472a-8993-00cebba76066)

# 2. Create rbac-user dev and devops
- create dev user and devops user in aws and get access key and secrets access key and update in the sh files
- 

