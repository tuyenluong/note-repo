---
Creation_date: 2024-08-16 16:41
Modification_date: Friday 16th August 2024 16:41:29
Indexes:
  - "[[class_design]]"
---

----

## Getter and Setter

In the [SOLID principle](https://viblo.asia/p/solid-la-gi-nguyen-tac-lap-trinh-solid-va-cach-ap-dung-chung-3kY4gEG9LAe) guidelines, there is a principle called "*Open/Closed Principle*". The rule behind this principle is **open** for extendable but **closed** for modification 

In this principle, when we want to access or change the value of the field of any given, we will use **getters** and **setters**. These method will enabled use a way to access or modify the value of the field.

```java
public class Mammal{
	private int age; // This field only access through getter and setter only
	protected String name;
	
	public int getAge(){
		return age;
	}
	public void setAge(int theAge){
		age = theAge;
	}
}
```

This is a very common practice and it's always recommended to use `private` fields and then access to them through `getter` and `setter`. It's just more safer and it gives you more control over your code and over the fields which might be updated or access.

## Extends Class

The next part we will create a new class called `Dog.java` which will extends from class `Mammal.java`. It'll inherits all the attribute and behavior from the `super` class, which is `Mamal.java` class

```run-java
public class Dog extends Mammal {
	public static void main(String... args){
		Dog dog = new Dog();
		dog.setNameAndAge("Rex", 5);
		dog.barks();
	}

	protected void setNameAndAge(String dogName, int age){
		name = dogName; // The name field protected modifier, it allows access from the sub classes.
		setAge(age); // But since age field is private, it can only access through getter and setter of the super class
	}
	public void barks(){
		System.out.println("Dog " + name + " (" + getAge() + ") says: woof!");
	}

	class Mammal{
		private int age; // This field only access through getter and setter only
		protected String name;
	
		public int getAge(){
			return age;
		}
		public void setAge(int theAge){
			age = theAge;
		}
	}
}
```









---
## Flash cards section
