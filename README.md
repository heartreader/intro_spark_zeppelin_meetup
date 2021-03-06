
**Hands-On Intro to Big Data Analytics using Apache Spark and Apache Zeppelin**


This workshop will provide an introduction to Big Data Analytics using Apache Spark and Apache Zeppelin.

Spark is a unified framework for big data analytics. Spark provides one integrated API for use by developers, data scientists, and analysts to perform diverse tasks that would have previously required separate processing engines such as batch analytics, stream processing and statistical modeling. Spark supports a wide range of popular languages including Python, R, Scala, SQL, and Java. Spark can read from diverse data sources and scale to thousands of nodes.

The lecture will be followed by demo . There will be a short lecture on Hadoop and how Spark and Hadoop interact and compliment each other. You will learn how to move data into HDFS using Spark APIs, create Hive table, explore the data with Spark and SQL, transform the data and then issue some SQL queries. We will be using Scala and/or PySpark for labs.

Users have 2 options to follow along with the demo labs. You can use the:

* Hortonworks Sandbox on a VM No data center, no cloud service and no internet connection needed! Full control of the environment. http://hortonworks.com/products/hortonworks-sandbox/#install

* HDP 2.3.2 on Azure with Hortonworks Sandbox. Try Hortonworks Sandbox on Windows Azure. It’s free for the the first month, and there’s no need to download the VM!
http://hortonworks.com/blog/hortonworks-sandbox-with-hdp-2-3-is-now-available-on-microsoft-azure-gallery/

**PRE-Requisite** in case we **don't** have internet connectivity at the location. 

1) Do the  initial setup of the  HDP sandbox. The initial root password is hadoop, but you are required to change it.

https://github.com/HortonworksUniversity/Essentials/blob/master/demos/SandboxSetup.md


    ssh root@127.0.0.1 -p 2222
    root@127.0.0.1's password: 
    You are required to change your password immediately (root enforced)
    Last login: Tue Mar  1 21:05:47 2016 from 10.0.2.2
    Changing password for root.
    (current) UNIX password: 
    New password: 
    Retype new password: 
    [root@sandbox ~]# ambari-admin-password-reset
    Please set the password for admin: 
    Please retype the password for admin: 
    
    The admin password has been set.
    Restarting ambari-server to make the password change effective...
    
    Using python  /usr/bin/python2
    Restarting ambari-server
    Using python  /usr/bin/python2
    Stopping ambari-server
    Ambari Server stopped
    Using python  /usr/bin/python2
    Starting ambari-server
    Ambari Server running with administrator privileges.
    Organizing resource files at /var/lib/ambari-server/resources...
    Server PID at: /var/run/ambari-server/ambari-server.pid
    Server out at: /var/log/ambari-server/ambari-server.out
    Server log at: /var/log/ambari-server/ambari-server.log
    Waiting for server start....................
    Ambari Server 'start' completed successfully.
    It is suggested that you set the admin Ambari user's password to admin for consistency with the other web UIs.

2) **ZEPPELIN SETUP**:

Open the webbrowser and go to http://sandbox:9995/#/ or the Azure HDP deployment where zeppelin is located:

Click: Import Notebook

Give Notebook Name: 

And choose Add from URL :  

copy and paste the RAW url of the notebook

3) **NOTEBOOKS:**

* phillyCrimeAnalysis.json - INTRO TO RDDS USING SCALA
https://raw.githubusercontent.com/zeltovhorton/intro_spark_zeppelin_meetup/master/notebooks/phillyCrimeAnalysis.json

* IntroToSparkDataFramesWithScala.json - INTRO TO DATA FRAMES AND SPARKSQL
https://raw.githubusercontent.com/zeltovhorton/intro_spark_zeppelin_meetup/master/notebooks/IntroToSparkDataFramesWithScala.json

* UsingSparkSQLUDFsTOCreateDateTimes.json - INTRO TO UDFs
https://raw.githubusercontent.com/zeltovhorton/intro_spark_zeppelin_meetup/master/notebooks/UsingSparkSQLUDFsTOCreateDateTimes.json

* PeopleJSONDemo.json - INTRO TO USING JSON AND DATAFRAMES IN SPARK
https://raw.githubusercontent.com/zeltovhorton/intro_spark_zeppelin_meetup/master/notebooks/PeopleJSONDemo.json

* SparkSQLFederatedSetup.json - SETUP scripts for demonstrating SPARKSQL federated  
 https://raw.githubusercontent.com/zeltovhorton/intro_spark_zeppelin_meetup/master/notebooks/SparkSQLFederatedSetup.json

* SparkSqlFederatedDemo.json - Spark
https://raw.githubusercontent.com/zeltovhorton/intro_spark_zeppelin_meetup/master/notebooks/SparkSqlFederatedDemo.json

4) **SPARK SQL FEDERATED SETUP**:

Zeppelin must be able to sudo and access Postgres. Run the following commands as root at the host console:

echo "zeppelin ALL=(ALL) NOPASSWD: ALL" >> /etc/sudoers

echo "host all all 127.0.0.1/32 md5" >> /var/lib/pgsql/data/pg_hba.conf

Log into Amabri as admin

Click on the Spark service in the left hand pane

* Click on Configs

* Click on the "Custom spark-defaults"

* Add a custom property key=spark.sql.hive.thriftServer.singleSession value=true

Restart the Spark service

Restart the Zeppelin service

http://sandbox.hortonworks.com:8080

Access The Zeppelin Notebook

http://sandbox.hortonworks.com:9995
