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
	-  If an`abstract` class or method mark `final`, then the `final` classes cannot be extended, and final methods cannot be overridden, which defeats the purpose of being abstract.
	- If an`abstract` method be mark `private`, then the `private` methods are not visible to subclasses, so they cannot be overridden.
	- `static` method **cannot** can be overridden. Therefore, `abstract static` is not allowed
## Summary

- An abstract class can have both abstract and non-abstract methods.
- Constructors in abstract classes are used to initialize common properties of the subclasses.
- The following combination of keywords is not allowed:
    - `abstract final`
    - `abstract private`
    - `abstract static`

By following these rules, you can effectively use abstract classes and methods in Java to create a clear and organized class hierarchy.





---
## Flash cards section

What is an abstract class? ;; A class which can be extended but cannot be instantiated.

How do you declare an abstract method in Java? ;; By using the `abstract` keyword and not providing a body.

Can abstract classes have constructors? ;; Yes, but they can only be called using `super()` from the child class.

Which keywords are not compatible with `abstract` classes or methods? ;; `final`, `private`, `static`.

What must a non-abstract class do if it extends an abstract class? ;; It must implement all inherited abstract methods.

Why can't an abstract method be marked as `private`? ;; Because private methods are not visible to subclasses and thus cannot be overridden.

Can static methods be abstract? ;; No, because static methods cannot be overridden.

What will happen if a class extending an abstract class does not implement all abstract methods? ;; The subclass must also be declared abstract.

What will the following code output?
```java
public abstract class Animal {
    public abstract void speak();
}

public class Dog extends Animal {
    @Override
    public void speak() { System.out.println("Woof!"); }
}

public class Main {
    public static void main(String[] args) {
        Dog dog = new Dog();
        dog.speak();
    }
}
```
?
`Woof!`

What will the following code output?
```java
public abstract class Mammal {
    public abstract void makeSound();
}

public class Cat extends Mammal {
    @Override
    public void makeSound() { System.out.println("Meow!"); }
}

public class Main {
    public static void main(String[] args) {
        Mammal mammal = new Cat();
        mammal.makeSound();
    }
}
```
?
`Meow!`

What will the following code output?
```java
public abstract class Animal {
    public abstract void run();
}

public class Bird extends Animal {
    @Override
    public void run() { System.out.println("Bird is running"); }
}

public class Main {
    public static void main(String[] args) {
        Animal animal = new Bird();
        animal.run();
    }
}
```
?
`Bird is running`

True or False: An abstract class can be instantiated directly. ;; False
True or False: An abstract class can have both abstract and non-abstract methods. ;; True
True or False: Abstract methods can be static. ;; False
True or False: A non-abstract subclass of an abstract class must implement all abstract methods. ;; True
True or False: An abstract class cannot have a constructor. ;; False

Which of the following can be marked as `abstract`? (Choose all that apply)
- [ ] A. Instance methods
- [ ] B. Constructors
- [ ] C. Variables
- [ ] D. Static methods
?
 `A`
Which of the following keywords cannot be used with abstract classes or methods? (Choose all that apply)
- [ ] A. final
- [ ] B. private
- [ ] C. public
- [ ] D. static
?
`A, B, D`

Given the following code, what will be the output?
```java
public class Cat extends Mammal {
    @Override
    public void speak() { System.out.println("Meow!"); }
}

public static void main(String... args) {
    Cat cat = new Cat();
    cat.speak();
}
```
- [ ] A. Compile-time error
- [ ] B. Runtime error
- [ ] C. "Meow!"
- [ ] D. No output
?
C

Which of the following statements are true about abstract classes? (Choose all that apply)
- [ ] A. An abstract class can have non-abstract methods.
- [ ] B. An abstract class can be instantiated directly.
- [ ] C. Abstract classes cannot have constructors.
- [ ] D. Abstract methods must be implemented in subclasses.
?
`A, D`
What will happen if a subclass does not implement all abstract methods of its abstract superclass? (Choose all that apply)
- [ ] A. It will compile successfully.
- [ ] B. It must be declared abstract.
- [ ] C. It will cause a compile-time error.
- [ ] D. It can still be instantiated.
?
`B, C`