# Architecture Guide

First you need to have a background knowledge over the following keywords:

* [CQRS](https://martinfowler.com/bliki/CQRS.html)
* [Event Sourcing](https://martinfowler.com/eaaDev/EventSourcing.html)
* [Hexagonal Architecture](https://fideloper.com/hexagonal-architecture)
* [SCS](https://scs-architecture.org/)
* Pub/Sub, queuing, messaging, RPC and distributed computing in general

Every application on GamaOps is built using the architectures explained above and the services topology reflect the hexagonal architecture where there are two distinct kinds of backends: **internal services** and **edge APIs**.

You can understand the 

## Internal Services

Internal services are the building blocks of everything that needs to be stateful

## Edge APIs