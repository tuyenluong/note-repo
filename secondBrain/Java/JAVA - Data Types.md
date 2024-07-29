---
Creation_date: 2024-02-14 10:57
Modification_date: Wednesday 14th February 2024 10:57:30
Indexes:
  - "[[java_building_block]]"
---

----

## Primitive Types

| Keyword | Type                  | Min            | Max           | Default | Example  |
| ------- | --------------------- | -------------- | ------------- | ------- | -------- |
| boolean | true or false         | -              | -             | false   | true     |
| byte    | 8-bit integral value  | -128           | 127           | 0       | 118      |
| short   | 16-bit integral value | -32,768        | 32767         | 0       | -202     |
| int     | 32-bit integral value | -2,147,483,648 | 2,174,483,647 | 0       | 5106     |
| long    | 64-bit integral value | -2^63          | 2^63 - 1      | 0L      | 5106L    |
| float   | 32-bit floating value | -              | -             | 0.0f    | 511.183f |
| double  | 64-bit floating value | -              | -             | 0.0     | 511.183  |
| char    | 16bit Unicode value   | 0              | 65,535        | \\u0000 | 'c'      |

^0a9df1

## To keep in mind
- In Java, boolean *true* and *false* are completely **unrelated** to 1 and 0!!
	- Bit size of boolean is not specified, it's depends on the JVM.
	- But any Java object is aligned to an 8 bytes.
	- A boolean has 8 bytes of header, plus 1 byte of payload, for a total of 9 bytes of information. The JVM then rounds it up to the next multiple of 8. so the one instance of java.lang.Boolean takes up 16 bytes of memory.n
	-  And the boolean value is just 1 bit, 1 and 0 is representative of *true* and *false*.
	- ![[Pasted image 20240219170809.png]]
