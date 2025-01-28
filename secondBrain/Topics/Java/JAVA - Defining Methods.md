---
Creation_date: 2024-07-05 17:11
Modification_date: Friday 5th July 2024 17:11:36
Indexes:
  - "[[methods]]"
---

----
## The Syntax

```java
public final void printName(String name) throws InterruptedException{ }
```

[[JAVA - Class Structure#^c92110|What is Method signature?]]

![[Pasted image 20240705171351.png]]

- `Method signature` must come after the `return type`

```java
public void final printName(String name);
==>> DOES NOT COMPILE
```

- `return type` can be any primitive or object

```java
public int addNumbers(int a, int b){
	return a + b;
}
System.out.println(addNumbers(2, 3))
==>> 5
```

- `return type` must be consistent

```java
public int addNumbers(int a, int b){
	long c = 1L;
	return c * (a + b); // DOES NOT COMPILE due to the long data type
}
System.out.println(addNumbers(2, 3))
==>> DOES NOT COMPILE
```

## To keep in mind

- Method name is java identifier (*same rules as variable names*)
- Parameters in parameter list are separated by comma
- After `throws` there can be more than one exception, separated by comma
- Method must have a body `{}`, even if it is empty

```java
public void doNothing() { } // This is OK
```



---
## Flash cards section

The keywords like `final`, `static` can come before the return type. It's true? ;; False
<!--SR:!2024-08-06,4,250-->

What is the output of this code?
```java
public int addNumbers(int a, int b){
	long c = 1L;
	return c * (a + b); 
}
System.out.println(addNumbers(2, 3))
```
?
==>> DOES NOT COMPILE
<!--SR:!2024-08-14,12,272-->

What must come after the return type in a method declaration? ;; The method signature must come after the return type.

Does the following method declaration compile?
```java
public void final printName(String name);
```
 ?
 No, it does not compile because the method signature must come after the return type.

What can the return type of a method be in Java? ;; The return type can be any primitive type or object.

What is the output of the following code?
```java
public int addNumbers(int a, int b){ 
	return a + b; 
}
System.out.println(addNumbers(2, 3));
```
?
5

What must be consistent in a method's return type? ;; The return type must be consistent with the type of the value being returned.

Why does the following code not compile?
```java
public int addNumbers(int a, int b){ 
	long c = 1L; return c * (a + b);
}
System.out.println(addNumbers(2, 3));
```
?
The code does not compile because the method's return type is `int`, but it attempts to return a long value.

What rules do method names follow in Java? ;; Method names follow the same rules as variable names (*Java identifier rules*).

How are parameters in the parameter list separated? ;; Parameters in the parameter list are separated by commas.

What can come after the `throws` keyword in a method declaration? ;; More than one exception can come after the throws keyword, separated by commas.

Must a method in Java have a body? ;; Yes, a method must have a body, even if it is empty.

Is the following method declaration valid?
```
public void doNothing() { } ;
```
?
Yes, it is valid because it has a body, even though it is empty.













