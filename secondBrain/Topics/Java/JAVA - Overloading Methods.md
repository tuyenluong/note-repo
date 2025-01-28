---
Creation_date: 2024-07-27 13:38
Modification_date: Saturday 27th July 2024 13:38:29
Indexes:
  - "[[methods]]"
---

----
## Overloading method

- Overloading method is having two or more than one method with the same name but different parameter list

```java
public void greet (int x ) {System.out.println("Hello")};
public void greet (double x ) {System.out.println("Good Afternoon")};
public void greet (int x, int y ) {System.out.println("Good day")};

great(5);
==>> Hello
great(3.14);
==>> Good Afternoon
great(5, -11);
==>> Good day
```

- If passing the argument that doesn't exactly match the parameter type, Java will pick the most similar version of the method
```java
public void greet (int x ) {System.out.println("Hello")};
public void greet (double x ) {System.out.println("Good Afternoon")};
public void greet (int x, int y ) {System.out.println("Good day")};

short a = 2;

great(a);
==>> There is no `greet(short x)` method, so Java looks for larger primitive type
==>> Hello
```

- By applying the [[JAVA - Boxing and Unboxing#^669fa5|auto boxing and auto unboxing mechanism]], passing literals value into the parameter list will also applicable for wrapper class parameter list.
- In the example below, 4 `greet()` methods have been overloaded with different parameter types. And there are no method `greet()` that will take in the `double` primitive data type value, but the method `greet(Object)` is the parent of all object, even the wrapper class `Double`. So the code is valid and eventually compiled and the result will be `Hi`
 ```run-java
public class Test{
	public static void main(String... args){
		greet(2.3);
	}

	public static void greet (Integer x ) {System.out.println("Hello");};
	public static void greet (Short x ) {System.out.println("Good Afternoon");};
	public static void greet (String x ) {System.out.println("Good day");};
	public static void greet (Object x ) {System.out.println("Hi");};
}
```

- If there are no applicant method in the overloading method list, then it will throw `no suitable method found for method`
- In this example, we removed the `greet(Object)` method. So there are no any applicant method for Java to compile. Thus, it will throw error.
```run-java
public class Test{
	public static void main(String... args){
		greet(2.3);
	}

	public static void greet (Integer x ) {System.out.println("Hello");};
	public static void greet (Short x ) {System.out.println("Good Afternoon");};
	public static void greet (String x ) {System.out.println("Good day");};
}
```






---
## Flash cards section

What is method overloading in Java? ;; Method overloading is when two or more methods in the same class have the same name but different parameter lists.

Given the following code, what will be the output of `greet(5)`?
```java
public void greet(int x) { System.out.println("Hello"); }
public void greet(double x) { System.out.println("Good Afternoon"); }
public void greet(int x, int y) { System.out.println("Good day"); }

greet(5);
```
?
The output will be `Hello`. The method with the matching parameter type `int` is called.

What will be the output of `greet(3.14)` given the following method overloads?
```java
public void greet(int x) { System.out.println("Hello"); }
public void greet(double x) { System.out.println("Good Afternoon"); }
public void greet(int x, int y) { System.out.println("Good day"); }

greet(3.14);
```
?
The output will be `Good Afternoon`. The method with the matching parameter type `double` is called.

What will happen if you call `greet(5, -11)` with the following overloaded methods?
```java
public void greet(int x) { System.out.println("Hello"); }
public void greet(double x) { System.out.println("Good Afternoon"); }
public void greet(int x, int y) { System.out.println("Good day"); }

greet(5, -11);
```
?
The output will be `Good day`. The method with the matching parameter list `(int, int)` is called.

Given the following code, what will be the output of `greet(a)` where `short a = 2`?
```java
public void greet(int x) { System.out.println("Hello"); }
public void greet(double x) { System.out.println("Good Afternoon"); }
public void greet(int x, int y) { System.out.println("Good day"); }

short a = 2;
greet(a);
```
?
The output will be `Hello`. The `short` value is automatically promoted to `int`.

What will be the output of `greet(2.3)` with the following overloaded methods?
```java
public class Test {
    public static void main(String... args) {
        greet(2.3);
    }

    public static void greet(Integer x) { System.out.println("Hello"); }
    public static void greet(Short x) { System.out.println("Good Afternoon"); }
    public static void greet(String x) { System.out.println("Good day"); }
    public static void greet(Object x) { System.out.println("Hi"); }
}
```
?
The output will be `Hi`. The `double` value is boxed into a `Double` object, and `Object` is the closest match.

What will happen if you call `greet(2.3)` with the following code, which lacks a matching method?
```java
public class Test {
    public static void main(String... args) {
        greet(2.3);
    }

    public static void greet(Integer x) { System.out.println("Hello"); }
    public static void greet(Short x) { System.out.println("Good Afternoon"); }
    public static void greet(String x) { System.out.println("Good day"); }
}
```
?
A compilation error will occur with the message `no suitable method found for greet(double)` because there is no matching method for a `double` parameter.
