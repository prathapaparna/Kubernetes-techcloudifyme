# Deploy nginx application and access using nodePort 
## Nodeport Range is 30000-32767

```
kubectl apply -f deployment.yaml
kubectl apply -f service-np.yaml
```
**Note:** add node port in node security group and access application using **external-ip**

![image](https://github.com/user-attachments/assets/c087b745-b104-4efb-a0d4-cda375a83dd6)

# Deploy the application and access using LoadBalancer
```
kubectl apply -f deployment.yaml
kubectl apply -f service-lb.yaml
```
**Note:** check heathstatus of loadbalancer in aws and wait until services come **in-serice** mode and access the application

![image](https://github.com/user-attachments/assets/e2de949b-c98d-4f77-b373-7f317bea09e9)

# Deploy an application and access using CIP inside cluster only
```
kubectl apply -f deployment.yaml
kubectl apply -f service-cip.yaml
```
**note:** we can access application inside cluster only(not from external sources like ec2, google browser or another apis)
- create a busybox pod to and access application using cluster-ip
```
kubectl run testpod --image=busybox --restart=Never --rm -it -- /bin/sh

# Test using ClusterIP:
curl http://10.100.180.91

# Test using DNS:
curl http://nginx-service-cip.default.svc.cluster.local
## if curl not working use wget
wget -qO- http://10.100.180.91
```

![image](https://github.com/user-attachments/assets/f2485a0c-519f-4970-b21c-ea6f5c6d229a)

```

![image](https://github.com/user-attachments/assets/a567336f-48a4-494c-a160-2f9a4d724a57)

```
# Test using ClusterIP:
curl http://10.100.180.91

# Test using DNS:
curl http://nginx-service-cip.default.svc.cluster.local

```


**Note:**
This didn’t work because ClusterIP services are not exposed outside of the Kubernetes cluster, meaning they cannot be resolved from outside the cluster or on your local machine. You can only access the service from inside the Kubernetes cluster.




  


