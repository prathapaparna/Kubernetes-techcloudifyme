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
