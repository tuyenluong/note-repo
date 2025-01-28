---
Creation_date: 2024-03-03 12:01
Modification_date: Monday 18th March 2024 20:31:39
Indexes: "[[api]]"
---

1.  What is an API and how does it work?
	1. Follow-up question: What are some examples of APIs that you have used or interacted with?
	2. Answer: An API is an interface that allows different applications to communicate and exchange data. Some examples of APIs are:
		1. Google Maps API, which allows developers to embed maps, geocoding, directions, and other features into their websites or apps.
		2. Twitter API, which allows developers to access and manipulate tweets, users, trends, and other data from Twitter.
		3. Stripe API, which allows developers to integrate online payment processing and billing services into their websites or apps.
2. What are the different types of API testing and what are their objectives?
	1. Follow-up question: How do you decide which type of API testing to use for a given scenario?
	2. Answer: Some of the different types of API testing are:
		1. Functional testing, which verifies that the API works as expected and meets the business requirements.
		2. Performance testing, which measures the speed, scalability, reliability, and resource consumption of the API under different load conditions.
		3. Security testing, which checks the API for any vulnerabilities, such as unauthorized access, data leakage, injection attacks, etc.
		4. Integration testing, which validates the compatibility and interoperability of the API with other APIs or systems.
		5. Contract testing, which ensures that the API conforms to the predefined specifications or contracts that define its inputs and outputs.
		6. The type of API testing to use depends on the scope, purpose, and complexity of the API. For example, functional testing is essential for any API, but performance testing may be more important for an API that handles high-volume transactions or real-time data. Security testing may be more critical for an API that deals with sensitive or personal information. Integration testing may be more relevant for an API that interacts with multiple external services. Contract testing may be more useful for an API that follows a standard or a protocol.
3. How do you design, execute, and report API test cases?
    1. Follow-up question: What are some best practices or guidelines for API test case design, execution, and reporting?
    2. Answer: Some of the best practices or guidelines for API test case design, execution, and reporting are:
        1. Design test cases that cover the positive, negative, and edge scenarios of the API functionality, performance, security, and integration.
        2. Use a consistent and descriptive naming convention for the test cases, such as [API name]_[test type]_[test scenario].
        3. Use a test management tool or a framework that supports API testing, such as TestNG, JUnit, PyTest, etc.
        4. Use an API testing tool or a library that simplifies the API request and response handling, such as Postman, RestAssured, Requests, etc.
        5. Use assertions or validations to verify the expected API response data and status codes.
        6. Use parameters or data-driven testing to run the same test case with different input values or data sets.
        7. Use mock services or stubs to simulate the dependent APIs or systems that are not available or accessible during the testing.
        8. Use logging or reporting tools to capture and document the test results, errors, and metrics of the API testing.
4. How do you perform API testing with Postman or other similar tools?
    1. Follow-up question: How do you use Postman collections and environments to organize and manage your API testing?
    2. Answer: Postman is a popular tool for API testing that allows users to create, send, and analyze API requests and responses. Postman collections are groups of related API requests that can be saved, shared, and executed as a single unit. Postman environments are sets of variables that can be used to store and switch between different values for the API requests, such as base URLs, authentication tokens, parameters, etc. To use Postman collections and environments to organize and manage your API testing, you can follow these steps:
        1. Create a Postman collection for each API or feature that you want to test. You can add folders within the collection to group similar requests or scenarios.
        2. Add the API requests to the collection with the appropriate HTTP methods, headers, body, parameters, etc. You can use variables in the request URL or body to make them dynamic and reusable.
        3. Add tests or assertions to each request using the Postman test scripts feature. You can use JavaScript code to validate the response data and status codes using the built-in Chai assertion library.
        4. Create a Postman environment for each testing stage or context that you want to test. You can add variables to the environment with their corresponding values for each stage or context. For example, you can have an environment for development, testing, production, etc.
        5. Select the appropriate environment from the Postman environment dropdown menu before sending the requests. You can also use the Postman environment quick look feature to view or edit the variables in the current environment.
        6. Run the requests individually or as a collection using the Postman runner feature. You can also use parameters or data files to run the same request or collection with different values. You can view the test results and metrics in the Postman runner window.
