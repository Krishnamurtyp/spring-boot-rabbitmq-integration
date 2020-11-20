# Spring Boot RabbitM Integration
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://github.com/DanielMichalski/spring-boot-java-swing-reservations/blob/master/LICENSE)

This project aims to present how to create and configure a Spring Boot + RabbitMQ application.
The project is built using Java, Spring Boot, RabbitMQ and Docker.

## Table of Contents
* [Prerequisites](#prerequisites)
* [Libraries](#libraries)
* [Running the application](#running-the-application)
    * [On Windows](#on-windows)
    * [On MacOS/ Linux](#on-macos-linux)
* [RabbitMQ access](#rabbitmq-access)
* [Sending message](#sending-message)

## Prerequisites
- [Java JDK](https://www.oracle.com/pl/java/technologies/javase-downloads.html) version 8+
- [Docker Desktop](https://www.docker.com/products/docker-desktop) 

## Libraries
| Library name                                                                                                     | Description                                                                                                                          |
|------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------|
| [Spring Boot 2](https://spring.io/projects/spring-boot)                                                          | Spring Boot makes it easy to create stand-alone, production-grade Spring based Applications that you can "just run".                 |
| [RabbitMQ](https://www.rabbitmq.com/)                                                                            | RabbitMQ is the most widely deployed open source message broker.                                                                     |
| [Docker Compose](https://docs.docker.com/compose/)                                                               | Compose is a tool for defining and running multi-container Docker applications.                                                      |

## Running the application
#### On Windows
```bash
## Run RabbitMQ on Docker
cd .docker/dependencies
start.sh

## Build and run publisher application using Maven Wrapper
cd rabbitmq-publisher
mvnw.cmd clean install
mvnw.cmd spring-boot:run

## Build and run receiver application using Maven Wrapper
cd rabbitmq-receiver
mvnw.cmd clean install
mvnw.cmd spring-boot:run
```

#### On MacOS/ Linux
```bash
## Run RabbitMQ on Docker
cd .docker/dependencies
./start.sh

## Build and run publisher application using Maven Wrapper
cd rabbitmq-publisher
./mvnw clean install
./mvnw spring-boot:run

## Build and run receiver application using Maven Wrapper
cd rabbitmq-receiver
./mvnw clean install
./mvnw spring-boot:run
```

## RabbitMQ access
| RabbitMQ URL            | Username     | Password   |
|-------------------------|--------------|----------- |
| http://localhost:15672  | user         | password   |

## Sending message
In order to send a message to the queue please send a request:
```bash
curl --header "Content-Type: application/json" --request POST --data "{\"firstName\":\"John\",\"lastName\":\"Black\"}" http://localhost:8080/api/messages
```