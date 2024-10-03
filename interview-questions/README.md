## CNI vs kube-proxy
- **CNI** handles **pod-to-pod networking** within the cluster. It’s responsible for assigning IP addresses to pods and ensuring that they can communicate across nodes.
- **Kube-proxy** handles **service-level networking**, ensuring that when traffic comes to a service, it’s routed correctly to one of the backend pods.
## why and how you drained nodes in k8
- In Kubernetes, node draining is the process of safely evicting all running pods from a node before it is taken down for maintenance, upgrades, or decommissioning. The idea is to gracefully move the workloads (pods) off the node so that the node can be safely removed or restarted without disrupting services.

## Observability vs monitoring
-  monitoring tells you when something is wrong, and observability helps you understand why it's wrong.
-  Monitoring is part of the abservability
  
   ![image](https://github.com/user-attachments/assets/99bcb248-8be8-4159-ac58-439118c0412e)

