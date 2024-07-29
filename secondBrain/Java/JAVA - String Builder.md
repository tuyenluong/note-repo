---
Creation_date: 2024-03-26 00:42
Modification_date: Tuesday 26th March 2024 00:42:32
Indexes:
  - "[[string]]"
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
- The `delete()` method of StringBuilder class removes the characters from index start to index end-1 from String contained by StringBuilder.
- This method takes two indexes as a parameter first start represents index of the first character and end Index represents index after the last character of the substring to be removed from String contained by StringBuilder and returns the remaining String as StringBuilder Object.
- **Parameters:** This method accepts two parameters: 
	- **start**: index of the first character of the substring.
	- **end**: index after the last character of the substring.

### `deleteCharAt(int index)` method
- The `deleteCharAt()`method of StringBuilder class removes the character index from a String contained by StringBuilder.
- If the integer pass in parameter is greater than the length of the String, then it will encounter the `StringIndexOutOfBoundsException`error. So be careful.

### `replace(int startIndex, int endIndex, String)`method
- These are actually two different method, the String `replace()` method and the StringBuilder `replace()` method. 
- It removes characters from start index to end index (*end index will be excluded*) and inserts new String.
- In below case, `b` and `c` will be removed and `JOHN` will be inserted.
```java
StringBuilder sb = new StringBuilder("abcdef");
sb.replace(1, 3, "John")    // insert "D." after index 5 first
System.out.println(sb);     // and then insert "A" after index 6
==>>John DA. Wayne          // which is the dot sign
```
- If the end index is to large, `replace()` through the end (*no exception!*)
- Although 100 is greater than the length of the String, but for the compiler, this just means go through the end of the String
```java
StringBuilder name = new StringBuilder("John Wayne");
name.replace(5, 100, "Doe"); 
System.out.println(name);   
==>>John Doe
```

## `reverse()`method
- `reverse()`method is a straightforward method, it will reverse the given string in the StringBuilder object. 
```java
StringBuilder name = new StringBuilder("LUKA");
name.reverse(); 
System.out.println(name);   
==>>AKUL
```

## `toString()`method
- `toString()`method helps return a String object from the StringBuilder object.
- This method not just present is StringBuilder class, but also present in many other classes that inherited from the Object class.
```java
StringBuilder name = new StringBuilder("John Wayne");
String strName = name.toString();
```

