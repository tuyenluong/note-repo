---
Creation_date: 2024-05-03 04:14
Modification_date: Friday 3rd May 2024 04:14:34
Indexes: "[[api]]"
---

----
When making API requests, verifying the response code is a crucial step in determining whether the request was successful and how to handle the outcome. **The HTTP response codes are standardized, providing a consistent way to interpret the results of a request.**
### Common HTTP Response Codes

- **200 OK**:  
    - The request has succeeded. The meaning of the success depends on the HTTP method:
        - GET: The resource has been fetched and is transmitted in the message body.
        - POST: The resource describing the result of the action is transmitted in the message body.
        - PUT or PATCH: The resource describing the result of the action may be transmitted in the message body.
        - DELETE: The resource might be gone. The response body should be empty.
- **201 Created**: 
	- The request has succeeded and a new resource has been created as a result. This is typically the response sent after POST requests, or some PUT requests. ^4b6c36
- **204 No Content**: 
	- The server has successfully fulfilled the request and there is no additional content to send in the response payload body.
- **400 Bad Request**: 
	- The server could not understand the request due to invalid syntax.
- **401 Unauthorized**: 
	- The request has not been applied because it lacks valid authentication credentials for the target resource.
- **403 Forbidden**: 
	- The server understood the request but refuses to authorize it.
- **404 Not Found**: 
	- The server can't find the requested resource. This is often used when the server does not wish to reveal exactly why the request has been refused, or when no other response is applicable.
- **405 Method Not Allowed**
	- The request method is known by the server but is not supported by the target resource. For example, an API may not allow calling `DELETE` to remove a resource.
- **408 Request Timeout**
	- This response is sent on an idle connection by some servers, even without any previous request by the client. It means that the server would like to shut down this unused connection. This response is used much more since some browsers, like Chrome, Firefox 27+, or IE9, use HTTP pre-connection mechanisms to speed up surfing. Also note that some servers merely shut down the connection without sending this message.
- **409 Conflict:**
	- This status code indicates that the request could not be completed due to a conflict with the current state of the resource. In the context of creating a user, it means that a user with the same identifier (such as a username or email) already exists in the system, and thus, the server is unable to fulfil the request to create a new user with the same identifier.
- **414 URI Too Long**
	- The URI requested by the client is longer than the server is willing to interpret.
- **422 Un-Processable Content:**
	- Indicates that the server understands the content type of the request entity, and the syntax of the request entity is correct, but it was unable to process the contained instructions.
- **429 Too many requests**:
	- The user has sent too many requests in a given amount of time ("rate limiting").
- **500 Internal Server Error**: 
	- The server has encountered a situation it doesn't know how to handle.




---
## Flash cards section

What is the response when a resource has been fetched and is transmitted in the message body after a GET request? ;; 200 OK
<!--SR:!2024-05-06,1,230-->
What status code is indicated when the result of a POST action is transmitted in the response body? ;; 200 OK
<!--SR:!2024-05-06,1,230-->
What status code applies when the result of a PUT or PATCH action may be transmitted in the message body? ;; 200 OK
<!--SR:!2024-05-06,1,230-->
What status code should be expected when a DELETE request has been successful and the resource is likely gone with an expected empty response body? ;; 200 OK
<!--SR:!2024-05-06,1,230-->
Which status code is used when a request has successfully led to the creation of a new resource, typically following a POST or some PUT requests? ;; 201 Created
<!--SR:!2024-05-06,1,230-->
Which status code indicates that the request has been successfully fulfilled and there is no additional content to send in the response payload body? ;; 204 No Content
<!--SR:!2024-05-08,3,250-->
What status code is returned when a request cannot be understood by the server due to invalid syntax? ;; 400 Bad Request
<!--SR:!2024-05-06,1,230-->
What status code is used when a request lacks valid authentication credentials for the target resource? ;; 401 Unauthorized
<!--SR:!2024-05-06,1,230-->
What status code is returned when the server refuses to authorize a request it understands? ;; 403 Forbidden
<!--SR:!2024-05-06,1,230-->
What status code is used when the server cannot find the requested resource, particularly when no more specific message is suitable? ;; 404 Not Found
<!--SR:!2024-05-06,1,230-->
What status code should be returned when there is a generic error on the server side that prevents it from fulfilling the request? ;; 500 Internal Server Error
<!--SR:!2024-05-06,1,230-->

