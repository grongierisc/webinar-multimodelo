# jdbc-springboot-maven

This example uses a simple SpringBoot project with Maven that uses InterSystems IRIS JDBC Java connector to connect to an instance of IRIS Community Edition that is lifted in a Docker container.

## Basic environment configuration

The first step will be to install [Maven](https://maven.apache.org/download.cgi) in our computer and if you use a Windows environment configure in the environment variables the path where mvn.exe is under the name M2_HOME.

The JDBC driver resides in a directory of the IRIS instance and must be brought to the local computer:

```bash
root@localhost:/# df
Filesystem 1K-blocks Used Available Use% Mounted on
overlay 61255492 35660284 22453884 62% /
tmpfs 65536 0 65536 0% /dev
tmpfs 2534072 0 2534072 0% /sys/fs/cgroup
osxfs 976900220 846849764 117767420 88% /shared
/dev/sda1 61255492 35660284 22453884 62% /etc/hosts
shm 65536 664 64872 2% /dev/shm
tmpfs 2534072 0 2534072 0% /proc/acpi
tmpfs 2534072 0 2534072 0% /sys/firmware

root@localhost:/shared# iris list

Configuration 'IRIS' (default)
        directory: /usr/irissys
        versionid: 2019.2.0.107.0com
        datadir: /usr/irissys
        conf file: iris.cpf (SuperServer port = 51773, WebServer = 52773)
        status: running, since Mon Jun 17 18:15:15 2019
        state: ok
        product: InterSystems IRIS

root@localhost:/shared# cp /usr/irissys/dev/java/lib/JDK18/intersystems-jdbc-3.0.0.jar /shared/
```

The library must then be registered so that it can be referenced by Maven:

```bash
mv intersystems-jdbc-3.0.0.jar ../drivers
mvn install:install-file -Dfile="drivers/intersystems-jdbc-3.0.0.jar" -DgroupId="com.intersystems.jdbc" -DartifactId="IRISDriver" -Dversion="3.0.0" -Dpackaging=jar
```

This project is developed following the framework of Spring Boot with MAVEN in such a way that we will have a class (Application.java) with a main method that will work as initiator. From this method we will create our tables in the database and insert records in them. Spring Boot by default will look for an application.properties file from which it will obtain the data to configure a DataSource object from which we will be able to manage our database.

We will consult in the file application.properties the data of connection to our bdd, being the most important:
	1 spring.datasource.driverClassName: name of the connection driver to bdd.
	2 spring.datasource.url: connection url and namespace to which we will connect.
	3 spring.datasource.username: user
	4 spring.datasource.password: password
	5 spring.datasource.initialization-mode: behavior with the database when starting the application (update, create if it doesn't exist, delete and recreate...)


## Starting the application

Once you have downloaded and configured the code on your PC, all you have to do is access the code's path and execute:

```
mvn clean install
mvn spring-boot:run
```

This will deploy our application (Spring Boot counts with, we will be able to access the [IRIS] portal (http://localhost:9092/csp/sys/UtilHome.csp) and check how the table we have defined has been generated.
