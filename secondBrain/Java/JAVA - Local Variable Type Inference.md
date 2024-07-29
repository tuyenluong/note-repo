---
Creation_date: 2024-02-24 15:51
Modification_date: Saturday 24th February 2024 15:51:58
Indexes:
  - "[[java_building_block]]"
---


----

This new feature called "***Local Variable Type Inference***" (*LVTI*), **this feature is introduced in** [[java-10|Java 10]]. 
- **Local variables** - can be used only for local variables.
- **Type inference** - the type of the variable is inferred by the compiler.
	- The way of the type inferred works is the compiler will figure out the type based on the assigned value to the variable.
- In this example, a is inferred to be type int.
```java
var a = 5;
```
- And the type inferred will stay so for the duration of [[JAVA - Variables#Variable scope|the variable scope]].
- So you **CANNOT** change the type of this variable in the same scope once you declared it using var.
```java
var a = 5; ==>> The compiler already figure this variable is int type 
var a = "John Wayne"; ==>> So this will NOT COMPILE.
```

- You **CANNOT** assign **null** to *LVTI* 
```java
var s = null; ==>> DOES NOT COMPILE.
```

- `var` is **NOT** the [[JAVA - Variables#^4706f6|reserved word]].
```java
public class Var () ==>> OK
var var = 5 ==>> OK
Var var = new Var(); ==>> OK
```

### REMEMBER - Only [[JAVA - Class Structure#^57453a|local variables]] can use type inferred

```java
public int sum(var a, var b){ ==>> cannot use type inferred on method parameters
	int result = a + b;
	return result; ==>> DOES NOT COMPILE
}
```

### Practical usage
- Old way
```java
SomeClassWithVeryLongName instance = new SomeClassWithVeryLongName();

ClientList<Client> clientList = new SomeClassWithVeryLongName().getClientList();
```
- New way
```java
var instance = new SomeClassWithVeryLongName();

var clientList = new SomeClassWithVeryLongName().getClientList();
```


---
## Flash cards section

What is the purpose of Local Variable Type Inference (LVTI) introduced in Java 10? ;; LVTI allows the compiler to infer the type of a local variable based on the assigned value, reducing the need for explicit type declarations.

Analyse the following code and determine the type inferred for `x`:
```java
var x = 10;
```
?
The type inferred for `x` is `int` because the assigned value `10` is an integer.

Why does the following code not compile?
```java
var x = null;
```
?
The code does not compile because `null` does not provide enough information for the compiler to infer a specific type for `x`.

What will be the result of this code snippet?
```java
var name = "John Doe";
System.out.println(name);
```
?
The result will be `"John Doe"`, and `name` is inferred to be of type `String`.

Why can't you use `var` for method parameters? ;; `var` cannot be used for method parameters because it is only valid for local variables within a method, not for method signatures.

Determine the output of this code snippet:
```java
var num = 3.14;
System.out.println(num);
```
?
The output is `3.14`, and `num` is inferred to be of type `double`.

Analyse the following code and explain why it compiles:
```java
var list = new ArrayList<String>();
```
?
The code compiles successfully because the type `ArrayList<String>` is inferred from the constructor, making `list` of type `ArrayList<String>`.

What will be the result of this code snippet?
```java
var str = "Hello";
str = 100;
```
?
The code will not compile because `str` was initially inferred as a `String`, and the reassignment to `100` (an `int`) is not allowed in the same scope.

Explain why this code is valid:
```java
public class Example {
    public static void main(String[] args) {
        var x = 5;
        var y = "Test";
        System.out.println(x);
        System.out.println(y);
    }
}
```
?
The code is valid because `x` is inferred to be `int` and `y` is inferred to be `String`, and they are used correctly within the `main` method.

Analyse the following code and determine if it compiles:
```java
var name;
name = "Alice";
```
?
The code does not compile because `var` requires an initializer to infer the type; the variable `name` must be initialized at the point of declaration.