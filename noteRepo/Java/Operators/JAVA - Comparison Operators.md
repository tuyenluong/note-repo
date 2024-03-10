
----
Creation date: 2024-03-03 12:02
Modification date: Sunday 3rd March 2024 12:02:53

----

#Java  
#InProgress 

## Comparison operators

1. Return a boolean value (*true or false*).
2. Equals operator (*a == b*).
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

