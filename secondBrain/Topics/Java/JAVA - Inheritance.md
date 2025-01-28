---
Creation_date: 2024-08-03 10:02
Modification_date: Saturday 3rd August 2024 10:02:01
Indexes:
  - "[[class_design]]"
---

----

## Inheritance
- Let's say we have a class `Dog` which extends class `Animal`
```java
public class Animal { }

public class Dog extends Animal { }
```
- Here, `Animal` is referred to as the **superclass (parent)**, and `Dog` as the **subclass (child)**
- A subclass can inherit members (fields and methods) from a superclass
    - This is called **inheritance**

## Inheritance is Transitive

```java
public class Animal { }

public class Mammal extends Animal { }

public class Dog extends Mammal { }
```

- Dog inherits from `Animal`, but only through `Mammal`.
- Java supports **single inheritance**
    - A class can have only one direct superclass.
    - (*Unlike in some other languages, like C++*)
    - **But** a class can implement multiple interfaces.

## Class Modifiers in Java

- `final`: A `final` class cannot be sub classed. This means no other class can extend a `final` class.
```java
public final class Animal {
    // class definition
}
```

- `abstract`: An `abstract` class cannot be instantiated directly. It is intended to be sub classed, and it may contain abstract methods (*methods without a body*).
```java
public abstract class Animal {
    public abstract void makeSound();
}
```

- `static`: The `static` modifier can be used with nested classes to denote that the nested class does not have an implicit reference to its enclosing instance.
```java
public class OuterClass {
    public static class StaticNestedClass {
        // class definition
    }
}
```

### New Modifiers in Java 17

Modifiers in [[java-17|Java 17]]
#### `sealed`
- The `sealed` modifier restricts which classes can extend or implement the sealed class or interface. This is useful for providing a controlled hierarchy.
- A sealed class must list the permitted subclasses using the `permits` clause.
```java
public sealed class Animal permits Dog, Cat {
    // class definition
}

public final class Dog extends Animal {
    // class definition
}

public final class Cat extends Animal {
    // class definition
}
```
- Benefits:
	- Provides a clear, controlled inheritance structure.
	- Helps in maintaining a fixed set of subclasses, which can be useful for pattern matching and ensuring certain invariants in the design.

#### `non-sealed`

- The `non-sealed` modifier is used to allow further sub classing of a sealed class. This provides flexibility in certain parts of the hierarchy while maintaining control elsewhere.
```java
public sealed class Animal permits Dog, Cat {
    // class definition
}

public non-sealed class Dog extends Animal {
    // class definition
}

public final class Cat extends Animal {
    // class definition
}
```
- In this example, `Dog` can be sub classed further, but `Cat` cannot.

#### Example: Combining Sealed and Non-sealed Modifiers

Here is a more comprehensive example that combines `sealed` and `non-sealed` modifiers:
```java
public sealed class Animal permits Dog, Cat, Bird {
    // class definition
}

public non-sealed class Dog extends Animal {
    // Dog can have further subclasses
}

public final class Cat extends Animal {
    // Cat cannot have further subclasses
}

public sealed class Bird extends Animal permits Sparrow, Eagle {
    // Bird permits specific subclasses
}

public final class Sparrow extends Bird {
    // Sparrow is a final subclass of Bird
}

public final class Eagle extends Bird {
    // Eagle is a final subclass of Bird
}
```

### Summary
- **sealed**: Used to control which classes or interfaces can extend or implement the sealed class or interface. This is useful for maintaining a fixed and predictable class hierarchy.
- **non-sealed**: Allows a sealed class to be sub classed further, providing flexibility in specific parts of the hierarchy.

## Object Class

- All Java classes implicitly inherit from `java.lang.Object` class.
- `Object` is the only class which doesn't have a parent class
```java
public class Dog { }

public class Dog extends java.lang.Object { }
```
- Every class has access to methods defined in `Object` class
	- e.g. `toString()`, `equals()`, `hashCode()`, etc.




---
## Flash cards section

**What is inheritance in Java?** ;; Inheritance is a mechanism where a subclass inherits members (*fields and methods*) from a superclass.

What is the superclass and subclass in the following code?
```java
public class Animal { }
public class Dog extends Animal { }
```
?
`Animal` is the superclass (parent), and `Dog` is the subclass (*child*).

**What does it mean that inheritance is transitive?** ;; If `Class A` extends `Class B` and `Class B` extends `Class C`, then `Class A` indirectly inherits from `Class C` as well.

**Can a Java class have multiple direct super classes?** ;; No, Java supports single inheritance, meaning a class can have only one direct superclass.

**What can a class implement to allow multiple types of behaviour in Java?** ;; A class can implement multiple interfaces.

Given the following code, what will be the output?
```java
public class Animal {
    public void makeSound() {
        System.out.println("Animal sound");
    }
}

public class Dog extends Animal {
    @Override
    public void makeSound() {
        System.out.println("Dog barks");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal animal = new Dog();
        animal.makeSound();
    }
}
```
?
`Dog barks`

What happens if you try to instantiate the following abstract class?
```java
public abstract class Animal {
    public abstract void makeSound();
}

public class Main {
    public static void main(String[] args) {
        Animal animal = new Animal();
    }
}
```
?
It will result in a compilation error because you cannot instantiate an abstract class.

**Is it possible for a class to be both `final` and `abstract`?** ;; No, a class cannot be both `final` and `abstract` because `final` means it cannot be sub classed, and `abstract` means it must be sub classed to be instantiated.

What will be the result of this code?
```java
public final class Animal {
    public void makeSound() {
        System.out.println("Animal sound");
    }
}

public class Dog extends Animal {
    @Override
    public void makeSound() {
        System.out.println("Dog barks");
    }
}
```
?
It will result in a compilation error because `Animal` is `final` and cannot be sub classed.

**Which of the following are true about the `sealed` modifier introduced in Java 17?**
- [ ] a) It restricts which classes can extend or implement the sealed class or interface.
- [ ] b) It allows a class to have multiple direct super classes.
- [ ] c) A sealed class must list the permitted subclasses using the `permits` clause.
- [ ] d) It can be combined with the `final` modifier.
?
`a)` and `c)`

**What are the benefits of using the `sealed` modifier?**
- [ ] a) Provides a clear, controlled inheritance structure.
- [ ] b) Allows multiple inheritance.
- [ ] c) Helps in maintaining a fixed set of subclasses.
- [ ] d) Ensures certain invariants in the design.
?
`a)`, `c)`, and `d)`

**What can a `sealed` class permit in its hierarchy?**
- [ ] a) Final classes
- [ ] b) Abstract classes
- [ ] c) Non-sealed classes
- [ ] d) Static classes
?
 `a)`, `b)`, and `c)`

**Which of the following methods are defined in the `Object` class?**
- [ ] a) `toString()`
- [ ] b) `equals()`
- [ ] c) `hashCode()`
- [ ] d) `clone()`
?
 `a)`, `b)`, and `c)`

**What are the characteristics of an `abstract` class?**
- [ ] a) It cannot be instantiated directly.
- [ ] b) It can contain abstract methods.
- [ ] c) It must be final.
- [ ] d) It is intended to be sub classed.
?
 `a)`, `b)`, and `d)`

**What are the properties of a `final` class?**
- [ ] a) It cannot be sub classed.
- [ ] b) It can be instantiated directly.
- [ ] c) It can contain static methods.
- [ ] d) It must be abstract.
?
 `a)`, `b)`, and `c)`