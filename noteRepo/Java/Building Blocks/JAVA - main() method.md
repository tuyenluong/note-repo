
----
Creation date: 2024-02-02 02:28
Modification date: Friday 2nd February 2024 02:28:56

----

#Java 

> If A is success in life, then A equals x plus y plus z. Work is x; y is play; and z is keeping your mouth shut.
> — <cite>Albert Einstein</cite>

1. Java program starts by executing the main() method:
	1. ![[Pasted image 20240206173202.png]]
2. There are other permissible ways to write the main method:
	1. public static void main(String[] args){ }
	2. public static void main(String[] someOthersSillyName){ }
	3. public static void main(String args[]){ }
	4. public static void main(String... args){ }
	5. public final static void main(final String[] args){ }
	6. static void main(String[] args){ }
3. Before we run the main method of its class, then must follow these steps first:
	1. javac --->>> to compile the file
	2. java --->>> filename that have the main method
	3. ***But javac command only required prior to Java 11***. At Java 11 and above, the java command can compile and auto-run your code and no .class file will be generated ^33c6b8
4. If lack of required parameters, then it will throw an out of bounds exceptions in array args of the main method. (*java Names John*)
	1. If the parameter is exceed the required parameter then it still able to run the program without any error, since the redundant parameter not affect the program. (*java Names John D. Wayne*)
	2. But you can use double quote to contains a multiple words into a String, then the java command will understand that it's 1 parameter. (*java Names "John D." Wayne*)


```java
public class Names {
	public static void main(String[] args){
		System.out.println("First name: " + args[0]);
		System.out.println("Last name: " + args[1]);
	}
}
```

```java
javac Names.java (compile into byte code)->> Names.class
```

```java
java Names John Wayne
	First name: John
	Last name: Wayne
```

```java
java Names John
	[index out of bounds exception]
```

```java
java Names John D. Wayne
	First name: John
	Last name: D.
```

```java
java Names "John D." Wayne
	First name: John D.
	Last name: Wayne
```