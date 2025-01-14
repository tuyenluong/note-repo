---
Creation_date: 2025-01-14 21:06
Modification_date: Tuesday 14th January 2025 21:06:34
Indexes:
  - "[[spring_boot]]"
---

----

Bean Validation is the standard for implementing validations in the Java ecosystem. It's well integrated with Spring and Spring Boot.

Below is the Maven dependency that we can add to implement Bean validations in any Spring or Spring Boot project.

```xml
<dependency>  
    <groupId>org.springframework.boot</groupId>  
    <artifactId>spring-boot-starter-validation</artifactId>  
</dependency>
```

- Bean Validation works by defining constrains to the fields of a class by annotating them with certain annotation.
- We can put the @Valid annotation on method parameters and and fields to tell Spring that we want a method parameter or field to be validated.
- Below are the important packages where validations related annotations can be identified:
```java
jakarta.validation.constraints.*
org.hibernate.validation.constraints.*
```
















---
## Flash cards section
