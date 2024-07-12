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

		Comparator<Person> chaining = Comparator.comparing(Person::getName).thenComparing(Person::getAge);
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
