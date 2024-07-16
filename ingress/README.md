**Note**: 
- we have k8 service, service itself provide using
  - 1. service discovery: (automatically takes the pod new ip)
  - 2. load balancing
  - 3. expose the application to outside world

## drawback with k8-service:
----------------
**1.** it can't provide 
ssl/tls termination
path/host based routing, raito based routing

**2.** if we use loadbalancer service mode, each application will take one load-balancer so that cloud provider will charge us.

- ingress can provide all above features, it will create one loadbalancer
  
# Ingress
- Kubernetes Ingress is a powerful way to manage external access to your services, providing capabilities like load balancing, SSL termination, and routing rules. By deploying an Ingress controller and creating Ingress resources, we can efficiently manage HTTP/S traffic in your Kubernetes cluster.
  
## Key Features of Ingress:
- **Path-based Routing:** Directs traffic to different services based on the request URL path.
- **Name-based Virtual Hosting:** Routes traffic based on the hostname in the request.
- **SSL/TLS Termination:** Manages HTTPS traffic by terminating SSL/TLS at the Ingress level.
- **Load Balancing:** Distributes traffic among multiple backend services to ensure availability and reliability.
  
## Ingress Controller
- An Ingress Controller is a component in a Kubernetes cluster that manages Ingress resources. The controller watches the Kubernetes API for Ingress resources and updates its configuration to fulfill the specified rules, ensuring that incoming traffic is properly routed to the backend services.

## Popular Ingress Controllers:
- **NGINX Ingress Controller:** A widely used and robust Ingress controller based on NGINX.
- **Traefik:** An edge router and Ingress controller with dynamic configuration capabilities.
- **HAProxy Ingress:** Provides advanced load balancing and traffic routing using HAProxy.
- **Istio:** A service mesh that provides Ingress functionality among other features like service-to-service authentication and authorization.
  
## How Ingress and Ingress Controllers Work Together

- Define an Ingress Resource: A user creates an Ingress resource that specifies rules for routing traffic to different services.
- Ingress Controller Watches for Changes: The Ingress controller continuously watches the Kubernetes API for new or updated -Ingress resources.
- Update Configuration: When the Ingress controller detects changes, it updates its internal configuration to reflect the new routing rules.
- Handle Incoming Traffic: The Ingress controller intercepts incoming traffic to the cluster and routes it based on the rules defined in the Ingress resources.

  
