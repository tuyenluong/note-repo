---
Creation_date: 2024-03-10 14:57
Modification_date: Sunday 10th March 2024 14:57:20
Indexes:
  - "[[flow_control]]"
---

----

## The Syntax of Do/While Loop

- The main difference compared to [[JAVA - While Loop|while loop]]
	- Block of code will be executed at least once
- Semicolon is not needed at the end.
```java
do{
	// executes while condition is true
}while (condition)
```

- The body will be executed at least once
```java
int a = 5, b = 7;
do{
	System.out.println("Hello");
}while (a > b);
==>> Result: print "Hello" once
```

- Infinite loop
```java
int a = 5, b = 7;
do{
	System.out.println("Hello");
}while (a < b);
==>> Result: print "Hello" forever
```

- Simple infinite loop
```java
int a = 5, b = 7;
do{
	System.out.println("Hello");
}while (true);
==>> Result: print "Hello" forever
```

### Everything else works the same as in while loop
- break, continue, nested loops, unreachable code, breaking with return, etc.



---
## Flash cards section

What is the main difference between a do/while loop and a while loop? ;; A do/while loop will execute the block of code at least once.

Does a do/while loop require a semicolon at the end of the loop? ;; No, a semicolon is not needed at the end of a do/while loop.

How is the syntax of a do/while loop structured in Java?
?
```java
do{
	// executes while condition is true
} while (condition)
```

What is the output of the following code?
```java
int a = 5, b = 7;
do{
	System.out.println("Hello");
} while (a > b);
```
?
The code will print "Hello" once.

What is the result of the following code?
```java
int a = 5, b = 7;
do{
	System.out.println("Hello");
} while (a < b);
```
?
The code will print "Hello" forever (infinite loop).
<!--SR:!2024-08-06,4,270-->

How can you create a simple infinite loop using a do/while loop?
?
```
int a = 5, b = 7;
do{
	System.out.println("Hello");
} while (true);
```

Does the do/while loop support break, continue, nested loops, and return statements like the while loop? ;; Yes, the do/while loop supports break, continue, nested loops, and return statements just like the while loop.




