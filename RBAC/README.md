# RBAC
- RBAC (Role-Based Access Control):
- RBAC is a Kubernetes feature that allows you to control access to the Kubernetes API and resources based on roles and role bindings. 
- RBAC defines roles and role bindings that determine what actions a user, group, or service account can perform.


## Service Account:
- a Service Account (SA) is an identity for processes that run in a Pod. This identity can be used to authenticate and authorize access to the Kubernetes API. Service accounts are used primarily by applications running inside the cluster to interact with the Kubernetes API.
- Designed for applications running in the cluster, scoped to namespaces, managed by Kubernetes, and authenticated via tokens. - when you create a namespace by default one default service account will create. When a pod is created, it is automatically assigned a default service account unless specified otherwise.
- before previous version(1.24) when we create sa it will automatically create a secret
## User Account:
- Designed for human users, cluster-wide, managed externally, and authenticated via external credentials

## Role: 
- A Role is a collection of permissions that allow users to perform specific actions (verbs, such as “get”, “create”, “and “delete”) on a defined set of Kubernetes resource types (such as Pods, Deployments, and Namespaces). Roles are namespaced objects; the permissions they grant only apply within the namespace that the Role belongs to.
## ClusterRole: 
- ClusterRoles work similarly to Roles but are a non-namespaced alternative for cluster-level resources. You’ll need to use a ClusterRole to control access to objects such as Nodes, which don’t belong to any namespace. ClusterRoles also allow you to globally access namespaced resources across all namespaces, such as every Pod in your cluster.
## RoleBinding: 
- RoleBindings represent the links between your Roles and Users or Service Accounts. A RoleBinding lets you reference a Role, then grant those permissions to one or more users (termed Subjects).
## ClusterRoleBinding: 
- ClusterRoleBinding is equivalent to RoleBinding, but targets ClusterRole resources instead of Roles.
