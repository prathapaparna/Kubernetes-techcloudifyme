# RBAC
- RBAC (Role-Based Access Control):
- RBAC is a Kubernetes feature that allows you to control access to the Kubernetes API and resources based on roles and role bindings. 
- RBAC defines roles and role bindings that determine what actions a user, group, or service account can perform.


## Service Account:
- Designed for applications running in the cluster, scoped to namespaces, managed by Kubernetes, and authenticated via tokens. - when you create a namespace by default one default service account will create. When a pod is created, it is automatically assigned a default service account unless specified otherwise.
- before previous version(1.24) when we create sa it will automatically create a secret
## User Account:
- Designed for human users, cluster-wide, managed externally, and authenticated via external credentials
