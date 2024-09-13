I tained one node with noExcute, the existing pods evicted from there(because its not tolerate)

![image](https://github.com/user-attachments/assets/88f00624-c16e-4011-b30f-8b2883f011d5)

![image](https://github.com/user-attachments/assets/5a1b9d00-b651-48c5-adba-2ba813b6cc87)

I created pods with toleration as same key value pair

the pods might created or not created in same node

![image](https://github.com/user-attachments/assets/d6e410aa-ab42-4f65-b0cf-c62a579f214d)

# Along with taints try to use nodeselector:
```
kubectl label node ip-192-168-31-173.ec2.internal app=ngnix
```




