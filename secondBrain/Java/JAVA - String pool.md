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




---
## Flash cards section

What is the **String pool** or **intern pool** in Java? ;; The **String pool** or **intern pool** is a place where the JVM stores new strings with literal values. When a new string variable is created with the same literal value, it points to the existing location in the **String Pool** instead of creating a new memory spot.

From which Java version is the **String pool** available? ;; The **String pool** is available from Java 7 and onward.

How can you prove that a new string variable points to an existing location in the String Pool?
?
By creating two string variables with the same literal value and comparing them using the == operator. For example: 
```java
String name = "John"
String theName = "John";
System.out.println(name == theName); // true
```

Why does the comparison `s1 == s2` return false when `s1` is "John" and `s2` is " John " with `trim()` method applied? ;; Because the Pool is created at compile-time and `trim()` is evaluated at run-time. The compiler treats the two literals as different and assigns them to different memory spots.

What will be the result of the following code and why?
```java
String s1 = "John Wayne";
String s2 = "John " + "Wayne";
System.out.println(s1 == s2);
```
?
The result will be true because concatenation is done at compile-time. The compiler recognizes that the two literals are identical and uses the pool mechanism, making `s1` and `s2` point to the same literal value.

What is the purpose of the `intern()` method in Java? ;; The `intern()` method creates an exact copy of a `String` object in the heap memory and stores it in the String constant pool (SCP). If another `String` with the same contents exists in the SCP, the new reference will point to the existing `String`.

What happens if you create a new string object with the keyword `new`? ;; A new memory spot is allocated for the string, and it does not use the String Pool, resulting in a different object reference.

How were strings internally represented in Java 8 and earlier versions? ;; Strings were represented as an array of characters (`char[]`), encoded in UTF-16, with each character using two bytes of memory.

What change was introduced in Java 9 regarding string representation? ;; Java 9 introduced Compact Strings, which choose the appropriate encoding between `char[]` and `byte[]` depending on the stored content, reducing heap memory usage and Garbage Collector overhead on the JVM.

How does the == operator work when comparing string references? ;; The == operator compares the memory addresses of the string references to check if they point to the same object in memory.

What will be the result of the following code and why? 
```java
String s1 = "John";
String s2 = new String("John");
System.out.println(s1 == s2);
```
?
The result will be false because `s2` is created using the `new` keyword, which allocates a new memory spot, resulting in different object references.

How does the `equals()` method work when comparing strings? ;; The `equals()` method compares the actual content of the strings, rather than their memory addresses.

What will be the result of the following code and why?
```java
String s1 = "John";
String s2 = "John".trim();
System.out.println(s1 == s2);
```
?
The result will be false because `trim()` is evaluated at run-time, and the compiler treats the two literals as different, resulting in different memory spots.

What is the result of the following code and why?
```java
String s1 = "John";
String s2 = "John";
System.out.println(s1.equals(s2));
```
?
 The result will be true because the `equals()` method compares the actual content of the strings, which are identical.

**What is the purpose of the String pool (intern pool) in Java?**  ;; To store String literals and reuse them to save memory.

**How can you verify that two String variables point to the same location in the String pool?**  ;; By using the == operator to compare the two variables.

What is the output of the following code?
```java
String s1 = "John";
String s2 = "John";
System.out.println(s1 == s2);
```
?
`true`

**What happens when you use the `trim()` method on a String that was initially created with leading and trailing spaces?**  ;; The `trim()` method will remove the spaces but will not affect the reference in the String pool, resulting in a different reference for the trimmed string.

**What is the result of comparing two Strings created with leading and trailing spaces using == after applying the `trim()` method?**  ;; The comparison will return false if the original strings were not interned or pooled.
<!--SR:!2024-08-06,4,270-->

**What does the `intern()` method do to a String in Java?**  ;; It ensures that a String is added to the String pool and returns a reference to the pooled String.

What is the output of the following code?
```java
String s1 = "John";
String s2 = new String("John").intern();
System.out.println(s1 == s2);
```
?
`true`

What is the result of the following code snippet?
```java
String s1 = "John" + " Wayne";
String s2 = "John Wayne";
System.out.println(s1 == s2);
```
?
`true`

**Why does the concatenation of literals result in the same reference in the String pool?**  ;; Because concatenation of literals is evaluated at compile-time and results in a single literal in the pool.

What will be the result of the following code snippet?
```java
String s1 = new String("John").intern();
String s2 = new String("John").intern();
System.out.println(s1 == s2);
```
?
`true`

**How does Java 9's Compact Strings representation improve memory usage?**  ;; It uses `byte[]` for strings with characters in the ASCII range and `char[]` for other characters, reducing memory usage.

What will the following code output?
```java
String s1 = "   John   ";
String s2 = s1.trim();
System.out.println(s1 == s2);
```
?
`false`

**What is the effect of creating a new String object with `new String("example")` on the String pool?**  ;; It creates a new object on the heap, but does not affect the String pool.

What is the output of the following code?
```java
String s1 = "abc";
String s2 = new String("abc").intern();
System.out.println(s1 == s2);
```
?
`true`

**What happens if you compare two Strings that are created with `new String("value")` but are then interned?**  ;; They will refer to the same object in the String pool if interned.

What will be the result of comparing these two strings?
```java
String s1 = "Hello World";
String s2 = new String("Hello World").intern();
System.out.println(s1 == s2);
```
?
`true`

**What is the main difference between compile-time and run-time evaluation of Strings in Java?**  ;; Compile-time evaluation occurs during code compilation (e.g., concatenation of literals), while run-time evaluation occurs when the code is executed (e.g., method calls).

**What does the `intern()` method guarantee about String references?**  ;; It guarantees that the returned reference will point to a unique instance of the String in the String pool.
<!--SR:!2024-08-06,4,270-->

What is the output of the following code?
```java
String s1 = "foo";
String s2 = "f" + "oo";
System.out.println(s1 == s2);
```
?
`true`

What is the output of the following code?
```java
String s1 = new String("foo");
String s2 = "foo";
System.out.println(s1.intern() == s2);
```
?
`true`