## StringBuilder doesn't implement `equals()`method!!
- `equals()` is the same as [[JAVA - Comparison Operators#^0c8660|equals operator]]
```java
StringBuilder name1 = new StringBuilder("John Wayne");
StringBuilder name2 = new StringBuilder("John Wayne");
System.out.println(name1 == name2);   
==>>false
System.out.println(name1.equals(name2));   
==>>false
```
- If you want to compare the content, we have to convert it back to String:
```java
StringBuilder name1 = new StringBuilder("John Wayne");
StringBuilder name2 = new StringBuilder("John Wayne");
System.out.println(name1.toString().equals(name2.toString()));   
==>>true
```

## `subString()`doesn't change the StringBuilder content if it don't returns a String
- The `subString()`method in the StringBuilder class need to return to a String variable, other wise it will not apply the changes on the StringBuilder content.
```java
StringBuilder name = new StringBuilder("John Wayne");
name.subString(2, 6);
System.out.println(name);   
==>>John Wayne
```

- Here are the fix code:
```java
StringBuilder name = new StringBuilder("John Wayne");
String subName = name.subString(2, 6);
System.out.println(subName);   
==>>hn W
```




---
## Flash cards section

What is `StringBuilder` in Java? ;; `StringBuilder` is a mutable class that contains a string and provides many methods for manipulating the string.

Which methods in `StringBuilder` work similarly to those in a normal `String`? ;; `subString()`, `indexOf()`, `length()`, and `charAt()`.

What does the `append()` method do in `StringBuilder`? ;; It appends the specified string to the end of the current `StringBuilder` object.

What is the result of chaining `append()` methods in `StringBuilder`? ;; Allows multiple append operations in a single statement, converting all arguments to strings and evaluating from left to right.

How does the `insert()` method in `StringBuilder` work? ;; It inserts the specified string at the given index of the `StringBuilder` object.

Explain the `delete(int start, int end)` method in `StringBuilder`. ;; Removes characters from the `start` index to the `end-1` index from the `StringBuilder` object and returns the remaining string as a `StringBuilder` object.

What does the `deleteCharAt(int index)` method do in `StringBuilder`? ;; Removes the character at the specified index from the `StringBuilder` object.

Describe the `replace(int startIndex, int endIndex, String)` method in `StringBuilder`. ;; Removes characters from the `startIndex` to `endIndex-1` and inserts the specified string at the `startIndex` position. If `endIndex` is too large, it replaces characters up to the end of the string.

What does the `reverse()` method do in `StringBuilder`? ;; Reverses the sequence of characters in the `StringBuilder` object.

How does the `toString()` method work in `StringBuilder`? ;; Converts the `StringBuilder` object to a `String` object.

Does `StringBuilder` implement the `equals()` method? ;; No, `equals()` in `StringBuilder` behaves the same as the == operator, comparing object references rather than content.

How can you compare the content of two `StringBuilder` objects? ;; Convert them to strings using the `toString()` method and then use the `equals()` method on the resulting strings.

Does the `subString()` method change the content of `StringBuilder`? ;; No, the `subString()` method does not change the `StringBuilder` content. It needs to be assigned to a `String` variable to see the substring.

What is the result of this code?
```java
StringBuilder name = new StringBuilder("John");
name.append("Wayne");
```
 ?
 The result is `JohnWayne`, as the `append()` method modifies the original `StringBuilder` object.

What will be the output of this code?
```java
StringBuilder name = new StringBuilder("John Wayne");
name.insert(5, "D. ");
System.out.println(name);
```
?
The output will be `John D. Wayne`.

Explain the difference in behaviour when `subString()` is used with and without assigning to a `String` variable. ;; Without assigning to a `String` variable, `subString()` does not affect the `StringBuilder` content. When assigned to a `String` variable, it extracts the substring.

What is the purpose of the `StringBuilder` class in Java? ;; `StringBuilder` is a mutable class that allows for efficient manipulation of strings.

What will be the result of the following code?
```java
StringBuilder name = new StringBuilder("John");
name.append("Wayne");
System.out.println(name);
```
?
The result will be:
```java
JohnWayne
```

How does chaining work with the `append()` method in `StringBuilder`? ;; Chaining works by allowing multiple `append()` calls to be combined in a single statement, with each argument being converted to a String and concatenated.

What is the result of the following code?
```java
StringBuilder name = new StringBuilder("John");
name.append("Wayne").append(1).append(true);
System.out.println(name);
```
?
The result will be:
```java
JohnWayne1true
```

What does the `insert()` method do in `StringBuilder`? ;; The `insert()` method adds a substring at a specified index in the `StringBuilder` object.

What will be the output of the following code?
```java
StringBuilder name = new StringBuilder("John Wayne");
name.insert(5, "D. ");
System.out.println(name);
```
?
The output will be:
```java
John D. Wayne
```

What is the result of the following code using `insert()` with chaining in StringBuilder?
```java
StringBuilder name = new StringBuilder("John Wayne");
name.insert(5, "D. ").insert(6, "A");
System.out.println(name);
```
?
The result will be:
```java
John DA. Wayne
```

How does the `delete(int start, int end)` method work in `StringBuilder`? ;; It removes characters from index `start` to index `end-1` from the `StringBuilder` object.

What will be the output of the following code?
```java
StringBuilder sb = new StringBuilder("abcdef");
sb.delete(1, 3);
System.out.println(sb);
```
?
The output will be:
```java
adef
```

What does the `deleteCharAt(int index)` method do in `StringBuilder`? ;; It removes the character at the specified index from the `StringBuilder` object.

What is the result of the following code?
```java
StringBuilder sb = new StringBuilder("abcdef");
sb.deleteCharAt(2);
System.out.println(sb);
```
?
The result will be:
```java
abdef
```

How does the `replace(int startIndex, int endIndex, String)` method work in `StringBuilder`? ;; It replaces the characters from `startIndex` to `endIndex-1` with the provided string.

What will be the output of the following code?
```java
StringBuilder sb = new StringBuilder("abcdef");
sb.replace(1, 3, "John");
System.out.println(sb);
```
?
The output will be:
```java
aJohndef
```

What does the `reverse()` method do in `StringBuilder`? ;; It reverses the sequence of characters in the `StringBuilder` object.

What will be the result of the following code?
```java
StringBuilder name = new StringBuilder("LUKA");
name.reverse();
System.out.println(name);
```
?
The result will be:
```java
AKUL
```

How does the `toString()` method work with `StringBuilder`? ;; The `toString()` method converts the `StringBuilder` object to a `String` object.

What will be the output of the following code?
```java
StringBuilder name = new StringBuilder("John Wayne");
String strName = name.toString();
System.out.println(strName);
```
?
The output will be:
```java
John Wayne
```

How does `StringBuilder` handle the `equals()` method? ;; `StringBuilder` does not override `equals()`; it uses the default implementation from the `Object` class, which compares references, not contents.

What is the result of the following code?
```java
StringBuilder name1 = new StringBuilder("John Wayne");
StringBuilder name2 = new StringBuilder("John Wayne");
System.out.println(name1 == name2);
System.out.println(name1.equals(name2));
```
?
The result will be:
```java
false
false
```

How can you compare the content of two `StringBuilder` objects? ;; Convert them to `String` and then use the `equals()` method on the `String` objects.

What will be the output of the following code?
```java
StringBuilder name1 = new StringBuilder("John Wayne");
StringBuilder name2 = new StringBuilder("John Wayne");
System.out.println(name1.toString().equals(name2.toString()));
```
?
The output will be:
```java
true
```

What happens if you call `subString()` on a `StringBuilder` object but do not assign it to a `String` variable? ;; The `StringBuilder` content remains unchanged; `subString()` only returns a new `String` object.

What will be the output of the following code?
```java
StringBuilder name = new StringBuilder("John Wayne");
name.subString(2, 6);
System.out.println(name);
```
?
The output will be:
```java
John Wayne
```

What is the result of the following code?
```java
StringBuilder name = new StringBuilder("John Wayne");
String subName = name.subString(2, 6);
System.out.println(subName);
```
?
The result will be:
```java
hn W
```

