---
Creation_date: 2024-06-10 16:01
Modification_date: Monday 10th June 2024 16:01:02
Indexes:
  - "[[collections]]"
---

----

## Sorting data in a collection

- We are already partly familiar with `sort()` method from the [[JAVA - Sorting, Searching & Comparing Array|Array sorting]] lesson.
- If elements in the collection are primitives, they are sorted by natural order
- If elements are Strings, then numbers sort before letters, and uppercase letters sort before lower letters. Much like the rules from the [[JAVA - Sorting, Searching & Comparing Array#^dea931|Arrays.compare() method]] of the Sorting Array lesson. 
- But elements in the collection can be any type of object
- In that case, you have to define your own criteria of sorting
- In order to do this you can choose one of two approaches:
	- Use a class which implements `Comparable<T>` interface, or
	- Pass the implementation of `Comparator<T>` interface in `sort()` method

## `Comparable<T>`interface
- This interface has one abstract method: `int compareTo(T o)`
	- This method has to be implemented in a concrete class
- This method returns an integer according to these rules:
	- If the current object is equivalent to the argument, it will returns 0
	- If the current object is smaller than the argument, it will returns a negative number
	- If the current object is larger than the argument, it will returns a positive number

- Sorted by age example
```run-java
import java.util.Arrays;
import java.util.List;
import java.util.Collections;
public class Test{
	public static void main(String... args){
		List<Person> people = Arrays.asList(
			new Person("John", 25),
			new Person("George", 20),
			new Person("Ben", 30)
		);
		Collections.sort(people);
		System.out.println(people);
	}
}
public class Person implements Comparable<Person>{
	private String name;
	private int age;
	public Person(String name, int age){
		this.name = name;
		this.age = age;
	}
	@Override
	public int compareTo(Person other){
		return this.age - other.age;
	}
	@Override
	public String toString(){
		return "Person{name='" + name + "', age=" + age + "}";
	}
}
```


- Sorted by name example
```run-java
import java.util.Arrays;
import java.util.List;
import java.util.Collections;
public class Test{
	public static void main(String... args){
		List<Person> people = Arrays.asList(
			new Person("John", 25),
			new Person("George", 20),
			new Person("Ben", 30)
		);
		Collections.sort(people);
		System.out.println(people);
	}
}
public class Person implements Comparable<Person>{
	private String name;
	private int age;
	public Person(String name, int age){
		this.name = name;
		this.age = age;
	}
	@Override
	public int compareTo(Person other){
		return this.name.compareTo(other.name);
	}
	@Override
	public String toString(){
		return "Person{name='" + name + "', age=" + age + "}";
	}
}
```

## `Comparator<T>`interface
- In the last example we had to define a criteria for sorting when designing a class Person (*either by name or by age*).
- But what if we don't want to make that commitment?
	- I.e what if we want to sort by name in one case, and by age in another?
- In that case we can use `Comparator<T>` interface
	- And provide the implementation for `compare(T o1, T o2)` method
- This implementation is then passed to `sort()` method
	- To do this we usually use lambda expression or method reference

```run-java
import java.util.Arrays;
import java.util.List;
import java.util.Collections;
public class Test{
	public static void main(String... args){
		List<Person> people = Arrays.asList(
			new Person("John", 25),
			new Person("George", 20),
			new Person("Ben", 30)
		);
		// Sort by Age
		Collections.sort(people, (p1, p2) -> p1.getAge() - p2.getAge());
		System.out.println(people);
		// Sort by Name
		Collections.sort(people, (p1, p2) -> p1.getName().compareTo(p2.getName()));
		System.out.println(people);
	}
}
public class Person {
	private String name;
	private int age;
	public Person(String name, int age){
		this.name = name;
		this.age = age;
	}
	public String getName(){
		return name;
	}
	public int getAge(){
		return age;
	}
	@Override
	public String toString(){
		return "Person{name='" + name + "', age=" + age + "}";
	}
}
```

- Compare the same thing without lambda (*The old way*)
```run-java
import java.util.Arrays;
import java.util.List;
import java.util.Collections;
import java.util.Comparator;
public class Test{
	public static void main(String... args){
		List<Person> people = Arrays.asList(
			new Person("John", 25),
			new Person("George", 20),
			new Person("Ben", 30)
		);
		// Sort by Age
		// Old way: add compare implementation by init anonymous class
		Comparator<Person> byAge = new Comparator<Person>(){
			public int compare(Person p1, Person p2){
				return p1.getAge() - p2.getAge();
			}
		};
		Collections.sort(people, byAge);
		System.out.println(people);
	}
}
public class Person {
	private String name;
	private int age;
	public Person(String name, int age){
		this.name = name;
		this.age = age;
	}
	public String getName(){
		return name;
	}
	public int getAge(){
		return age;
	}
	@Override
	public String toString(){
		return "Person{name='" + name + "', age=" + age + "}";
	}
}
```

- Using `comparing()`method with method reference (*This might appear in the exam*)
```run-java
import java.util.Arrays;
import java.util.List;
import java.util.Collections;
import java.util.Comparator;
public class Test{
	public static void main(String... args){
		List<Person> people = Arrays.asList(
			new Person("John", 25),
			new Person("George", 20),
			new Person("Ben", 30)
		);
		Comparator<Person> byName = Comparator.comparing(Person::getName);
		Collections.sort(people, byName);
		System.out.println("byName= " +people);

		Comparator<Person> inReversed = Comparator.comparing(Person::getName).reversed();
		Collections.sort(people, inReversed);
		System.out.println("inReversed= " +people);

		Comparator<Person> chaining = Comparator.comparing(Person==getName).thenComparing(Person==getAge);
		Collections.sort(people, chaining);
		System.out.println("chaining= " +people);
	}
}
public class Person {
	private String name;
	private int age;
	public Person(String name, int age){
		this.name = name;
		this.age = age;
	}
	public String getName(){
		return name;
	}
	public int getAge(){
		return age;
	}
	@Override
	public String toString(){
		return "Person{name='" + name + "', age=" + age + "}";
	}
}
```


## `Comparable` vs `Comparator` Summary

| Table                          | Comparable    | Comparator  |
| ------------------------------ | ------------- | ----------- |
| Package name (*for import*)    | java.lang     | java.util   |
| Must be implemented by a class | Yes           | No          |
| Method name in interface       | `compareTo()` | `compare()` |
| Number of method parameters    | 1             | 2           |
| Usually used with lambda       | No            | Yes         |



---
## Flash cards section

What is the `Comparator` interface used for? ;; To define multiple ways of comparing two objects, using the `compare(T o1, T o2)` method.

How do you implement the `Comparable` interface in a class? ;; By overriding the `compareTo(T o)` method.

How do you implement the `Comparator` interface? ;; By creating a class that implements `Comparator<T>` and overriding the `compare(T o1, T o2)` method.

Provide an example of a class implementing `Comparable`.
?
```java
public class Student implements Comparable<Student> {
    private String name;
    private int age;
    
    @Override
    public int compareTo(Student other) {
        return this.age - other.age; // Compare by age
    }
}
```

Provide an example of a class implementing `Comparator`.
?
```java
public class NameComparator implements Comparator<Student> {
    @Override
    public int compare(Student s1, Student s2) {
        return s1.getName().compareTo(s2.getName()); // Compare by name
    }
}
```

How do you sort a list of objects using `Comparable`?
?
```java
List<Student> students = new ArrayList<>();
Collections.sort(students); // Uses compareTo method
```

How do you sort a list of objects using `Comparator`?
?
```java
List<Student> students = new ArrayList<>();
Collections.sort(students, new NameComparator()); // Uses compare method
```

What is the main difference between `Comparable` and `Comparator`?
?
`Comparable` modifies the class to define a natural ordering with a single `compareTo` method, while `Comparator` allows multiple comparison strategies without modifying the class, using compare and equals methods.

How can you sort a list by multiple criteria using `Comparator`?
?
```java
Comparator<Student> byAge = Comparator.comparingInt(Student::getAge);
Comparator<Student> byName = Comparator.comparing(Student::getName);
students.sort(byAge.thenComparing(byName));
```

What is the advantage of using `Comparator` over `Comparable`?
?
`Comparator` allows multiple comparison strategies without modifying the class, providing greater flexibility.

What does the `Comparator.comparing` method do?
?
It creates a comparator based on a function.
```java
Comparator<Student> byAge = Comparator.comparing(Student::getAge);
```

What is the difference between the `Comparable` and `Comparator` interfaces in Java? ;; `Comparable` is used to define the natural ordering of objects of a class and is implemented by the class itself, requiring the implementation of the `compareTo()` method. `Comparator` is used to define custom orderings and is implemented externally, requiring the implementation of the `compare()` method.

How do you sort a list of objects by their natural ordering using the `Comparable` interface? ;; Implement the `Comparable` interface in the class of the objects and override the `compareTo()` method. Then, use `Collections.sort()` or `List.sort()` to sort the list.
<!--SR:!2024-08-03,1,230-->

Given the following code, what will be the result when sorting by age?
```java
import java.util.Arrays;
import java.util.List;
import java.util.Collections;

public class Test {
    public static void main(String... args) {
        List<Person> people = Arrays.asList(
            new Person("John", 25),
            new Person("George", 20),
            new Person("Ben", 30)
        );
        Collections.sort(people);
        System.out.println(people);
    }
}

public class Person implements Comparable<Person> {
    private String name;
    private int age;

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    @Override
    public int compareTo(Person other) {
        return this.age - other.age;
    }

    @Override
    public String toString() {
        return "Person{name='" + name + "', age=" + age + "}";
    }
}
```
?
The list will be sorted by age in ascending order. The output will be:
```java
[Person{name='George', age=20}, Person{name='John', age=25}, Person{name='Ben', age=30}]
```

How can you sort a list of `Person` objects by name using the `Comparator` interface?
?
Use the `Comparator` interface to define the sorting criteria and pass it to `Collections.sort()`. For example:
```java
Collections.sort(people, (p1, p2) -> p1.getName().compareTo(p2.getName()));
```
<!--SR:!2024-08-03,1,228-->

Given the following code, what will be the output when sorting by name using a `Comparator`?
```java
import java.util.Arrays;
import java.util.List;
import java.util.Collections;

public class Test {
    public static void main(String... args) {
        List<Person> people = Arrays.asList(
            new Person("John", 25),
            new Person("George", 20),
            new Person("Ben", 30)
        );
        Collections.sort(people, (p1, p2) -> p1.getName().compareTo(p2.getName()));
        System.out.println(people);
    }
}

public class Person {
    private String name;
    private int age;

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public String getName() {
        return name;
    }

    public int getAge() {
        return age;
    }

    @Override
    public String toString() {
        return "Person{name='" + name + "', age=" + age + "}";
    }
}
```
?
The list will be sorted by name in ascending order. The output will be:
```java
[Person{name='Ben', age=30}, Person{name='George', age=20}, Person{name='John', age=25}]
```

How do you sort a list using `Comparator` with method references?
?
Use `Comparator.comparing()` to create a comparator based on a method reference, then pass it to `Collections.sort()`. For example:
```java
Comparator<Person> byName = Comparator.comparing(Person::getName);
Collections.sort(people, byName);
```

Given the following code, what will be the output when using `Comparator.comparing()` and `reversed()`?
```java
import java.util.Arrays;
import java.util.List;
import java.util.Collections;
import java.util.Comparator;

public class Test {
    public static void main(String... args) {
        List<Person> people = Arrays.asList(
            new Person("John", 25),
            new Person("George", 20),
            new Person("Ben", 30)
        );
        Comparator<Person> inReversed = Comparator.comparing(Person::getName).reversed();
        Collections.sort(people, inReversed);
        System.out.println(people);
    }
}

public class Person {
    private String name;
    private int age;

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public String getName() {
        return name;
    }

    public int getAge() {
        return age;
    }

    @Override
    public String toString() {
        return "Person{name='" + name + "', age=" + age + "}";
    }
}
```
?
The list will be sorted by name in descending order. The output will be:
```java
[Person{name='John', age=25}, Person{name='George', age=20}, Person{name='Ben', age=30}]
```

What is the result of chaining multiple comparators using `Comparator.comparing()`? ;; Chaining comparators allows you to sort by multiple criteria. For example, `Comparator.comparing(Person==getName).thenComparing(Person==getAge)` will first sort by name and then by age if names are the same.

Given the following code, what will be the result of chaining comparators?
```java
import java.util.Arrays;
import java.util.List;
import java.util.Collections;
import java.util.Comparator;

public class Test {
    public static void main(String... args) {
        List<Person> people = Arrays.asList(
            new Person("John", 25),
            new Person("John", 20),
            new Person("George", 20)
        );
        Comparator<Person> chaining = Comparator.comparing(Person==getName).thenComparing(Person==getAge);
        Collections.sort(people, chaining);
        System.out.println(people);
    }
}

public class Person {
    private String name;
    private int age;

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public String getName() {
        return name;
    }

    public int getAge() {
        return age;
    }

    @Override
    public String toString() {
        return "Person{name='" + name + "', age=" + age + "}";
    }
}
```
?
The list will be sorted first by name and then by age. The output will be:
```java
[Person{name='George', age=20}, Person{name='John', age=20}, Person{name='John', age=25}]
```
