## create a table in mysql
```
  kubectl exec -it <pod-name>  /bin/bash  # enter to pod
  mysql -u root -p                       # enter mysql
  show databases;
  use mysql;                             # use my sql db
# create table <table-name>(values)
 create table employee(eno varchar(40), ename varchar(40));
 select * from employee;
# enter employee info in that table
 insert into employee(eno, ename) values(101, "appu");
# this employee information is available in /var/lib/mysql folder of inside container
```
