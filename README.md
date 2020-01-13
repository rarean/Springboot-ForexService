# Forex Microservice

Code Forked from:
[Microservices with Spring Boot](https://github.com/in28minutes/spring-boot-examples/tree/master/spring-boot-basic-microservice) 
and Java - [Part 2 Tutorial](https://www.springboottutorial.com/creating-microservices-with-spring-boot-part-2-forex-microservice)

Example code part of in28minutes. Added google jib for docker builds

# TL;DR
1. clone repo
2. create docker image locally : `mvn clean compile package jib:dockerBuild`
3. run docker image locally: `docker run -it -p 8000:8000 localhost/sb-ms-fxsvc`


# Resources Overview
Forex Service (FS) is the Service Provider. It provides currency exchange values for various currency. Let’s assume that it talks to a Forex Exchange and provides the current conversion value between currencies.

An example request and response is shown below:

GET to http://localhost:8000/currency-exchange/from/EUR/to/INR

```
{
  id: 10002,
  from: "EUR",
  to: "INR",
  conversionMultiple: 75,
  port: 8000,
}
```
The request above is the currency exchange value for EUR to INR. In the response, conversionMultiple is 75.

# Notes
* to publish to docker registry, you will need to add your registry info to [pom.xml](https://github.com/rarean/springboot-currencyconversion/blob/master/pom.xml#L87) with your creds [see google jib docs](https://github.com/GoogleContainerTools/jib/tree/master/jib-maven-plugin#to-object)
* [flatten-maven-plugin](https://github.com/rarean/springboot-currencyconversion/blob/master/pom.xml#L117) is probably not needed
