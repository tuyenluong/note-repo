---
Creation_date: 2024-03-10 14:58
Modification_date: Sunday 10th March 2024 14:58:02
Indexes:
  - "[[flow_control]]"
---

----

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


---
## Flash cards section

What is the syntax of a for-each loop in Java?
?
```java
for(Type element : array) {
    // code to be executed
}
```

How can you use a for-each loop to print all elements in a string array called `cars`?
?
```java
String[] cars = {"Ford", "Renault", "Fiat", "Kia"};
for(String car : cars) {
    System.out.println(car);
}
```

What is a common use case for a traditional for loop when working with arrays? ;; A traditional for loop is often used to access members of the array and control over the indices.
<!--SR:!2024-08-06,4,270-->

How can you use a traditional for loop to print all elements in a string array called `cars`?
?
```java
String[] cars = {"Ford", "Renault", "Fiat", "Kia"};
for(int i = 0; i < cars.length; i++) {
    System.out.println(cars[i]);
}
```

What is an advantage of using a for-each loop over a traditional for loop? ;; A for-each loop is more convenient for accessing all members of the array.

What is a disadvantage of using a for-each loop compared to a traditional for loop? ;; You don't have control over the indices in a for-each loop.
<!--SR:!2024-08-06,4,270-->

In what scenarios would a traditional for loop be preferable over a for-each loop? ;; In scenarios involving mathematical purposes, such as multiplication of matrices or where index control is required, a traditional for loop is preferable.

How can you use a for-each loop with Local Variable Type Inference (LVTI) in Java 17 to print all elements in a string array called `cars`?
?
```java
String[] cars = {"Ford", "Renault", "Fiat", "Kia"};
for(var car : cars) {
    System.out.println(car);
}
```







