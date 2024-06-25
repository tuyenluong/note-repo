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

