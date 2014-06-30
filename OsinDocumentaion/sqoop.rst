===================
SQOOP INSTALLATION
===================

This section refers to the installation settings of Sqoop.


INTRODUCTION
============

- Sqoop is a tool designed to transfer data between Hadoop and relational databases.
- You can use Sqoop to import data from a relational database management system (RDBMS) such as MySQL or Oracle into the Hadoop Distributed File System (HDFS), transform the data in Hadoop MapReduce, and then export the data back into an RDBMS. Sqoop automates most of this process, relying on the database to describe the schema for the data to be imported. Sqoop uses MapReduce to import and export the data, which provides parallel operation as well as fault tolerance. This document describes how to get started using Sqoop to move data between databases and Hadoop and provides reference information for the operation of the Sqoop command-line tool suite.

.. figure:: _static/images/25.png
   :height: 700 px
   :width: 1000 px
   :scale: 50 %
   :alt: Use case diagram of the Ticketing System
   :align: center

Stable release and Download
===========================

Sqoop is an open source software product of the Apache Software Foundation.
Sqoop source code is held in the Apache Git repository.

Prerequisites
=============

Before we can use Sqoop, a release of Hadoop must be installed and con?gured. Sqoop is currently supporting 4 major Hadoop releases - 0.20, 0.23, 1.0 and 2.0. We have installed Hadoop 2.2.0 and it is compatible with sqoop 1.4.4.We are using a Linux environment Ubuntu 12.04 to install and run sqoop. The basic familiarity with the purpose and operation of Hadoop is required to use this product.

Installation
============

To install the sqoop 1.4.4 we followed the given sequence of steps :

1.  Download the sqoop-1.4.4.bin_hadoop-1.0.0.tar.gz  file from
    www.apache.org/dyn/closer.cgl/sqoop/1.4.4

2.  Unzip the tar ?le: sudo tar -zxvf sqoop-1.4.4.bin hadoop1.0.0.tar.gz

3.  Move sqoop-1.4.4.bin hadoop1.0.0 to sqoop using command ::

    user@ubuntu:~$  sudo mv sqoop  1.4.4.bin hadoop1.0.0 /usr/local/sqoop

4.  Create a directory sqoop in usr/lib using command ::

    user@ubuntu:~$ sudo mkdir /usr/lib/sqoop

5.  Go to the zipped folder sqoop-1.4.4.bin_hadoop-1.0.0 and run the command ::

    user@ubuntu:~sudo mv ./* /usr/lib/sqoop

6.  Go to root directory using cd command ::

    user@ubuntu:~$  cd

7.  Open bashrc file using ::

    user@ubuntu:~$  sudo gedit ~/.bashrc

8. Add the following lines ::

    export SQOOP_HOME=¡usr/lib/sqoop
    export PATH=$PATH:$SQOOP_HOME/bin


9. To check if the sqoop has been installed  successfully type the command ::

    sqoop version

