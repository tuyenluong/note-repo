

----
Creation date: 2024-03-26 00:41
Modification date: Tuesday 26th March 2024 00:41:48

----

#Java  

## Create and Concatenate a String

String is a **sequence of characters**, implementing CharSequence interface. 

```java
String name = "John Wayne";
String name1 = new String("John Wayne");
==>> Both ways is valid
```

**Concatenation**:
- Concatenation is means that merge one string into another.
- You can perform it in two different ways

```java
str1 + str2; ==>> Most common way
// or
str1.concat(str2); ==>> Not popular as the one above but still work
```

### There are rules when you use plus sign for concatenation

1. If both operands are numeric, + means addition.
2. If either the operand is String, + means concatenation.
3. Evaluation is left to right

#### Examples:

- Result is 11 because both operands are numeric
```java
System.out.println(3 + 8);             ==>> 11
```

- Result is "JohnWayne" because both operands are String 
```java
System.out.println("John" + "Wayne");  ==>> JohnWayne
```

- Result is "John8" because either the operands is String 
```java
System.out.println("John" + 8);        ==>> John8
```

- Concatenation evaluation is from evaluation is left to right
```java
System.out.println("John" + 3 + 8);    ==>> John38
```

- Concatenation evaluation is from left to right but the numeric are using parenthesis sign so it will perform first and then continue to concatenate.
```java
System.out.println("John" + (3 + 8));  ==>> John11 
```

- It's allowed to concatenate with null String
```java
System.out.println("John" + null);    ==>> Johnnull
```

- Able use assignment operators with concatenation
```java
String name = "John";
name += "Wayne"; ==>> equivilent to 'name = name + "Wayne"'
System.out.println(name);  ==>> JohnWayne 
```

## String Methods

### `length()`
- This method will gives you the length of the String.
```java
String name = "John";
System.out.println(name.length());  ==>> 4 
```

### `charAt()`
- This method will gives you the character at any index of you desire in a String.
- The index start with 0 based
```java
String name = "John Wayne";
System.out.println(name.charAt(6));  ==>> a
```
- But be careful when you trying to get the character that exceed the length of the String
```java
String name = "John Wayne";
System.out.println(name.charAt(12));  ==>> StringIndexOutOfBoundsException
```

### `indexOf()`
- This method will gives you the index at any character of you desire in a String.
```java
String name = "Doctor Dolittle";
System.out.println(name.indexOf('t'));  ==>> 3
```
- You can also tell the method start searching from a certain index. 
```java
String name = "Doctor Dolittle";
System.out.println(name.indexOf('t', 5)); ==>> 11
```
- The `indexOf()` method can also take a String, so it can take character, but it can also take a String. Then the compiler will look for this combination of characters.
- With this approach, it will return the index where this sequence of characters is located.
```java
String name = "Doctor Dolittle";
System.out.println(name.indexOf("cto")); ==>> 2
```
- And you can also look for the String with a starting index.
```java
String name = "Doctor Dolittle";
System.out.println(name.indexOf("Do", 4)); ==>> 7
```
- And if you try to find out the index of something which is not present in the String, it will return a minus one value.
```java
String name = "Doctor Dolittle";
System.out.println(name.indexOf("A")); ==>> -1 // not found
```

### `substring()`
- This method will gives you the substring from the original string.
- Create a substring by passing one integer number into the method.
- So this means that the substring will be created from the original string by taken everything from the declared index to the end.
```java
String name = "John Wayne";
System.out.println(name.substring(3)); ==>> "n Wayne"
```
- If you pass two values like this, you will have the substring between those values.
```java
String name = "John Wayne";
System.out.println(name.substring(3, 8));
==>> "n Way" // from index 3 to 8 (8 is not included!)
```
- But if you try to pass two same values, then the method will return an empty String.
```java
String name = "John Wayne";
System.out.println(name.substring(3, 3));
==>> "" //  empty String
```
- And if you not careful and mix up the order of the string, then it will not work and just give you a String index out of bounds exception.
```java
String name = "John Wayne";
System.out.println(name.substring(8, 3));
==>> StringIndexOutOfBoundsException
```
- And if you try pass the out of bounds, you will also get the exception.
```java
String name = "John Wayne"; 
System.out.println(name.substring(3, 14)); 
==>> StringIndexOutOfBoundsException
==>> 14 is greater than the length of the String
```

### `toLowercase()`
- Turn the String to lower case
```java
String name = "John Wayne"; 
System.out.println(name.toLowercase()); 
==>> john wayne
```

### `toUppercase()`
- Turn the String to upper case
```java
String name = "John Wayne"; 
System.out.println(name.toUppercase()); 
==>> JOHN WAYNE
```

### `equals()`, `equalsIgnoreCase()`
- First of all, the `equals()` method only make assertion for the content of the object .
- And `==` operator is the one who make assertion between objects. 
```java
String name1 = new String("John Wayne"); 
String name2 = new String("John Wayne"); 
String name3 = new String("john wayne"); 
System.out.println(name1 == name2); 
==>> false // not referencing to the same object
System.out.println(name1.equals(name2));
==>> true // the content of both object is the same
System.out.println(name1.equals(name3));
==>> false // String is case-sensitive
System.out.println(name1.equalsIgnoreCase(name3));
==>> true // the equalsIsIgnoreCase will ignore case-sensitive.
```

### `startWith()`, `endWith()`
- Like the name of the method said, they just make assertion if the string is starts of ends with some sub string. 
```java
String name = "John Wayne";
System.out.println(name.startsWith("J")); 
==>> true 
System.out.println(name.startsWith("Jo")); 
==>> true 
System.out.println(name.endWith("e")); 
==>> true 
System.out.println(name.endWith("Wayne")); 
==>> true 
```
- Note that you have to be careful with this starts and ends with method is that it ***ONLY ACCEPTS STRING***
- So if you try to pass the character, for example `'J'` and try to test if it starts with J.
- This will not compile because the argument of these methods is always a string and it cannot be character.
```java
String name = "John Wayne";
System.out.println(name.startsWith('J')); 
==>> DOES NOT COMPILE // argument is a String, not char!!
```

### `contains()`
- This method just assert that if your string contains some other substring.
- This method is [[JAVA - What is case-sensitive and non case-sensitive|case-sensitive]].
```java
String name = "John Wayne";
System.out.println(name.contains("n")); 
==>> true 
System.out.println(name.contains("John")); 
==>> true 
System.out.println(name.contains("j")); 
==>> false  // contains() method is case-sensitive
```

### `replace()`
- Like the name suggested, this method will replace some string/char with others string/char
```java
String name = "abcdeabc";
System.out.println(name.replace('c', 'y')); 
==>> abydeaby // replace all instances of 'c' with 'y' 
System.out.println(name.replace("c", "y")); 
==>> abydeaby // parameters can be both String and char
System.out.println(name.replace("bcd", "xyz")); 
==>> axyzeaby
```

### `strip()`, `trim()`, `stripLeading()`, `stripTrailing()`






---
## Flash cards section