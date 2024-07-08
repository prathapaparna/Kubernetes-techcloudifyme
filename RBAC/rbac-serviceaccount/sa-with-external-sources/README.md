# IRSA-demo
```
aws eks describe-cluster --name eksdemo --query "cluster.identity.oidc.issuer" --output text
```
- if you run the above command it will provide oidc arn

![image](https://github.com/prathapaparna/Kubernetes-techcloudifyme/assets/99127429/4b8ed84c-b1c7-4553-9571-ab28c52b2a44)



![image](https://github.com/prathapaparna/Kubernetes-techcloudifyme/assets/99127429/40d99e5b-576c-4e12-8313-968aa390b8e0)

```
eksctl utils associate-iam-oidc-provider --region=us-east-1 --cluster=eksdemo --approve
```
- it will add oidc as identiry provider in aws

- after running command

![image](https://github.com/prathapaparna/Kubernetes-techcloudifyme/assets/99127429/fdbd8d26-b3f7-4622-b1ac-cca395021257)

- or else you can add provider manually by selecting add provider

I have created s3 bucket and upload sample file in s3 bucket

![image](https://github.com/prathapaparna/Kubernetes-techcloudifyme/assets/99127429/4e6f5c64-7874-41c1-9693-39eb5948d5b5)

## create iam policy
----------------
```
vi irsa-iam-policy.json

{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "s3:ListBucket",
                "s3:GetObject"
            ],
            "Resource": [
                "arn:aws:s3:::irsa-test-bucket19"
            ]
        }
    ]
}
```
```
aws iam create-policy --policy-name irsa-iam-policy --policy-document file://irsa-iam-policy.json
```

![image](https://github.com/prathapaparna/Kubernetes-techcloudifyme/assets/99127429/e4039841-b69d-4525-9dbd-ce597c9da92c)

- check iam-policy is created or not in aws console
- create an iam-role, service account by using below command 

  ```
  eksctl create iamserviceaccount --name irsa-sa --namespace irsa-demo --cluster eksdemo --region us-east-1 --role-name irsa-iam-role \
    --attach-policy-arn arn:aws:iam::533267082839:policy/irsa-iam-policy --approve --override-existing-serviceaccounts
  ```

  ![image](https://github.com/prathapaparna/Kubernetes-techcloudifyme/assets/99127429/781bd7f8-8f83-496b-bd4e-d83ceffb345c)
  
**NOTE:** after creating service account check sa, iam-role and trust-policy --(trust-policy is main to enable the connection from eks to s3)	




  <img width="608" alt="image" src="https://github.com/prathapaparna/Kubernetes-techcloudifyme/assets/99127429/3075c28e-5ae6-4193-bf26-dc64801db538">

  ![image](https://github.com/prathapaparna/Kubernetes-techcloudifyme/assets/99127429/33aa45c4-01cb-4cd7-92df-0d880dda9ae9)

```
kubectl apply -f pod.yaml
kubectl apply -f pod-sa.yaml
kubectl exec -it aws-cli -n irsa-demo -- /bin/bash
aws sts get-caller-identity
aws s3 ls s3://irsa-test-bucket19
```
**NOTE:** observe the pods can able to access s3 bucket or not


  ![image](https://github.com/prathapaparna/Kubernetes-techcloudifyme/assets/99127429/3a980444-f596-48c3-b53b-50af4b135135)

  ![image](https://github.com/prathapaparna/Kubernetes-techcloudifyme/assets/99127429/1c391608-3869-4a28-88a7-b8d05217bef1)

  ![image](https://github.com/prathapaparna/Kubernetes-techcloudifyme/assets/99127429/89624bef-c2ba-41e7-9c56-3c0ee178a1fc)







