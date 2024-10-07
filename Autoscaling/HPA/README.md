
![image](https://github.com/user-attachments/assets/acd62d95-d603-44d3-a349-a3f550c5c814)

before installing metric server
![image](https://github.com/user-attachments/assets/4ec833f9-b5fc-4dfc-9405-1283d65fbf4c)

- The command `kubectl top pods -n kube-system ` is used to display resource usage metrics (CPU and memory) for all pods running in the kube-system namespace in a Kubernetes cluster.
- ![image](https://github.com/user-attachments/assets/a6533f0d-5680-43dd-aacb-dea38a21f59b)

### install metric server
- The Metrics Server is used in Kubernetes to collect and provide resource usage metrics such as CPU and memory utilization for nodes and pods.

```
  kubectl apply -f https://github.com/kubernetes-sigs/metrics-server/releases/latest/download/components.yaml
```

![image](https://github.com/user-attachments/assets/aae8064c-e26d-42d8-88ee-51bdd19f5d15)

![image](https://github.com/user-attachments/assets/01a176ad-28ee-436c-9a5a-cf40ca63e754)

### deploy hpa
```
apiVersion: autoscaling/v1
kind: HorizontalPodAutoscaler
metadata:
 name: hpa-demo-deployment
spec:
 scaleTargetRef:
   apiVersion: apps/v1
   kind: Deployment
   name: nginx-deployment
 minReplicas: 1
 maxReplicas: 10
 targetCPUUtilizationPercentage: 50
```

![image](https://github.com/user-attachments/assets/a5e5c6e0-a919-42fa-bb2c-7194d4add9ed)

![image](https://github.com/user-attachments/assets/6f61096d-ff65-451d-bb77-35a24926b56f)

![image](https://github.com/user-attachments/assets/6c512f3c-3791-4c76-a32f-9113c972565c)

before load
![image](https://github.com/user-attachments/assets/04204d4f-a898-4616-8a20-742609bb12b0)

after load
![image](https://github.com/user-attachments/assets/2b838fbd-55d6-4051-8558-8c93ab140333)

![image](https://github.com/user-attachments/assets/26592925-a9e3-4d3c-a963-15c6bfc5e747)






