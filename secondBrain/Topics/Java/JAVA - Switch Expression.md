---
Creation_date: 2024-03-10 14:56
Modification_date: Sunday 10th March 2024 14:56:33
Indexes:
  - "[[flow_control]]"
---

----
Expression only available for Java 17 and above only

- Improved syntax for combining values from Java 8 to Java 17

[[java-8-or-lower|Java 8 version]]
```java
==>> Java 8
==>> Standard way to use Switch statment
switch(a){
	case 0:
	case 1:
	case 2:
		System.out.println("Good day");
		break;
	case 3:
	case 4:
		System.out.println("Hi");
		break;
	default:
		System.out.println("Hello");
		break;
	
}
```

[[java-17|Java 17 version]]
```java
==>> Java 17
==>> Able to combind and delimate values by commas 
==>> but this way it not recommended
switch(a){
	case 0, 1, 2:
		System.out.println("Good day");
		break;
	case 3, 4:
		System.out.println("Hi");
		break;
	default:
		System.out.println("Hello");
		break;
	
}
```
## Preferred syntax in Java 17
```java
 ==>> Used "->" instead of ":"
 ==>> No need for break statement
 switch(a){
	 case 0, 1, 2 -> System.out.println("Good day");
	 case 3, 4 -> System.out.println("Hi");
	 default -> System.out.println("Hello");
 }
```

 - Multiple commands should be in the block code:
```java
 switch(a){
	 case 0, 1, 2 -> {
		 System.out.println("Good day");
		 System.out.print(" to you");
	 } 
	 case 3, 4 -> System.out.println("Hi");
	 default -> System.out.println("Hello");
 }
```

## But the real improvement is that Switch statement can be treated as an expression
```java
==>> Now this swtich expression has a value which you can assign to a variable
String greeting =  switch(a){
					 case 0, 1, 2 -> "Good day";
					 case 3, 4 -> "Hi";
					 default -> "Hello";
				}; ==>> This swtich expression used the semicolon becasue the compiler 
				   ==>> treated it as a expression.
				   ==>> String greeting = <expression>;
System.out.println(greeting);
```

- We can use `yield` keyword (*similar to return statement in methods*)
	- `yield` only used for switch expression only.
```java
int a = 1
String greeting =  switch(a){
					 case 0, 1, 2 -> {
						 String arg1 = "Good";
						 String arg2 = " day";
						 yield arg1 + arg2;
					 }
					 case 3, 4 -> "Hi";
					 default -> "Hello";
				};
System.out.println(greeting);
```

- Another examples
```java
public void greeet (int a, int b){
	String greeting =  switch(a){
					 case 0 -> "Good morning";
					 case 1 -> {
						 if(b > 0){
							 yield "Good morning";
						 } else{
							 yield "Good afternoon";
						 }
					 }
					 case 2 -> "Good afternoon";
					 default -> "Hello";
				};
	System.out.println(greeting);
}
greet (1, -1);
==>> Result: Good afternoon
```

- You can use `yield` in a single statement (*but this is not a good practice*)
	- If you use this case, then make sure that the `yield` keyword is inside the block of code
```java
public void greeet (int a){
	String greeting =  switch(a){
					 case 0, 1, 2 -> "Good day";
					 case 3, 4 -> { yield "Hi" };
					 default -> "Hello";
				};
	System.out.println(greeting);
}
greet (3);
==>> Result: Hi
```

### Switch expression can return different values types using in [[JAVA - Local Variable Type Inference|type inference]].

```java
public void greeet (int a){
	var greeting =  switch(a){
					 case 0 -> "Good morning"; ==>> String
					 case 1 -> 7;  ==>> int
					 case 2 -> true;  ==>> boolean
					 default -> 3.14;  ==>> double
				};
	System.out.println(greeting);
}
greet (2);
==>> Result: true
```
- The type of the inference variable will be determined in the runtime depending on the value.