- All numeric types are signed (*It allowed negative numbers*).
- float requires an f (*or F*) character at the end to distinguish it from double type value: ^50b425
	- [[JAVA - Data Types#^13eb3a|Does not compile!!]]
	- [[JAVA - Data Types#^f05d0b|OK!!]]
- long requires an l (*or L for readability*) character at the end to distinguish it from int type value: ^c97ad1
	- [[JAVA - Data Types#^6a0e1e|Does not compile!!]]
	- [[JAVA - Data Types#^dc8858|OK!!]]
## Supported digital formats

- *Base 10* (digits 0-9), "normal" numbers.
- *Octal*  (digits 0-7), uses 0 as a prefix (e.g 017)
- Hexadecimal  (digits 0-9 and letters A-F/a-f), uses 0x or 0X as a prefix
	- Format is case insensitive (e.g. 0xFF, 0XFF, 0Xff, 0xff, etc.) 
- *Binary* (digits 0 and 1), uses 0b or 0B as prefix (e.g. 0b10,0B11, etc.)

For readability, the use of underscore is allowed.
But NOT in the beginning, at the end, right before or after the decimal point

```java
int a = 1_000_000               ==>> normal usage
int b = 1_2                     ==>> OK, but not very useful
int c = 1_______2;              ==>> even less useful, but still ok
double d = 1_000_000.000_001;   ==>> OK and makes sense

double x = _10.1;      ==>> Not OK
double x = 10.1_;      ==>> Not OK
double x = 10_.1;      ==>> Not OK
double x = 10._1;      ==>> Not OK
```

## Wrapper classes

- Primitives are not objects, and sometimes we prefer to work with objects 
- Each primitive has a wrapper class 
	- An object type which corresponds to the primitive 
- Most common way to create an object from the primitive 
	- Use static method valueOf() :
- ![[Pasted image 20240222012937.png]]

| Primitive Type | Wrapper Class | Example |
| ---- | ---- | ---- |
| boolean | Boolean | Boolean.valueOf(true); |
| byte | Byte | Byte.valueOf((byte) 12); |
| short | Short | Short.valueOf((short) 12); |
| int | Integer | Integer.valueOf(12) |
| long | Long | Long.valueOf(12L) |
| float | Float | Float.valueOf(12.0F) |
| double | Double | Double.valueOf(12.0) |
| char | Character | Character.valueOf('c') |

- valueOf() can be used to convert String into wrapper class
```java
Integer n = Integer.valueOf("12");
```

- Wrapper classes come with some useful methods, e.g.
```java
int m = Integer.parseInt("101");
```

- Before Java 9, this was possible (might appear on OCA exam)
```java
Integer p = new Integer(5);
```

- Wrapper classes offer many useful helper methods
	- byteValue()
	- shortValue()
	- intValue()
	- floatValue()
	- doubleValue()
	- booleanValue()
	- charValue()
```java
Double d = Double.valueOf(314.67); 
System.out.println(d.byteValue()); ==>> 58 (wrap: 314-256=58) 
System.out.println(d.intValue()); ==>> 314 
System.out.println(d.doubleValue()); ==>> 314.67
```

## Strings

- Strings (e.g. "Hello World") are not primitive types in Java 
- But they are commonly use like primitives
```java
String greeting = "Hello"; String name = "John Wayne"; 
System.out.println(greeting + ", " + name + "!") ==>> Hello, John Wayne!
```


```java
float x = 2.7;
```
^13eb3a

```java
float x = 2.7f;
```
^f05d0b

```java
long a = 298374612936;
```
^6a0e1e

```java
long a = 298374612936L;
```
^dc8858


---
## Flash cards section

What are the primitive types in Java and their respective keywords?
?
boolean, byte, short, int, long, float, double, char

What is the range of a byte in Java? ;; -128 to 127

What is the range of a short in Java? ;; -32,768 to 32,767

What is the range of an int in Java? ;; -2,147,483,648 to 2,147,483,647

What is the range of a long in Java? ;; -2^63 to 2^63 - 1

What is the default value of a boolean in Java? ;; false

What character is required at the end of a float literal? ;; `f` or `F`

What character is required at the end of a long literal? ;; `l` or `L`

What are the supported digital formats in Java?
?
Base 10, Octal, Hexadecimal, Binary

How do you denote an octal number in Java? ;; Use 0 as a prefix, e.g., `017`

How do you denote a hexadecimal number in Java? ;; Use `0x` or `0X` as a prefix, e.g., `0xFF`

How do you denote a binary number in Java? ;; Use `0b` or `0B` as a prefix, e.g., `0b10`

What is the rule for using underscores in numeric literals in Java? ;; Underscores can be used for readability but not at the beginning, end, right before, or after the decimal point.

What is the wrapper class for an int in Java? ;; Integer

What method is commonly used to create a wrapper object from a primitive? ;; `valueOf()`

How do you convert a String into a wrapper class?
?
```java
Integer n = Integer.valueOf("12");
```

How do you parse a String into a primitive int?
?
```java
int m = Integer.parseInt("101");
```

Before Java 9, how could you create a wrapper object?
?
```java
Integer p = new Integer(5);
```

What are some useful methods provided by wrapper classes?
?
`byteValue()`, `shortValue()`, `intValue()`, `floatValue()`, `doubleValue()`, `booleanValue()`, `charValue()`

What will the following code print:
```java
Double d = Double.valueOf(314.67); 
System.out.println(d.byteValue());
System.out.println(d.intValue());
System.out.println(d.doubleValue());
```
?
```java
58
314
314.67
```

Are Strings considered primitive types in Java? ;; No, Strings are not primitive types but are commonly used like primitives.

What is the output of the following code:
```java
String greeting = "Hello"; 
String name = "John Wayne"; 
System.out.println(greeting + ", " + name + "!");
```
?
```java
Hello, John Wayne!
```

Will the following code compile:
```java
float x = 2.7;
```
?
No, it will not compile because a float literal requires an `f` or `F` at the end.

Will the following code compile:
```java
float x = 2.7f;
```
?
Yes, it will compile because the float literal has an `f` at the end.

Will the following code compile:
```java
long a = 298374612936;
```
?
No, it will not compile because a long literal requires an `L` at the end.

Will the following code compile:
```java
long a = 298374612936L;
```
?
Yes, it will compile because the long literal has an `L` at the end.





