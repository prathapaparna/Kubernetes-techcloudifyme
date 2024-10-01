# Node Affinity
- **Node Affinity** controls the scheduling of pods based on node labels. It ensures that a pod is only scheduled on nodes that meet specific criteria.
- Node A has the label region: us-east
- Node B has the label region: us-west
```
apiVersion: v1
kind: Pod
metadata:
  name: my-pod
spec:
  affinity:
    nodeAffinity:
      requiredDuringSchedulingIgnoredDuringExecution:
        nodeSelectorTerms:
        - matchExpressions:
          - key: region
            operator: In
            values:
            - us-east
  containers:
  - name: my-container
    image: nginx
```
- **nodeAffinity:** The pod will only be scheduled on nodes where the label region is set to us-east.

# Pod Affinity
- **Pod Affinity** ensures that a pod is scheduled on a node where other specific pods are already running. This is useful when certain workloads need to be co-located.
- Let’s assume you want to schedule a new pod on the same node as another pod with the label app: frontend.
```
apiVersion: v1
kind: Pod
metadata:
  name: my-pod
spec:
  affinity:
    podAffinity:
      requiredDuringSchedulingIgnoredDuringExecution:
        labelSelector:
          matchExpressions:
          - key: app
            operator: In
            values:
            - frontend
        topologyKey: "kubernetes.io/hostname"
  containers:
  - name: my-container
    image: nginx
```
- **podAffinity:** The pod will only be scheduled on a node where a pod with the label **app: frontend** is already running.
- **topologyKey:** Specifies that the affinity rule should be applied at the node level (kubernetes.io/hostname refers to individual nodes).

| name | Description |
| --- | --- |
| **Node Affinity** | When you need to ensure your pod runs on a specific type of node (e.g., nodes with certain hardware, or in specific regions). |
| **Pod Affinity**| When you want your pod to be located with other specific pods (e.g., pods that need to share resources or data). |
