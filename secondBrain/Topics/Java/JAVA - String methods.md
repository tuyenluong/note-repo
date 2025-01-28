---
Creation_date: 2024-03-26 00:41
Modification_date: Tuesday 26th March 2024 00:41:48
Indexes:
  - "[[string]]"
---

----


## Create and Concatenate a String

String is a **sequence of characters**, implementing `CharSequence` interface. 

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
- And == operator is the one who make assertion between objects. 
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
- This method is [[COMMON - What is case-sensitive and non case-sensitive|case-sensitive]].
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
- [[java-11|stirp(), stripLeading(), stripTrailing() was introduced in Java 11]]
	- Whitespaces also includes `\t (tab)`, `\n (new line)`, `\r (carriage return)`.
	- All escape sequences count as one character in length.
- [[JAVA - What is the different between trim() and strip()|More detail about stirp(), stripLeading(), stripTrailing()]]
- `strip()` method return a string that provides a string with both leading and trailing white spaces removed.
```java
String str = "   abc   ";
System.out.println("|" + str.strip() + "|");
==>> |abc|
```
- `trim()` is the same as `strip()`, but supports Unicode.
```java
String str = "   abc   ";
System.out.println("|" + str.trim() + "|");
==>> |abc|
```
- `stripLeading()` method return a string that provides a string with all leading white spaces removed.
```java
String str = "   abc   ";
System.out.println("|" + str.strip() + "|");
==>> |abc   |
```
- `stripTrailing()` method return a string that provides a string with all trailing white spaces removed.
```java
String str = "   abc   ";
System.out.println("|" + str.strip() + "|");
==>> |   abc|
```

### `indent(n)` method
- [[java-12|indent() method was introduced in Java 12]]
- This method is useful to add or remove white spaces from the beginning of the line to adjust indentation for each string line. 
- `indent(n)` method takes one parameter, which is integer.
- It also normalizes exiting line terminators
	- This is a characteristic of the `indent()` method
- Then, suffix each line with `\n`.
- If `n = 0` then it will does nothing
```java
String str = "    John\n    D.\n    Wayne"
System.out.println("--");
System.out.println(str);
System.out.println("--");
==>> Result
--
    John
    D.
    Wayne
--
```
- If `n > 0`, adds the same number of blank spaces to each line
```java
String str = "    John\n    D.\n    Wayne"
System.out.println("--");
System.out.println(str.indent(2));
System.out.println("--");
==>> Result
--
      John
      D.
      Wayne  // suffix each line with `\n`
      // This is a characteristic of the `indent()` method
--
```
- If `n < 0`, tries to remove n number of whitespace characters from the beginning of line 
```java
String str = "    John\n    D.\n    Wayne"
System.out.println("--");
System.out.println(str.indent(-2));
System.out.println("--");
==>> Result
-- 
    John // Remove 2 spaces in each line.
    D.
    Wayne // suffix each line with `\n`
    // This is a characteristic of the `indent()` method
--
```

### `stripIndent()` method
^3062c7

- Removes all leading [[JAVA - What is Incidental white spaces|incidental whitespace]]
```java
String str = "    John\n      D.\n      Wayne"
System.out.println("--");
System.out.println(str.stripIndent());
System.out.println("--");
==>> Result
-- 
John // Remove all all leading incidental whitespace
D.
Wayne 
-- //DOES NOT add line break at the end
```
- Normalizes exiting line breaks
- *DOES NOT* add line break at the end if missing
- So this means that the method looks for the first non-empty character.
```java
String str = "    John\n      D.\n      Wayne"
System.out.println("--");
System.out.println(str.stripIndent());
System.out.println("--");
==>> Result
-- 
John // Remove all all leading incidental whitespace
  D.
  Wayne 
-- //DOES NOT add line break at the end
```

### `translateEscapes()` method
^71eb32
- First, we don't use `translateEscapes()`
```java
String name = "John\\tWayne"
System.out.println(name);
==>> John\tWayne //The first backslash will escapes the second one
				// Because of that the compiler don't recognize the 
				// "\t" sequence
```
- Now we will use the `translateEscapes()` method to translate all the escapes sequence
```java
String name = "John\\tWayne"
System.out.println(name.translateEscapes());
==>> John    Wayne //The methid will translate the escapes sequence to tab
```

