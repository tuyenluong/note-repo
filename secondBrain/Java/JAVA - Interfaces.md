---
Creation_date: 2024-07-30 14:47
Modification_date: Tuesday 30th July 2024 14:47:18
Indexes:
  - "[[interfaces]]"
---

----

## What Are Interfaces?

- A class can only extend one class
- But what if we want to `extends` more (*abstract*) classes?
- Then we use `interface`
	- Similar to `abstract` class
	- But now one class can `implements` any number of interfaces
	- Keyword `implemnents` separated by comma
- Like in `abstract` classes, you cannot create an instance of the interface using keyword `new`
- All interfaces and its methods are implicitly `abstract`, so they cannot be marked as `final`

### Fields in Interfaces

- And all fields declared in an interface are implicitly `public`, `static`, and `final`. This means that any field in an interface is a constant. You do not need to explicitly specify these modifiers, as they are automatically applied.

```java
public interface Car{
	int distanceWithFullTank (int tankVolume); // Abstract method has no body
	int MAXIMUM_WEIGHT = 2000; // Constant field
}
```

- The keyword between the asterisks is explicitly written of the previous example.
```java
public *abstract* interface Car{ 
	*public abstract* int distanceWithFullTank (int tankVolume); 
	*public static final* int MAXIMUM_WEIGHT = 2000; 
}
```

- All interfaces are implicitly `abstract`, so they cannot be marked as `final`. 

### Methods in Interfaces

Prior to [[java-8-or-lower|Java 8]], all methods in interfaces were implicitly `public` and `abstract` (*except for static methods which were not allowed*).
- From [[java-8-or-higher|Java 8]] onwards, interfaces can contain: 
	- **Default methods:** These methods have a body and are declared with the `default` keyword. They are not `final` and can be overridden by implementing classes.
	- **Static methods:** These methods have a body and are declared with the `static` keyword. They cannot be overridden by implementing classes.
- From [[java-9|Java 9]] onwards, interfaces can also contain:
	- **Private methods:** These methods have a body and are declared with the `private` keyword. They are used to share code between default methods within the same interface. They cannot be accessed outside the interface.
	- **Private static methods:** These methods also have a body and are declared with the `private static` keyword. They can be used to share code between static methods and default methods.

```java
public interface MyInterface {
    // Implicitly public and abstract
    void abstractMethod();

    // Default method (from Java 8)
    default void defaultMethod() {
        System.out.println("Default method");
    }

    // Static method (from Java 8)
    static void staticMethod() {
        System.out.println("Static method");
    }

    // Private method (from Java 9)
    private void privateMethod() {
        System.out.println("Private method");
    }

    // Private static method (from Java 9)
    private static void privateStaticMethod() {
        System.out.println("Private static method");
    }
}
```
## Rules of implementation

