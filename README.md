# Hola Docker with Spring Boot

This project shows you how to dockerize a Spring Boot application using a single `Dockerfile` or combining it with `docker-compose`.

The guide to build the code and understand the different concepts is located at [https://thepracticaldeveloper.com/2017/12/11/dockerize-spring-boot/](https://thepracticaldeveloper.com/2017/12/11/dockerize-spring-boot/).

## Datadog Enabled
This containerized Java Spring Boot deployment is using [Datadog's](https://docs.datadoghq.com/agent/basic_agent_usage/docker/) v.6.1.2 of their Docker agent image. This is an example of how to configure the HTTP_CHECK integration while using our [Docker agent's autodiscovery](https://docs.datadoghq.com/agent/autodiscovery/#how-it-works) feature.

*Some key things to change:*

1. Change the [DD_API_KEY](https://github.com/lowkeyshift/docker-dd-http-check/blob/master/docker-compose.yml#L19) in the docker-compose.yml file; This should reflect your account API-KEY
2. If you are going to change the app associates from this deployment you will need to change the name in the [Dockerfile-build](https://github.com/lowkeyshift/docker-dd-http-check/edit/master/README.md)
3. Depending on your scale you may want to change the [*template variables*](https://docs.datadoghq.com/agent/autodiscovery/#supported-template-variables) being used in the dockerfile-build file

## Spring Boot API
This Spring Boot app already has the [Actuator](http://www.baeldung.com/spring-boot-actuators) api installed and enaabled. This is a configuration within the [pom.xml](https://github.com/lowkeyshift/docker-dd-http-check/blob/master/pom.xml#L40) file.


## Running the app with Docker

You will neeed both the latest version of [Docker-ce](https://www.docker.com/community-edition#/download) and [docker-compose](https://docs.docker.com/compose/install/).

Make sure you generate first the `.jar` file by running:

`mvn clean package`

You just need to execute:

`docker-compose up`

