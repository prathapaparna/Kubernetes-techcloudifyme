# taint and tolerence
## taint
- in Kubernetes, taints and tolerations work together to ensure that which pods are allowed to run on which nodes
- A taint is applied to a node
- Taints prevent pods from being scheduled on nodes unless the pod has a matching toleration.
**Taint Structure:**
  
### A taint consists of three parts:

- **Key:** A string that represents the taint.
- **Value:** An optional value for the taint.
- **Effect:** Defines what happens to pods that don’t tolerate the taint. It can be one of the following:
     - **NoSchedule:** Pods that don’t tolerate the taint will not be scheduled on this node.
     - **PreferNoSchedule:** Kubernetes will try to avoid placing pods that don’t tolerate the taint on this node, but it's 
                               not guaranteed.
     - **NoExecute:** Existing pods that don’t tolerate the taint will be evicted from the node, and new pods that don’t 
                        tolerate the taint will not be scheduled.
       
- I tained one node with noExcute, the existing pods evicted from there(because its not tolerate)
```
kubectl taint nodes <node-name> key=value:NoExecute #replace node name and key value 
```

![image](https://github.com/user-attachments/assets/88f00624-c16e-4011-b30f-8b2883f011d5)

**observation:**
 we tained 173 node with noExcute, so pod3 evicted from there and created in another node
 
## toleration
- A toleration is applied to a pod to indicate that it can tolerate a node's taint, allowing it to be scheduled on that node despite the taint.

### Toleration Structure:

**Key:** The key of the taint.

**Operator:** Defines the relationship between the toleration and the taint. Can be Equal (default) or Exists (matches any 
        taint with that key, ignoring the value).
        
**Value:** The value of the taint (optional, used if the operator is Equal).

**Effect:** The same as the taint effect (NoSchedule, PreferNoSchedule, or NoExecute).

**TolerationSeconds:** For NoExecute taints, defines how long the pod can tolerate the taint before being evicted. 

### add toleration to pods

![image](https://github.com/user-attachments/assets/134256b4-04a1-49ed-a6eb-e74067326ca6)


### I created pods with toleration as same key value pair

![image](https://github.com/user-attachments/assets/d6e410aa-ab42-4f65-b0cf-c62a579f214d)

**observation** the pods might created or not created in same node

# Along with taints try to use nodeselector:
```
kubectl label node ip-192-168-31-173.ec2.internal app=ngnix
```
![image](https://github.com/user-attachments/assets/bbca058b-26a3-4607-b594-cc26fa597f33)

![image](https://github.com/user-attachments/assets/a8eda397-d6e6-49b5-8649-430e7a734485)
![image](https://github.com/user-attachments/assets/b1cef384-8ce0-49b5-906d-9d1c58fb5551)

**Observation** all pods are created on this node only





