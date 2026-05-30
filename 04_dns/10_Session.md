# HTTP Status Codes - Study Notes

## Index

1. [Introduction to HTTP Status Codes](#introduction-to-http-status-codes)
2. [HTTP Methods](#http-methods)
3. [1XX - Informational Responses](#1xx---informational-responses)
4. [2XX - Success Responses](#2xx---success-responses)
5. [3XX - Redirection Responses](#3xx---redirection-responses)
6. [4XX - Client Error Responses](#4xx---client-error-responses)
7. [5XX - Server Error Responses](#5xx---server-error-responses)
8. [Examples](#examples)
9. [Interview Questions](#interview-questions)
10. [Quick Revision Table](#quick-revision-table)

---

# Introduction to HTTP Status Codes

HTTP Status Codes are standard response codes returned by a web server to indicate the result of a client's request.

Example API Endpoint:

```text
http://daws88s.online/api/transaction
```

When a client (browser, mobile app, Postman, etc.) sends a request to a server, the server responds with:

* Response Body (data)
* HTTP Status Code

Example:

```http
GET /api/transaction

HTTP/1.1 200 OK
```

The status code tells us whether the request succeeded, failed, or requires further action.

---

# HTTP Methods

## GET

Used to retrieve data from the server.

Example:

```http
GET /api/transaction
```

Response:

```http
200 OK
```

---

## POST

Used to create new data on the server.

Example:

```http
POST /api/transaction
```

Response:

```http
201 Created
```

---

# 1XX - Informational Responses

These status codes indicate that the request has been received and processing continues.

### 100 Continue

Meaning:

* The initial part of the request has been received.
* Client can continue sending the remaining request body.

Example:

```http
100 Continue
```

### Protocol Switching

Example:

```http
101 Switching Protocols
```

Used when changing protocols, such as:

* HTTP → HTTPS
* HTTP → WebSocket

---

# 2XX - Success Responses

The request was successfully received, understood, and processed.

## 200 OK

Meaning:

* Request succeeded.
* Most common success status.

Example:

```http
GET /api/transaction

200 OK
```

---

## 201 Created

Meaning:

* A new resource was successfully created.

Example:

```http
POST /api/transaction

201 Created
```

---

## 204 No Content

Meaning:

* Request succeeded.
* No response body returned.

Commonly used after delete operations.

Example:

```http
DELETE /api/transaction/10

204 No Content
```

---

# 3XX - Redirection Responses

The client must take additional action to complete the request.

## 301 Moved Permanently

Meaning:

* Resource URL has permanently changed.
* Search engines update stored URLs.

Example:

```http
301 Moved Permanently
```

Old URL:

```text
http://example.com
```

New URL:

```text
https://example.com
```

---

## 302 Found (Temporary Redirect)

Meaning:

* Resource temporarily available at another location.
* Original URL may be used again later.

Example:

```http
302 Found
```

---

## 304 Not Modified

Meaning:

* Browser cache already contains the latest version.
* Server tells browser to use cached copy.

Benefits:

* Faster loading
* Reduced network traffic

Example:

```http
304 Not Modified
```

---

# 4XX - Client Error Responses

Errors caused by the client.

## 400 Bad Request

Meaning:

* Invalid request format.
* Invalid JSON.
* Missing required fields.

Example Request:

```json
{
  "amountt": 200,
  "description": ""
}
```

Possible issue:

```json
{
  "amount": 200,
  "description": ""
}
```

Field name is incorrect (`amountt` instead of `amount`).

Response:

```http
400 Bad Request
```

---

## 401 Unauthorized

Meaning:

* Authentication is required.
* User has not provided valid credentials.

Example:

```http
401 Unauthorized
```

Examples:

* Missing token
* Invalid JWT token
* Expired login session

---

## 403 Forbidden

Meaning:

* User is authenticated.
* User does not have permission.

Example:

```text
https://emacet.ap.gov.in/api/results/2026/
```

Accessible only by government administrators.

Normal user trying to access:

```http
403 Forbidden
```

---

## 404 Not Found

Meaning:

* Requested resource does not exist.

Example:

```text
https://emacet.ap.gov.in/api/results/2026/1234567
```

If hall ticket number does not exist:

```http
404 Not Found
```

---

# 5XX - Server Error Responses

Errors caused by the server.

## 500 Internal Server Error

Meaning:

* Unexpected server failure.
* Bug in application code.
* Database issues.

Example:

```http
500 Internal Server Error
```

---

## 503 Service Unavailable

Meaning:

* Server is temporarily unavailable.
* Maintenance mode.
* Server overloaded.

Example:

```http
503 Service Unavailable
```

Common Reasons:

* Too many users
* Deployment in progress
* Server maintenance

---

# Examples

## Successful Request

```http
GET /api/transaction

Response:
200 OK
```

---

## Create Transaction

```http
POST /api/transaction

Response:
201 Created
```

---

## Invalid JSON

```json
{
  "amountt": 500
}
```

Response:

```http
400 Bad Request
```

---

## Missing Login

```http
GET /api/profile

Response:
401 Unauthorized
```

---

## No Permission

```http
GET /admin/users

Response:
403 Forbidden
```

---

## Invalid URL

```http
GET /products/999999

Response:
404 Not Found
```

---

## Server Crash

```http
500 Internal Server Error
```

---

# Interview Questions

### Q1. Difference between 401 and 403?

**401 Unauthorized**

* User is not authenticated.

**403 Forbidden**

* User is authenticated but lacks permission.

Example:

* Not logged in → 401
* Logged in as normal user trying admin page → 403

---

### Q2. Difference between 200 and 201?

**200 OK**

* Resource fetched successfully.

**201 Created**

* New resource created successfully.

---

### Q3. Why is 304 useful?

* Reduces bandwidth usage.
* Improves performance.
* Uses browser cache efficiently.

---

### Q4. What status code is commonly returned after DELETE?

```http
204 No Content
```

---

# Quick Revision Table

| Status Code | Meaning               |
| ----------- | --------------------- |
| 100         | Continue              |
| 200         | OK                    |
| 201         | Created               |
| 204         | No Content            |
| 301         | Moved Permanently     |
| 302         | Temporary Redirect    |
| 304         | Not Modified          |
| 400         | Bad Request           |
| 401         | Unauthorized          |
| 403         | Forbidden             |
| 404         | Not Found             |
| 500         | Internal Server Error |
| 503         | Service Unavailable   |

---

## Memory Trick

### 2XX → Success

"Everything is OK"

### 3XX → Redirect

"Go somewhere else"

### 4XX → Client Error

"You made a mistake"

### 5XX → Server Error

"Server made a mistake"

---

**Summary:**

* 1XX → Information
* 2XX → Success
* 3XX → Redirection
* 4XX → Client Errors
* 5XX → Server Errors

These are the most frequently used HTTP status codes in REST APIs, web applications, Postman testing, and backend development.
