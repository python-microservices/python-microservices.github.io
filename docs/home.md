# Welcome to PyMS

PyMS, Python MicroService, is a [Microservice chassis pattern](https://microservices.io/patterns/microservice-chassis.html) 
like Spring Boot (Java) or Gizmo (Golang). PyMS is a collection of libraries, best practices and recommended ways to build 
microservices with Python which handles cross-cutting concerns: 

- [Externalized configuration](configuration.md)
- Logging
- Health checks
- [Metrics](/services/services/#metrics)
- [Distributed tracing](/tutorials/tutorial_propagate_traces/)
- [Service Discovery](/services/services_discovery/)
- [Encryption](/encrypt_decryt_configuration/)

PyMS is powered by [Flask](https://flask.palletsprojects.com/en/1.1.x/), [Connexion](https://github.com/zalando/connexion) 
and [Opentracing](https://opentracing.io/).

Get started with an Introduction to Microservices in [English](microservices.md) or [Spanish](microservicios.md) and then the [Installation](installation.md). Get an overview with the [Quickstart](quickstart.md). 

## Motivation

When we started to create a microservice with no previous knowledge, we started looking for tutorials, guides, best practices, but we found
nothing to create professional projects. Most articles say:

- "Install flask"
- "Create routes"
- (Sometimes) "Create a swagger specs"
- "TA-DA! you have a microservice"

But... what happens when we want our configuration out of the code, such as a Kubernetes configmap? what happens with transactionality? 
If we have many microservices, what happens with traces?.

There are many problems around Python and microservices, and we couldn't find anyone to give us a solution.

We start creating these projects to try to solve all the problems we have found in our professional lives about 
microservices architecture.

Nowadays, is not perfect, and we have a looong roadmap, but we hope this library could help other felas and friends ;)
