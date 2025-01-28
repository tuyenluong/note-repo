---
Creation_date: 2025-01-20 20:17
Modification_date: Monday 20th January 2025 20:17:15
Indexes:
  - "[[spring_mvc]]"
---

----
## What is Model object in Spring MVC?
In **Spring MVC**, the `Model` object is a central part of the framework used to pass data from the **controller** to the **view**. It serves as a container to store attributes that will be used for rendering the view, such as HTML templates in **Thymeleaf**, **JSP**, or other templating engines.

### **Key Features of the `Model` Object**
1. **Stores Attributes for Views**
	1. The `Model` object allows you to add key-value pairs (attributes) that the view can access and render.
	2. Example: The `message` attribute is now accessible in the `greeting` view.
```java
@GetMapping("/greeting")
public String greeting(Model model) {
    model.addAttribute("message", "Hello, World!");
    return "greeting"; // View name (e.g., greeting.html or greeting.jsp)
}
```
1. Simplifies Data Passing
	1. The `Model` eliminates the need for manually constructing and passing data to views.
2. Provides Flexibility
	1. You can store various types of objects in the `Model`, such as strings, collections, or custom objects.

## How the `Model` Works
- When a controller method is invoked, the `Model` object is created by Spring.
- Attributes added to the `Model` are automatically passed to the view for rendering.
- Views access these attributes using their respective templating syntax, such as `${attributeName}` in **Thymeleaf** or `${attributeName}` in **JSP**.

## **Commonly Used Methods in `Model`**

Here are the most frequently used methods in the `Model` interface:

|Method|Description|
|---|---|
|`addAttribute(String key, Object value)`|Adds an attribute to the model.|
|`addAllAttributes(Map<String, ?> attributes)`|Adds multiple attributes to the model.|
|`containsAttribute(String key)`|Checks if a specific attribute exists in the model.|













---
## Flash cards section
