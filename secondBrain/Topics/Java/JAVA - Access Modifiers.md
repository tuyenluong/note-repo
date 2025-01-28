---
Creation_date: 2024-07-09 00:34
Modification_date: Tuesday 9th July 2024 00:34:58
Indexes:
  - "[[methods]]"
---

----
## Access Modifiers

| Modifiers              | Behavior                                                                                              |
| ---------------------- | ----------------------------------------------------------------------------------------------------- |
| private                | Method or field can be accessed only within the class in which they are declared                      |
| default (*no keyword*) | Method or field can be accessed only within the same package                                          |
| protected              | Method or field can be accessed within the same package and outside the package through child classes |
| public                 | Method or field can be accessed from everywhere in the program                                        |

## Example

- `private` modifier example
```run-java
public class Test{
	public static void main(String... args){
		Dog dog = new Dog();
		System.out.println(dog.genus);  // This will not compile
	}
}
class Dog{
	private String genus = "Canis";
}
```

- `public` modifier example
- This will compile due to the dog reference is calling the public print method despite the field `genus` is private. This is called a getter.
```run-java
public class Test{
	public static void main(String... args){
		Dog dog = new Dog();
		dog.printGenus();  
		// This will compile
	}
}
class Dog{
	private String genus = "Canis";
	public void printGenus(){
		System.out.println("Genus: "+ genus);
	}
}
```

- `default` modifier don't need to explicitly type out. Just leave the Access modifier empty then Java will automatically  consider it to be `default`
- `default` modifier example within a same package
![[Pasted image 20240710162910.png]]

- `protected` modifier example outside of package but extends from a parent class
![[Pasted image 20240710163613.png]]






---
## Flash cards section

Which access modifier that allow method or field can be accessed only within the class in which they are declared? ;; `private`

Which access modifier that allow method or field can be accessed only within the same package? ;; `default`

Which access modifier that allow method or field can be accessed within the same package and outside the package through child classes? ;; `protected`

Which access modifier that allow method or field can be accessed from everywhere in the program? ;; `public`

In the example with a `private` modifier, why does the following code not compile? The class `Test` has a `main` method that tries to access the `genus` field of a `Dog` object, which is declared as `private` in the `Dog` class.
```java
public class Test {
    public static void main(String... args) {
        Dog dog = new Dog();
        System.out.println(dog.genus);  // This will not compile
    }
}
class Dog {
    private String genus = "Canis";
}
```
?
The code does not compile because the `genus` field in the `Dog` class is `private` and cannot be accessed outside of the `Dog` class.

Why does the example with the `public` modifier compile? The class `Test` has a `main` method that calls the `printGenus` method of a `Dog` object, despite the `genus` field being `private`.
```java
public class Test {
    public static void main(String... args) {
        Dog dog = new Dog();
        dog.printGenus();  // This will compile
    }
}
class Dog {
    private String genus = "Canis";
}
```
?
The code compiles because the `printGenus` method is `public` and can be accessed, allowing it to print the value of the `private` field `genus`.
```java
class Dog {
    private String genus = "Canis";
    public void printGenus() {
        System.out.println("Genus: " + genus);
    }
}
```

How do you indicate a `default` modifier for a method or field in Java? ;; You do not explicitly type out a keyword; leaving the access modifier empty will automatically make it `default`.

Can a `protected` field be accessed outside of its package? ;; Yes, a `protected` field can be accessed outside of its package through child classes.

How is access to a `protected` modifier demonstrated in the provided example? ;; A `protected` field or method in the parent class can be accessed by a child class, even if the child class is in a different package.

What is the purpose of using a getter method with a `private` field? ;; A getter method allows controlled access to the value of a `private` field from outside the class.






