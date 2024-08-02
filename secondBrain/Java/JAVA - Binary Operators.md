---
Creation_date: 2024-03-03 12:01
Modification_date: Sunday 3rd March 2024 12:01:51
Indexes:
  - "[[operator]]"
---

----
## Arithmetic Binary Operators

```java
a + b ==>> addition
```

```java
a - b ==>> subtraction
```

```java
a * b ==>> multuplication
```

```java
a / b ==>> division
```

```java
a % b ==>> modulo operator
```

Example division:
- If `int a` was a double data type, then it will get the decimal number.
- But since `int a` is an integer, the result of this operation will get a FLOOR value.
- FLOOR value means that you ignore the decimal point and everything which is right of the decimal point.
```java
int a = 11 / 4;
==>> a = 2 (FLOOR value)
```

Example modulo:
- This operator will give you the reminder of the operation.
```java
int b = 11 % 4;
==>> b = 3 (reminder of division)
```
- Modulo is often used to determine odd and even numbers.
```java
if (n % 2 == 0){
	System.out.println("Number " + n + " is even.");
}else{
	System.out.println("Number " + n + " is odd.");
}
```

## Rules of numeric promotion

- If operands have different data types, Java automatically promotes one of the operands to a larger of two data types.
```java
short a = 17;
float b = 15;
double c = 35;
System.out.println(a * b / c);
==>> a and b are promoted to double, result is double
```
- If one value is integer, and another is decimal, Java promotes int to decimal.
```java
int intValue = 5; 
double decimalValue = 3.5; 
double result = intValue + decimalValue;
System.out.println(result);
==>>  The int value is promoted to double before addition
```
- `byte, short, char` are **always** first promoted to int before the operation is done (!!) ^94102f
```java
short x = 17;
short y = 15;
System.out.println(x + y);
==>> x and y are promoted to int, result is int
```

```java
short x = 17;
short y = 15;
short z = x + y
System.out.println(z);
==>> DOES NOT COMPILE, because this is violate the third rule. 
==>> byte, short, char are always first promoted to int before the operation is done
```
- The resulting value has the same data type as the promoted operands. 
```java
int intValue = 5; 
double decimalValue = 3.5; 
double result = intValue + decimalValue;
System.out.println(result);
==>>  The data types that get promoted is intvalue, so the result data type will be double as well.
```


---
## Flash cards section

What is the result of 11 divided by 4 if the result is assigned to an integer?
?
The result is 2 because integer division returns the floor value, ignoring the decimal part.
```java
int a = 11 / 4;
```

How do you determine the remainder of the division of 11 by 4?
?
Use the modulo operator: `int b = 11 % 4;` The result is 3.

How can you check if a number is even or odd using the modulo operator?
?
Use `if (n % 2 == 0)` for even and `else` for odd.
<!--SR:!2024-08-06,4,270-->

What happens if operands have different data types in an arithmetic operation?
?
Java promotes one of the operands to the larger of the two data types.

What will be the result and data type of the expression 
```java
short a = 17;
float b = 15;
double c = 35;
System.out.println(a * b / c);
```
?
The result will be a double because both `a` and `b` are promoted to double.

What happens when an integer and a decimal value are used in an arithmetic operation?
?
Java promotes the integer to a decimal before performing the operation.

What happens when you perform an arithmetic operation with `byte`, `short`, or `char`?
?
They are always promoted to `int` before the operation.

Why does this code not compile?
```java
short x = 17;
short y = 15;
short z = x + y;
```
?
Because `x` and `y` are promoted to `int`, making the result `int`, which cannot be assigned to `short` without explicit casting.

What will be the data type of the result if an `int` and a `double` are used in an arithmetic operation?
?
The result will be of type `double`.

What does the following code do:
```java
int intValue = 5;
double decimalValue = 3.5;
double result = intValue + decimalValue;
```
?
The `int` value is promoted to `double`, and the result is a `double` with the value 8.5.
<!--SR:!2024-08-06,4,270-->
