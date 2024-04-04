

----
Creation date: 2024-03-10 14:57
Modification date: Sunday 10th March 2024 14:57:20

----

#Java 
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