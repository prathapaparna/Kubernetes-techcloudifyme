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
      #groups:
       # - system:masters
    - userarn: arn:aws:iam::533267082839:user/devops
      username: devops
      #groups:
       # - system:masters
## system
Group: If the user is mapped to the system:masters group in the aws-auth ConfigMap, they will have full admin access to the cluster.
```
# 4. Test new users
**test new user they have get pod permissions or not**
```
kubectl auth can-i get pods --as arn:aws:iam::533267082839:user/dev
kubectl auth can-i get pods --as arn:aws:iam::533267082839:user/devops
```
**switch the user and and check** 
```
. dev-user-creds.sh
aws sts get-caller-identity
kubectl get pods
```
- if you observe the user can't get the pods, we are getting error, as we have not assigned any role with the user. Lets create role and role-binding
![image](https://github.com/prathapaparna/Kubernetes-techcloudifyme/assets/99127429/447c8788-a40e-4d43-90de-38eeb7a36930)

**unset the user and create roles and rolebinding**
```
# unset AWS_SECRET_ACCESS_KEY 
# unset AWS_ACCESS_KEY_ID
```




