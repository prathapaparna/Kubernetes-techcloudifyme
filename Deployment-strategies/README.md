# Deployment-strategies

## Recreate 

**Recreae**: shutdown existing pods and deploy new pods with updated version, we face downtime here
- An example Spec: section in the manifest file could look like this:
![image](https://github.com/user-attachments/assets/fe7c0b67-d575-4f47-b80f-5507f4944e6f)

## Rolling update(default-deployment)

**Rolling update:** Start new pods with the new version and Gradually scale down the old pods as the new ones become ready.
 - An example Spec: section in the manifest file could look like this:
![image](https://github.com/user-attachments/assets/0fd6f749-c5bb-4175-b3dc-c541d6f8bec5)

- **MaxSurge** specifies the maximum number of pods the Deployment is allowed to create at one time.
- **MaxUnavailable** specifies the maximum number of pods that are allowed to be unavailable during the rollout.
- To achieve this, **Readiness probes** are used:
- Once the readiness probe detects the new version of the application is available, the old version of the application is removed. If there is a problem, the rollout can be stopped and rolled back to the previous version, avoiding downtime across the entire cluster.

## blue-green deployment(costly)

**Blue-Green deployment:** Deploy the new version to the blue environment.Test and verify the blue environment.Switch traffic from green to blue by updating the service.
- In Blue-Green Deployment, two environments (blue and green) are maintained. The blue environment is the old version of the application, and the green environment is the new version. Traffic is only switched to the green environment after it's validated.


## canary deployment(real-traffic-testing)

**canary-deployment:** Canary deployment is a technique used to reduce the risk of introducing a new version of software into **production** by gradually rolling out the change to a small set of users before making it available to the wider audience.

![image](https://github.com/user-attachments/assets/893086f1-9d87-4c3a-8ea3-7e47b0717e54)



- UAT, QA, and pre-prod environments are similar to production but may have different configurations. By using canary deployment, we can achieve real traffic testing and gradually increase traffic to the new version




![image](https://github.com/user-attachments/assets/a4758325-c9b3-429f-ad1c-6f1fffa3ed8b)

