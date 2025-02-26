---
Creation_date: 2025-01-29 20:53
Modification_date: Wednesday 29th January 2025 20:53:55
Indexes:
  - "[[class_design]]"
  - "[[to_do_notes]]"
tags:
  - tuyenLuong
---


----
## What is `this()` keyword

- Special method this() is used to call another constructor in a constructor

## Rules for using `this()`
- `this()` can only be called in the first line in the constructor 
- `this()` can be called only once 
- You must be careful not to create a "cycle"
	- Constructors which call each other ad infinitum

This does not compile:
```java
public Dog() {
	System.out.println("Woof!");
	this("Chip", 1);
}
```

This will result in cycle (infinite loop):
```java
public Dog() {
	this(); // cycle (infinite loop)
	System.out.println("Woof!");
}
```

```java
public Dog() {
	this("Chip", 1); // cycle (infinite loop)
	System.out.println("Woof!"); 
}
	
public Dog(String name, int age) { 
	this(); // cycle (infinite loop)
	this.name = name;
	this.age = age;
}
```

## What is `super()` keyword

- Special method `super()` is used to call a constructor of a superclass in a constructor of the subclass:
```java
class Mammal { 
	public int age; 
	public Mammal(int age) {  // <<<------
		this.age = age; 
	} 
} 
public class Dog extends Mammal {
	private String name; 
	public Dog(String name, int age) {
		super(age);   // <<<------
		this.name = name; 
		System.out.println("Woof!") 
	} 
}
```
- If there is no `this()` or `super()` in the first line then the compiler will insert `super()` automatically:
```java
class Mammal {
	public int age; 
} 
public class Dog extends Mammal { 
	private String name; 
	public Dog() { 
		// The compiler inserts `super()`; right here
		System.out.println("Woof!") 
	} 
}
```
- Be careful if the superclass doesn't have the no-argument constructor:
```java
class Mammal { 
	public int age; 
	// We have provided a constructor with arguments.
	// Therefore the compiler will not auto-generate no-arg constructor
	public Mammal(int age) { this.age = age; } 
} 
public class Dog extends Mammal { 
	private String name; 
	public Dog() { 
		// The compiler should be inserts `super()`; right here
		System.out.println("Woof!")
	}
}
// Since there is no Mammal() constructor ==>> it does not compile
```

## Rules for using `super()`
- If there is no explicit `this()` or `super()` in the first line of the constructor
	- The compiler will insert `super()` at the beginning of every constructor
- Can be called only once
- Must be called in the first line of the constructor








---
## Flash cards section
