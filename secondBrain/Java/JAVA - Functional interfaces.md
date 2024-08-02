---
Creation_date: 2024-05-20 10:21
Modification_date: Monday 20th May 2024 10:21:43
Indexes:
  - "[[functional_interfaces]]"
---
----
# Four available Functional interfaces and examples

There are four main functional interfaces in Java, three of which are commonly used in the **Stream API**:
- `Function<T, R>`: This functional interface takes an input of type `T`, processes it through its functional method `apply`, and returns a result of type `R`. It is primarily used in the `map()` method of the Stream API.
- `Predicate<T>`: This functional interface takes an input of type `T`, processes it through its functional method `test`, and returns a `Boolean` result. It is mainly used in the `filter()` method of the Stream API.
- `Consumer<T>`: This functional interface takes an input of type `T`, processes it through its functional method `accept`, and returns no result. It is often used in terminal operations such as `forEach()` and `collect()` methods of the Stream API.
    
The fourth functional interface is `Supplier<T>`, which is not typically used within the Stream API. It is the opposite of `Consumer<T>`:
- `Supplier<T>`: This functional interface takes no input, processes whatever code is passed through its functional method `get`, and returns a result of type `T`.


---
## Flash cards section

What does the `Function<T, R>` functional interface do? ;; It takes an input of type `T`, processes it through its functional method `apply`, and returns a result of type `R`. It is primarily used in the `map()` method of the Stream API.

How is the `Predicate<T>` functional interface used in the Stream API? ;; It takes an input of type `T`, processes it through its functional method `test`, and returns a `Boolean` result. It is mainly used in the `filter()` method of the Stream API.

What is the purpose of the `Consumer<T>` functional interface? ;; It takes an input of type `T`, processes it through its functional method `accept`, and returns no result. It is often used in terminal operations such as `forEach()` and `collect()` methods of the Stream API.

Which functional interface is the opposite of `Consumer<T>`? ;; `Supplier<T>`.

What does the `Supplier<T>` functional interface do? ;; It takes no input, processes whatever code is passed through its functional method `get`, and returns a result of type `T`.

How is the `Function<T, R>` interface used in the Stream API? ;; It is primarily used in the `map()` method to transform elements of the stream.

In which Stream API method is the `Predicate<T>` interface commonly used? ;; It is commonly used in the `filter()` method to test elements of the stream.

Which Stream API methods often use the `Consumer<T>` interface? ;; Terminal operations such as `forEach()` and `collect()` methods.

What does this code do?
```java
List<String> names = Arrays.asList("Alice", "Bob", "Charlie");
List<Integer> nameLengths = names.stream()
                                 .map(String::length)
                                 .collect(Collectors.toList());
System.out.println(nameLengths);
```
?
It creates a list of strings, transforms each string to its length using the `map()` method, collects the lengths into a list, and prints the list of name lengths: `[5, 3, 7]`.

What does this code snippet accomplish?
```java
List<String> names = Arrays.asList("Alice", "Bob", "Charlie");
List<String> longNames = names.stream()
                              .filter(name -> name.length() > 3)
                              .collect(Collectors.toList());
```
?
It filters the list of names to only include names longer than 3 characters and prints the resulting list: `["Alice", "Charlie"]`.

Explain what this code does:
```java
List<String> names = Arrays.asList("Alice", "Bob", "Charlie");
names.forEach(System.out::println);
```
?
It iterates through the list of names and prints each name on a new line:
```java
Alice
Bob
Charlie
```
<!--SR:!2024-08-05,3,268-->

What does this code do?
```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);
int sum = numbers.stream()
                 .mapToInt(Integer::intValue)
                 .sum();
System.out.println(sum);
```
?
It creates a list of integers, converts the list to an `IntStream` using `mapToInt()`, sums the values, and prints the sum: `15`.

Describe the purpose of this code:
```java
List<String> words = Arrays.asList("apple", "banana", "cherry");
boolean allMatch = words.stream()
                        .allMatch(word -> word.length() > 4);
System.out.println(allMatch);
```
?
It checks if all strings in the list have a length greater than 4 using the `allMatch()` method and prints the result: `true`.

What is the output of this code?
```java
List<String> fruits = Arrays.asList("apple", "banana", "cherry");
List<String> upperCaseFruits = fruits.stream()
                                     .map(String::toUpperCase)
                                     .collect(Collectors.toList());
System.out.println(upperCaseFruits);
```
?
It transforms each string in the list to uppercase and prints the resulting list: `["APPLE", "BANANA", "CHERRY"]`.

Explain what this code snippet does:
```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);
numbers.stream()
       .filter(n -> n % 2 == 0)
       .forEach(System.out::println);
```
?
It filters the list to include only even numbers and prints each even number:
```java
2
4
```

What does this code achieve?
```java
List<String> animals = Arrays.asList("cat", "dog", "elephant");
long count = animals.stream()
                    .filter(animal -> animal.length() > 3)
                    .count();
System.out.println(count);
```
?
It counts the number of strings in the list with a length greater than 3 and prints the count: `1`.
<!--SR:!2024-08-03,1,230-->

What is the result of the following code?
```java
List<String> items = Arrays.asList("pen", "notebook", "eraser");
Optional<String> anyItem = items.stream()
                                .findAny();
anyItem.ifPresent(System.out::println);
```
?
It retrieves any element from the stream (which could be any of the strings "pen", "notebook", or "eraser") and prints it if present. The output could be any one of the items in the list, depending on the stream's state.










---
## Flash cards section
