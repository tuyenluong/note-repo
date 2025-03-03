---
Creation_date: 2025-03-01 22:37
Modification_date: Saturday 1st March 2025 22:38:02
Indexes:
  - "[[spring]]"
  - "[[to_do_notes]]"
---

----
**Spring JDBC** simplifies the use of JDBC and helps avoid common errors. It takes care of core JDBC workflows, allowing developers to focus on writing SQL and processing results. This is achieved using **JDBC templates**, which are provided by Spring and can be used directly in applications.
#### **Maven Dependency for Spring JDBC**

To use Spring JDBC templates in a Spring or Spring Boot project, add the following Maven dependency:
```xml
<dependency>  
    <groupId>org.springframework.boot</groupId>  
    <artifactId>spring-boot-starter-jdbc</artifactId>  
</dependency>
```
#### **Key Spring JDBC Templates**

Spring provides multiple templates for JDBC-related operations. The most commonly used ones are:
1. **`JdbcTemplate`**
    - This is the most widely used Spring JDBC approach.
    - It provides the "lowest-level" JDBC abstraction.
    - Other JDBC templates, like `NamedParameterJdbcTemplate`, are built on top of `JdbcTemplate`.
2. **`NamedParameterJdbcTemplate`**
    - A wrapper around `JdbcTemplate` that supports **named parameters** instead of positional `?` placeholders.
    - Improves code readability and maintainability, especially for queries with multiple parameters.

| Action                                                  | Handled by Spring JDBC | Handled by Developer |
| ------------------------------------------------------- | ---------------------- | -------------------- |
| Define connection parameters                            |                        | X                    |
| Open the connection                                     | X                      |                      |
| Specify the SQL statment                                |                        | X                    |
| Declare parameters and provide parameters               |                        | X                    |
| Prepare and run the statement                           | X                      |                      |
| Set up the loop to iterate through the results          | X                      |                      |
| Do the work for each iteration                          |                        | X                    |
| Process any exception                                   | X                      |                      |
| Handle transactions                                     | X                      |                      |
| Close the connection, the statement, and the result set | X                      |                      |
n










---
## Flash cards section
