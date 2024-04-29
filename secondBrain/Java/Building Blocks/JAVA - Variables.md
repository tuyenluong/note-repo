
----
Creation date: 2024-02-23 01:23
Modification date: Friday 23rd February 2024 01:23:30

----

 Tags: [[java]]
## Variables (terminology)

- **Variable** is a name for a piece of memory which stores data
- To **declare a variable** means to state variable type and give it a name
```java
int x;
```
- To **initialize a variable** means to give a variable a value
```java
int x = 5;
```

- Name of the variable (method, class, interface, package...) is called **identifier**.
## Identifier rules

- Must begin with a letter, currency symbol or underscore 
```java
int first;
int $first;
int _first;
```
- Can include numbers, but **NOT** start with a number.
```java
int 1first; ==>> NOT OK
int first1; ==>> OK
int f1rst; ==>> OK
```
- Single underscore is not allowed as an identifier
```java
int _; ==>> NOT OK
```
- You cannot use the reserved word from Java. ^4706f6
	- These are the words that commonly used in Java, so you don't need to remember all of them.
	- ![[Pasted image 20240224140020.png]]

## Naming conventions

- For variables, use **camelCase**
- For constants, use **SNAKE_CASE**
- Identifiers of classes, interfaces, enums records start with first uppercase letter. Example:
	- MyClass
	- MyInterface
	- StudentRecord
- Identifiers variables and methods start with first lower letter. Example:
	- fullName
	- getFullName()
### JAVA IDENTIFIERS ARE CASE SENSITIVE !!
- Which means if you have two different variables with the same name and different uppercase and lowercase, Java will treated it as two different variables.
```java
int firstOrder; ==>> Two different variables
int firstORDER; ==>>
```
- Multiple variables can be declare and/or initialized in a single command.
- This is ok as long as all the variables is the same data type.
```java
==>> Bad practice, but it compiles
int x, y; 
String firstName = "John", lastName = "Wayne";
boolean v = true, w, z = false;
```
- But you cannot declare two variables with different data types in a single command. ^7254a8
```java
int x, String name; ==>> DOES NOT COMPILE
```
- What I means when I said "In a single command" not "in a single line"?
	- A single command is when a line a code end with a semi colon sign. [[JAVA - Variables#^0220b8|Example]]
	- And a singe line is just a line in the file.
	- And [[JAVA - Variables#^7254a8|"the two different data types in a single command"]] also [[JAVA - Variables#^1ada98|applied in this situation.]] 
```java
1| int x,  ==>> line 1, single line
2|     v;  ==>> command, single command
```
^0220b8
```java
1| int x,            
2|     String name;  ==>> DOES NOT COMPILE
```
^1ada98
## Three kinds of variables

1. [[JAVA - Class Structure#^57453a|Local variables]] - exist only within the block of code { ... }
2. [[JAVA - Class Structure#^320288|Instance variables (fields)]] -  defined within the specific instance of the object.
3. [[JAVA - Class Structure#^4f6c63|Class variables]] - belong to a class and is shared with all instances of the class.

- Local variables must be initialized before use !!
```java
public int doesNotCompile(){
	int a = 5;
	int b;
	return a + b; ==>> You are trying to use uninitialized variable b, so it won't compile
}
```

```java
public int doesCompile(){
	int a = 5, b = 3;
	int c;
	return a + b; ==>> c is not initialized, but it's never used, to this code compiles
}
```

- Be careful if initialization is within if-statement
```java
public void doesNotCompile(boolean isOk){
	int a;
	if (isOk){
		a = 5; ==>> Might never be reached
	}
	System.out.println(a); ==>> so this will not compile
}
```
```java
public void doesCompile(boolean isOk){
	int a;
	if (isOk){ ==>> Cause a will initialized one way or another.
		a = 5; 
	}else{
		a = 2;
	}
	System.out.println(a); ==>> so this will compile
}
```

- Final variables (constants)
	- Also called as constants
	- When a variable became constants is when you using keyword "final"
	- And once you assign a variable as final, you cannot change the value in the further course of the programs.
	- That's why it's used for constants.
	- If you try to change the final variable, you will get a error.

```java
final int MAX_HEIGHT = 100;
```

- Final can be applied to a reference:
```java
final int[] MY_NUMBERS = new int[5];
```

- Reference cannot be modified, but the **CONTENT OF THE OBJECT CAN**
```java
final int[] MY_NUMBERS = new int[5];
MY_NUMBERS[2] = 13; ==>> OK
MY_NUMBERS = null; ==>> DOES NOT COMPILE
```

## Variable scope

- Variables can go out of scope (cease to exist)

1. [[JAVA - Class Structure#^57453a|Local variables]]: in scope from { to }.
2. [[JAVA - Class Structure#^e7f712|Method parameters]]: in scope for the duration of the method.
3. [[JAVA - Class Structure#^320288|Instance variables (fields)]]: in scope from declaration until the object is eligible for garbage collector.
4. [[JAVA - Class Structure#^4f6c63|Class variables]] : in scope from declaration until the program ends.

- Scope example:
```java
if(isOk){
	int x = 5;
	System.out.println(x) ==>> OK
}
System.out.println(x) ==>> DOES NOT COMPILE
					==>> x is out of scope
```

