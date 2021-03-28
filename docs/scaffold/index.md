# Python Microservices
Python Microservice Scaffold is an example of how to structure a Flask Microservice Project.
This Scaffold is build over [PyMS](https://github.com/python-microservices/pyms) package. PyMS is a [Microservice chassis pattern](https://microservices.io/patterns/microservice-chassis.html)
like Spring Boot (Java) or Gizmo (Golang). PyMS is a collection of libraries, best practices and recommended ways to build
microservices with Python which handles cross-cutting concerns:

- [Externalized configuration](configuration.md)
- Logging
- Health checks
- [Metrics](/services/services/#metrics)
- [Distributed tracing](/tutorials/tutorial_propagate_traces/)
- [Service Discovery](/services/services_discovery/)
- [Encryption](/encrypt_decryt_configuration/)

## Stack

* [PyMS](https://github.com/python-microservices/pyms)
   * [Flask](https://github.com/pallets/flask)
   * [connexion](http://connexion.readthedocs.io)
   * [Opentracing](https://github.com/opentracing-contrib/python-flask)
* [SQLAlchemy](https://www.sqlalchemy.org/)
* [Flask-SQLAlchemy](http://flask-sqlalchemy.pocoo.org/2.3/)
* [Flask-Script](https://flask-script.readthedocs.io/en/latest/)