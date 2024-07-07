## rbac-with-serviceaccount-demo for access kube api
### create 2 namespaces for sao and cao
```
kubectl create ns cao
kubectl create ns sao
```

![image](https://github.com/prathapaparna/Kubernetes-techcloudifyme/assets/99127429/10fd1c6f-b974-46e7-8f53-2b3da06fb8d4)
### create sa,role,rolebinding, and create a pod by attching sa
```
kubectl apply -f cao-sa.yaml
kubectl apply -f cao-role.yaml
kubectl apply -f cao-rolebinding.yaml
kubectl apply -f cao-kubectl-pod.yaml
```

![image](https://github.com/prathapaparna/Kubernetes-techcloudifyme/assets/99127429/dc8f3cc2-1dd1-463e-bf35-b291ecded7e2)

![image](https://github.com/prathapaparna/Kubernetes-techcloudifyme/assets/99127429/52f00472-d553-4f19-83ed-efc572d18490)

![image](https://github.com/prathapaparna/Kubernetes-techcloudifyme/assets/99127429/18ada300-0776-40d8-80b8-4c8ba9896e2d)

![image](https://github.com/prathapaparna/Kubernetes-techcloudifyme/assets/99127429/783b2acb-e47d-47fb-b38b-73a0c0955a5e)
### login to pod and check to able get pods are not
```
kubectl exec -it <pod-name> -- /bin/bash
kubectl get pods
```

![image](https://github.com/prathapaparna/Kubernetes-techcloudifyme/assets/99127429/32104eda-4dce-416a-b98e-170e7c5cbb36)

![image](https://github.com/prathapaparna/Kubernetes-techcloudifyme/assets/99127429/34852cb3-48e6-4a84-b74f-a55f90b5eaaa)

- here I have given permission only for get and list pods not for deployment

  ![image](https://github.com/prathapaparna/Kubernetes-techcloudifyme/assets/99127429/8c348f74-d086-4a2f-9143-a561f2dd00bb)

  ![image](https://github.com/prathapaparna/Kubernetes-techcloudifyme/assets/99127429/8257fcd6-9726-41ab-86a9-fd8bcb91279b)

- here sao service account don't have roles that's why its not able to get pods

  --------------------------------

  ## rbac-with-serviceaccount-demo for access external services (ex: s3 bucket)

![image](https://github.com/prathapaparna/Kubernetes-techcloudifyme/assets/99127429/e82f0b54-0bf2-4b12-8063-c6d779311500)

![image](https://github.com/prathapaparna/Kubernetes-techcloudifyme/assets/99127429/fcd20473-edce-4d08-bcd2-80c2bebb363b)

![image](https://github.com/prathapaparna/Kubernetes-techcloudifyme/assets/99127429/d854f420-3d27-4513-bd13-ac939679bda9)

![image](https://github.com/prathapaparna/Kubernetes-techcloudifyme/assets/99127429/5616d515-c57e-41d2-8cb7-bba1eb07fe8e)











