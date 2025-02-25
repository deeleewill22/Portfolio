# API Documentation

## Description

Comprehensive guide detailing how to effectively use and integrate an Application Programming Interface (API). This includes information on endpoints, methods, parameters, and authentication.

## Table of Contents

1. Introduction
2. Authentication
3. Endpoints
4. Methods
5. Parameters
6. Examples
7. Error Handling
8. FAQs

## Introduction

#### What is an API? APIs (Application Programming Interfaces) allow applications to communicate, enabling features like data retrieval, updates, and automation.

Example: A weather app uses an API to fetch real-time weather data from a weather service, such as
``` https://api.weather.com/v1/today?city=Austin. ```

### Types of APIs

1. REST APIs (Representational State Transfer): Uses HTTP methods for communication, such as GET, POST, PUT, and DELETE.
2. SOAP APIs (Simple Object Access Protocol): Uses XML-based messages and specific formatting rules for more rigid data structure.
3. GraphQL: Allows clients to request only the data they need, rather than a fixed response.

Examples:
1. REST API: ```GET https://api.example.com/v1/products``` retrieves a list of products.
2. SOAP API: A SOAP request to a currency exchange API to get conversion rates.
3. GraphQL: A client might query ```https://api.example.com/graphql``` for only the product names and prices, reducing data transfer.

## Authentication

API Keys and Tokens: These are unique identifiers for authenticated access to the API.

Example: API key ```abc123-key``` is provided as a query parameter (```?api_key=abc123-key```) or in the headers (```Authorization: abc123-key```).

### Types of Authentication:

1. Bearer Token: Requires a token that is passed in the request headers.

Example: ```Authorization: Bearer abc1234-token``` sends the token in the request headers for secure access.

2. OAuth: Uses an access token exchange process that grants access for specific scopes, often used for third-party applications.

Example: A user grants access to their Google Calendar through OAuth, and the API returns an access token.

### Managing API Tokens: Tokens should be stored securely and refreshed periodically.

Example: Use environment variables (```process.env.API_TOKEN```) in your application to avoid hardcoding tokens directly in the codebase.

### Endpoints

Understanding Endpoints: Endpoints specify the resource or action available at a particular URL.

Example: ```https://api.example.com/v1/users``` could retrieve or manage user data.

### Common HTTP Methods:
1. GET: Retrieves data without changing the server state.

Example: ```GET /products``` fetches a list of all products.

2. POST: Submits data to create a new resource.

Example: ```POST /products``` with data like ```{"name": "New Product", "price": 19.99}``` to create a new product.

3. PUT: Updates an existing resource.

Example: ```PUT /products/123``` with data like ```{"price": 29.99}``` to update the price of the product with ID 123.

4. DELETE: Removes a resource.

Example: ```DELETE /products/123``` deletes the product with ID 123.

## API Request Structure

Headers: Headers provide additional context or information about the request.
Example:
1. Authorization: Bearer abc1234-token for secure access.
2. Content-Type: application/json to specify the data format.
3. Body: Contains the data you’re sending to the server, typically in JSON format.

Example: To create a new user, the request might look like:

```{"username": "new_user", "email": "new_user@example.com","password": "password123"}```

## Using Tokens with Endpoints
* Purpose of Tokens: Tokens allow secure, authenticated access to specific API functions and limit unauthorized use.

Example: A user logs in and receives a token for their session, used in all API requests while the session is active.

* Token-Based Authentication: A token is passed in the header of each request.

Example: For a request to ```GET /account-info```, you’d include ```Authorization: Bearer abc1234-token``` in the headers.

* Refreshing Tokens: Tokens may expire after a set period, requiring a refresh.
* 
Example: ```POST /auth/refresh-token``` endpoint takes the expired token as input and provides a new token in the response.

Request:
{```"refresh_token": "expired123token"```}

Response:
{```"new_token": "new_token_456"```}


## Examples API Calls
### GET Request to Retrieve Data

Endpoint: ```GET /users```

```
GET /users HTTP/1.1
Host: api.example.com
Authorization: Bearer abc1234-token
```

Response:
```
[
  {"id": 1, "name": "Alice"},
  {"id": 2, "name": "Bob"}
]
```
### POST Request to Submit Data

Endpoint: ```POST /products```

```
POST /products HTTP/1.1
Host: api.example.com
Authorization: Bearer abc1234-token
Content-Type: application/json
```
Body
```
{
  "name": "Smartphone",
  "price": 599.99,
  "category": "Electronics"
}
```

Response:
```
{
"id": 101,
  "name": "Smartphone",
  "price": 599.99,
  "category": "Electronics"
}
```

## Error Handling and Responses
### Common Error Codes:

1. 400 Bad Request: The server cannot process the request due to client error. If the API expects ```{"name": "product"}```, but ```{price: 29.99}``` is sent, it might return a 400 error.
2. 401 Unauthorized: Authentication token is missing or invalid. For example, if the token is incorrect or expired, the API will return a 401 error.
3. 403 Forbidden: The user lacks permissions for the requested action.

Example response for 401 Unauthorized:

```
{
  "status": "error",
  "message": "Unauthorized access - token invalid or expired."
}
```

## Best Practices for API Security

1. Token Management: Rotate tokens periodically, especially for sensitive data. For instance, tokens can be set to expire every 24 hours and implement a refresh system.

2. Rate Limiting: Adhere to usage limits to prevent service interruptions and avoid throttling. If the rate limit is 100 requests/minute, a looped script might have a cooldown period to stay under the threshold.

## FAQs

Q: "What should I do if my token expires?"
A: Request a new token via the ```/auth/refresh-token``` endpoint.

Q: "How do I manage multiple API requests?"
A: Use asynchronous functions or batch requests to handle high volumes efficiently.


[Back to Portfolio](../README.md)
