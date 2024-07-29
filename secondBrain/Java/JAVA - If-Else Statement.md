---
Creation_date: 2024-03-10 14:55
Modification_date: Sunday 10th March 2024 14:55:25
Indexes:
  - "[[flow_control]]"
---

----

## The Syntax of If/Else statement

```java
if(expression1){
  // block of code 1
}else if(expression2){
  // block of code 2
}else if(expression3){
  // block of code 3
}else{
  // block of code 4
}
```

- Argument is `boolean` expression
- Block evaluates if expression is `true` 
	- `else-if` block is optional
	- But the `else-if` block can be as many as you want
- `else` block is also optional
	- but the `else` block just can be one only 
	- and the `else` block only exist only the `if` block present
- If there is only one command in the block, you can omit the curly bracket.



---
## Flash cards section

What is the purpose of the `else-if` block in an `if/else` statement? ;; The `else-if` block allows you to test multiple conditions sequentially. Each `else-if` block is optional and can be used as many times as needed to handle different scenarios.

Analyse the following code and determine the output:
```java
int x = 10;
if (x > 15) {
    System.out.println("Greater than 15");
} else if (x > 5) {
    System.out.println("Greater than 5");
} else {
    System.out.println("5 or less");
}
```
?
The output is `"Greater than 5"`, because `x` is 10, which satisfies the condition of the second `else-if` block.

What does the following code do?
```java
int x = 3;
if (x == 1) {
    System.out.println("One");
} else if (x == 2) {
    System.out.println("Two");
}
```
?
The code does not produce any output because `x` is neither 1 nor 2, and there is no `else` block to handle other cases.

What is the effect of omitting curly brackets for a single statement in an `if/else` block? ;; Omitting curly brackets when there is only one statement in a block is allowed. However, it is generally considered good practice to use curly brackets to avoid errors and improve readability.

Analyse this code and determine the output:
```java
int a = 7;
if (a > 10) {
    System.out.println("A");
} else if (a > 5) {
    System.out.println("B");
} else {
    System.out.println("C");
}
```
?
The output is `"B"`, because `a` is 7, which satisfies the condition of the second `else-if` block.

Determine the output of this code snippet:
```java
int y = 20;
if (y == 10) {
    System.out.println("Ten");
} else if (y == 20) {
    System.out.println("Twenty");
} else if (y == 30) {
    System.out.println("Thirty");
} else {
    System.out.println("None");
}
```
?
The output is `"Twenty"`, because `y` equals 20, which matches the condition of the second `else-if` block.

What will the following code output?
```java
boolean isRainy = false;
if (isRainy) {
    System.out.println("Stay inside");
} else {
    System.out.println("Go outside");
}
```
?
The output is `"Go outside"`, because `isRainy` is `false`, so the `else` block is executed.

Analyse this code and determine the output:
```java
int number = 5;
if (number > 10) {
    System.out.println("Number is greater than 10");
} else if (number == 5) {
    System.out.println("Number is 5");
} else {
    System.out.println("Number is something else");
}
```
?
The output is `"Number is 5"`, because `number` equals 5, which matches the condition of the second `else-if` block.



