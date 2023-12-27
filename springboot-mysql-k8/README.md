# springboot-mysql-k8

## springboot-mysql deployment with docker
  - install git
  - install maven
  - install docker
### create a package , docker image and push using following commands
```
git clone <repalce-your-git-url>
mvn clean istall
docker build -t <your-docker-imagename>:<version> .
docker login -u <username>
docker push
```
### create deployment
- cd k8 -> check yaml files and replace your deatils accordingly
- and run yaml files using below command
```
kubectl apply -f <yaml-file-name>
```


### Create new customer using "/createnewcustomer" API
<img width="731" alt="image" src="https://github.com/TechCloudifyMe/Kubernetes/assets/141027817/775cb70f-7f98-482f-baec-389b9e8621cb">

### Check List of customer in UI using "/listallcustomers" API
<img width="716" alt="image" src="https://github.com/TechCloudifyMe/Kubernetes/assets/141027817/1f628382-6957-4988-bcf2-509f310a010c">

