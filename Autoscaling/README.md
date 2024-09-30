# Autoscaling

- autoscaling refers to the automatic adjustment of the number of running pods or nodes based on resource utilization
- 
## Horizontal Pod Autoscaling
- HPA automatically scales the number of pods in a deployment or replica set based on observed CPU or memory utilization, or custom metrics (like HTTP requests).
- It periodically checks the metrics server to assess the load on the pods and adjusts the replicas accordingly.

## Vertical Pod Autoscaling
- VPA automatically adjusts the CPU and memory requests/limits of the containers in a pod based on historical and current usage.
- It helps in resizing the resources of containers without the need to scale the number of pods.

## cluster autoscaling
- This is used to scale the number of nodes in the cluster based on the scheduling needs of the pods. When the cluster is running out of resources (CPU or memory), it can add more nodes. Similarly, it can remove underutilized nodes.
- It works by monitoring pods in a pending state due to lack of resources and adds nodes if required. Similarly, it removes idle nodes.
