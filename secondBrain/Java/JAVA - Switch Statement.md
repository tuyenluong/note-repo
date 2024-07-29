---
Creation_date: 2024-03-10 14:56
Modification_date: Sunday 10th March 2024 14:56:01
Indexes:
  - "[[flow_control]]"
---

----

## The Syntax of Switch Statement

```java
swtich(variable) {
	case constantExpression1:
		// codes
		break;
	case constantExpression2:
		// codes
		break;
	case constantExpression2:
		// codes
		break;
	default:
		// codes
}
```

- Switch statement required curly bracket
	- `break` statement is optional
	- `default` block is optional
	- Can be placed anywhere in the statement
- You don't need curly bracket for the command block
- Allowed variable types: 
	- `int` (`Interger`), `byte` (`Byte`), `short` (`Short`), `char` (`Character`), String, `enum` type
	- But ***NOT*** `boolean`, `long`, `float`, and `double`!! Which will be easier if you remember the not allowed one.

### `break` statement is optional, but what happen if we don't use it in the Switch statement?
- If we remove the `break` statement, then the switch expression will find the correct case based on the expression, executed the block code and after that the compiler fall-through the next case or cases.
- But in some cases, this is not what we want, so we used `break` statement.
Example:
```java
int variable = 1   ==>> if variable is the first case
swtich(variable) {
	case 1:
		System.out.println("Morning");  ==>> then the compiler will fall into case 1 
	case 2:
		System.out.println("Afternoon");  ==>> and then walk-through the rest of the 
	case 3:                              
		System.out.println("Evening");    ==>> cases: case 2, case 3, 
	default:
		System.out.println("hello");    ==>> and even the default one.
}
==>> Result: 
Morning
Afternoon
Evening
hello
```

```java
int variable = 2   ==>> if variable is the secoond case
swtich(variable) {
	case 1:
		System.out.println("Morning");  ==>> because the variable is 2 
	case 2:
		System.out.println("Afternoon");  ==>> then the compiler will fall into case 2  
	case 3:                              
		System.out.println("Evening");    ==>> and then walk-through the rest of the
	default:
		System.out.println("hello");    ==>> cases: case 2  and even the default one.
}
==>> Result: 
Afternoon
Evening
hello
```

### `switch` syntax before and after Java 14 released.

- Combining values (*before Java 14*)
	- Purpose: Same block a code will be executed but have 2 difference values.
```java
int variable = 1
swtich(variable) {
	case 1:  ==>> if `variable` are 1 or 2 is meet,
	case 2:  ==>> then this block of code will be executed 
		System.out.println("Afternoon"); 
		break;
	case 3:                              
		System.out.println("Evening"); 
		break;
	default:
		System.out.println("hello"); 
		break;
}
==>> Result: Afternoon
```

- Combining values (*Java 14 and so on*)
	- In Java 14 and so on, cases could be in the same line.
```java
int variable = 2
swtich(variable) {
	case 1: case 2: case 3: ==>> Starting from Java 14, cases can be in the same line
		System.out.println("Evening"); 
		break;
	default:
		System.out.println("hello"); 
		break;
}
==>> Result: Evening
```
### `default` block is optional and can be placed anywhere in the statement?

- `default` could be anywhere in the block
- but be careful if there no `break` statement

```java
int variable = 5  
swtich(variable) {
	case 1:
		System.out.println("Morning");
	default:  ==>> because case 1, 2, and 5 is not correct 
	          ==>> so it fall into the default statement
		System.out.println("hello");
	case 2:   ==>> but because there is no `break` statement,
	          ==>>  the compiler keep on fall-through next cases
		System.out.println("Afternoon");
	case 3:                              
		System.out.println("Evening");
    
}
==>> Result: 
hello
Afternoon
Evening
```




---
## Flash cards section

**What types of variables are allowed in a traditional switch statement?**  
;; `int`, `byte`, `short`, `char`, `String`, and `enum`. Not allowed: `boolean`, `long`, `float`, `double`.

**Is the `break` statement required in a switch statement?**  ;; No, `break` is optional. If omitted, the execution falls through to subsequent cases.

**What happens if you omit the `break` statement in a switch statement?**  ;; The switch will fall through and execute subsequent case blocks until it encounters a `break` or the end of the switch.

What does the following code output?
```java
int variable = 1;
switch(variable) {
    case 1:
        System.out.println("Morning");
    case 2:
        System.out.println("Afternoon");
    case 3:
        System.out.println("Evening");
    default:
        System.out.println("hello");
}
```
?
```java
Morning
Afternoon
Evening
hello
```

What will the following code output?
```java
int variable = 2;
switch(variable) {
    case 1:
        System.out.println("Morning");
    case 2:
        System.out.println("Afternoon");
    case 3:
        System.out.println("Evening");
    default:
        System.out.println("hello");
}
```
?
```java
Afternoon
Evening
hello
```

**What was a major syntax improvement for combining case values in Java 14?**  
;; In Java 14 and onwards, you can combine case values on the same line.

**What is the output of this Java 14+ switch statement?**
```java
int variable = 2;
switch(variable) {
    case 1: case 2: case 3:
        System.out.println("Evening");
        break;
    default:
        System.out.println("hello");
}
```
?
```java
Evening
```

**Can the `default` block be placed anywhere in the switch statement?**  ;; Yes, the `default` block can be placed anywhere, but be cautious as it can lead to fall-through if no `break` is present.

**What is the output of this code with a misplaced `default` block?**
```java
int variable = 5;
switch(variable) {
    case 1:
        System.out.println("Morning");
    default:
        System.out.println("hello");
    case 2:
        System.out.println("Afternoon");
    case 3:
        System.out.println("Evening");
}
```
?
```java
hello
Afternoon
Evening
```

What does the following code output, and why?
```java
int variable = 4;
switch(variable) {
    case 2:
        System.out.println("Two");
    case 4:
        System.out.println("Four");
        break;
    default:
        System.out.println("Default");
}
```
?
```java
Four
```

**What happens if a switch statement does not have a `default` case?**  
;; If all case values are covered, the absence of a `default` case is not problematic. If not all cases are covered, it may lead to incomplete execution depending on the context.

What does the following code output, and why?
```java
int variable = 0;
switch(variable) {
    case 0:
    case 1:
        System.out.println("A");
        break;
    case 2:
        System.out.println("B");
        break;
    default:
        System.out.println("C");
}
```
?
```java
A
```










