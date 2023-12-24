## create atable in mysql
 - kubectl exec -it <pod-name>  /bin/bash  -> enter to pod
 - mysql -u root -p -> enter mysql
 - show databases;
- use mysql;
- create table <table-name>(values)
- ex: create table employee(eno varchar(40), ename varchar(40));
- select * from employee;
- insert into employee(eno, ename) values(101, "appu");
- this employee information is available in /var/lib/mysql folder of inside container
