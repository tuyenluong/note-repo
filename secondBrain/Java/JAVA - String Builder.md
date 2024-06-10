---
Creation_date: 2024-03-26 00:42
Modification_date: Tuesday 26th March 2024 00:42:32
Indexes:
  - "[[java]]"
---

----

## Creating a `StringBuilder`
- `StringBuilder` is a [[JAVA - What is mutable and immutable means|mutable]] class which contains a String
	- it has many useful methods for manipulation the strings
```java
StringBuilder name = new StringBuilder("John Wayne");
```
- Some methods work in the way identical with a normal String
	- `subString()`, `indexOf()`, `length()`,  and `charAt()`

### `append()` method
```java
StringBuilder name = new StringBuilder("John");
name.append("Wayne");
System.out.println(name);
==>>JohnWayne // StringBuilder is mutable
```

### chaining with `append()`
- `append()`also allow chaining method because all arguments are converted to String and you can use chaining.
- chaining is evaluate from left to right.
```java
StringBuilder name = new StringBuilder("John");
name.append("Wayne").append(1).append(true);
System.out.println(name);
==>>JohnWayne1true // all arguments are converted to String
```

### `insert()`
- `StringBuilder` provide an`insert()`method.
```java
StringBuilder name = new StringBuilder("John Wayne");
name.insert(5, "D. ");
System.out.println(name);
==>>John D. Wayne // insert into after the definded index. 
```

### chaining with `insert()`
- `insert()` allow chaining method because it's have the same reason with the `append()` method.
- chaining is evaluate from left to right.
```java
StringBuilder name = new StringBuilder("John Wayne");
name.insert(5, "D. ").insert(6, "A"); // insert "D." after index 5 first
System.out.println(name);            // and then insert "A" after index 6
==>>John DA. Wayne // which is the dot sign
```

### `delete(int start, int end)` method
- The `delete()` method of StringBuilder class removes the characters starting from index start to index end-1 from String contained by StringBuilder.
- This method takes two indexes as a parameter first start represents index of the first character and end Index represents index after the last character of the substring to be removed from String contained by StringBuilder and returns the remaining String as StringBuilder Object.
- **Parameters:** This method accepts two parameters: 
	- **start**: index of the first character of the substring.
	- **end**: index after the last character of the substring.

### `deleteCharAt(int index)` method
- The `deleteCharAt()`method of StringBuilder class removes the character index from a String contained by StringBuilder.
- If the integer pass in parameter is greater than the length of the String, then it will encounter the `StringIndexOutOfBoundsException`error. So be careful.

### `replace()`method
- These are actually two different method, the String `replace()` method and the StringBuilder `replace()` method. 
- 








---
## Flash cards section