### `isEmpty()` and  `isBlank()`
- The different between `isEmpty()` and  `isBlank()` is:
- `isEmpty()` only checks for the character presence, if the string even has a non-word character like space or tab present, it will consider the string is not empty.
```java
System.out.println("".isEmpty());
==>> true
```

```java
System.out.println(" ".isEmpty());
==>> false
```

- While `isBlank()` is check for both the presence and non-word characters like space or tab.
```java
System.out.println("".isBlank());
==>> true
```

```java
System.out.println(" ".isBlank());
==>> true
```

### String formatting symbols
^417dce
- `%s` = for any type, usually for String
- `%d` = for integral values (`int` and `long`)
- `%f` = for decimal number (`float` and `double`)
- `%n` = inserts a system-dependent line separator
### `format()`and `formatted()`

The different between these to methods lies within the code.
- `format()` method only use as a static method and have to pass in the format and the arguments is a must, but for locale parameter is optional
- `format()` method returns a formatted string, specified format string and, arguments. It's also have a locale argument as well, but locale arguments in not used very often.
- The format will replace the [[#^417dce|String formatting symbols]] by the given string arguments.
```java
String name = "John";
int numberOfMarbles = 5;
String printOut1 = name + " has " + numberOfmarbles + " marbles.";
String printOut2 = String.format("%s has %d marbles.", name, numberOfMarbles);
System.out.println(printOut1);
System.out.println(printOut2);
==>> 
John has 5 marbles.
John has 5 marbles.
```
- While for the `formatted()` method, it can use directly on the format itself and only need to pass in the arguments.
```java
String name = "John";
int numberOfMarbles = 5;
String printOut1 = name + " has " + numberOfmarbles + " marbles.";
String printOut2 = "%s has %d marbles.".formatted(name, numberOfMarbles);
System.out.println(printOut1);
System.out.println(printOut2);
==>> 
John has 5 marbles.
John has 5 marbles.
```

### method chaining: left -> right
- String method also support method chaining.
```java
String name = "   John Wayne   "
System.out.println(name.trim().toUpperCase()).replace('Y','R'));
==>>JOHN WARNE
```

### String are immutable!
Be careful when using String method in a individual line like below:
Because [[JAVA - What is mutable and immutable means|String are immutable]].
```java
String name = "   John Wayne   "
name.trim();
System.out.println(name);
==>>   John Wayne   
```
Due to all String methods is always returning a new String, so it's the best if the method can return to a reference that can hold the value or pass it inside a method as parameter.
```java
String name = "   John Wayne   "
System.out.println(name.trim());
==>>John Wayne   
```



---
## Flash cards section

How do you create a new String object in Java? ;; You can create a new String object by using the `new String("text")` syntax or by string literal like `"text"`.
<!--SR:!2024-09-15,44,290-->
What are two ways to concatenate strings in Java? ;; The two ways to concatenate strings in Java are using the `+` operator (e.g., `str1 + str2`) and the `concat()` method (e.g., `str1.concat(str2)`).
<!--SR:!2024-09-01,30,283-->
What does the `+` operator do when both operands are numeric in Java? ;; When both operands are numeric, the `+` operator performs addition.
<!--SR:!2024-09-21,50,290-->
What is the result of `"John" + 3 + 8` in Java? ;; The result is `John38` because concatenation in Java is evaluated from left to right.
<!--SR:!2024-09-05,34,270-->
What happens when you concatenate a string with `null` in Java? ;; When you concatenate a string with `null`, Java converts `null` to the string `"null"` and concatenates it, resulting in strings like `"Johnnull"`.
<!--SR:!2024-08-19,17,263-->
How do you use the `+=` operator for string concatenation? ;; The `+=` operator is used to append the string on the right to the variable on the left, equivalent to `variable = variable + "string"`.
<<<<<<< HEAD
<!--SR:!2024-08-05,3,210-->
=======
<!--SR:!2024-07-31,1,170-->
>>>>>>> 9bb2d12 ([Java] modify notes)
What does the `length()` method of a String return? ;; The `length()` method returns the number of characters in the string.
<!--SR:!2024-08-05,3,243-->
What exception is thrown when accessing a character index that exceeds the string length? ;; Accessing an index that exceeds the string length throws a `StringIndexOutOfBoundsException`.
<!--SR:!2024-08-09,7,243-->
What does the `indexOf()` method do?
?
The `indexOf()` method find the first occurrence of the character 't' by using `string.indexOf('t')`.
<!--SR:!2024-07-17,3,250-->
What does the `substring(int start, int end)` method do? ;; It returns a new string that is a substring of the original string, starting from the index `start` and ending at index `end` (exclusive).
<!--SR:!2024-08-03,1,184-->
What does the `toLowerCase()` method do to a string? ;; The `toLowerCase()` method converts all characters of the string to lower case.
<!--SR:!2024-08-05,3,203-->
How does the `equals()` method compare two strings in Java? ;; The `equals()` method compares the content of two strings, returning `true` if they are identical.
<!--SR:!2024-08-30,28,270-->
What does the `startsWith()` method do, and what type of argument does it accept? ;; The `startsWith()` method checks if the string starts with the specified substring and accepts a String argument.
<!--SR:!2024-08-16,17,250-->

Describe what the `replace(char oldChar, char newChar)` method does. ;; The `replace(char oldChar, char newChar)` method returns a new string resulting from replacing all occurrences of `oldChar` in the string with `newChar`.
<!--SR:!2024-09-08,37,290-->
What is the difference between `trim()` and `strip()` methods in Java? ;; Both methods remove leading and trailing white space from a string, but `strip()` is Unicode-aware and thus can handle a wider range of white space characters than `trim()`.
<!--SR:!2024-08-05,3,223-->
Explain the function of the `indent(int n)` method introduced in Java 12. ;; The `indent(int n)` method adjusts the indentation of each line in the string by adding or removing spaces, normalizes line terminators, and adds a line break after each line.
<!--SR:!2024-08-11,9,263-->
What does the `isEmpty()` method check for in a string? ;; The `isEmpty()` method checks if the string has a length of zero, meaning it is empty.
<!--SR:!2024-08-09,7,250-->

**What does the `+` operator do when used with two numeric values in Java?** ;; It performs addition.

**What does the `+` operator do when used with at least one String value in Java?** ;; It performs concatenation.
<!--SR:!2024-08-03,1,221-->

**What is the output of `System.out.println("John" + 3 + 8);`?**  ;; John38

**What is the output of `System.out.println("John" + (3 + 8));`?**  ;; John11

**What will be the result of concatenating `"John"` and `null`?**  ;; Johnnull

**What is the purpose of the `concat()` method in Java Strings?**  ;; It concatenates two Strings.

**How does `StringBuilder` differ from `String` regarding immutability?** ;; `StringBuilder` is mutable while `String` is immutable.

**What is the output of `new String("John Wayne").length()`?**  ;; 10

**What does the `charAt()` method do in Java?**  ;; It returns the character at a specified index.

**What is the output of `System.out.println("Doctor Dolittle".indexOf('t'));`?**  ;; 3

**How does `indexOf()` behave when searching for a String instead of a character?**  ;; It returns the index of the first occurrence of the specified substring.

**What will `System.out.println("John Wayne".substring(3, 8));` output?** ;; n Way

**What is the result of `System.out.println(" abc ".strip());`?**  ;; |abc|

**What is the output of `System.out.println(" abc ".trim());`?**  ;; |abc|

**What does the `replace()` method do in Java Strings?**  ;; It replaces occurrences of a specified character or substring with another character or substring.
<!--SR:!2024-08-04,2,240-->

**What is the difference between `isEmpty()` and `isBlank()` in Java Strings?**  ;; `isEmpty()` checks if the string has zero length, while `isBlank()` checks if the string is empty or contains only whitespace characters.

**What does the `stripIndent()` method do?**  ;; It removes all leading incidental whitespace from each line of a multi-line string.

**What is the output of `System.out.println("John\\tWayne".translateEscapes());`?**  ;; John Wayne (translates the escape sequence to a tab)

**What is the result of `System.out.println("%s has %d marbles.".formatted("John", 5));`?**  ;; John has 5 marbles

**What will `String.format("%s has %d marbles.", "John", 5);` return?**  ;; John has 5 marbles

**What is the output of `System.out.println(" John Wayne ".trim().toUpperCase().replace('Y', 'R'));`?**  ;; JOHN RARNE

**How does method chaining work with Java Strings?**  ;; Methods are executed in a left-to-right order, and each method call operates on the result of the previous one.
<!--SR:!2024-08-05,3,260-->

**What is the effect of using `String.trim()` on an immutable String object?**  ;; It returns a new String with the leading and trailing whitespace removed; the original String remains unchanged.

**What does `name.isEmpty()` return for an empty string?**  ;; true


**What does `name.isBlank()` return for a string containing only whitespace?**  ;; true


