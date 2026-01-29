# Assignment No. 4 – API Testing with Postman

## Overview

This repository contains the solution for Assignment No. 4 – API Testing using Postman. The project demonstrates structured API testing with the **Simple Books API**, covering authentication, CRUD operations, variable handling, automated assertions, dynamic request data generation, and API chaining.

The assignment aims to develop practical skills in API workflows and Postman automation.

---

## API Details

**Base URL:**

```
https://simple-books-api.glitch.me
```

**Endpoints Used:**

| HTTP Method | Endpoint          | Description                        |
| ----------- | ----------------- | ---------------------------------- |
| POST        | /api-clients      | Generate access token              |
| GET         | /books            | Retrieve all books                 |
| POST        | /orders           | Create a new order                 |
| PUT         | /orders/{orderId} | Update an existing order           |
| PATCH       | /orders/{orderId} | Partially update an existing order |
| DELETE      | /orders/{orderId} | Delete an order                    |

---

## Features Implemented

* Base URL as a Postman collection variable
* Token-based authentication with dynamic environment variable storage
* Random request body generation for customer names
* Parsing and logging JSON responses
* Chai.js assertions, including a failing test example
* Pre-request and test scripts for variable handling
* API chaining using response variables (token and orderId)

---

## Postman Collection Variables

| Variable Name  | Purpose                                      |
| -------------- | -------------------------------------------- |
| `baseUrl`      | Base URL of the API                          |
| `token`        | Access token generated via `/api-clients`    |
| `orderId`      | Order ID generated during POST request       |
| `customerName` | Randomly generated customer name for testing |

---

## Workflow

Requests must be executed in the following order for proper API chaining:

1. Generate Token (`POST /api-clients`)
2. Get All Books (`GET /books`)
3. Create Order (`POST /orders`)
4. Update Order (`PUT /orders/{orderId}`)
5. Partial Update Order (`PATCH /orders/{orderId}`)
6. Delete Order (`DELETE /orders/{orderId}`)

---

## Running the Project

1. Clone or download the repository:

```bash
git clone <your-github-repo-link>
```

2. Open Postman and import the `Postman_Collection.json` file.

3. Ensure environment variables are set correctly:

* `baseUrl` → `https://simple-books-api.glitch.me`
* `token` → leave empty (generated automatically)
* `orderId` → leave empty

4. Execute requests in the order defined in **Workflow**.

---

## Sample Test Scripts

**Status Code Assertion:**

```javascript
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
```

**Random Data Generation:**

```javascript
let randomName = "User_" + Math.floor(Math.random() * 1000);
pm.environment.set("customerName", randomName);
```

**API Chaining Example:**

```javascript
pm.environment.set("orderId", pm.response.json().orderId);
```

---

## Conclusion

This project demonstrates professional API testing using Postman, including authentication, CRUD operations, dynamic testing, assertions, and API chaining. The structured approach provides practical knowledge for REST API testing.

---

## Author

**Muhammad Hassaan**
(QA Intern - 10Pearls)
