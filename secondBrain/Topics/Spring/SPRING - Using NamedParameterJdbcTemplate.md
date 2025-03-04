---
Creation_date: 2025-03-04 00:30
Modification_date: Tuesday 4th March 2025 00:30:44
Indexes:
  - "[[spring_boot]]"
  - "[[to_do_notes]]"
  - "[[spring_core]]"
---

----

### Why Use `NamedParameterJdbcTemplate`?

- It allows **named parameters** (e.g., `:name`, `:department`) instead of **positional placeholders (`?`)**, improving readability.
- It avoids **positional mistakes** when working with multiple parameters.
- It makes queries more **maintainable and self-documenting**.

Example: Employee DAO using `NamedParameterJdbcTemplate`
#### Define the Model Class
```java
public class Employee {
    private int id;
    private String name;
    private String department;

    // Constructors
    public Employee() {}
    
    public Employee(int id, String name, String department) {
        this.id = id;
        this.name = name;
        this.department = department;
    }

    // Getters and Setters
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

#### Implement DAO Using `NamedParameterJdbcTemplate`
```java
@Repository
public class EmployeeDaoImpl implements EmployeeDao {

    private final NamedParameterJdbcTemplate namedParameterJdbcTemplate;

    @Autowired
    public EmployeeDaoImpl(NamedParameterJdbcTemplate namedParameterJdbcTemplate) {
        this.namedParameterJdbcTemplate = namedParameterJdbcTemplate;
    }

    @Override
    public int save(Employee employee) {
        String sql = "INSERT INTO employees (name, department) VALUES (:name, :department)";

        Map<String, Object> params = new HashMap<>();
        params.put("name", employee.getName());
        params.put("department", employee.getDepartment());

        return namedParameterJdbcTemplate.update(sql, params);
    }

    @Override
    public Employee getById(int id) {
        String sql = "SELECT * FROM employees WHERE id = :id";

        Map<String, Object> params = new HashMap<>();
        params.put("id", id);

        return namedParameterJdbcTemplate.queryForObject(sql, params, new BeanPropertyRowMapper<>(Employee.class));
    }

    @Override
    public List<Employee> getAll() {
        String sql = "SELECT * FROM employees";
        return namedParameterJdbcTemplate.query(sql, new BeanPropertyRowMapper<>(Employee.class));
    }
}
```

### How This Works
1. **Named Parameters (`:name`, `:department`, `:id`)** make the query more readable.
2. **A `Map<String, Object>`** is used to pass values to the named parameters.
3. **`queryForObject()`** retrieves a single record.
4. **`query()`** retrieves a list of records.

### Advantages of `NamedParameterJdbcTemplate` over `JdbcTemplate`
| Feature                      | `JdbcTemplate`              | `NamedParameterJdbcTemplate` |
| ---------------------------- | --------------------------- | ---------------------------- |
| Uses Named Parameters        | ❌ No, uses `?` placeholders | ✅ Yes, uses `:paramName`     |
| Readability                  | ❌ Less readable             | ✅ More readable              |
| Suitable for Complex Queries | ❌ Hard to manage parameters | ✅ Easier to manage           |
| Prevents Positional Mistakes | ❌ No                        | ✅ Yes                        |











---
## Flash cards section
