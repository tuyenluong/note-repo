---
Creation_date: 2024-02-24 19:05
Modification_date: Saturday 24th February 2024 19:05:00
Indexes:
  - "[[operator]]"
---


----
## An operation consist of 3 part
- Operands ^d8d14f
- Operator
- Result

![[Pasted image 20240303132231.png]]
## There are three kinds of operators in java

- Unary operator
```java
a++;
```
- Binary operator
```java
a = b + c;
```
- Ternary operator
```java
a = (b > 0) ? 3 : 2
```


## Operator precedence

- Operator precedence means that some operators are executed before some others operators 
- And you've seen this in mathematics ([[JAVA - Operators in Java#^216732|Example:]]) or in some other programming languages.
	- In mathematics, the calculation with multiplication and division will be executed first
	- Along with the calculation within the parenthesis.

```java
a = 2 + (2*2) + (10/5) + 1
```
^216732

![[Pasted image 20240303101822.png]]

## What is the differences between Operator precedence and Operator associativity?

![[Pasted image 20240303102215.png]]

### A better table about the Operators precedence and associativity

- Precedence and associativity of Java operators. The table below shows all Java operators from highest to lowest precedence, along with their associativity. Most programmers do not memorize them all, and, even those that do, use parentheses for clarity. ^5c4efa

| Level  | Operator                                                            | Description                                                                                                                 | Associativity |
| ------ | ------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------- | ------------- |
| **16** | ()  <br>[]  <br>.                                                   | parentheses  <br>array access  <br>member access                                                                            | left-to-right |
| **15** | ++  <br>--                                                          | unary post-increment  <br>unary post-decrement                                                                              | left-to-right |
| **14** | +  <br>-  <br>!  <br>~  <br>++  <br>--                              | unary plus  <br>unary minus  <br>unary logical NOT  <br>unary bitwise NOT  <br>unary pre-increment  <br>unary pre-decrement | right-to-left |
| **13** | ()  <br>new                                                         | cast  <br>object creation                                                                                                   | right-to-left |
| **12** | * / %                                                               | multiplicative                                                                                                              | left-to-right |
| **11** | + -  <br>+                                                          | additive  <br>string concatenation                                                                                          | left-to-right |
| **10** | << >>  <br>>>>                                                      | shift                                                                                                                       | left-to-right |
| **9**  | < <=  <br>> >=  <br>instanceof                                      | relational                                                                                                                  | left-to-right |
| **8**  | ==  <br>!=                                                          | equality                                                                                                                    | left-to-right |
| **7**  | &                                                                   | bitwise AND                                                                                                                 | left-to-right |
| **6**  | ^                                                                   | bitwise XOR                                                                                                                 | left-to-right |
| **5**  | \|                                                                  | bitwise OR                                                                                                                  | left-to-right |
| **4**  | &&                                                                  | logical AND                                                                                                                 | left-to-right |
| **3**  | \|\|                                                                | logical OR                                                                                                                  | left-to-right |
| **2**  | ?:                                                                  | ternary                                                                                                                     | right-to-left |
| **1**  | =   +=   -=  <br>*=   /=   %=  <br>&=   ^=   \|=  <br><<=  >>= >>>= | assignment                                                                                                                  | right-to-left |
| **0**  | ->                                                                  | lambda expression arrow                                                                                                     | right-to-left |


---
## Flash cards section

What is the difference between unary and binary operators in Java? ;; Unary operators operate on a single operand (e.g., `a++`), while binary operators operate on two operands (e.g., `a = b + c`).

What is the ternary operator in Java and how is it used? ;; The ternary operator is `? :`, used for conditional expressions. For example, `a = (b > 0) ? 3 : 2` assigns `3` to `a` if `b` is greater than `0`, otherwise assigns `2`.

Given the expression `a = 2 + (2*2) + (10/5) + 1`, what is the result? ;; The result is `9`. The expression is evaluated with multiplication and division first, then addition.

What is operator precedence in Java? ;; Operator precedence determines the order in which operators are evaluated in an expression. Operators with higher precedence are evaluated before those with lower precedence.

What is the difference between operator precedence and operator associativity? ;; Operator precedence defines the order in which operators are evaluated, while associativity determines the order of operations for operators of the same precedence level (left-to-right or right-to-left).

Given the following code, what will be the output and explain why?
```java
int a = 5;
int b = 10;
int c = 2;
int result = a + b * c;
System.out.println(result);
```
?
The output will be `25`. Multiplication has higher precedence than addition, so `b * c` is evaluated first (`10 * 2 = 20`), and then `a + 20` (`5 + 20 = 25`).

What will be the result of the following expression considering operator precedence?
```java
int result = 3 + 4 * 2 / (1 - 5) ^ 2 ^ 3;
```
?
The result will be `3`. The expression is evaluated as follows:
1. `4 * 2 = 8`
2. `1 - 5 = -4`
3. `8 / -4 = -2`
4. `-2 ^ 2 = 0` (bitwise XOR, not exponentiation)
5. `0 ^ 3 = 3`
6. Finally, `3 + 3 = 6`

Given the following code, what will be the output and explain the precedence and associativity?
```java
int x = 10;
int y = 5;
int z = x > y ? x : y;
System.out.println(z);
```
?
The output will be `10`. The ternary operator `? :` has higher precedence than the `>` operator, so `x > y` is evaluated first. Since `10 > 5` is `true`, `x` is assigned to `z`.

Given the following code, determine the output and explain the use of operators:
```java
boolean result = true && false || true;
System.out.println(result);
```
?
The output will be `true`. The `&&` operator has higher precedence than the `||` operator, so `true && false` evaluates to `false`. Then `false || true` evaluates to `true`.

What will the following code output?
```java
int a = 8;
int b = 4;
int c = a / b * (2 + 3) % 3;
System.out.println(c);
```
?
The output will be `2`. Here’s the evaluation:
1. `2 + 3 = 5`
2. `a / b = 8 / 4 = 2`
3. `2 * 5 = 10`
4. `10 % 3 = 1`
