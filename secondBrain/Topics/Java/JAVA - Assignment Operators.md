---
Creation_date: 2024-03-03 12:02
Modification_date: Sunday 3rd March 2024 12:02:24
Indexes:
  - "[[operator]]"
---

----

## Assignment operators

- Assignment operator ( **=** ) has the lowest precedence
- First the operation on the right-hand side is performed
	- The result is assigned to a variable on the left-hand side
```java
a = b + c
```

## Auto-casting

- Java automatically promotes smaller to larger [[JAVA - Data Types#^0a9df1|data type]]
```java
short x = 5
int y;
y = x; ==>> OK (x is casted to int)
```

```java
int a = 5;
short b;
b = a; ==>> NOT OK (you cannot put int in short)
```

## Explicit casting

- But there is a solution if you want you cast a larger to smaller data type, is by explicit casting ^dc2545
```java
int a = 5;
short b;
b = (short) a; ==>> OK
```

## Some examples

- Cannot assign a double (*a larger data type, 64-bits* ) value into a int variable (*a smaller data type, 32-bits* ). ^1e7a63
```java
int x = 1.0; ==>> NOT OK
```

- This also not work because it have the same reason with [[JAVA - Assignment Operators#^1e7a63|the previous one]]. It can tell by [[JAVA - Data Types#^c97ad1|the L character at the end]]
```java
int y = 123L; ==>> NOT OK
```

- This is ok, because int data type is smaller then long data type.
```java
long z = 5; ==>> OK
```

- This is ok, because byte data type is smaller then long data type. You can tell by [[JAVA - Assignment Operators#^dc2545|the explicit casting.]]
```java
long w = (byte) 7; ==>> OK
```

- This also not work because it have the same reason with [[JAVA - Assignment Operators#^1e7a63|the previous one]]. Because the value 2.3 don't have [[JAVA - Data Types#^50b425|the F character at the end]], so Java will see the value as double.
```java
float k = 2.3; ==>> NOT OK
```

- This is ok, because now it have [[JAVA - Data Types#^50b425|the F character at the end]]. Now it's ok.
```java
float k = 2.3F; ==>> OK
```

- Smaller data type (*Float - [[JAVA - Data Types#^50b425|the F character at the end]]*) to larger data type (*Double*) is ok.
```java
double m = 2.3F; ==>> OK
```

- Same data type is ok.
```java
double n = 3.14; ==>> OK
```

- This is not ok, because this is larger to smaller data type.
```java
double n = 3.14;
float pi = n; ==>> NOT OK
```

- This is ok, because the compiler can figure out that 7 is short. 
```java
short a = 7;
```

- This is ok, because the compiler can figure out that 5 is short. 
```java
short b = 5;
```

- [[JAVA - Binary Operators#^94102f|Whenever you do an operation with short and byte, then all values are promoted to integer]] and the result is integer.
```java
short c = (short) (a + b); ==>> OK
```

## Compound assign operators

- There are also someething called compound assign operators, and this is just a shorthand notation of an assignment operation.
- So mathematically expressions like `a = a + 5` doesn't make much sense. But in programming they are perfectly fine because first the right hand side is evaluated.

```java
a += 5 ==>> a = a + 5
```

```java
a -= 5  ==>> a = a - 5
```

```java
a *= 5  ==>> a = a * 5
```

```java
a /= 5  ==>> a = a / 5
```

## Return value of assignment operator

- The assignment operator will does two things when it get used in a expression:
	- First, it will assign the value from the right-hand side to the left-hand side.
	- Second, it will also return the value of the variable.

Examples:
```java
int x = 5; ==>> Initialized x 
int y = (x = 3) * 2; ==>> In this line, x get re-assign as 3 and IT'S ALSO RETURN THE VALUE OF 3 
                    ==>> as an operand to get multiplied by 2.
==>> Result: x = 3, y = 6
```

```java
==>> Exam trick
boolean isOk = false;
if(isOk = true){  ==>> One equal sign is an assignment operator
				==>>  Two equal sign is an logical comparison operator
	System.out.println("A");
}else{
	System.out.println("B");
}
==>> Result: A 
==>> Because the isOk variable get re-assign as true and also return the true value.
```

```java
boolean isOk = false;
if(isOk == true){ ==>> The correct operator
	System.out.println("A");
}else{
	System.out.println("B");
}
==>> Result: B
```



---
## Flash cards section

What is the precedence of the assignment operator ( = )?
?
The assignment operator ( = ) has the lowest precedence. First, the operation on the right-hand side is performed, and the result is assigned to a variable on the left-hand side.
<!--SR:!2024-08-03,1,230-->

How does Java handle auto-casting with smaller to larger data types?
?
Java automatically promotes smaller data types to larger data types. For example: 
```java
short x = 5;
int y; y = x;
```
This is OK because `x` is casted to `int`.

Why can't you assign an `int` value to a `short` variable without explicit casting?
?
You cannot assign an `int` value to a `short` variable because `int` is a larger data type. For example: 
```java
int a = 5;
short b;
b = a;
```
This is not OK.

How do you explicitly cast a larger data type to a smaller data type?
?
You can explicitly cast a larger data type to a smaller data type by specifying the cast. For example: 
```java
int a = 5;
short b;
b = (short) a;
```
 This is OK.

Can you assign a `double` value to an `int` variable directly? Why or why not?
?
No, you cannot assign a `double` value to an `int` variable directly because `double` is a larger data type. For example: `int x = 1.0;` This is not OK.

Why can't you assign a `long` value to an `int` variable directly?
?
You can't assign a `long` value to an `int` variable because `long` is a larger data type. For example: `int y = 123L;` This is not OK.
<!--SR:!2024-08-06,4,270-->

Is it acceptable to assign an `int` value to a `long` variable? Why?
?
Yes, it is acceptable to assign an `int` value to a `long` variable because `int` is smaller than `long`. For example: `long z = 5;` This is OK.

How do you cast a `byte` value to a `long` variable?
?
You can cast a `byte` value to a `long` variable explicitly. For example: `long w = (byte) 7;` This is OK.

Why can't you assign a `double` value to a `float` variable directly?
?
You cannot assign a `double` value to a `float` variable directly because `double` is a larger data type. For example: `float k = 2.3;` This is not OK.

Why is it acceptable to assign an integer literal to a `short` variable directly?
?
It is acceptable because the compiler can figure out that the value is within the range of `short`. For example: `short a = 7;` This is OK.

What happens when you perform arithmetic operations with `short` and `byte`?
?
Whenever you perform operations with `short` and `byte`, all values are promoted to `int`, and the result is an `int`. For example: `short c = (short) (a + b);` This is OK.
<!--SR:!2024-08-06,4,270-->

What are compound assignment operators and provide an example?
?
Compound assignment operators are shorthand notations of assignment operations. For example: `a += 5` is equivalent to `a = a + 5`.

What does the assignment operator do in an expression?
?
The assignment operator assigns the value from the right-hand side to the left-hand side and also returns the value of the variable. For example:
```java
int x = 5;
int y = (x = 3) * 2;
```
The result is `x = 3` and `y = 6`.

What is the common mistake in the following code:
```java
boolean isOk = false
if(isOk = true) { ... }
```
?
The mistake is using a single equal sign ( = ) instead of a double equal sign ( == ) for comparison. The result will be `true` because the assignment operator reassigns `isOk` to `true`.

What is the correct way to compare a boolean variable in an if statement?
?
The correct way is to use the double equal sign ( == ) for comparison. For example:
```java
boolean isOk = false;
if(isOk == true) { ... }
```
The result will be `false`.










