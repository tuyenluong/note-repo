

----
Creation date: 2024-03-03 12:02
Modification date: Sunday 3rd March 2024 12:02:24

----

#Java  
#Done 

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



