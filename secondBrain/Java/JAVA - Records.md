---
Creation_date: 2024-08-01 12:10
Modification_date: Thursday 1st August 2024 12:10:04
Indexes:
  - "[[advanced_classes]]"
---

----
## What are records?

`record` are a new feature introduced in [[java-14|Java 14]] as a preview feature and became a standard feature in [[java-16|Java 16]]. They provide a compact syntax for declaring classes that are primarily used to store data.

- Encapsulated classes, but without boilerplate code
- The encapsulation is secured
- `constructor`, `getters`, `toString()`, `equals()` and `hashCode()` are generated
- `records` cannot have explicit instance fields
- `records` can have `static` fields and methods
- `records` can have instance methods

## The old way of creating encapsulated class

```java
// The old way of creating encapsulated class
public final class Student {

    // 1. Declare private final fields
    private final String firstName;
    private final String lastName;
    private final int id;

    // 2. Define the constructor
    public Student(String firstName, String lastName, int id) {
        this.firstName = firstName;
        this.lastName = lastName;
        this.id = id;
    }

    // 3. Define getters
    public int getId() {
        return id;
    }

    public String getFirstName() {
        return firstName;
    }

    public String getLastName() {
        return lastName;
    }

    // 4. Override toString() method
    @Override
    public String toString() {
        return "Student{" +
               "firstName='" + firstName + '\'' +
               ", lastName='" + lastName + '\'' +
               ", id=" + id +
               '}';
    }
}
// 5. Override equals() method
@Override
public boolean equals(Object o) {
    if (this == o) return true;
    if (o == null || getClass() != o.getClass()) return false;
    Student student = (Student) o;
    return id == student.id && 
           Objects.equals(firstName, student.firstName) && 
           Objects.equals(lastName, student.lastName);
}

// 6. Override hashCode() method
@Override
public int hashCode() {
    return Objects.hash(firstName, lastName, id);
}
```
## All this can be replaced by only ONE line

- NOTE: the `getters` in the `record` will not follow the conventional naming. 
- `record` just use the variable name of the field members for `getters`, not `getFirstName()`, but `firstName()` !!

```run-java
public class Main {
    public static void main(String[] args) {
        // Create a new Student object
        var theStudent = new Student("Luka", "Popov", 1);
        
        // Access and print the first name using the getter
        System.out.println(theStudent.firstName());
        // => Luka
        
        // Access and print the last name using the getter
        System.out.println(theStudent.lastName());
        // => Popov
        
        // Access and print the ID using the getter
        System.out.println(theStudent.id());
        // => 1
        
        // NOTE: the getter is not like getFirstName(), but firstName() !!
        
        // toString() is nicely implemented
        System.out.println(theStudent);
        // => Student{firstName='Luka', lastName='Popov', id=1}
        
        // equals() is implemented as we would expect
        var anotherStudent = new Student("Luka", "Popov", 1);
        
        // Check reference equality (should be false)
        System.out.println(theStudent == anotherStudent);
        // => false
        
        // Check logical equality using equals() (should be true)
        System.out.println(theStudent.equals(anotherStudent));
        // => true
    }
}
// All in one line
public record Student (String firstName, String lastName, int id){}
```

- The compiler will auto-generated constructor implicitly, this will be called "*canonical constructor*"

## Compact Constructor

- Sometimes, you want to make some modification on the member's value of the `record`, but unable to so due to the immutable property of the `record` it self.
- There is a solution for that, it's called Compact constructor.
- A compact constructor allows you to include validation logic without repeating the parameter list. In the following example, a `Student` `record` is defined with a compact constructor that validates the `id` field:
	- **Validation**: Ensures that the `id` is between 10 and 1,000,000. If the `id` is outside this range, an `IllegalArgumentException` is thrown.
	- **Normalization**: Transforms the `firstName` and `lastName` to have the first letter in uppercase and the rest in lowercase, ensuring consistent formatting of names. For instance, "luka" or "lUka" is converted to "Luka".
```java
public record Student(String firstName, String lastName, int id) {
    public Student {
        if (id < 10 || id > 1_000_000) throw new IllegalArgumentException();
        firstName = firstName.substring(0, 1).toUpperCase() +
            firstName.substring(1).toLowerCase();
		lastName = lastName.substring(0, 1).toUpperCase() +
           lastName.substring(1).toLowerCase();
    }
}
```
- Notice the syntax: the constructor does not include parentheses `()` for the parameter list, as it is implicitly defined by the `record` components. 
- Additionally, instance fields do not need to be explicitly initialized because they are automatically assigned from the constructor parameters.

