---
Creation_date: 2024-02-12 13:09
Modification_date: Monday 12th February 2024 13:09:49
Indexes:
  - "[[java_building_block]]"
---


----

 - Creating objects
	 - [[JAVA - Class Structure#^a36269|Object is an instance of the class.]] (*Object = house, Class = blueprint*)
	 - New object is created using a keyword called *new*:
		 - [[JAVA - Objects#^77110b|Student s = new Student();]]
	 - When an object created, *the constructor* of the object is called
	 - The constructor like method, but <u>no return type.</u>
		 - Which means the constructor will not having the <u>void</u> return type as well.
		 - [[JAVA - Objects#^6f7319|This is an example of a valid constructor.]]
	- But [[JAVA - Objects#^5a7d1c|if a constructor added a return type]], then will it compile?
		- The answer is YES!! It will compile. But this time, it will be treated as a method, not as a constructor anymore.
		- A valid constructor DO NOT have any return type, and the name of the constructor will be the same as the class name. The constructor naming is a convention to tell the different between a method and a constructor.
		- A [[JAVA - Objects#^5a7d1c|method naming convention]] is the first letter of the method name must be lowercase and must contains a return type or a void.
		- A [[JAVA - Objects#^6f7319|constructor naming convention]] is the constructor name must be identical as the class name and there will be no return type even a void.
	- If you don't provide any constructor, the compiler will generate [[JAVA - Objects#^2bbda1|a simple no-argument constructor]].
- Order of initialization
	- [[JAVA - Objects#^f93564|Static initialization blocks]] will run whenever the class is loaded first time in JVM, which means the static initialize block will run one time only when the class is initialize for the first time.
		- And it will run before any the constructor, data members and any initialization blocks.
	- [[JAVA - Objects#^4dbc9d|Initialization Blocks]] run in the same order in which they appear in the program.
		- [[JAVA - Objects#^a31683|If the data member placed before the Initialization block]] then the data member will run first.
		- On the other hands, [[JAVA - Objects#^33e48a|if the Initialization block is placed before the data member]], then it will run first.
	- And the [[JAVA - Objects#^4dbc9d|Initialization Blocks]] are executed whenever the class is initialized and before constructors are invoked. They are typically placed above the constructors within braces.
		- [[JAVA - Objects#^a4e19d|Example.]]

```java
Student s = new Student(); -->> new object is created and constructor is called.
```
^77110b

```java
public Student() { -->> this is a valid constructor.
	System.out.println("New student is created."); 
}
```
^6f7319

```java
public void Student() { -->> if the constructor added the return type??
	System.out.println("New student is created."); 
}
```
^5a7d1c

```java
public Student() { } -->> a simple no-argument constructor.
```
^2bbda1

```java
static  
{  
    System.out.println("1st static init");  
}
```
^f93564

```java
{
	System.out.println("1st instance init");
}
```
^4dbc9d

```java
{  
    System.out.println("2nd instance init");  -->> this will run first
}  
  
int j = 10; -->> run second
```
^a31683

```java
int j = 10; -->> this will run first
{  
    System.out.println("2nd instance init");  -->> run second
}  
```
^33e48a

```java
{  
    System.out.println("2nd instance init"); -->> this will run first
}
GFG(int x)
{
	System.out.println("ONE argument constructor"); -->> this will run after the Initializer Blocks
}
GFG()
{
	System.out.println("No  argument constructor"); -->> this will run after the Initializer Blocks
}
```
^a4e19d


---
## Flash cards section

What is the purpose of the `new` keyword in Java? ;; The `new` keyword is used to create new objects and invoke the constructor of the class.
<!--SR:!2024-08-06,4,270-->

How does the Java compiler handle a class if no constructor is provided? ;; If no constructor is provided, the Java compiler generates a default no-argument constructor.

What is a valid constructor in Java? ;; A valid constructor does not have a return type, not even `void`, and its name must match the class name exactly.

What happens if a constructor has a return type? ;; If a constructor has a return type, it is treated as a method, not a constructor.

Given this code, what will be the output?
```java
public class Student {
    public Student() {
        System.out.println("New student is created.");
    }
    public static void main(String[] args) {
        Student s = new Student();
    }
}
```
?
The output will be:
```java
New student is created.
```
This code creates a new `Student` object and invokes the constructor, which prints a message.

Analyze the following code. What will be the output and in what order will the statements execute?
```java
public class Test {
    static {
        System.out.println("1st static init");
    }
    {
        System.out.println("1st instance init");
    }
    {
        System.out.println("2nd instance init");
    }
    int j = 10;
    public Test() {
        System.out.println("Constructor");
    }
    public static void main(String[] args) {
        Test t = new Test();
    }
}
```
?
The output will be:
```java
1st static init
2nd instance init
1st instance init
Constructor
```
Explanation: The static initialization block runs first, followed by instance initialization blocks in the order they appear, then the constructor.

What is the order of execution for static initialization blocks, instance initialization blocks, and constructors? ;; The order of execution is: static initialization blocks (once per class load), instance initialization blocks (in the order they appear), and then constructors.

Given this code, what will be the output?
```java
public class GFG {
    {
        System.out.println("2nd instance init");
    }
    public GFG(int x) {
        System.out.println("ONE argument constructor");
    }
    public GFG() {
        System.out.println("No argument constructor");
    }
    public static void main(String[] args) {
        GFG obj = new GFG(10);
    }
}
```
?
The output will be:
```java
2nd instance init
ONE argument constructor
```
Explanation: The instance initialization block runs before the constructor, so the instance initialization block executes first, followed by the constructor with one argument.

Given this code, what will be the output and in what order will the statements execute?
```java
public class Example {
    int j = 10;
    {
        System.out.println("1st instance init");
    }
    {
        System.out.println("2nd instance init");
    }
    public Example() {
        System.out.println("Constructor");
    }
    public static void main(String[] args) {
        Example e = new Example();
    }
}
```
?
The output will be:
```java
2nd instance init
1st instance init
Constructor
```
Explanation: Instance initialization blocks execute in the order they appear, so "2nd instance init" is printed before "1st instance init", followed by the constructor.

What is the difference between instance initialization blocks and constructors? ;; Instance initialization blocks run whenever a class is initialized and before constructors are invoked. They are executed in the order they appear, whereas constructors are used to initialize new objects and can take parameters.