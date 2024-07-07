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

  ![image](https://github.com/prathapaparna/Kubernetes-techcloudifyme/assets/99127429/554d79b3-85fc-44bd-bf72-1e3ed2c5df11)
  

  - https://spacelift.io/blog/kubernetes-network-policy
  - https://docs.tigera.io/calico/latest/getting-started/kubernetes/managed-public-cloud/eks

  ![image](https://github.com/prathapaparna/Kubernetes-techcloudifyme/assets/99127429/93c54069-9af8-48a3-8d9d-2d999c291795)

