---
Creation_date: 2025-01-22 00:28
Modification_date: Wednesday 22nd January 2025 00:28:41
Indexes:
  - "[[spring_core]]"
  - "[[to_do_notes]]"
---

----

In Spring Framework, a **bean scope** determines the lifecycle and visibility of a bean within the Spring IoC container. Different scopes are suited for different use cases depending on the context in which the bean is being used. Here's a detailed breakdown of all the bean scopes supported in Spring:

## Core Bean Scopes

These are the most commonly used scopes in both standalone and web applications:

| **Scope**      | **Description**                                                                     | **Default?** |
|-----------------|-------------------------------------------------------------------------------------|--------------|
| **singleton**   | A single instance of the bean is created and shared across the entire application context. | ✅ Default   |
| **prototype**   | A new instance of the bean is created each time it is requested from the container.        | ❌ No        |

## Web-Specific Scopes

These scopes are only applicable in web-aware applications:

| **Scope**       | **Description**                                                                                         |
| --------------- | ------------------------------------------------------------------------------------------------------- |
| **request**     | A new bean instance is created for each HTTP request. Scoped to the lifecycle of a single HTTP request. |
| **session**     | A single instance of the bean is created per HTTP session.                                              |
| **application** | A single instance of the bean is shared across the entire ServletContext.                               |
| **websocket**   | A single instance of the bean is created per WebSocket session.                                         |

## Usage of Scopes

- Singleton Scope (Default)
	- **Purpose**: Used for stateless beans where a single instance is shared across all requests.
```java
@Bean
@Scope("singleton")
public MyService myService() {
    return new MyService();
}
```
- Prototype Scope
	- **Purpose**: For stateful or non-thread-safe beans where each request gets a new instance.
```java
@Bean
@Scope("prototype")
public MyService myService() {
    return new MyService();
}
```
- Request Scope
	- **Purpose**: For beans that need to last only for the duration of an HTTP request.
```java
@Bean
@Scope(value = WebApplicationContext.SCOPE_REQUEST, proxyMode = ScopedProxyMode.TARGET_CLASS)
public MyService myService() {
    return new MyService();
}
```
- Session Scope
	- **Purpose**: For beans that need to persist for the duration of an HTTP session.
```java
@Bean
@Scope(value = WebApplicationContext.SCOPE_SESSION, proxyMode = ScopedProxyMode.TARGET_CLASS)
public MyService myService() {
    return new MyService();
}
```
- Application Scope
	- **Purpose**: For beans shared across the entire ServletContext in a web application.
```java
@Bean
@Scope(value = WebApplicationContext.SCOPE_APPLICATION)
public MyService myService() {
    return new MyService();
}
```
- WebSocket Scope
	- **Purpose**: For beans scoped to the lifecycle of a WebSocket session.
```java
@Bean
@Scope(value = "websocket")
public MyService myService() {
    return new MyService();
}
```

## How to Define a Scope

Scopes can be defined in two ways:

- Using Annotations:
	- At the class level or method level using the `@Scope` annotation.
```java
@Component
@Scope("prototype")
public class MyPrototypeBean { }
```
- Using XML Configuration:
	- In older Spring applications or when configuring beans in XML.
```xml
<bean id="myBean" class="com.example.MyService" scope="prototype" />
```

## Choosing the Right Scope

- **Use `singleton`** for stateless, thread-safe beans (most common).
- **Use `prototype`** when a new instance is required for each use (stateful beans).
- **Use `request`** or `session` for web applications with short-lived or session-specific data.
- **Use `application`** for data that should persist across the web application lifecycle.

By understanding and choosing the appropriate scope, you can optimize resource usage and ensure thread safety in your Spring application.














---
## Flash cards section
