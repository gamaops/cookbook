# Registry System

The registry system deals with: authentication, authorization and auditing. This is our identity provider system and consists of the following microservices:

## Current Version

Microservice | Version | gRPC Port | Metrics Port
-------------|---------|-----------|-------------
Identity API | v1      | 35102     | 32004

## Index

* **Identity** - microservice responsible for dealing with identities (authentication and auditing).
   * API Respository: https://github.com/gamaops/identity-api
   * Service Respository: https://github.com/gamaops/identity-service