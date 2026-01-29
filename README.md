# API-Testing-Simple-Books

Overview

This repository contains the complete solution for Assignment No. 4 – API Testing with Postman. The project demonstrates structured API testing using the Simple Books API. It covers all aspects of REST API testing, including authentication, CRUD operations, variable handling, automated assertions, dynamic request data generation, and API chaining.

The purpose of this assignment is to develop a comprehensive understanding of API workflows and Postman automation capabilities, which are critical skills for modern software testing.

API Details

Base URL:

https://simple-books-api.glitch.me


Endpoints Used:

Method	Endpoint	Description
POST	/api-clients	Generate access token
GET	/books	Retrieve all books
POST	/orders	Create a new order
PUT	/orders/{orderId}	Update an existing order
PATCH	/orders/{orderId}	Partially update an existing order
DELETE	/orders/{orderId}	Delete an order
Features Implemented

Base URL configured as a Postman collection variable

Token-based authentication with dynamic storage in environment variables

Random request body generation for customer names

Parsing and logging JSON responses

Comprehensive Chai.js assertions, including a failing test example

Pre-request and test scripts for variable handling

API chaining using response variables (token and orderId)

Postman Collection Variables
Variable Name	Purpose
baseUrl	Base URL of the API
token	Access token generated via /api-clients
orderId	Order ID generated during POST request
customerName	Randomly generated customer name for testing
Workflow

To maintain proper dependencies and API chaining, the requests must be executed in the following sequence:

Generate Token (POST /api-clients)

Get All Books (GET /books)

Create Order (POST /orders)

Update Order (PUT /orders/{orderId})

Partial Update Order (PATCH /orders/{orderId})

Delete Order (DELETE /orders/{orderId})

This workflow demonstrates sequential dependency, token usage, and dynamic data handling.

Running the Project

Clone or download the repository:

git clone <your-github-repo-link>


Open Postman and import the Postman_Collection.json file.

Ensure environment variables are configured correctly:

baseUrl → https://simple-books-api.glitch.me

token → empty (will be generated)

orderId → empty

Execute requests in the sequence defined under Workflow.

Sample Test Scripts

Status Code Assertion:

pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});


Random Data Generation:

let randomName = "User_" + Math.floor(Math.random() * 1000);
pm.environment.set("customerName", randomName);


API Chaining Example:

pm.environment.set("orderId", pm.response.json().orderId);

Conclusion

This project demonstrates professional API testing using Postman. It includes authentication, CRUD operations, dynamic testing, assertions, and API chaining. By completing this assignment, a structured and practical approach to REST API testing is demonstrated.
