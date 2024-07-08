# Network policy
- Network Policies are a mechanism for controlling network traffic flow in Kubernetes clusters. They allow you to define which of your Pods are allowed to exchange network traffic. You should use them in your clusters to prevent apps from reaching each other over the network, which will help limit the damage if one of your apps is compromised.
- you should ensure you’re using a compatible CNI networking  plugin

- Each Network Policy you create targets a group of Pods and sets the Ingress (incoming) and Egress (outgoing) network endpoints those Pods can communicate with.

- There are three different ways to identify target endpoints:
  - **Specific Pods** (Pods matching a label are allowed)
  - **Specific Namespaces** (all Pods in the namespace are allowed)
  - **IP address blocks** (endpoints with an IP address in the block are allowed)
    
**uses:**
- Ensuring a database can only be accessed by the app it’s part of
- Isolating Pods from your cluster’s network
- Allow specific apps or namespaces to communicate with each other
## LAB:
- craete namespace
```
kubectl create namespace netpol-demo
```
- create sample frontend, backend and database service to check communication
```
kubectl run backend --image=nginx --namespace=netpol-demo
kubectl run database --image=nginx --namespace=netpol-demo
kubectl run frontend --image=nginx --namespace=netpol-demo	

kubectl get pod -n netpol-demo
```
- create services to expose them
``` 
kubectl expose pod backend --port 80 --namespace=netpol-demo
kubectl expose pod database --port 80 --namespace=netpol-demo
kubectl expose pod frontend --port 80 --namespace=netpol-demo

kubectl get svc -n netpol-demo
```

## check frontend application can connect backend and database
```
kubectl exec -it frontend --namespace=netpol-demo -- curl <BACKEND-CLUSTER-IP>
```
**NOTE**: by default all workloads can communicate eachother 

- apply default-deny netpol to restrict the communication
```
vi default-deny.yaml
--------------------
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: default-deny
  namespace: netpol-demo
spec:
  podSelector: {}
  policyTypes:
  - Ingress
  - Egress
```  
- after applying netpol check the communication between workloads

####
install calico for networkpolicy
--------------------------------
```
kubectl create -f https://raw.githubusercontent.com/projectcalico/calico/v3.28.0/manifests/tigera-operator.yaml
```

configure calico:
-----------------
```
kubectl create -f - <<EOF
kind: Installation
apiVersion: operator.tigera.io/v1
metadata:
  name: default
spec:
  kubernetesProvider: EKS
  cni:
    type: AmazonVPC
  calicoNetwork:
    bgp: Disabled
EOF
``` 

- now allow communication from frontend to backend and backend to database

# Frontend -> Backend -> Database

- frontend ---> egress to backend
- backend ----> ingress from fronend and egress to  backend
- dabase -----> ingress from backend

---------------------------------
```
vi frontend-default-policy.yaml

apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: frontend-default
  namespace: netpol-demo
spec:
  podSelector:
    matchLabels:
      run: frontend
  policyTypes:
    - Egress
  egress:
    - to:
        - podSelector:
            matchLabels:
              run: backend
```
```			  
vi 	backend-default.yaml
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: backend-default
  namespace: netpol-demo
spec:
  podSelector:
    matchLabels:
      run: backend
  policyTypes:
    - Ingress
    - Egress
  ingress:
    - from:
        - podSelector:
            matchLabels:
              run: frontend
  egress:
    - to:
        - podSelector:
            matchLabels:
              run: database	
```
```	
vi 	database-default-policy.yaml
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: database-default
  namespace: netpol-demo
spec:
  podSelector:
    matchLabels:
      run: database
  policyTypes:
    - Ingress
  ingress:
    - from:
        - podSelector:
            matchLabels:
              run: backend
```	
			  
**Note:** check communication between all workloads and observe the difference
 
  


