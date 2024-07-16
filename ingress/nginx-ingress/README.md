# nginx-ingress
### install nginx ingress controller 
```
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/main/deploy/static/provider/cloud/deploy.yaml
```

![image](https://github.com/user-attachments/assets/63bd23cb-3012-482f-a9cf-dad83dd5f4ce)

### deploy 2 applications to test ingress and deploy ingress resource
- in ingress resource file we can mention ingress rules

```
kubectl apply -f app1.yaml
kubectl apply -f app2.yaml
kubectl apply -f ingress-resource.yaml
```
- ingress controller provide one load balancer url by using that url we can access our applications
  
 ![image](https://github.com/user-attachments/assets/6698c58f-9f02-424a-949a-da9dd8889108)
 

  ![image](https://github.com/user-attachments/assets/e8b2ae81-3064-4418-bddd-d7c2c5612e42)

  ![image](https://github.com/user-attachments/assets/ff9ae001-b9f2-4ba3-bce4-8abcb1d26d40)

    
