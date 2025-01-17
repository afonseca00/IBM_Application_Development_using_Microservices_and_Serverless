# Microservices and Cloud Application Development

## Description

This repository contains the labs and the final project for the Microservices and Cloud Application Development course. The course covers various aspects of creating, deploying, and managing microservices using Python, Flask, Docker, and IBM Cloud Code Engine.

## Table of Contents

1. [Lab1: Creating a HELLO WORLD REST API with Python & Flask](#lab1-creating-a-hello-world-rest-api-with-python--flask)
2. [Lab2: CRUD Operations with Python & Flask](#lab2-crud-operations-with-python--flask)
3. [Lab3: Creating Swagger Documentation for REST API](#lab3-creating-swagger-documentation-for-rest-api)
4. [Lab4: Querying with GraphQL](#lab4-querying-with-graphql)
5. [Lab5: Deploying Your First Docker Image on Code Engine](#lab5-deploying-your-first-docker-image-on-code-engine)
6. [Lab6: Deploy, Update, and Scale Microservices using Serverless](#lab6-deploy-update-and-scale-microservices-using-serverless)
7. [Final Project: Microservices Based Serverless Application](#final-project-microservices-based-serverless-application)

## Lab1: Creating a HELLO WORLD REST API with Python & Flask

### Description

In this lab, I created my first REST API Hello World application using Flask. Flask is a lightweight WSGI web application framework in Python. It's designed with simplicity in mind, making it easy to create simple web applications quickly.

### Learning Objectives

After completing this lab:
- I am able to create a simple web application using Flask.
- I am able to access the REST API endpoints of my application through the browser.

### Steps to Complete the Lab

1. Set up a Flask server.
2. Create a simple "Hello World" REST API.
3. Access the REST API endpoints through the browser.

For detailed steps, refer to the [Lab1 README](Labs/lab1/README.md).

## Lab2: CRUD Operations with Python & Flask

### Description

In this lab, I created a product list using a Flask server. The application allows you to add a product, retrieve all products, retrieve a specific product by its ID, update a specific product by its ID, and delete a product by its ID. All these operations are achieved through REST API endpoints in the Flask server.

### Learning Objectives

After completing this lab, I am able to:
- Create API endpoints to perform Create, Retrieve, Update, and Delete operations on transient data with a Flask server.
- Create REST API endpoints and use POSTMAN to test the REST APIs.

### Steps to Complete the Lab

1. Set up the application.
2. Understand the server application.
3. Run and test the server with cURL.
4. Test the REST API endpoints with POSTMAN.

For detailed steps, refer to the [Lab2 README](Labs/lab2/README.md).

## Lab3: Creating Swagger Documentation for REST API

### Description

In this lab, I learned how to create Swagger documentation for REST APIs. Swagger is an open-source tool that helps design, build, document, and consume REST APIs. This lab covers using the Swagger Editor to create documentation, accessing REST API endpoints using SwaggerUI, and generating server code with Swagger documentation.

### Learning Objectives

After completing this lab, I am able to:
- Use the Swagger Editor to create Swagger documentation for REST APIs.
- Use SwaggerUI to access REST API endpoints of an application.
- Generate server code with Swagger documentation.

### Steps to Complete the Lab

1. Get your application started.
2. Create Swagger documentation.
3. Set up the server.
4. Build and run the server.
5. Update the API response.

For detailed steps, refer to the [Lab3 README](Labs/lab3/README.md).

## Lab4: Querying with GraphQL

### Description

In this lab, I learned how to use GraphQL to query APIs served through a GraphQL service running on a server using Postman. GraphQL is a query language for APIs and a runtime for executing those queries by providing a complete and understandable description of the data in an API.

### Learning Objectives

After completing this lab, I am able to:
- Use GraphQL with Postman to access a GraphQL Service.
- Structure queries to access APIs to get selective information that I need.

### Steps to Complete the Lab

1. Sign-up for Postman.
2. Run a GraphQL service.
3. Run GraphQL queries on Postman.

For detailed steps, refer to the [Lab4 README](Lab4/README.md).

## Lab5: Deploying Your First Docker Image on Code Engine

### Description

In this lab, I learned how to deploy a "Hello World" web application from GitHub on IBM Cloud Code Engine. IBM Cloud Code Engine has been made available to me through this lab environment.

### Learning Objectives

After completing this lab, I am able to:
- Start the Code Engine service to create applications.
- Use the Code Engine service to deploy an application from a Docker image and create a remote access URL for the application.
- List the applications I have deployed.

### Steps to Complete the Lab

1. Set up Code Engine CLI.
2. Deploy the Docker image.
3. Access the application.
4. Practice exercise.

For detailed steps, refer to the [Lab5 README](Lab5/README.md).

## Lab6: Deploy, Update, and Scale Microservices using Serverless

### Description

In this lab, I learned how to create a UK University information application composed of two microservices on IBM Cloud Code Engine, and how to scale and update each microservice independently of the other.

### Learning Objectives

After completing this lab, I am able to:
- Start Code Engine service to create an application.
- Use the Code Engine service to deploy two microservices that are part of an application.
- Scale one of the microservices to have more than one instance.
- Update one of the microservices without having to stop and redeploy it.

### Steps to Complete the Lab

1. Deploy the backend microservices.
2. Deploy the frontend microservice.
3. Verify the application.

For detailed steps, refer to the [Lab6 README](Lab6/README.md).

## Final Project: Microservices Based Serverless Application

### Description

In this final project, I deployed multiple microservices to create an integrated application. These components consist of two backend microservices, one developed in Python and the other in Node.js, complemented by a front-end microservice.

### Objectives

After completing this project, I am able to:
- Create an application consisting of multiple microservices.
- Deploy Python and Node.js microservices on IBM Cloud Code Engine.
- Deploy the frontend microservice on IBM Cloud Code Engine.

### Steps to Complete the Project

1. Deploy the backend microservices.
2. Deploy the frontend microservice.
3. Verify the application.

For detailed steps, refer to the [Final Project README](Final_Project/README.md).

## Conclusion

This repository showcases my journey through learning and applying various technologies for microservices and cloud application development. Each lab and the final project demonstrate my understanding and skills in using tools like Flask, Docker, Swagger, GraphQL, and IBM Cloud Code Engine to build and deploy robust microservice-based applications.