### SWITCH EXPRESSION MUST HANDLE ALL POSSIBLE CASES!!
- When you using the switch expression, _switch expressions_ need to be exhaustive.
- Intuitively, _expressions_ have to evaluate to a value, but statements don't have to. Therefore, switch expressions have to cover all cases. If they don't, then there will be situations where it can't evaluate to anything.
- A switch expression must be exhaustive , or a compile-time error occurs. [Documentation](https://docs.oracle.com/javase/specs/jls/se19/preview/specs/patterns-switch-record-patterns-jls.html#jls-15.28.1)
- But this case can be possible if we use `default` statement.
```java
public void greeet (int a){
	var greeting =  switch(a){  ==>> Becasue if a variable don't return any value
	                            ==>> then this switch expression will not
	                            ==>> return anything.
					 case 0 -> "Good morning"; 
					 case 1 -> "Good afternoon";
					 case 2 -> "Good afternoon";
				};
	System.out.println(greeting);
}
greet (2);
==>> Result: DOES NOT COMPILE
```

### Solution is use `enum`

- If we use `enums`, we can just list all possible values
```java
enum Compass {NORTH, SOUTH, EAST, WEST}

String getDirection (Compass value){
	return swtich(value){
		case NORTH -> "Up";
		case SOUTH -> "Down";
		case EAST -> "Right";
		case WEST -> "Left";
	}
}
```



---
## Flash cards section

**What is a significant syntax improvement for switch statements in Java 17?** ;; The use of `->` instead of `:` and the elimination of the need for `break` statements.

**What is the preferred syntax for a switch statement in Java 17 when using multiple cases?** 
?
Use a comma to separate multiple cases and `->` for the action, like this:
```java
switch(a) {
    case 0, 1, 2 -> System.out.println("Good day");
    case 3, 4 -> System.out.println("Hi");
    default -> System.out.println("Hello");
}
```

**How can you handle multiple commands within a single case block in a Java 17 switch expression?**  
?
By using curly braces `{}` to create a block of code, like this:
```java
switch(a) {
    case 0, 1, 2 -> {
        System.out.println("Good day");
        System.out.print(" to you");
    }
    case 3, 4 -> System.out.println("Hi");
    default -> System.out.println("Hello");
}
```

**How does a switch expression return values in Java 17?**  
?
By assigning the result of the switch expression to a variable, like this:
```java
String greeting = switch(a) {
    case 0, 1, 2 -> "Good day";
    case 3, 4 -> "Hi";
    default -> "Hello";
};
```

What is the output of the following switch expression code?
```java
int a = 1;
String greeting = switch(a) {
    case 0, 1, 2 -> {
        String arg1 = "Good";
        String arg2 = " day";
        yield arg1 + arg2;
    }
    case 3, 4 -> "Hi";
    default -> "Hello";
};
System.out.println(greeting);
```
?
`Good day`

**What does the `yield` keyword do in a switch expression?**  
;; It returns a value from a case block of a switch expression.

What is the result of the following code?
```java
public void greet(int a) {
    String greeting = switch(a) {
        case 0 -> "Good morning";
        case 1 -> {
            if (a > 0) {
                yield "Good morning";
            } else {
                yield "Good afternoon";
            }
        }
        case 2 -> "Good afternoon";
        default -> "Hello";
    };
    System.out.println(greeting);
}
greet(1);
```
?
`Good morning`

**What happens if you use `yield` in a single statement block in a switch expression?**  
?
It is valid but not recommended. Example:
```java
public void greet(int a) {
    String greeting = switch(a) {
        case 0, 1, 2 -> "Good day";
        case 3, 4 -> { yield "Hi"; }
        default -> "Hello";
    };
    System.out.println(greeting);
}
greet(3);
```
`Hi`

**What types of values can a switch expression in Java 17 return?**  
;; It can return different types of values depending on the case, such as `String`, `int`, `boolean`, or `double`.

What is the output of the following code with type inference?
```java
public void greet(int a) {
    var greeting = switch(a) {
        case 0 -> "Good morning"; // String
        case 1 -> 7;              // int
        case 2 -> true;           // boolean
        default -> 3.14;          // double
    };
    System.out.println(greeting);
}
greet(2);
```
?
`true`

**What is required for a switch expression to compile in Java 17?**  
;; It must handle all possible cases or provide a `default` case.

What will be the result of the following switch expression code if `default` is missing?
```java
public void greet(int a) {
    var greeting = switch(a) {
        case 0 -> "Good morning";
        case 1 -> "Good afternoon";
        case 2 -> "Good evening";
    };
    System.out.println(greeting);
}
greet(3);
```
?
`DOES NOT COMPILE`

**How can using `enum` improve handling of switch expressions?**  ;; By listing all possible values of the `enum`, ensuring all cases are covered.

**How can you ensure a switch expression handles all possible cases?**  
;; By providing a `default` case or using an `enum` to list all possible values.

**What is the output of the following code using an `enum` in a switch expression?**
```java
enum Compass {NORTH, SOUTH, EAST, WEST}

String getDirection(Compass value) {
    return switch(value) {
        case NORTH -> "Up";
        case SOUTH -> "Down";
        case EAST -> "Right";
        case WEST -> "Left";
    };
}
System.out.println(getDirection(Compass.EAST));
```
?
`Right`

