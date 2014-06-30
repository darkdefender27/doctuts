=================
HIVE INSTALLATION
=================

This section refers to the installation settings of Hive on a standalone system
as well as on a system existing as a node in a cluster.

INTRODUCTION
************

    Apache Hive is a data warehouse infrastructure built on top of Hadoop for providing data summarization, query, and analysis. Apache Hive supports analysis of large datasets stored in Hadoop's HDFS and compatible file systems such as Amazon S3 filesystem. It provides an SQL-like language called HiveQL(Hive Query Language) while maintaining full support for map/reduce.

Hive Installation
*****************

Installing HIVE:
================

- Browse to the link: http://apache.claz.org/hive/stable/

- Click the apache-hive-0.13.0-bin.tar.gz

- Save and Extract it

    Commands ::

        user@ubuntu:~$  cd  /usr/lib/
        user@ubuntu:~$  sudo mkdir hive
        user@ubuntu:~$  cd Downloads
        user@ubuntu:~$  sudo mv apache-hive-0.13.0-bin /usr/lib/hive

Setting Hive environment variable:
==================================

Commands ::

    user@ubuntu:~$  cd
    user@ubuntu:~$  sudo gedit  ~/.bashrc


Copy and paste the following lines at end of the file ::

    # Set HIVE_HOME
    export HIVE_HOME="/usr/lib/hive/apache-hive-0.13.0-bin"
    PATH=$PATH:$HIVE_HOME/bin
    export PATH

Setting HADOOP_PATH in HIVE config.sh
=====================================

Commands ::

    user@ubuntu:~$ cd  /usr/lib/hive/apache-hive-0.13.0-bin/bin
    user@ubuntu:~$ sudo gedit hive-config.sh

Go to the line where the following statements are written ::

    # Allow alternate conf dir location.
    HIVE_CONF_DIR="${HIVE_CONF_DIR:-$HIVE_HOME/conf"
    export HIVE_CONF_DIR=$HIVE_CONF_DIR
    export HIVE_AUX_JARS_PATH=$HIVE_AUX_JARS_PATH



Below this write the following ::

    export HADOOP_HOME=/usr/local/hadoop    (write the path where hadoop file is there)

Create Hive directories within HDFS
===================================

Command ::

    user@ubuntu:~$   hadoop fs -mkdir /usr/hive/warehouse


Setting READ/WRITE permission for table
========================================

Command ::

    user@ubuntu:~$  hadoop fs -chmod g+w /usr/hive/warehouse

HIVE launch
============

Command ::

    user@ubuntu:~$  hive


Hive shell will prompt:

OUTPUT
------

Shell will look like ::

    Logging initialized using configuration in jar:file:/usr/lib/hive/apache-hive-0.13.0-bin/lib/hive- common-0.13.0.jar!/hive-log4j.properties
    hive>

Creating a database
===================

Command ::

    hive> create database mydb;

OUTPUT ::

    OK
    Time taken: 0.369 seconds
    hive>

Configuring hive-site.xml:
==========================

Open with text-editor and change the following property ::

    <property>
        <name>hive.metastore.local</name>
        <value>TRUE</value>
        <description>controls whether to connect to remove metastore server or open a new metastore server in Hive Client JVM</description>
    </property>

    <property>
        <name>javax.jdo.option.ConnectionURL</name>
        <value>jdbc:mysql://usr/lib/hive/apache-hive-0.13.0-bin/metastore_db? createDatabaseIfNotExist=true</value>
        <description>JDBC connect string for a JDBC metastore</description>
    </property>

    <property>
        <name>javax.jdo.option.ConnectionDriverName</name>
        <value>com.mysql.jdbc.Driver</value>
        <description>Driver class name for a JDBC metastore</description>
    </property>

    <property>
        <name>hive.metastore.warehouse.dir</name>
        <value>/usr/hive/warehouse</value>
        <description>location of default database for the warehouse</description>
     </property>


Writing a Script
================

Open a new terminal (CTRL+ALT+T) ::

    user@ubuntu:~$ 	sudo gedit sample.sql

    create database sample;
    use sample;
    create table product(product int, productname string, price float)[row format delimited fields terminated by ',';]
    describe product;

load data local inpath '/home/hduser/input_to_product.txt' into table product ::

    select * from product;

SAVE and CLOSE ::

    user@ubuntu:~$ sudo gedit input_to_product.txt
    user@ubuntu:~$ cd /usr/lib/hive/apache-hive-0.13.0-bin/ $ bin/hive -f /home/hduser/sample.sql




