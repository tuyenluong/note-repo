

----
Creation date: 2024-02-24 19:05
Modification date: Saturday 24th February 2024 19:05:00

----

#Java 
#Done 

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
| **3**  | \|                                                                  | logical OR                                                                                                                  | left-to-right |
| **2**  | ?:                                                                  | ternary                                                                                                                     | right-to-left |
| **1**  | =   +=   -=  <br>*=   /=   %=  <br>&=   ^=   \|=  <br><<=  >>= >>>= | assignment                                                                                                                  | right-to-left |
| **0**  | ->                                                                  | lambda expression arrow                                                                                                     | right-to-left |
