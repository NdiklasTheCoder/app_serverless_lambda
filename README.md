# Getting Started


## Serverless 

![sta](https://miro.medium.com/max/650/1*XuR8U6TOa5ar88lf2IbNNQ.png)

Building a Serverless Lumen API with AWS Lambda and DynamoDB
AWS Lambda is a service that lets you run code without provisioning or managing servers
AWS DynamoDB is a key-value and document database that delivers single-digit millisecond performance at any scale

## Amazon S3

![s3](https://user-images.githubusercontent.com/80678596/177031215-0ad4013e-4111-4f29-a4e4-d916a9b8eec0.png)

Amazon Simple Storage Service is a cloud-based object storage service with industry-leading scalability, data availability, security, and performance. Amazon S3 is a simple web service interface that allows you to store and retrieve any amount of data from anywhere on the internet.

Customers of all sizes and industries can use it to store and protect any amount of data for a variety of use cases, including websites, mobile apps, backup and restore, archiving, enterprise applications, IoT devices, and big data analytics.

# Demo
<img width="1245" alt="Screenshot 2022-06-17 at 15 09 12" src="https://user-images.githubusercontent.com/80678596/174304587-9a1a282b-d0b5-40d2-8fc8-e26b33a1b493.png">  

# Serverless TODO

In this project I develop and deploy a simple "TODO" application using AWS Lambda and Serverless framework. This application will allow users to create/remove/update/get TODO items. Each TODO item contains the following fields: 
   - todoId (string) - a unique id for an item
   - createdAt (string) - date and time when an item was created
   -  name (string) - name of a TODO item (e.g. "Change a light bulb")
   - dueDate (string) - date and time by which an item should be completed
   - done (boolean) - true if an item was completed, false otherwise
   - attachmentUrl (string) (optional) - a URL pointing to an image attached to a TODO item

# Functions implemented

To implement this project you need to implement the following functions and configure them in the `serverless.yml` file:

* `Auth` - this function should implement a custom authorizer for API Gateway that should be added to all other functions.
* `GetTodos` - should return all TODOs for a current user. 
* `CreateTodo` - should create a new TODO for a current user. A shape of data send by a client application to this function can be found in the `CreateTodoRequest.ts` file
* `UpdateTodo` - should update a TODO item created by a current user. A shape of data send by a client application to this function can be found in the `UpdateTodoRequest.ts` file
* `DeleteTodo` - should delete a TODO item created by a current user. Expects an id of a TODO item to remove.
* `GenerateUploadUrl` - returns a presigned url that can be used to upload an attachment file for a TODO item. 

All functions are already connected to appriate events from API gateway

An id of a user can be extracted from a JWT token passed by a client

You also need to add any necessary resources to the `resources` section of the `serverless.yml` file such as DynamoDB table and and S3 bucket.


## Deploy Backend

                  cd backend

                  npm install
  
                  serverless

                  npm install --save-dev serverless-iam-roles-per-function@next 

                  serverless deploy --verbose


# Endpoints
   
  - GET - https://im1th8rr46.execute-api.us-east-2.amazonaws.com/dev/todos
  - POST - https://im1th8rr46.execute-api.us-east-2.amazonaws.com/dev/todos
  - PATCH - https://im1th8rr46.execute-api.us-east-2.amazonaws.com/dev/todos/{todoId}
  - DELETE - https://im1th8rr46.execute-api.us-east-2.amazonaws.com/dev/todos/{todoId}
  - POST - https://im1th8rr46.execute-api.us-east-2.amazonaws.com/dev/todos/{todoId}/attachment

functions:
  
# Lambda Functions

  - Auth: serverless-dev-Auth
  - GetTodos: serverless-dev-GetTodos
  - CreateTodo: serverless-dev-CreateTodo
  - UpdateTodo: serverless-dev-UpdateTodo
  - DeleteTodo: serverless-dev-DeleteTodo
  -  GenerateUploadUrl: serverless-dev-GenerateUploadUrl 
  
# Serverless 
  <img width="1438" alt="Screenshot 2022-06-17 at 14 52 03" src="https://user-images.githubusercontent.com/80678596/174301979-2bd3fe32-df87-4417-8f9c-88e7e43adbea.png">

  
  <img width="1440" alt="Screenshot 2022-06-17 at 14 50 52" src="https://user-images.githubusercontent.com/80678596/174301833-78e5a059-ad52-468b-ac52-ff371b130ed6.png">

  
# Auth0
  
 <img width="1440" alt="Screenshot 2022-06-17 at 14 53 08" src="https://user-images.githubusercontent.com/80678596/174302159-192628e6-ea03-4d56-9253-a22c349286d1.png">

  
# AWS Cloud Formation 

  <img width="1440" alt="Screenshot 2022-06-17 at 14 55 40" src="https://user-images.githubusercontent.com/80678596/174302538-4c3a2a21-321c-4a81-b143-5873c9c94c15.png">
