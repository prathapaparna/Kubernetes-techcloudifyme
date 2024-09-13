# taint and tolerence
## taint
- in Kubernetes, taints and tolerations work together to ensure that which pods are allowed to run on which nodes
- A taint is applied to a node
- Taints prevent pods from being scheduled on nodes unless the pod has a matching toleration.
**Taint Structure:**
  
- A taint consists of three parts:

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
kubectl taint nodes <node-name> key=value:NoExecute #replace node name 
```

![image](https://github.com/user-attachments/assets/88f00624-c16e-4011-b30f-8b2883f011d5)

![image](https://github.com/user-attachments/assets/5a1b9d00-b651-48c5-adba-2ba813b6cc87)

I created pods with toleration as same key value pair

the pods might created or not created in same node

![image](https://github.com/user-attachments/assets/d6e410aa-ab42-4f65-b0cf-c62a579f214d)

# Along with taints try to use nodeselector:
```
kubectl label node ip-192-168-31-173.ec2.internal app=ngnix
```




