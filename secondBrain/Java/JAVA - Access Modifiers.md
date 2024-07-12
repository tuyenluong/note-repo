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