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

The keywords like `final`, `static` can come before the `return type`. It's true? ;; False
<!--SR:!2024-07-09,4,270-->

What is the output of this code?
```java
public int addNumbers(int a, int b){
	long c = 1L;
	return c * (a + b); // DOES NOT COMPILE due to the long data type
}
System.out.println(addNumbers(2, 3))
```
?
==>> DOES NOT COMPILE
<!--SR:!2024-07-11,3,252-->