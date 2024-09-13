# Deploy nginx application using nodePort 
## Nodeport Range is 30000-32767

```
kubectl apply -f deployment.yaml
kubectl apply -f svc-np.yaml
```
**Note:** add node port in node security group and access application using **external-ip**
![image](https://github.com/user-attachments/assets/c087b745-b104-4efb-a0d4-cda375a83dd6)

# Deploy the application using LoadBalancer
```
kubectl apply -f deployment.yaml
kubectl apply -f svc-lb.yaml
```
**Note:** check heathstatus of loadbalancer in aws and wait until services come **in-serice** mode and access the application
![image](https://github.com/user-attachments/assets/e2de949b-c98d-4f77-b373-7f317bea09e9)


