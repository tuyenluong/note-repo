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

## `subString()`returns a String and doesn't change the StringBuilder content
- The `subString()`method in the StringBuilder class need to return to a String variable, other wise it will not apply the changes on the StringBuilder content.
```java
StringBuilder name = new StringBuilder("John Wayne");
name.subString(2, 6);
System.out.println(name);   
==>>John Wayne
```

- Here the fix code:
```java
StringBuilder name = new StringBuilder("John Wayne");
String subName = name.subString(2, 6);
System.out.println(subName);   
==>>hn W
```








---
## Flash cards section