| ID  | Rules                                                                                               | Overriding rules |
| --- | --------------------------------------------------------------------------------------------------- | ---------------- |
| 1   | Keyword `public` is required                                                                        | REQUIRED         |
| 2   | Return type must be covariant with the interface method                                             | REQUIRED         |
| 3   | [[JAVA - Class Structure#^15d35c\|Signature]] (*name & parameters*) must match the interface method | REQUIRED         |
| 4   | All inherited methods must be implemented                                                           | REQUIRED         |

- An interface can extend another interface, forming an interface hierarchy.
- When a class implements an extended interface, it is required to implement all methods declared in both the `super interface` and the `sub interface`.
```java
// An interface can extend another interface
public interface CanSwim extends Mammal {
    int swim();
}

public interface Mammal {
    int eats();
}

public class Elephant implements CanSwim {
    public int swim() { 
        return 5; 
    }
    public int eats() { 
        return -1; 
    }
}
```

- Interfaces can declare methods with the same signature.
- When a class implements multiple interfaces that have methods with the same [[JAVA - Class Structure#^15d35c|signature]], the class must provide a single implementation for that method.
```java
// Duplicate methods, example #1
public interface Tetrapod {
    void eats();
}

public interface Mammal {
    void eats();
}

// This class implements two interfaces that have methods with the same signature
public class Dog implements Tetrapod, Mammal {
    @Override
    public void eats() { // This is OK because the return types match (covariant or same)
        System.out.println("Dog is eating.");
    }

    public static void main(String... args) {
        Dog dog = new Dog();
        dog.eats();
    }
}
```

- But in order to have interfaces declare methos with the same signature, the return type must be the same.
```java
// Duplicate methods, example #2
public interface Tetrapod {
    void eats(); // no return type
}

public interface Mammal {
    int eats(); // int type
}

public class Dog implements Tetrapod, Mammal {
    // This does not compile (non-covariant return types)
    public void eats() {
        System.out.println("Dog is eating.");
    }

    public static void main(String[] args) {
        Dog dog = new Dog();
        dog.eats();
    }
}
```

## Default Interface Methods

In Java, starting from [[java-8-or-higher|Java 8]], interfaces can have methods with a default implementation. These are known as default methods.
- Imagine you have an interface which is implemented by 100 classes
- For some reason you need to add a another method in your interface
- If this method were abstract, you would need to implement it in all 100 classes
- This is solved by making a method default (*non-abstract*)
- Default method must have a body (*default implementation*)

```java
public interface Mammal {
    public void walks();
    public void eats();
    
	// no need to implements sleeps() in classes which implement Mammal
    default void sleeps() { 
        System.out.println("A mammal sleeps.");
    }
}

public class Dog implements Mammal {
    public void walks() { System.out.println("Dog walks."); }
    public void eats() { System.out.println("Dog eats."); }
}

public class Cat implements Mammal {
    public void walks() { System.out.println("Cat walks."); }
    public void eats() { System.out.println("Cat eats."); }
}
```

## Rules for Using Default Methods 

1. Keyword `default` with a method can only be used in the `interface`
2. Has to have a body (`default` implementation)
3. Implicitly `public`
4. Cannot be `abstract`, `final` or `static`
5. May or may not be overridden by a class implementing the `interface`
6. If the class inherits two or more default methods with the same method signature, then it must override the method
### Example

- Override the default method if the implemented interfaces have the same signature method.
```java
public interface Car {
    public default int getMaxSpeed() { return 100; }
}

public interface Truck {
    default int getMaxSpeed() { return 70; }
}

public class Van implements Car, Truck {
    public int getMaxSpeed() {
        // We must override getMaxSpeed() because there are two of them with the same signature
        return 80;
    }
    
    public int getMaxSpeedCar() {
        // This is how we call the default method from the Car interface
        return Car.super.getMaxSpeed();
    }
}
```

- Static Interface Methods
```java
// Static interface methods
public interface Car {
    static int getMaxSpeed() { return 100; }
}

public class Ford implements Car {
    // I want to access getMaxSpeed() from Car
    public int getMaxSpeedCar() {
        return Car.getMaxSpeed(); // Static methods cannot be overridden!
    }
}
```

- Private Interface Methods
```java
// Private interface methods
public interface Car {
    private static int calculateSpeed() {
        int speed = 70 * 2;
        return speed;
    }

    public default int getMaxSpeed() {
        return calculateSpeed();
    }

    public default int getRecommendedSpeed() {
        return (int)(calculateSpeed() * 0.8);
    }
}
```
## Rules for Using Private Interface Methods

1. Marked with keyword `private`
2. Must have a body
3. `private static` methods may be called by any method in the interface
4. `non-static private` methods may be called only by non-static methods

```java
// Default and private non-static methods can call abstract methods!
public interface Car {
    // Private static method
    private static int calculateSpeed(int factor) {
        return 70 * factor;
    }

    // Private non-static method
    private int calculateRecommendedSpeed() {
        return calculateSpeed(2);
    }

    // Public default method
    default int getMaxSpeed() {
        return calculateSpeed(2);
    }

    // Public default method using private non-static method
    default int getRecommendedSpeed() {
        return calculateRecommendedSpeed() * 80 / 100;
    }
}

// These methods are abstract and they have to be implemented
// => When you call printCarFeatures() from a class which implements the interface,
// the implementation given in that class will be used in printCarFeatures()
```

## Summary of Java Interfaces:

- **Purpose**: Interfaces allow for defining methods that must be implemented by classes, enabling multiple inheritance.
- **Implementation**: Classes use the `implements` keyword to implement interfaces. A class can implement multiple interfaces.
- **Fields**: All fields in an interface are implicitly `public`, `static`, and `final`.
- **Methods**:
    - Prior to [[java-8-or-lower|Java 8]]: Methods in interfaces were implicitly `public` and `abstract`.
    - [[java-8-or-higher|Java 8+]]: Interfaces can have default methods (with `default` keyword) and static methods.
    - [[java-9|Java 9]]: Interfaces can also have `private` methods and `private` `static` methods.
- **Default Methods**: These methods have a body, are not `final`, and can be overridden by implementing classes.
- **Static Methods**: These methods have a body and cannot be overridden by implementing classes.
- **Private Methods**: Used to share code between default methods within the same interface and cannot be accessed outside the interface.
- **Implementation Rules**:
    - Methods must match the signature and return type of the interface methods.
    - All inherited methods must be implemented.
- **Extending Interfaces**: An interface can extend another interface, forming an interface hierarchy.
- **Conflicting Methods**: If a class implements multiple interfaces with the same method signature, it must provide a single implementation for that method.



---
## Flash cards section

**What is the purpose of an interface in Java?** ;; To define methods that must be implemented by any class that implements the interface, allowing for multiple inheritance.

**What keyword is used to implement an interface in a class?** ;; `implements`

**Can a Java class implement multiple interfaces?** ;; Yes, a class can implement multiple interfaces.

**Can you create an instance of an interface using the `new` keyword?** ;; No, you cannot create an instance of an interface directly.

**What are the implicit modifiers for fields in an interface?** ;; `public`, `static`, and `final`

**What are the implicit modifiers for methods in an interface prior to Java 8?** ;; `public` and `abstract`

**From which Java version can interfaces have default and static methods?** ;; Java 8

**What additional type of methods can interfaces have from Java 9 onwards?** ;; Private methods and private static methods

Given the following interface and implementation, what will be the output?
```java
public interface Vehicle {
    default void honk() {
        System.out.println("Vehicle is honking");
    }
}

public class Car implements Vehicle {
    public void honk() {
        System.out.println("Car is honking");
    }

    public static void main(String[] args) {
        Vehicle myCar = new Car();
        myCar.honk();
    }
}
```
?
`Car is honking`

Given the following code, what will be the output?
```java
public interface Vehicle {
    static void display() {
        System.out.println("Static method in Vehicle");
    }
}

public class Car implements Vehicle {
    public static void main(String[] args) {
        Vehicle.display();
    }
}
```
?
`Static method in Vehicle`
<!--SR:!2024-08-06,4,270-->

**True or False: Static methods in an interface can be overridden by implementing classes.** ;; False

**True or False: Default methods in an interface can be overridden by implementing classes.** ;; True

**Which of the following are true about interface fields in Java?**
- [ ] a) They can be `public`
- [ ] b) They can be `protected`
- [ ] c) They can be `private`
- [ ] d) They are implicitly `final`
?
`a)` and `d)`

