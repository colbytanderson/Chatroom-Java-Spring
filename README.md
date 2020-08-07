# Chatroom-Java-Spring

## Multi-instance Reactive Chat App using Spring Boot WebFlux and Redis Pub/Sub

Scalable Java 11 Spring Boot WebFlux Chat Application to demonstrate use of Reactive Redis [Pub/Sub] using Reactive [WebSocket Handler], without using any external Message Broker like RabbitMQ to sync messages between different instances. 

### Installation and Configuration

##### Pre-requisite:
Install and run [Redis] locally or on Docker.

To run Redis in Docker:
```sh
$ docker run -d -p 6379:6379 -e REDIS_PASSWORD=SuperSecretRedisPassword bitnami/redis:4.0.11-r6
```
 
#### Build and Run the applications:

Build and run the **spring-redis-websocket** application:
```sh
$ cd spring-redis-websocket

$ mvn clean package

$ mvn spring-boot:run
```

### Run in Docker

#### Build and run the *spring-redis-websocket* locally in Docker:

Build the JAR file:
```sh
$ mvn clean package
```

Build docker image:
```sh
$ mvn spring-boot:build-image
```

Run docker image:
```sh
$ docker run -d -p 8080:8080 \
$ chatroom
```

#### Run multiple instance using docker-compose locally
 
Run multiple instances of *spring-redis-websocket* locally load balanced via Ngnix connected to redis container in Docker:
```sh
$ cd src/main/docker
$ docker-compose up
```

### Run in Kubernetes

#### Assuming you have a Kubernetes Cluster up and running locally:

```sh
$ kubectl apply -f src/main/k8s
```

#### Or try [Play with Kubernetes] to quickly setup a K8S cluster:
1. Follow the instructions to create Kuberenetes cluster.
2. Install git by running: 
```sh
$ yum install git -y
```
4. Run multiple instances of *spring-redis-websocket* load balanced by native Kubernetes Service. All instances connected to a single [Redis] pod.     
```sh
$ kubectl apply -f src/main/k8s
```


### Tech

**spring-redis-websocket** uses a number of open source projects:

* [Spring Boot] - An opinionated framework for building production-ready Spring applications. It favors convention over configuration and is designed to get you up and running as quickly as possible.
* [Spring Data Redis] - Spring Data Redis provides easy configuration and access to Redis from Spring applications.
* [Redis] - Redis is an open source (BSD licensed), in-memory data structure store, used as a database, cache and message broker.
* [Bootstrap] - Bootstrap is an open source toolkit for developing with HTML, CSS, and JS. Custom Bootstrap theme - [Bootswatch Sketch]. 
* [Docker] - Docker is an open platform for developers and sysadmins to build, ship, and run distributed applications.
* [NGINX] - NGINX is High Performance Load Balancer, Web Server, & Reverse Proxy.
* [Kubernetes] - Kubernetes is an open-source system for automating deployment, scaling, and management of containerized applications.
