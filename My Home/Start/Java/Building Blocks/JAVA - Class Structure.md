
----
Creation date: 2024-01-31 07:10
Modification date: Wednesday 31st January 2024 07:10:27

----

#Java  
#Done 

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
			- Modifier
			- The return type or void if the method not return a value
			- The method name
			- The parameter list in parenthesis
			- An exception list
			- The method body
		- And there are something called **Method signature**, it's a combination of two components:
			- Method name: 
				- Serving as a distinctive identifier within a class, the method name is used to call or invoke the method. It plays a pivotal role in the overall method signature.
			- Parameter Types:
				- In the process of defining a method, one specifies the types of parameters it can accept. These parameter types, along with their respective order, collectively form part of the method signature. They essentially articulate the expected input parameters for the method.
			- Purpose:
				- Therefore, the method signature is essentially a combination of the method name and its parameter types. ***This combination serves to differentiate one method from another within a class based on their names and the types and order of their parameters.*** While syntax variations may exist across different programming languages, the fundamental concept of a method signature remains consistently applicable.
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