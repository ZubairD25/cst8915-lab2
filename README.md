# CST8915 Lab 2 

## Service Repositories

- Order Service: https://github.com/ZubairD25/order-service
- Product Service: https://github.com/ZubairD25/product-service
- Store Front: https://github.com/ZubairD25/store-front

## Deployment Architecture

The lab was designed to use four separate Azure virtual machines. 
However, I was only allowed to create 3 VM's due to restrictions on Azure for Students Subscription.

RabbitMQ and Product Service each were deployed on their own VM's
Order Service and Store Front shared a VM 


## 12-Factor App Refactoring

### Configuration and Backing Services

For configuration: The Order Service was modified so that its port and RabbitMQ connection string are provided through environment variables instead of being hardcoded in the application. The Product Service was also modified to read its port from an environment variable. The Store Front uses environment variables to configure the URLs of the Order Service and Product Service.

RabbitMQ was treated as an external backing service. 


### Why Environment Variables?

Environment variables protect sensitive information from being hard coded and committed to github. In addition, environment variables makes the codebase easier to delpoy in different environments because they separate the deployment specific configurations from the application code.

### Separate Repositories for Microservices

It's better to separate the repo's of microservices because each microservice can then be developed and maintained independently. This makes the process more organized and makes it easier for the individual microservice to be updated or scaled without having to worry about the other microservices.

## Demo Video

YouTube: **https://youtu.be/hRszhSj7b-4**
