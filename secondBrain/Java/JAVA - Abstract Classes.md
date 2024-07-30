---
Creation_date: 2024-07-29 10:33
Modification_date: Monday 29th July 2024 10:33:44
Indexes:
  - "[[abstraction]]"
---

----

## Abstract Classes

- Classes which can be extended, but cannot be initialized
## Abstract Methods

- Abstract method marked with `abstract` keyword
- Abstract method don't have a body
- The implementation (*body*) is done in classes (*concrete class*) which extend an `abstract class`

Example:
```java
public abstract class Mammal{
	public abstract void speak();
}

public class Dog extends Mammal{
	public void speak() { System.out.println("Woof!"); }
}

public class Cat extends Mammal{
	public void speak() { System.out.println("Meow!"); }
}
```


## Rules for Using `Abstract` Methods

1. Only instance methods can be marked `abstract`
	1. Not variables, constructors, static members, etc.
2. `Abstract` method can only be declared in an `Abstract` class
3. Non-abstract class which extents `abstract` class must implement ***ALL*** inherited methods.
4. All others rules with overriding methods are apply.
```java
public static void main(String... args){
	Dog dog = new Dog();
	dog.speak();
	dog.walks();
}

abstract class Animal{
	public abstract void speak();
}

abstract class Mammal{
	public abstract void walks();
}

class Dog extends Mammal{
	@Override
	public void speak() { System.out.println("Woof!"); }
	
	@Override
	public void walks() { System.out.println("Dog walks!"); }
}
```


## Keep in mind...

- `abstract` classes can have constructors
	- But they can be called only using `super()` from the child class
- `abstract` classes or methods is not works with these keywords:  `final`, `private` `static`. Because:
	-  If an`abstract` class or method mark `final`, then the classes or methods **cannot** be extends or overridden. 
		- So there is no point for doing such thing.
	- If an`abstract` method be mark `private`, then the methods **cannot** be overridden. 
		- So it's obviously cannot be done
	- `static` method **cannot** can be overridden
		- Therefore, `abstract static` is not allowed







---
## Flash cards section