By using compact constructors, you can encapsulate such business logic directly within the record definition, ensuring that all instances of the record are valid and correctly formatted.





---
## Flash cards section

**What is a Java `record`?** ;; A new feature introduced in Java 14 as a preview feature and became standard in Java 16, providing a compact syntax for declaring data classes.

**What are the benefits of using Java records?** ;; Encapsulated classes without boilerplate code, secure encapsulation, automatically generated `constructor`, `getters`, `toString()`, `equals()`, and `hashCode()` methods.

**Can records have explicit instance fields?** ;; No, records cannot have explicit instance fields.

**Can records have static fields and methods?** ;; Yes, records can have static fields and methods.

**Can records have instance methods?** ;; Yes, records can have instance methods.

**How do the getter methods in a record differ from those in a traditional class?** ;; In records, getters use the field name directly (e.g., `firstName()`) instead of the conventional `getFirstName()`.

**What is a compact constructor in a Java record?** ;; A compact constructor allows you to include validation and normalization logic without repeating the parameter list.

Given the following record definition, what will be the output?
```java
public record Person(String name, int age) {}
var person = new Person("Alice", 30);
System.out.println(person.name());
System.out.println(person.age());
```
?
`Alice` and `30`

What happens if you try to compile and run this code?
```java
public record Car(String model, int year) {
    public Car {
        if (year < 1886) throw new IllegalArgumentException("Invalid year");
        model = model.toUpperCase();
    }
}
var car = new Car("Model T", 1885);
```
?
It throws an `IllegalArgumentException` with the message "Invalid year".

Given the following code, what will be the output?
```java
public record Animal(String type) {
    public Animal {
        type = type.toLowerCase();
    }
}
var animal = new Animal("Cat");
System.out.println(animal.type());

```
?
`cat`

What will be the result of this code?
```java
public record Book(String title, double price) {
    public Book {
        if (price < 0) throw new IllegalArgumentException("Price cannot be negative");
    }
}
var book = new Book("Java Programming", -50.0);
```
?
It throws an `IllegalArgumentException` with the message "Price cannot be negative".

**Is the following statement true or false: "Java records can have instance fields that are not part of the record components."** ;; False

What will this code print?
```java
public record City(String name, int population) {}
var city = new City("New York", 8000000);
System.out.println(city);
```
?
`City[name=New York, population=8000000]`

What happens if you try to compile and run this code?
```java
public record Country(String name, String continent) {
    public Country {
        if (name.isEmpty()) throw new IllegalArgumentException("Name cannot be empty");
    }
}
var country = new Country("", "Asia");
```
?
It throws an `IllegalArgumentException` with the message "Name cannot be empty".

**Which of the following statements are true about Java records?**
 - [ ] a) Records can extend other classes.
 - [ ] b) Records are implicitly final.
 - [ ] c) Records automatically generate `toString()`, `equals()`, and `hashCode()` methods.
 - [ ] d) Records can have instance methods.
 ?
 `b)`, `c)`, and `d)`
 
**Which of the following methods are automatically generated in a Java record?**
- [ ] a) `toString()`
- [ ] b) `equals()`
- [ ] c) `hashCode()`
- [ ] d) `clone()`
?
`a)`, `b)`, and `c)`

**What are the key features of a Java record?**
- [ ] a) Compact syntax for data classes
- [ ] b) Automatic generation of constructor and method
- [ ] c) Ability to have explicit instance fields
- [ ] d) Immutability of fields
?
`a)`, `b)`, and `d)`

**Which of the following are true about compact constructors in Java records?**
- [ ] a) They allow modification of record fields.
- [ ] b) They can include validation logic
- [ ] c) They must repeat the parameter list
- [ ] d) They can normalize data.
?
`b)` and` d)`

**What are the restrictions on Java records?**
- [ ] a) Cannot have explicit instance fields
- [ ] b) Cannot be abstract
- [ ] c) Cannot implement interfaces
- [ ] d) Cannot extend other classes
?
 `a)`, `b)`, and `d)`

**Which of the following are valid uses of a compact constructor in a Java record?**
- [ ] a) Enforcing constraints on the data
- [ ] b) Modifying the constructor's parameter list
- [ ] c) Normalizing input data
- [ ] d) Including complex initialization logic
?
 `a)`, `c)`, and `d)`