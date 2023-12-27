# springboot-mysql-k8

## springboot-mysql deployment with docker
  - install git
  - install maven
  - install docker
### create a package and docker image using following commands
```
git clone <repalce-your-git-url>
mvn clean istall
docker build -t <your-docker-imagename>:<version> .
```
### create a dokcer network
```
docker network create springboot-mysql-net
docker network ls
```
### create a docker image and create a docker container
- create mysql container
```
docker run --name mysqldb --network springboot-mysql-net -e MYSQL_ROOT_PASSWORD=Admin#123 -e MYSQL_DATABASE=employeedb -d mysql
```
- check application.properties file and change database details accordingly
```
cat /src/main/resources/application.properties
```
- create docker container
```
docker run --network springboot-mysql-net --name springboot-mysql-container -p 33333:33333 -d techcloudifyme/springboot-mysql:v4
```
**important Note** mysql container and docker container should be on same network

### Create new customer using "/createnewcustomer" API
<img width="741" alt="image" src="https://github.com/TechCloudifyMe/springboot-mysql-k8/assets/141027817/40360690-cdae-4506-9971-a6151ed7978b">

### Check List of customer in UI using "/listallcustomers" API
<img width="595" alt="image" src="https://github.com/TechCloudifyMe/springboot-mysql-k8/assets/141027817/2bd8cbb1-4566-474c-b234-e409835f0cb4">

