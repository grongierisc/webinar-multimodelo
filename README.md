# Webinar-multimodel

Examples and demonstrations for the IRIS Webinar Multimodel Databases

The project is divided into several examples:

## jdbc-springboot-maven

This example uses a simple springboot project with maven that uses InterSystems IRIS JDBC Java connector to connect to an instance of IRIS Community Edition that is lifted in a Docker container.

More details in the [README](https://github.com/grongierisc/webinar-multimodelo/tree/master/jdbc-springboot-maven) of the project

## jdbc-jpa-rest

Spring Boot and Maven are also used in this example. In this case Hybernate JPA is used to link the tables to entities. A REST API is generated that can be used by any application.

More details in the [README](https://github.com/grongierisc/webinar-multimodelo/tree/master/jdbc-jpa-rest) of the project

## webinar-web

Angular application of example that uses the API developed in the previous example

More details in the [README](https://github.com/grongierisc/webinar-multimodelo/tree/master/webinar-web) of the project

## rest-docdb

This example presents the IRIS Document Database capabilities. To do it in a simple way we will show an example of Use by means of the API REST incorporated.

More details in the [README](https://github.com/grongierisc/webinar-multimodelo/tree/master/rest-docdb) of the project

## node-express-rest

In this example we use node.js and access Globals directly from InterSystems IRIS to establish, retrieve and delete stored data. We build a REST API that is able to receive GET, POST and DELETE from a custom JSON object and structure its properties in InterSystems IRIS Globals.

More details in the [README](https://github.com/grongierisc/webinar-multimodelo/tree/master/node-express-rest) of the project

## iris-phoneapp

This example has two projects.

The first project is a fully developed API in IRIS using ObjectScript. In this example IRIS features are used for use as an Object-Oriented Database. IRIS native object persistence is used and a REST API is provided to manipulate the objects in the database.

The second project is a simple application developed in Angular 7 that makes use of the API published in IRIS.

More details in the [README of the api](https://github.com/grongierisc/webinar-multimodelo/tree/master/iris-phoneapp/api) and in the [README of the app](https://github.com/grongierisc/webinar-multimodelo/tree/master/iris-phoneapp/app)
