

----
Creation date: 2024-03-10 14:56
Modification date: Sunday 10th March 2024 14:56:01

----

#Java 
#Done 
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