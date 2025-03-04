---
Creation_date: 2025-03-04 00:28
Modification_date: Tuesday 4th March 2025 00:28:12
Indexes:
  - "[[spring_boot]]"
  - "[[to_do_notes]]"
  - "[[spring_core]]"
---

----

### Using Multiple DataSources in Spring JDBC

In some applications, you may need to interact with multiple databases. Spring provides a way to configure multiple `DataSource` beans and use them effectively in different parts of your application.

### Steps to Configure Multiple DataSources in Spring JDBC

#### Define Multiple DataSources in Configuration

Since Spring Boot automatically configures a `DataSource` when using `spring-boot-starter-jdbc`, you'll need to manually define multiple `DataSource` beans.

##### Example Configuration (Java-based)
```java
@Configuration
public class DataSourceConfig {

    @Bean(name = "dataSource1")
    @Primary  // Marks this as the default DataSource
    @ConfigurationProperties(prefix = "spring.datasource.first")
    public DataSource dataSource1() {
        return DataSourceBuilder.create().build();
    }

    @Bean(name = "dataSource2")
    @ConfigurationProperties(prefix = "spring.datasource.second")
    public DataSource dataSource2() {
        return DataSourceBuilder.create().build();
    }
}
```

#### Configure `application.properties` or `application.yml`

Define the connection settings for both databases.

**For `application.properties`:**
```java
# First Database
spring.datasource.first.url=jdbc:mysql://localhost:3306/db1
spring.datasource.first.username=root
spring.datasource.first.password=root
spring.datasource.first.driver-class-name=com.mysql.cj.jdbc.Driver

# Second Database
spring.datasource.second.url=jdbc:postgresql://localhost:5432/db2
spring.datasource.second.username=admin
spring.datasource.second.password=admin
spring.datasource.second.driver-class-name=org.postgresql.Driver
```
#### Inject Different DataSources in DAOs

You can inject different `JdbcTemplate` instances for different databases.
```java
@Repository
public class EmployeeDaoImpl {

    private final JdbcTemplate jdbcTemplate1;
    private final JdbcTemplate jdbcTemplate2;

    @Autowired
    public EmployeeDaoImpl(@Qualifier("dataSource1") DataSource dataSource1,
                           @Qualifier("dataSource2") DataSource dataSource2) {
        this.jdbcTemplate1 = new JdbcTemplate(dataSource1);
        this.jdbcTemplate2 = new JdbcTemplate(dataSource2);
    }

    public List<Employee> getEmployeesFromDb1() {
        return jdbcTemplate1.query("SELECT * FROM employees", new BeanPropertyRowMapper<>(Employee.class));
    }

    public List<Employee> getEmployeesFromDb2() {
        return jdbcTemplate2.query("SELECT * FROM employees", new BeanPropertyRowMapper<>(Employee.class));
    }
}
```

### Key Points

✅ Use `@Primary` to specify the default `DataSource`.  
✅ Use `@Qualifier("dataSourceName")` to inject the correct `DataSource` where needed.  
✅ Each `DataSource` should be configured separately in `application.properties`.  
✅ If using Spring transactions, configure a `PlatformTransactionManager` for each `DataSource`.

Would you like an example with transaction management across multiple databases? 🚀










---
## Flash cards section
