---
Creation_date: 2024-07-18 09:38
Modification_date: Thursday 18th July 2024 09:38:35
Indexes:
  - "[[methods]]"
---

----

## Static member

- Static members belong to class, not to an instances of the class 
```run-java
public class Main {
    public static void main(String[] args) {
        Clone one = new Clone();
        one.setNameCard("John");

        Clone two = new Clone();
        String nameCard = two.getNameCard();
        System.out.println(nameCard);
    }
}
public class Clone {
    private static String nameCard;
    public static String getNameCard() {
        return nameCard;
    }
    public static void setNameCard(String nameCard) {
        Clone.nameCard = nameCard;
    }
}
```
##  Static method

- Static method can be accessed directly, you don't need to create an instance of the object to access them.
```run-java
public class Main {
    public static void main(String[] args) {
        Clone.setNameCard("John");
        System.out.println(Clone.getNameCard());
    }
}
public class Clone {
    private static String nameCard;
    public static String getNameCard() {
        return nameCard;
    }
    public static void setNameCard(String nameCard) {
        Clone.nameCard = nameCard;
    }
}
```

- NOTICE: Static methods can only call static member directly
- Like some error of this code below:
```java
public class Main {
    public static void main(String[] args) {
        Clone.greetAll();
    }
}
public class Clone {
    String hi = "Good morning!";
    public static void greet1() {
        System.out.println("Hello!");
    }
    public static void greet2() { // Failed due to accessing a non-static field
        System.out.println(hi);  // in a static method
    }
    public void greet3() {
        System.out.println("Good day!");
    }
    public static void greet3() {
        greet1();
        greet2();
        greet3(); // Failed due to accessing a non-static method in a static method
    }
}
```

- You can fix this problem by a several ways:
- First way is makes all fields and methods `static`
- Second way is create an instance for each call. Example:
```run-java
public class Main {
    public static void main(String[] args) {
        Clone.greetAll();
    }
}
public class Clone {
    String hi = "Good morning!";
    public static void greet1() {
        System.out.println("Hello!");
    }
    public static void greet2() { 
        System.out.println(new Clone().hi);
        // Create an instance to accessing the non-static field
    }
    public void greet3() {
        System.out.println("Good day!");
    }
    public static void greetAll() {
        greet1();
        greet2();
        new Clone().greet3();
        // Create an instance to accessing the non-static method
    }
}
```

- Third way is create just one instance and use it every time
```run-java
public class Main {
    public static void main(String[] args) {
        Clone.greetAll();
    }
}
public class Clone {
    String hi = "Good morning!";
    static Clone clone = new Clone();
    public static void greet1() {
        System.out.println("Hello!");
    }
    public static void greet2() { 
        System.out.println(clone.hi);
        // Accessing the Clone instance created as a field for reused purposes
    }
    public void greet3() {
        System.out.println("Good day!");
    }
    public static void greetAll() {
        greet1();
        greet2();
        clone.greet3();
        // Accessing the Clone instance created as a field for reused purposes
    }
}
```

## Constants

- Constants are usually marked `static final` and written in SNAKE_CASE convention
```run-java
public class Main {
    public static void main(String[] args) {
        System.out.println(new Item().calculatePrice(20));
    }
}
public class Item {
    public static final double VALUE_ADDED_TAX = 0.25;
    public double calculatePrice(double price) {
        return price + price * VALUE_ADDED_TAX;
    }
}
```

- `static final` fields must be initialized before use, but this could be done in a static block.
```run-java
public class Main {
    public static void main(String[] args) {
        System.out.println(new Item().calculatePrice(20));
    }
}
public class Item {
    public static final double VALUE_ADDED_TAX;
	static{
		VALUE_ADDED_TAX = 0.25;
	}
    public double calculatePrice(double price) {
        return price + price * VALUE_ADDED_TAX;
    }
}
```

- `static` blocks are useful when you need to calculate values
- Let say you have several constants in a class that you want to calculate, but you don't know the initial value of it. Then you can use `static` block to initialized and calculate.
- You can have multiple `static` block, they are execution order base on their position.
```java
public class MetalBlock {
    public static final double MASS_IN_BLOCK;
    public static final double VOLUME_IN_CUBIC_METERS;
    public static final double DENSITY_IN_KILOS_PER_CUBIC_METER;
	static{ // this block execute first 
		MASS_IN_BLOCK = 100;
		MASS_IN_BLOCK = 0.01;
	}
    static{ // then this block execute after 
		DENSITY_IN_KILOS_PER_CUBIC_METER = MASS_IN_BLOCK / MASS_IN_BLOCK;
	}
}
```

- `static imports` are used to import `static members` of classes
```java
System.out.println(Math.pow(2,5));
```

- `pow()` is the static method, so we can use static import
```java
import static java.lang.Math.pow;
System.out.println(pow(2,5));
```

- Be careful about the order 
	- `import` must be at the beginning
- And the`import`keyword must goes first before any option keyword for importation
```java
static import java.lang.Math.pow; // THIS WILL NOT COMPILE
System.out.println(pow(2,5));
```




---
## Flash cards section

It's true that every static member is belong to the class, not instance?
- [ ] True
- [ ] False
?
Yes, it's true that static members is belong to class himself, not for instance.

What is the result of this code example:
```java
public class Main {
    public static void main(String[] args) {
        Clone one = new Clone();
        one.setNameCard("John");

        Clone two = new Clone();
        String nameCard = two.getNameCard();
        System.out.println(nameCard);
    }
}
public class Clone {
    private static String nameCard;
    public static String getNameCard() {
        return nameCard;
    }
    public static void setNameCard(String nameCard) {
        Clone.nameCard = nameCard;
    }
}
```
?
The out put is `John` since the `nameCard` member is static which is belong to the class, not instances. So even if you create a new instance of the class and get the member value, it still able to get the value without any error being occur.
```run-java
public class Main {
    public static void main(String[] args) {
        Clone one = new Clone();
        one.setNameCard("John");

        Clone two = new Clone();
        String nameCard = two.getNameCard();
        System.out.println(nameCard);
    }
}
public class Clone {
    private static String nameCard;
    public static String getNameCard() {
        return nameCard;
    }
    public static void setNameCard(String nameCard) {
        Clone.nameCard = nameCard;
    }
}
```

Is this `import` syntax correct?
```java
static import java.lang.Math.pow;
```
- [ ] Yes
- [ ] No
?
It's not allowed to have any optional keyword such as `static` goes before the `import` keyword, It will result in the compiler will not compiles.

Is there a way that a `static final` member get assign a value later, after the initialized?
- [ ] Yes, it's possible
- [ ] No, `static final` member must be initialized before use
?
Yes, it's possible, because you can use `static` block to assign a value to it.
```run-java
public class Main {
    public static void main(String[] args) {
        System.out.println(new Item().calculatePrice(20));
    }
}
public class Item {
    public static final double VALUE_ADDED_TAX;
	static{
		VALUE_ADDED_TAX = 0.5;
	}
    public double calculatePrice(double price) {
        return price + price * VALUE_ADDED_TAX;
    }
}
```
<!--SR:!2024-08-05,3,250-->
