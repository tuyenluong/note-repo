---
Creation_date: 2025-03-04 00:13
Modification_date: Tuesday 4th March 2025 00:13:17
Indexes:
  - "[[spring]]"
  - "[[to_do_notes]]"
  - "[[spring_boot]]"
---

----
- If you use Spring (without Spring Boot), you must manually define a `DataSource` bean in your configuration. Spring Boot, on the other hand, automatically configures a `DataSource` when the appropriate dependencies are present.
- `NamedParameterJdbcTemplate`, which reduce boilerplate code when interacting with the database.

### Configure the DataSource (`application.properties`)

Define database connection properties:
```java
spring.datasource.url=jdbc:mysql://localhost:3306/mydatabase
spring.datasource.username=root
spring.datasource.password=root
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver
```

Here is the question [[SPRING - What if I have multiple Data Source|if you have multiple DataSource]].

### Create an Employee Model Class
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

### Create the DAO Interface
```java
public interface EmployeeDao {
    int save(Employee employee);
    Employee getById(int id);
    List<Employee> getAll();
    int update(Employee employee);
    int deleteById(int id);
}
```

### Implement the DAO Using `JdbcTemplate`
```java
@Repository  // Marks this class as a Spring-managed component
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

    @Override
    public int update(Employee employee) {
        String sql = "UPDATE employees SET name = ?, department = ? WHERE id = ?";
        return jdbcTemplate.update(sql, employee.getName(), employee.getDepartment(), employee.getId());
    }

    @Override
    public int deleteById(int id) {
        String sql = "DELETE FROM employees WHERE id = ?";
        return jdbcTemplate.update(sql, id);
    }
}
```

### Using the DAO in a Service Class
```java
@Service
public class EmployeeService {

    private final EmployeeDao employeeDao;

    @Autowired
    public EmployeeService(EmployeeDao employeeDao) {
        this.employeeDao = employeeDao;
    }

    public void performOperations() {
        // Create a new employee
        Employee emp = new Employee(0, "John Doe", "IT");
        employeeDao.save(emp);

        // Fetch employee by ID
        Employee fetched = employeeDao.getById(1);
        System.out.println("Employee: " + fetched.getName());

        // Update employee details
        fetched.setDepartment("HR");
        employeeDao.update(fetched);

        // Fetch all employees
        List<Employee> allEmployees = employeeDao.getAll();
        allEmployees.forEach(e -> System.out.println(e.getName()));

        // Delete an employee
        employeeDao.deleteById(1);
    }
}
```

### How This Works

1. **Define SQL Queries** as `String` values.
2. **Execute Queries Using `JdbcTemplate`**:
    - `update()` → For **INSERT, UPDATE, DELETE** operations.
    - `queryForObject()` → For retrieving a **single row**.
    - `query()` → For retrieving **multiple rows**.
3. **Handle Mapping Automatically** using `BeanPropertyRowMapper<>(Employee.class)`, which maps result set columns to Java object fields.

### Advantages of `JdbcTemplate`

| Feature                           | `JdbcTemplate` |
|-----------------------------------|--------------|
| Simplifies JDBC Code              | ✅ Yes |
| Automatically Closes Resources    | ✅ Yes |
| Reduces Boilerplate Code          | ✅ Yes |
| Provides Exception Handling       | ✅ Yes |



---
## Flash cards section
