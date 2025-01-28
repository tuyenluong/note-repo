---
Creation_date: 2025-01-20 20:23
Modification_date: Monday 20th January 2025 20:23:02
Indexes:
  - "[[spring_mvc]]"
  - "[[spring_boot]]"
---

----
## Difference Between `Model`, `ModelMap`, and `ModelAndView`

| Feature              | `Model`                   | `ModelMap`                                | `ModelAndView`                                                  |
| -------------------- | ------------------------- | ----------------------------------------- | --------------------------------------------------------------- |
| **Type**             | Interface                 | Implementation of `Map`                   | Object containing both `Model` and view.                        |
| **Primary Purpose**  | Add attributes for views. | Add attributes for views (extends `Map`). | Combine model data and view name in one object.                 |
| **Example Use Case** | Simple data passing.      | Use when a `Map` is preferred.            | Use when both model and view logic need to be defined together. |

## **Use Case**

- **[[SPRING - Model interface|Model]]**: Use when you're only passing data to the view.
- **ModelMap**: Use when you need more flexibility, such as iterating over attributes like a map.
- **[[SPRING - ModelAndView class|ModelAndView]]**: Use for more complex scenarios where you need to combine model attributes and view names programmatically.

## **Summary**

The `Model` object in Spring MVC is a powerful and flexible tool for passing data from controllers to views. It helps make your applications cleaner and more maintainable by abstracting away the process of binding data to views. By using `Model`, you can efficiently manage the data flow in your Spring MVC applications.

















---
## Flash cards section
