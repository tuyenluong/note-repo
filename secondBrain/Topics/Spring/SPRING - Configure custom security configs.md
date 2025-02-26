---
Creation_date: 2025-01-28 17:24
Modification_date: Tuesday 28th January 2025 17:24:41
Indexes:
  - "[[spring_security]]"
  - "[[to_do_notes]]"
---

----

- `permitAll()` can be used to allow access w/o security for **all users**
- `denyAll()` can be used to restrict access to a resource or endpoint for **all users**
- `authenticated()` can be used to protect a web page or API

In common scenarios, most projects often used React or Angular as their front-end. 

When those FE project make a POST or PUT call to our Spring Boot BE project, it tend to stopped with 403 error due to [[COMMON - What is CSRF|CSRF]] protection in our default Spring Security. 

But if we used Thymeleaf in a Spring MVC project then this was not the issue because Thymeleaf is also part of the Spring ecosystem, therefore Thymeleaf automatically resolved the [[COMMON - What is CSRF|CRSF issue]]

- We can also disable the `CRSF` with this line `http.csrf(AbstractHttpConfigurer:\:disable)`
- Reference in Udemy lesson 117














---
## Flash cards section
