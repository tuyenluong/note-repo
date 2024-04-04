

----
Creation date: 2024-03-10 14:58
Modification date: Sunday 10th March 2024 14:58:02

----

#Java 
## The Syntax of for-each loop
```java
String[] cars = {"Ford", "Renault", "Fiat", "Kia"}
for(String car : cars){
	System.out.println(car);
}
```
- For loop is often used to access the members of the array (*or Collection*)
- Using traditional for loop
```java
String[] cars = {"Ford", "Renault", "Fiat", "Kia"}
for(int i = 0; i < cars.length; i++){
	System.out.println(cars[i]);
}
```

- Using for-each loop
```java
String[] cars = {"Ford", "Renault", "Fiat", "Kia"}
for(String car : cars){
	System.out.println(car);
}
```

- For-each loop is more convenient to access all member of the array
- But you don't have control over the indices.
- For that, for-each loop will encounter disadvantage in case of mathematical purpose, multiplication of matrices problem or whatever, you will not use for each loop, but you will use traditional for loop.

## In Java 17, for each-loop is often used with [[JAVA - Local Variable Type Inference|LVTI]]

```java
String[] cars = {"Ford", "Renault", "Fiat", "Kia"}
for(var car : cars){
	System.out.println(car);
}
```