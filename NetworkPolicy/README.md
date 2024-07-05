# Network policy
- Network Policies are a mechanism for controlling network traffic flow in Kubernetes clusters. They allow you to define which of your Pods are allowed to exchange network traffic. You should use them in your clusters to prevent apps from reaching each other over the network, which will help limit the damage if one of your apps is compromised.

- Each Network Policy you create targets a group of Pods and sets the Ingress (incoming) and Egress (outgoing) network endpoints those Pods can communicate with.

- There are three different ways to identify target endpoints:

- Specific Pods (Pods matching a label are allowed)
- Specific Namespaces (all Pods in the namespace are allowed)
- IP address blocks (endpoints with an IP address in the block are allowed)
