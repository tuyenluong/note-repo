---
Creation_date: 2025-01-20 20:01
Modification_date: Monday 20th January 2025 20:01:53
Indexes:
  - "[[spring_annotation]]"
  - "[[spring_mvc]]"
---

----

## What `@ModelAttribute` does in Spring?
The `@ModelAttribute` annotation in Spring MVC is used to bind data to a model object and make it available to the view. It plays an important role in handling form data, populating models, and sharing data between controllers and views.

## Key Uses of `@ModelAttribute`
### Binding Request Data to an Object

- `@ModelAttribute` is commonly used to bind request parameters (e.g., form inputs) to an object. It helps in automatically populating an object from incoming HTTP request data.
```java
@PostMapping("/submit")
public String handleForm(@ModelAttribute User user) {
    // The 'user' object is automatically populated with form data (e.g., name, email).
    System.out.println(user.getName());
    return "success";
}
```

Example Form:
```html
<form action="/submit" method="post">
    <input type="text" name="name" value="John" />
    <input type="email" name="email" value="john@example.com" />
    <button type="submit">Submit</button>
</form>
```

In this example:
- Spring binds the `name` and `email` form fields to the `User` object passed into the controller method.
## Difference Between `@ModelAttribute` and `@RequestBody`

| Feature        | `@ModelAttribute`                           | `@RequestBody`                               |
| -------------- | ------------------------------------------- | -------------------------------------------- |
| **Purpose**    | Binds request parameters to a model object. | Maps the HTTP request body to a Java object. |
| **Input Type** | Form data, query parameters.                | JSON, XML, or plain text in the body.        |
| **Use Case**   | Form-based applications.                    | REST APIs handling JSON/XML requests.        |
## **Summary**
- `@ModelAttribute` is a powerful tool in Spring MVC for binding form data, pre-populating models, and sharing data across views and controllers.
- It simplifies form handling by automatically mapping request parameters to Java objects.
- It allows developers to keep controllers clean and reduce boilerplate code.










---
## Flash cards section
