===================================
IMPORTING DATA FROM HADOOP TO MYSQL
===================================

Steps to install mysql
======================

- Run the command :sudo apt-get install mysql-server and give appropriate username and password.

Using sqoop to perform import to hadoop from sql
================================================

1. Download mysql-connector-java-5.1.28-bin.jar and move to /usr/lib/sqoop/lib using command ::

    user@ubuntu:~$ sudo cp mysql-connnectpr-java-5.1.28-bin.jar /usr/lib/sqoop/lib/

2. Login to mysql using command ::

    user@ubuntu:~$   mysql -u root -p

3. Login to secure shell using command ::

    user@ubuntu:~$  ssh localhost

4. Start hadoop using the command ::

    user@ubuntu:~$  bin/hadoop start-all.sh

5. Run the command ::

    user@ubuntu:~$ sqoop import -connect jdbc:mysql://localhost:3306/sqoop -username root -pasword abc -table employees -m


This command imports the employees table from the sqoop directory of myql to hdfs.

Error points
============

1. Do check if the hadoop is in safe mode using command ::

    user@ubuntu:~$hadoop dfsadmin -safemode get

If you are getting safemode is on, run the command ::

    user@ubuntu:~$hadoop dfsadmin -safemode leave

and again run the command ::

    user@ubuntu:~$hadoop dfsadmin -safemode get

and confirm that you are getting safemode is off.

2. Do make sure that haoop is running before performing the import action.



