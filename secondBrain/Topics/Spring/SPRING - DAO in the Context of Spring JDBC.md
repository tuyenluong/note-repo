---
Creation_date: 2025-03-04 00:25
Modification_date: Tuesday 4th March 2025 00:25:21
Indexes:
  - "[[spring_boot]]"
  - "[[to_do_notes]]"
---

----
### What is DAO Implementation?

**DAO (Data Access Object)** is a design pattern used to separate the persistence logic (database operations) from the business logic in an application. It provides an abstraction layer between the database and the application, ensuring that database access code is modular, reusable, and easier to maintain.
### DAO in the Context of Spring JDBC

Spring JDBC simplifies DAO implementation by providing template classes such as `JdbcTemplate` and `NamedParameterJdbcTemplate`, which reduce boilerplate code when interacting with the database.
### DAO Implementation with Spring JDBC
In a Spring-based application, a DAO typically consists of:
1. **An interface** that defines database operations.
2. **A concrete class** that implements the interface using `JdbcTemplate` or `NamedParameterJdbcTemplate`.
3. **A model/entity class** representing database records.

### Example DAO Implementation using Spring JDBC

#### Define the Model Class
```java
public class Employee {
    private int id;
    private String name;
    private String department;

    // Constructors, Getters, and Setters
}
```

#### Create the DAO Interface
```java
public interface EmployeeDao {
    int save(Employee employee);
    Employee getById(int id);
    List<Employee> getAll();
}
```

#### Implement DAO Using `JdbcTemplate`
```java
@Repository  // Marks this class as a Spring-managed DAO component
public class EmployeeDaoImpl implements EmployeeDao {

    private final JdbcTemplate jdbcTemplate;

    @Autowired
    public EmployeeDaoImpl(JdbcTemplate jdbcTemplate) {
        this.jdbcTemplate = jdbcTemplate;
    }

    @Override
    public int save(Employee employee) {
        String sql = "INSERT INTO employees (name, department) VALUES (?, ?)";
        return jdbcTemplate.update(sql, employee.getName(), employee.getDepartment());
    }

    @Override
    public Employee getById(int id) {
        String sql = "SELECT * FROM employees WHERE id = ?";
        return jdbcTemplate.queryForObject(sql, new BeanPropertyRowMapper<>(Employee.class), id);
    }

    @Override
    public List<Employee> getAll() {
        String sql = "SELECT * FROM employees";
        return jdbcTemplate.query(sql, new BeanPropertyRowMapper<>(Employee.class));
    }
}
```

### **How Does Spring JDBC Help in DAO Implementation?**

✅ **Reduces Boilerplate Code:** Eliminates the need to manually open/close connections, handle exceptions, and iterate over results.  
✅ **Improves Readability:** With `JdbcTemplate`, queries are clear and concise.  
✅ **Better Exception Handling:** Spring JDBC converts SQL exceptions into `DataAccessException`, making error handling more manageable.  
✅ **Flexible Configuration:** Works well with **Spring transactions** and other persistence solutions like JPA.

Would you like an example of using `NamedParameterJdbcTemplate` for better parameter handling? 🚀












---
## Flash cards section
