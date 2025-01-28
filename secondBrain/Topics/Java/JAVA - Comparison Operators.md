---
Creation_date: 2024-03-03 12:02
Modification_date: Sunday 3rd March 2024 12:02:53
Indexes:
  - "[[operator]]"
---

----
## Comparison operators

1. Return a `boolean` value (*true or false*).
2. Equals operator (*a == b*). ^0c8660
	1. Primitives: returns true if values are the same.
	2. Objects: [[JAVA - Comparison Operators#^bf36c0|returns true if both values reference to the same object.]]
3. Not-equals operator (*a != b*) works in the same way.
	1. Primitives: returns false if values are the same.
	2. Objects: returns false if both values reference to the same object.
4. You can only compare values of similar type (*auto-casting applies*)
5. If both reference point to null, they are equal.

```java
String name1 = new String("John Wayne"); ==>> Same content
String name2 = new String("John Wayne"); ==>> but two different object
String name3 = name1; ==>> Now we create name3 and assign name1 to it.
```

```java
System.out.println(name1 == name2); ==>> name1 and name2 point to different objects, so the result is false.
```

```java
System.out.println(name1 == name3); ==>> name1 and name3 point to sanme objects, so the result is true.
```
^bf36c0
## Relational operators

These operators just straight forward.

| Operators  | Description                                                                         |
| ---------- | ----------------------------------------------------------------------------------- |
| <          | less                                                                                |
| <=         | less or equal                                                                       |
| >          | greater                                                                             |
| >=         | greater or equal                                                                    |
| instanceof | instanceof in Java is a comparison operator which specified in comparison data type |
### `instanceof`
- `instanceof` can compare the reference data type and return the value `true` or `false` base on the result.
	- `instanceof` can also compares the reference it's a specified type of a class or sub-class or a interface
	- It returns `true` or `false`.
```java
public class MyApp{
	public static void isInteger(Number num){
		if(num instanceof Integer){
			System.out.println(num + " is an Integer");
		}else{
			System.out.println(num + " is not an Integer");
		}
	}
	public static void main(String args[]){
		isInteger(5);
		isInteger(3.14);
	}
}

==>> Result: 5 is an Integer
==>> Result: 3.14 is not an Integer
```

- Comparing any object instance with a null type through `instanceof` operator returns a `false`. [[JAVA - Comparison Operators#^55f8bf|Example.]]
	- And if `null` on the right-hand side of  `instanceof` operator DOES NOT COMPILE.  [[JAVA - Comparison Operators#^098439|Example.]]
```java
public class Dog2 {
	public static void main(String args[]) {
		Dog2 d = null;
		System.out.println(d instanceof Dog2);// false
	}
}
```
^55f8bf

```java
public class Dog2 {
	public static void main(String args[]) {
		System.out.println(null instanceof null);// DOES NOT COMPILE.
	}
}
```
^098439

## Logical and Conditional operators

- AND: 
	- Logical AND: `true` if at least one of the operands is `true` : a & b 
	- Conditional AND: `true` if at least one of the operands is `true` : a && b 
- OR:
	- Logical inclusive OR: `true` if at least one is `true` : a | b
		- Logical exclusive OR (*XOR*): `true` only if one value is `true`, another is `false`: a ^ b
	- Conditional OR: `true` if at least one is `true` : a || b
- So, what is the difference between logical and conditional operators?
	- Conditional evaluation stops once the result can be determined.
	- This property is know as short-circuit
### Conditional operator
![[Pasted image 20240310145103.png]]

### Logical operator
![[Pasted image 20240310145155.png]]

### Short-circuit property
![[Pasted image 20240310145305.png]]


---
## Flash cards section

What do comparison operators return in Java? ;; A boolean value (true or false).

How does the equals operator (a == b) work for primitives? ;; Returns true if the values are the same.

How does the equals operator (a == b) work for objects? ;; Returns true if both values reference the same object.

How does the not-equals operator (a != b) work for primitives? ;; Returns false if the values are the same.

How does the not-equals operator (a != b) work for objects? ;; Returns false if both values reference the same object.

Can you compare values of different types in Java? ;; No, you can only compare values of similar types, though auto-casting applies.

What happens if both references point to null? ;; They are considered equal.

What will the following code print:
```java
String name2 = new String("John Wayne");
String name1 = new String("John Wayne");
System.out.println(name1 == name2);
```
?
False, because name1 and name2 point to different objects.

What will the following code print:
```java
String name1 = new String("John Wayne");
String name3 = name1;
System.out.println(name1 == name3);
```
?
True, because `name1` and `name3` point to the same object.

What are the relational operators in Java?
?
< (*less*), <= (*less or equal*), > (*greater*), >= (*greater or equal*)

What does the `instanceof` operator do in Java? ;; It compares the reference data type and returns true or false based on the result.

What can `instanceof` compare?
?
It can compare whether a reference is a specified type of a class, a subclass, or an interface.

What does the following code print:
```java
public class MyApp{
	public static void isInteger(Number num){
		if(num instanceof Integer){
			System.out.println(num + " is an Integer");
		}else{
			System.out.println(num + " is not an Integer");
		}
	}
	public static void main(String args[]){
		isInteger(5);
		isInteger(3.14);
	}
}
```
?
```java
5 is an Integer
3.14 is not an Integer
```

What is the result of comparing any object instance with a null type using `instanceof`? ;; It returns false.

What happens if null is on the right-hand side of the `instanceof` operator? ;; The code does not compile.

What does the following code print:
```java
public class Dog2 {
	public static void main(String args[]) {
		Dog2 d = null;
		System.out.println(d instanceof Dog2);
	}
}
```
?
`false`

What happens with the following code:
```java
public class Dog2 {
	public static void main(String args[]) {
		System.out.println(null instanceof null);
	}
}
```
?
`DOES NOT COMPILE.`

What is the logical AND operator in Java? ;; `a & b`, true if both operands are true.

What is the conditional AND operator in Java? ;; `a && b`, true if both operands are true and stops evaluation once the result can be determined.

What is the logical inclusive OR operator in Java? ;; `a | b`, true if at least one operand is true.

What is the logical exclusive OR (XOR) operator in Java? ;; `a ^ b`, true only if one operand is true and the other is false.

What is the conditional OR operator in Java? ;; `a || b`, true if at least one operand is true and stops evaluation once the result can be determined.

What is the difference between logical and conditional operators in Java? ;; Conditional operators stop evaluation once the result can be determined (short-circuit evaluation).
