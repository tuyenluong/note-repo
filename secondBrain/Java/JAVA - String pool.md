---
Creation_date: 2024-03-26 00:43
Modification_date: Tuesday 26th March 2024 00:43:03
Indexes:
  - "[[string]]"
---

----

## What is **String pool** or **intern pool**?

-  **String pool** is available from [[java-8-or-lower|Java 7 and onward]]
- **String pool** or **intern pool** is a place for JVM to stores new string with literal value into it.
- Now if you create a new string variable and assign it with the sane literal value.
	- Instead of creating a new memory spot for this literal value.
	- Java will save the memory and look in the **String Pool**.
	- new variable will point to the existing location in the **String Pool**.

## How do you prove that the new variable will point to the existing location of the Pool?

- You can test it by write a command like this
```java
String name = "John";
String the Name = "John";
System.out.println(name == theName);
==>> true 
```

^663b55


![[Pasted image 20240623111452.png]]

- This concept has been explained in [[JAVA - Garbage Collector|Garbage Collector lesson]]. It' the same with how stack and heap memory work.

## Tricky example

- What happens when you have 2 objects, s1 is "John" and s2 is "    John    ", and you added a `trim()`method to remove all the spaces before evaluate these two object to see if it's equals. What do you think the result is?

![[Pasted image 20240623135612.png]]

- The result will be false. Why you asked?

Because the Pool is created at Compile-time, and `trim()`is evaluated at Run-time. [[JAVA - What is the differ between Run-time and Compile-time|>>>See more what is the differ between Compile-time and Run-time]]

The compiler doesn't know that these two literals are equivalent because the `trim()`will be evaluated only at Run-time.

So the compiler treats this as two different literals and it will assign it to two different memory spots for each of these literals value. And as a consequence, s1 and s2 will point to the two different objects.

This is why s1 == s2 return `false`.

## Another example

- What do you think the result in this code below?

![[Pasted image 20240623143302.png]]

- The result will be true. Why you asked?

Because concatenation is done in the compile-time.

Unlike methods, when you apply methods, they are executed in the Run-time. But when you apply concatenation of strings, this is done in the Compile-time.

So now compiler knows that these are the same literals because this concatenation will be evaluated in Compile-time and then the compiler will figure out "John Wayne" and "John Wayne" are two identical literals and it will just perform this pull mechanism and both s1 and s2 will point to the same literal value.

## But there is a possibility to instruct the compiler to use the Pool, even when you have the Run-time.

### `intern()` method

[Reference for intern() method](https://www.javatpoint.com/java-string-intern)

The `intern()`method creates an exact copy of a _String_ object in the heap memory and stores it in the _String_ constant pool.
Note that, if another _String_ with the same contents exists in the String constant pool (*SCP*), then a new object won’t be created and the new reference will point to the other String.

![[Pasted image 20240624011005.png]]

- If you don't want the compiler to use the SCP, then you can achieve this by creating a new object with the keyword "new"
![[Pasted image 20240624011359.png]]

## A note from Java 9

Until [[java-8-or-lower|Java 8]], _Strings_ were internally represented as an array of characters – _char[]_, encoded in _UTF-16_, so that every character uses two bytes of memory.

With [[java-9|Java 9]] a new representation is provided, called _Compact Strings._ This new format will choose the appropriate encoding between _char[]_ and _byte[]_ depending on the stored content.

Since the new _String_ representation will use the _UTF-16_ encoding only when necessary, the amount of _heap_ memory will be significantly lower, which in turn causes less _Garbage Collector_ overhead on the _JVM._

[Reference by Baeldung page](https://www.baeldung.com/java-string-pool#a-note-about-java-9)