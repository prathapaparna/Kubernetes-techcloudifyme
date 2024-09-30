# Deployment-strategies

## Recreate 

**Recreae**: shutdown existing pods and deploy new pods with updated version, we face downtime here
- An example Spec: section in the manifest file could look like this:
![image](https://github.com/user-attachments/assets/fe7c0b67-d575-4f47-b80f-5507f4944e6f)

## Rolling update(default-deployment)

**Rolling update:** Start new pods with the new version and Gradually scale down the old pods as the new ones become ready.
 - An example Spec: section in the manifest file could look like this:
![image](https://github.com/user-attachments/assets/0fd6f749-c5bb-4175-b3dc-c541d6f8bec5)
- To achieve this, **Readiness probes** are used:
- Once the readiness probe detects the new version of the application is available, the old version of the application is removed. If there is a problem, the rollout can be stopped and rolled back to the previous version, avoiding downtime across the entire cluster.

## blue-green deployment

**Blue-Green deployment:** Deploy the new version to the blue environment.Test and verify the blue environment.Switch traffic from green to blue by updating the service.


## canary deployment

**canary-deployment:** Deploy a few instances of the new version alongside the old version.Gradually increase traffic to the new version while monitoring.Once validated, switch all traffic to the new version.