5. What are some common API testing methods such as REST, SOAP, GraphQL, etc. and what are their differences and advantages?
    1. Follow-up question: How do you compare and contrast REST and SOAP as two of the most widely used API testing methods?
    2. Answer: REST and SOAP are two different approaches to implement and test web services or APIs. Some of the differences and advantages of REST and SOAP are:
        1. REST stands for Representational State Transfer, while SOAP stands for Simple Object Access Protocol.
        2. REST is based on the HTTP protocol and uses different HTTP methods (such as GET, POST, PUT, DELETE, etc.) to perform different operations on the resources or data. SOAP is based on the XML protocol and uses a single HTTP method (POST) to send and receive XML messages that contain the operations and data.
        3. REST is more flexible and lightweight than SOAP, as it does not have any predefined rules or standards for the message format, structure, or content. SOAP is more rigid and complex than REST, as it follows a strict specification for the message envelope, header, body, and fault elements.
        4. REST is more suitable for stateless or cacheable web services that deal with simple or dynamic data. SOAP is more suitable for stateful or transactional web services that deal with complex or static data.
        5. REST supports multiple data formats (such as JSON, XML, HTML, etc.), while SOAP only supports XML data format.
        6. REST is easier to test and debug than SOAP, as it uses plain HTTP requests and responses that can be easily inspected and manipulated using tools like Postman, curl, etc. SOAP is harder to test and debug than SOAP, as it uses XML messages that require special tools or libraries to parse and validate.
6. How do you validate the API response data and status codes?
    1. Follow-up question: What are some common API response status codes and what do they mean?
    2. Answer: API response status codes are numerical codes that indicate the outcome of the API request. They are divided into five categories based on the first digit of the code:
        1. 1xx: Informational codes that indicate that the request has been received and is being processed.
        2. 2xx: Success codes that indicate that the request has been successfully completed and the response contains the expected data.
        3. 3xx: Redirection codes that indicate that the request has been redirected to another URL or resource.
        4. 4xx: Client error codes that indicate that the request has failed due to some error on the client side, such as invalid parameters, unauthorized access, not found resource, etc.
        5. 5xx: Server error codes that indicate that the request has failed due to some error on the server side, such as internal server error, service unavailable, gateway timeout, etc. 
        6. Some of the common API response status codes are:
            1. 200 OK: The request has succeeded and the response contains the requested data.
            2. 201 Created: The request has created a new resource and the response contains the location of the new resource.
            3. 204 No Content: The request has succeeded but there is no data to return in the response.
            4. 301 Moved Permanently: The requested resource has been permanently moved to a new URL and the response contains the new URL.
            5. 302 Found: The requested resource has been temporarily moved to a new URL and the response contains the new URL.
            6. 304 Not Modified: The requested resource has not been modified since the last request and there is no need to return it in the response.
            7. 400 Bad Request: The request is invalid or malformed and cannot be processed by the server.
            8. 401 Unauthorized: The request requires authentication but the client has not provided valid credentials or tokens.
            9. 403 Forbidden: The request is valid but the client does not have permission to access or modify the requested resource.
            10. 404 Not Found: The requested resource does not exist on the server or cannot be found by the server.
            11. 405 Method Not Allowed: The request method is not supported by the requested resource or endpoint.
            12. 500 Internal Server Error: The server encountered an unexpected error while processing the request and cannot return a meaningful response.
            13. 503 Service Unavailable: The server is temporarily unable to handle the request due to overload or maintenance.
7. How do you handle authentication, authorization, and security issues in API testing?
    1. Follow-up question: What are some common authentication and authorization mechanisms or protocols that are used in API testing?
    2. Answer: Authentication and authorization are two related but distinct concepts that deal with the identity and access control of the API users or clients. Authentication is the process of verifying the identity of the user or client, while authorization is the process of granting or denying the access or permissions to the user or client based on their identity or role. Some of the common authentication and authorization mechanisms or protocols that are used in API testing are:
        1. Basic authentication, which uses a username and password combination to authenticate the user or client. The username and password are encoded in base64 and sent as a header in the API request.
        2. Token-based authentication, which uses a token (such as a JSON Web Token or JWT) to authenticate the user or client. The token is generated by the server after validating the user or client credentials and contains information such as the user or client identity, role, expiration time, etc. The token is sent as a header or a parameter in the API request.
        3. OAuth (Open Authorization), which is a protocol that allows the user or client to authorize a third-party application to access their data or resources from another service provider without sharing their credentials. The user or client grants permission to the third-party application by obtaining an access token from the service provider. The access token is sent as a header or a parameter in the API request.
        4. API key, which is a unique identifier that is assigned to the user or client by the API provider. The API key is used to track and control the usage and access of the API by the user or client. The API key is sent as a header or a parameter in the API request.
        5. To handle authentication, authorization, and security issues in API testing, you need to:
            1. Understand the authentication and authorization mechanism or protocol that is used by the API and how it works.
            2. Obtain the valid credentials, tokens, keys, etc. that are required to access or test the API.
            3. Include the appropriate headers, parameters, etc. that contain the authentication and authorization information in the API request.
            4. Verify that the API response contains the expected data and status codes based on the authentication and authorization information.
            5.  Test for any security vulnerabilities, such as unauthorized access, data leakage, injection attacks, etc. by using invalid, expired, tampered, or malicious credentials, tokens, keys, etc.

