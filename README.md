# nahidnooree_devops_lab3

# Ansible_Project
Java Application deployment using Ansible - Java, Tomcat and MySQL installation &amp; configuration management

## Project Setup
**About**: This is a simple java project Deployment to a remote server using Ansible. In this demo, you can see how to install the pre-requisites and other requirements before deploying the project.

Tasks:
-----
1. JAVA installation
2. Tomcat web server
3. MySQL database
4. Python packages
3. User creation
4. DB Creation
5. Table creation

Steps:
-----

1. I create two roles.. one `tomcat` & other `mysql` using `ansible-galaxy`
```
ansible-galaxy init tomcat
ansible-galaxy init mysql
```

It will create all defult folder structure.. keep the folders which you require and remove the rest for better visibility and understanding.

2. Create a folder called `group_vars` in the same folder where 'Roles' folder is present, to keep the variables and vault information.
```
$ls -l group_vars/all
total 8
-rw-r--r--. 1 root root  99 Nov 20 18:24 vars
-rw-r--r--. 1 root root 419 Nov 20 18:25 vault
```
3. Create a folder called `db` in the same folder where 'Roles' folder is present, to store the sql script to import whie installing the mysql
```
$ ls -l db/
total 4
-rw-r--r--. 1 root root 402 Nov 20 18:47 devopsclass.sql
```
4. Add the tasks into the *main.yml* file of the respective roles.
```
$ ls -l roles/tomcat/tasks/
total 4
-rw-r--r--. 1 root root 1117 Nov 20 19:16 main.yml

$ ls -l roles/mysql/tasks/
total 4
-rw-r--r--. 1 root root 1245 Nov 20 19:17 main.yml
```
5. Once you setup the project run the play book (site.yml) - site.yml contains the roles which need to be executed.
```
ansible-playbook roles/site.yml
```

After the successfull execution of the playbook, you can view the application by logging into it.

![image](https://github.com/NahidNuri03/nahidnooree_devops_lab3/assets/95105922/4f6c51a2-e1b2-4028-bf1f-59dfce4364c9)

And check the Databae:

```
$ mysql -u nahid -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 2
...

Copyright (c) 2000, 2023, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| devopsclass        |
| mysql              |
| performance_schema |
+--------------------+
4 rows in set (0.00 sec)

mysql>
```
