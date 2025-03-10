---
Creation_date: 2024-01-31 07:10
Modification_date: Wednesday 31st January 2024 07:10:27
Indexes:
  - "[[java_building_block]]"
---


----

> Conflict is the gadfly of thought. It stirs us to observation and memory. It instigates to invention. It shocks us out of sheep like passivity, and sets us at noting and contriving.
> — <cite>John Dewey</cite>

- ***Classes***
	- ***Classes*** are basic building blocks of every Java program
	- To design a class means to describe parts and characteristics of these blocks 
	- In object-oriented programming,
		- Object is: 
			- In order to use a class you need to create *an object* (*most of the times)
			- You can think about a class as a blueprint, and a object as realization
		- Instance is:
			- An object is a single representation of the class, also called *instance* of a class
		- Reference is:
			- A *reference* variable that points to an object
- ***Fields*** and ***Methods***
	- Two elements (*members*) of Java classes are *fields* and *methods*
	- Fields
		- Fields are sometimes referred to *variables*. But to be precise:
		- **Class variables:** ^4f6c63
			- Definition: Variables declared with the *static* keyword after the type and before the name of the variable within a class.
			- Shared Data: Class variables are shared by all instances of the class.
		- **Instance Variables (Fields or Member Variables or Attributes or Properties):** ^320288
			- Definition: Variables declared within a class but outside of any method or block of code.
			- Scope: Instance variables are associated with an instance of the class and have different values for each instance.
		- **Local variables:** ^57453a
			- Definition: Variables declared within a method or block of code.
			- Scope: Limited to the method or block in which they are declared and are not accessible outside that scope.
		- **Parameters:** ^e7f712
			- Definition: Variables declared in method declarations, used to receive values from the caller.
			- Purpose: Parameters allow methods to accept input values and make the behaviour of the method more flexible.
	- Methods
		- Methods often perform actions or operations on the state (attributes or properties) of the current instance (object) of the class. The behaviour of a class is encapsulated within its methods, allowing objects to interact with each other and with their own internal state.
		- Method declarations have six components:
			- [[JAVA - Access Modifiers|Modifier]]
			- The return type or void if the method not return a value
			- The method name
			- The parameter list in parenthesis
			- An exception list
			- The method body
		- And there are something called **Method signature**, it's a combination of two components: ^c92110
			- Method name: 
				- Serving as a distinctive identifier within a class, the method name is used to call or invoke the method. It plays a pivotal role in the overall method signature.
			- Parameter Types:
				- In the process of defining a method, one specifies the types of parameters it can accept. These parameter types, along with their respective order, collectively form part of the method signature. They essentially articulate the expected input parameters for the method.
			- Purpose:
				- Therefore, the method signature is essentially a combination of the method name and its parameter types. ***This combination serves to differentiate one method from another within a class based on their names and the types and order of their parameters.*** While syntax variations may exist across different programming languages, the fundamental concept of a method signature remains consistently applicable.
			-  Be careful to some statement like below one. The Method signature did not include the return type.
				- "Overloading is the ability to have a class with multiple methods of the same name where the arguments and return type (method signature) allow the compiler to determine which of the same named methods were meant to be called."
			- Method signature and method overloading are not the same terms, although they are related concepts:
				- Method Signature: ^15d35c
					- The method signature consists of the method's name and the types and order of its parameters.
					- It uniquely identifies a method within a class or interface.
					- **The return type is not considered part of the method signature in Java.**
					- Method signature helps distinguish overloaded methods.
				- Method Overloading:
					- Method overloading refers to defining multiple methods in the same class with the same name but different method signatures.
					- These methods can have different numbers or types of parameters.
					- Method overloading allows for providing multiple ways to perform a similar operation with different parameter types or numbers.
					- It provides flexibility and convenience in programming, making code more readable and expressive.
- ***Comments***
	- Comments are used to make a code more readable.
		- They are ignored by the compiler.
	- There are three ways to comment out the text:
		- Comment until the end of a line: //
		- Comment everything within /* and \*/
		- Comment starting with /** (*Javadoc*) and end with \*/
- ***Classes and source files***
	- **Good practice to have each class in its own .java file:**
	    - This is a common practice in Java to enhance code organization and maintainability.
	- **Possible to have more classes in one file:**
	    - Yes, it is possible to have multiple classes in a single .java file.
	- **Only one of them is a top-level class:**
	    - Correct, in a Java file with multiple classes, only one class can be declared as the top-level class.
	- **Top-level class is almost always marked as public, but not necessary:**
	    - While it is a common convention to declare the top-level class as public, it's not strictly necessary. However, if the class is public, the file name must match the class name.
	- **If top-level class is marked as public, filename must match class name:**
	    - Correct, this is a Java naming convention. The filename must match the name of the public class in the file.
	- **Only one class in the .java file can be marked as public:**
	    - Yes, only one class in a Java file can be declared as public. If there's more than one public class, the compilation will fail.
	- **If there's another class marked as public, it will not compile:**
	    - Correct, having more than one public class in a Java file will result in a compilation error.



---
## Flash cards section

What is a class in Java? ;; A class is a basic building block of every Java program, describing the parts and characteristics of objects.

What is an object in Java? ;; An object is a realization of a class, often called an instance of the class.

What is an instance in Java? ;; An instance is a single representation of a class, also known as an object.

What is a reference in Java? ;; A reference is a variable that points to an object.
<!--SR:!2024-08-05,3,252-->

What are the two main elements of Java classes? ;; Fields and methods.

What are class variables? ;; Variables declared with the static keyword within a class, shared by all instances of the class.

What are instance variables? ;; Variables declared within a class but outside any method, associated with an instance and having different values for each instance.

What are local variables? ;; Variables declared within a method or block of code, limited in scope to that method or block.

What are parameters in Java? ;; Variables declared in method declarations, used to receive values from the caller.

What do methods in Java do? ;; Methods perform actions or operations on the state of the current instance of the class.

What are the six components of a method declaration? ;; Modifier, return type or void, method name, parameter list in parentheses, exception list, and method body.

What is a method signature in Java? ;; A combination of the method name and its parameter types.

Does the method signature include the return type? ;; No, the return type is not part of the method signature.

What is method overloading? ;; Defining multiple methods in the same class with the same name but different method signatures.

What is the purpose of comments in Java? ;; To make the code more readable, ignored by the compiler.

What are the three ways to comment out text in Java? ;; Single-line comments (//), block comments (/* ... _/), and Javadoc comments (/_* ... */).
<!--SR:!2024-08-06,4,270-->

Is it good practice to have each class in its own .java file? ;; Yes, to enhance code organization and maintainability.

Can you have multiple classes in one .java file? ;; Yes, but only one can be a top-level class.

What is a top-level class in Java? ;; The main class in a .java file, often marked as public but not necessarily.

What happens if the top-level class is marked as public? ;; The filename must match the class name.

How many classes in a .java file can be marked as public? ;; Only one. If there's more than one, the compilation will fail.

What will happen if there's another class marked as public in the same .java file? ;; The compilation will fail.