Which of the following are true for default methods in interfaces?
- [ ] a) They must be overridden by implementing classes
- [ ] b) They can have a body
- [ ] c) They cannot be overridden
- [ ] d) They are implicitly `public`
?
`b)` and `d)`
<!--SR:!2024-08-06,4,270-->

**Which of the following are rules for private methods in interfaces?**
- [ ] a) They must be static
- [ ] b) They must have a body
- [ ] c) They can be called by default methods
- [ ] d) They can be called by implementing classes
?
`b)` and `c)`
**Which of the following statements are true about methods in an interface?**
- [ ] a) They can be abstract
- [ ] b) They can be static
- [ ] c) They can be final
- [ ] d) They can be default
?
`a)`, `b)`, and `d)`
**Which of the following are characteristics of a method declared in an interface?**
- [ ] a) It can be private if it is declared static
- [ ] b) It can be protected if it is declared static
- [ ] c) It can be public if it is declared abstract
- [ ] d) It can be overridden if it is declared default 
?
`a)`, `c),` and `d)`

**What happens if a class implements two interfaces that have methods with the same signature but different return types?** ;; The class will not compile because it cannot implement methods with the same signature but different return types.

**When a class implements multiple interfaces, how does it decide which default method to use if they have the same signature?** ;; The class must override the method to resolve the conflict.

What will be the output of the following code?
```java
public interface Animal {
    default void makeSound() {
        System.out.println("Animal sound");
    }
}

public interface Bird {
    default void makeSound() {
        System.out.println("Bird sound");
    }
}

public class Sparrow implements Animal, Bird {
    public void makeSound() {
        Bird.super.makeSound();
    }

    public static void main(String[] args) {
        Sparrow sparrow = new Sparrow();
        sparrow.makeSound();
    }
}
```
?
`Bird sound`