# Deployment-strategies

## Recreate        
## Rolling update(default-deployment)
## canary deployment
## blue-green deployment

**Recreae**: shutdown existing pods and deploy new pods with updated version, we face downtime here
- An example Spec: section in the manifest file could look like this:
![image](https://github.com/user-attachments/assets/fe7c0b67-d575-4f47-b80f-5507f4944e6f)


**Rolling update:** Start new pods with the new version and Gradually scale down the old pods as the new ones become ready.

**Blue-Green deployment:** Deploy the new version to the blue environment.Test and verify the blue environment.Switch traffic from green to blue by updating the service.

**canary-deployment:** Deploy a few instances of the new version alongside the old version.Gradually increase traffic to the new version while monitoring.Once validated, switch all traffic to the new version.
