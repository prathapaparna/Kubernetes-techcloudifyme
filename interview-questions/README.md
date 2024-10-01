## CNI vs kube-proxy
- **CNI** handles **pod-to-pod networking** within the cluster. It’s responsible for assigning IP addresses to pods and ensuring that they can communicate across nodes.
- **Kube-proxy** handles **service-level networking**, ensuring that when traffic comes to a service, it’s routed correctly to one of the backend pods.
