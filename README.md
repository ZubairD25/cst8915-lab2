# CST8915 Lab 2 – 12-Factor App Refactoring

## Service Repositories

- Order Service: https://github.com/ZubairD25/order-service
- Product Service: https://github.com/ZubairD25/product-service
- Store Front: https://github.com/ZubairD25/store-front

## Deployment Architecture

The lab was designed to use four separate Azure virtual machines. Due to VM-size availability limitations with my Azure for Students subscription in the Sweden Central region, I was able to deploy three VMs.

The services were deployed as follows:

- RabbitMQ – dedicated VM
- Product Service – dedicated VM
- Order Service – VM shared with the Store Front
- Store Front – VM shared with the Order Service

The application still uses separate services and codebases. The Store Front communicates with the Product Service and Order Service over HTTP, while the Order Service communicates with RabbitMQ using AMQP.

## 12-Factor App Refactoring

### Configuration and Backing Services

The Order Service was modified so that its port and RabbitMQ connection string are provided through environment variables instead of being hardcoded in the application. RabbitMQ is treated as an external backing service, allowing its connection information to be changed without modifying the application code.

The Product Service was also modified to read its port from an environment variable. The Store Front uses environment variables to configure the URLs of the Order Service and Product Service.

### Why Environment Variables?

Environment variables separate deployment-specific configuration from application code. This makes the same codebase easier to deploy in different environments without changing the source code. It also prevents sensitive configuration, such as the RabbitMQ connection credentials, from being hardcoded or committed to GitHub.

### Separate Repositories for Microservices

Each microservice has its own Git repository so that it can be developed, versioned, deployed, and maintained independently. This supports the 12-Factor principle of having one codebase per application and makes it easier for individual services to be updated or scaled without requiring changes to the other services.

## Demo Video

YouTube: **https://youtu.be/hRszhSj7b-4**
