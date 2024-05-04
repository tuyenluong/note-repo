---
Creation_date: 2024-05-03 04:14
Modification_date: Friday 3rd May 2024 04:14:34
Indexes: "[[api]]"
---


----
When making API requests, verifying the response code is a crucial step in determining whether the request was successful and how to handle the outcome. **The HTTP response codes are standardized, providing a consistent way to interpret the results of a request.**
### Common HTTP Response Codes

- **200 OK**: The request has succeeded. The meaning of the success depends on the HTTP method:
    - GET: The resource has been fetched and is transmitted in the message body.
    - POST: The resource describing the result of the action is transmitted in the message body.
    - PUT or PATCH: The resource describing the result of the action may be transmitted in the message body.
    - DELETE: The resource might be gone. The response body should be empty.
- **201 Created**: The request has succeeded and a new resource has been created as a result. This is typically the response sent after POST requests, or some PUT requests.
    
- **204 No Content**: The server has successfully fulfilled the request and there is no additional content to send in the response payload body.
    
- **400 Bad Request**: The server could not understand the request due to invalid syntax.
    
- **401 Unauthorized**: The request has not been applied because it lacks valid authentication credentials for the target resource.
    
- **403 Forbidden**: The server understood the request but refuses to authorize it.
    
- **404 Not Found**: The server can't find the requested resource. This is often used when the server does not wish to reveal exactly why the request has been refused, or when no other response is applicable.
    
- **500 Internal Server Error**: The server has encountered a situation it doesn't know how to handle.






---
## Flash cards section
