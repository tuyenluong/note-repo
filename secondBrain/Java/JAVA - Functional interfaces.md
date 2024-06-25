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
