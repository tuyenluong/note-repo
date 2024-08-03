---
Creation_date: 2024-07-08 21:23
Modification_date: Monday 8th July 2024 21:23:47
Indexes:
  - "[[methods]]"
---

----

## Variable Arguments (*Varargs*)

- Method can accept any number of parameters of the same type.
- Two rules to keep in mind:
	- A method can have at most one varargs argument
	- Varargs argument must be the last parameter in the parameter list

### Example

```run-java
public class Test{
	public static void greet (String greeting, String... names){
		for(String name : names){
			System.out.println(greeting + ", " + name +"!");
		}
	}
	public static void main(String... args){
		greet("Hello", "John", "George", "Luke");
	}
}
```


### You can pass an array as varargs

```run-java
public class Test{
	public static void greet (String greeting, String... names){
		for(String name : names){
			System.out.println(greeting + ", " + name +"!");
		}
	}
	public static void main(String... args){
	String[] allNames = {"Peter", "Paul"};
		greet("Hello", allNames);
	}
}
```

### You cannot pass an anonymous array (!!!)

```run-java
public class Test{
	public static void greet (String greeting, String... names){
		for(String name : names){
			System.out.println(greeting + ", " + name +"!");
		}
	}
	public static void main(String... args){
		greet("Hello", {"John", "George", "Luke"});
		// This anonymous array will not compile
	}
}
```

- You can pass a List or an [[JAVA - Creating an Array|Array]] in one single line, which is not recommended, but you can define a new array using the [[JAVA - Creating an Array#^2960c3|new]] keyword.
```run-java
public class Test{
	public static void greet (String greeting, String... names){
		for(String name : names){
			System.out.println(greeting + ", " + name +"!");
		}
	}
	public static void main(String... args){
		greet("Hello", new String[]{"John", "George", "Luke"});
		// init an array with `new` keyword will work
	}
}
```





---
## Flash cards section

The number of varargs arguments should be in the same data type. it's true? ;; Yes, it's true
<!--SR:!2024-10-09,68,310-->

Varargs argument can place anywhere in the parameter list. It's true? ;; No, it's false, it should be at the end of the parameterlist
<!--SR:!2024-09-26,55,310-->

A method can have more than one varargs argument. It's true? ;; No, it's false
<<<<<<< HEAD
<!--SR:!2024-09-13,42,290-->
=======
<!--SR:!2024-09-08,40,290-->
>>>>>>> 9bb2d12 ([Java] modify notes)


Will this code compile?
```java
public class Test{
	public static void greet (String greeting, String... names){
		for(String name : names){
			System.out.println(greeting + ", " + name +"!");
		}
	}
	public static void main(String... args){
		greet("Hello", new String[]{"John", "George", "Luke"});
	}
}
```
?
Yes, it's. Despite that initialize a new array using `new` keyword to pass into the varargs is not recommended, but it allow we to initialize an array and cast it into the varargs. So it's valid.
<!--SR:!2024-08-13,14,290-->

Can I pass an anonymous array into the varargs?
```java
public class Test{
	public static void greet (String greeting, String... names){
		for(String name : names){
			System.out.println(greeting + ", " + name +"!");
		}
	}
	public static void main(String... args){
		greet("Hello", {"John", "George", "Luke"});
	}
}
```
?
No, it will not compile.
Run the code to review.
```run-java
public class Test{
	public static void greet (String greeting, String... names){
		for(String name : names){
			System.out.println(greeting + ", " + name +"!");
		}
	}
	public static void main(String... args){
		greet("Hello", {"John", "George", "Luke"});
	}
}
```
<!--SR:!2024-08-16,14,290-->

**What is a varargs parameter in Java?** ;; A varargs parameter allows a method to accept any number of parameters of the same type, represented as an array.

**What are the two rules for using varargs in a method?** ;; A method can have at most one varargs argument, and the varargs argument must be the last parameter in the parameter list.
<!--SR:!2024-08-06,4,281-->

**Can a method have multiple varargs parameters?** ;; No, a method can have only one varargs parameter.
<!--SR:!2024-08-06,4,284-->

**Where must the varargs parameter be positioned in the method parameter list?** ;; The varargs parameter must be the last parameter in the method parameter list.

Given the following code, what will be the output?
```java
public class Test{
    public static void greet(String greeting, String... names){
        for(String name : names){
            System.out.println(greeting + ", " + name + "!");
        }
    }
    public static void main(String[] args){
        greet("Hello", "John", "George", "Luke");
    }
}
```
?
The output will be:
```java
Hello, John!
Hello, George!
Hello, Luke!
```
<!--SR:!2024-08-06,4,281-->

What is the output of this code?
```java
public class Test{
    public static void greet(String greeting, String... names){
        for(String name : names){
            System.out.println(greeting + ", " + name + "!");
        }
    }
    public static void main(String[] args){
        String[] allNames = {"Peter", "Paul"};
        greet("Hello", allNames);
    }
}
```
?
The output will be:
```java
Hello, Peter!
Hello, Paul!
```

What will happen if you try to use an anonymous array with varargs in this code?
```java
public class Test{
    public static void greet(String greeting, String... names){
        for(String name : names){
            System.out.println(greeting + ", " + name + "!");
        }
    }
    public static void main(String[] args){
        greet("Hello", {"John", "George", "Luke"});
    }
}
```
?
The code will not compile because Java does not support passing anonymous arrays directly with varargs.

What is the output of this code?
```java
public class Test{
    public static void greet(String greeting, String... names){
        for(String name : names){
            System.out.println(greeting + ", " + name + "!");
        }
    }
    public static void main(String[] args){
        greet("Hello", new String[]{"John", "George", "Luke"});
    }
}
```
?
The output will be:
```java
Hello, John!
Hello, George!
Hello, Luke!
```

**True or False: You can have more than one varargs parameter in a method.** ;; False. A method can have only one varargs parameter.

**True or False: Varargs must be the first parameter in a method parameter list.** ;; False. Varargs must be the last parameter in the method parameter list.

**True or False: Passing an anonymous array to a method with varargs is allowed in Java.** ;; False. Anonymous arrays cannot be passed directly with varargs.

**True or False: You must use the `new` keyword when creating an array to pass to a method with varargs.** ;; False. While using `new` is one way to create an array, it's not required. You can also pass a pre-defined array directly.

**True or False: The following method signature is valid: `public static void method(String... args, int... numbers)`.** ;; False. The varargs parameter must be the last parameter in the method signature.
