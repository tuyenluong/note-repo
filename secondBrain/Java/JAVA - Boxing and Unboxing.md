---
Creation_date: 2024-07-27 13:11
Modification_date: Saturday 27th July 2024 13:11:21
Indexes:
  - "[[methods]]"
---

----

## Boxing and unboxing 

^669fa5

- **Boxing**: converting a primitive data type into its wrapper class
	- (*putting primitive in the box*)
- **Unboxing**: converting a wrapper class to a primitive
	- (*getting a primitive out of the box*)

## Explicit way

```java
int a = 3;
Integer b = Integer.valueOf(a);
==>> int ->  Integer (boxing)

int c = b.intValue();
==>> Integer -> int (unboxing)
```

## Implicit way

```java
int a = 3;
Integer b = a;
==>> int ->  Integer (auto boxing)

int c = b;
==>> Integer -> int (auto unboxing)
```

## Java will also auto cast a smaller primitive type into a lager one

- But Java will not do both automatic operations at the same time!!
```java
int x = 7;
long y = x; // auto casting is ok
Long z = x; // auto casting and auto boxing cannot be done at once ==>> NOT OK!
```

- If you need both auto casting and auto boxing, one of these operation should be done by hand (*or both*)
```java
int x = 7;
 
// Explixit boxing, then the compiler will do the auto casting
Long z = Long.valueOf(x);

//Explicit casting, then the compiler will do the auto boxing
Long z = (long)x;

// Or explicit everything
Long z = Long.valueOf((long)x);
```

## Be careful when working with primitive literals

```java
Long x = 10;
// NOT OK, this also violate the rule that cannot do both automatic operation at the same time
Long x = 10L;
// OK, this line is ok because now it just need to do one automatic operation only due to we have explicit the casting

```








---
## Flash cards section

What is the Explicit way to boxing and unboxing?
?
Used these methods:
- For boxing: `valueOf(int)`, `valueOf(long)`, `valueOf(char)`, `valueOf(boolean)`, `valueOf(short)`, `valueOf(byte)`, `valueOf(float)`, `valueOf(double)`
- For unboxing: `intValue()`,`longValue()`,`charValue()`, `booleanValue()`, `shortValue()`, `byteValue()`, `floatValue()`, `doubleValue()`

What is wrong with this code?
```java
int x = 7;
Long z = x; 
```
?
Java will not do both automatic operations at the same time!!
```java
int x = 7;
Long z = x; // auto casting and auto boxing cannot be done at once ==>> NOT OK!
```
<!--SR:!2024-08-06,4,270-->

What happen if I assign a `int` literal value to `Long` wrapper variable like this?
```java
Long x = 10;
```
?
It's also violate the rule of automatic operation that Java will not allow to do both automatic operations at the same time, auto boxing and auto casting, you have to o either one the the operation by hand, then leave another to the compiler.
```java
Long x = 10L;
```



