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
# 3.	MAP user to K8S

**Add the user details to aws-auth.yaml and apply it to k8s cluster, so that we can map users to k8s.**

**kubectl edit configmap -n kube-system aws-auth -o yaml** 

```
cat aws-auth.yaml 
apiVersion: v1
kind: ConfigMap
metadata:
  name: aws-auth
  namespace: kube-system
data:
  mapRoles: |
    - groups:
      - system:bootstrappers
      - system:nodes
      rolearn: arn:aws:iam::533267082839:role/eksctl-eksdemo-nodegroup-eksdemo-n-NodeInstanceRole-lDzqWls5c3dG
      username: system:node:{{EC2PrivateDNSName}}
  mapUsers: |
    - userarn: arn:aws:iam::533267082839:user/dev
      username: dev
      groups:
        - system:masters
    - userarn: arn:aws:iam::533267082839:user/devops
      username: devops
      groups:
        - system:masters
```
# 4. Test new users
**test new user they have get pod permissions or not**
```
kubectl auth can-i get pods --as arn:aws:iam::533267082839:user/dev
kubectl auth can-i get pods --as arn:aws:iam::533267082839:user/devops
```



