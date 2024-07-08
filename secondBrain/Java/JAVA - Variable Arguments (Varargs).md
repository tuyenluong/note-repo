---
Creation_date: 2024-07-08 21:23
Modification_date: Monday 8th July 2024 21:23:47
Indexes:
  - "[[methods]]"
---

----

## Variable Arguments (*Varargs*)

- Method can accept any number of parameters of the same type.
- Two rules to keep in mind:
	- A method can have at most one varargs argument
	- Varargs argument must be the last parameter in the parameter list

### Example

```run-java
public class Test{
	public static void greet (String greeting, String... names){
		for(String name : names){
			System.out.println(greeting + ", " + name +"!");
		}
	}
	public static void main(String... args){
		greet("Hello", "John", "George", "Luke");
	}
}
```


### You can pass an array as varargs

```run-java
public class Test{
	public static void greet (String greeting, String... names){
		for(String name : names){
			System.out.println(greeting + ", " + name +"!");
		}
	}
	public static void main(String... args){
	String[] allNames = {"Peter", "Paul"};
		greet("Hello", allNames);
	}
}
```

### You cannot pass an anonymous array (!!!)

```run-java
public class Test{
	public static void greet (String greeting, String... names){
		for(String name : names){
			System.out.println(greeting + ", " + name +"!");
		}
	}
	public static void main(String... args){
		greet("Hello", {"John", "George", "Luke"});
		// This anonymous array will not compile
	}
}
```

- You can pass a List or an [[JAVA - Creating an Array|Array]] in one single line, which is not recommended, but you can define a new array using the [[JAVA - Creating an Array#^2960c3|new]] keyword.
```run-java
public class Test{
	public static void greet (String greeting, String... names){
		for(String name : names){
			System.out.println(greeting + ", " + name +"!");
		}
	}
	public static void main(String... args){
		greet("Hello", new String[]{"John", "George", "Luke"});
		// init an array with `new` keyword will work
	}
}
```





---
## Flash cards section

The number of varargs arguments should be in the same data type;; Yes, it's true
<!--SR:!2024-07-13,4,270-->

Varargs argument can place anywhere in the parameter list. It's true? ;; No, it's false
<!--SR:!2024-07-13,4,270-->

A method can have more than one varargs argument. It's true? ;; No, it's false
<!--SR:!2024-07-13,4,270-->


Will this code compile?
```java
public class Test{
	public static void greet (String greeting, String... names){
		for(String name : names){
			System.out.println(greeting + ", " + name +"!");
		}
	}
	public static void main(String... args){
		greet("Hello", new String[]{"John", "George", "Luke"});
	}
}
```
?
Yes, it's. Despite that initialize a new array using `new` keyword to pass into the varargs is not recommended, but it allow we to initialize an array and cast it into the varargs. So it's valid.
<!--SR:!2024-07-13,4,270-->

Can I pass an anonymous array into the varargs?
```run-java
public class Test{
	public static void greet (String greeting, String... names){
		for(String name : names){
			System.out.println(greeting + ", " + name +"!");
		}
	}
	public static void main(String... args){
		greet("Hello", {"John", "George", "Luke"});
	}
}
```
?
No, it will not compile.
<!--SR:!2024-07-13,4,270-->