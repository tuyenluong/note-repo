---
Creation_date: 2025-01-31 19:38
Modification_date: Friday 31st January 2025 19:38:28
Indexes:
  - "[[spring_annotation]]"
  - "[[fleeting_notes]]"
tags:
  - tuyenLuong
---

----

- `@ExceptionHandler` + `@Controller` = The exception handling logic only applicable within that `@Controller` class.
- `@ExceptionHandler` + `@ControllerAdvice` = The exception handling logic applicable across **ALL** `@Controller` classes.
- `@ExceptionHandler` can handle any number exceptions, consider that the `ExceptionHandler` already define all the exceptions in an array.
	- We can even declare our own custom exception as well.
Single exception:
```java
@ExceptionHandler(Exception.class)  
public ModelAndView exceptionHandler(Exception exception){  
    ModelAndView errorPage = new ModelAndView();  
    errorPage.setViewName("error");  
    errorPage.addObject("errormsg", exception.getMessage());  
    return errorPage;  
}
```

Multiple exceptions:
```java
@ExceptionHandler({Exception.class, NullPointerException.class, ArrayIndexOutOfBoundsException.class})  
public ModelAndView exceptionHandler(Exception exception){  
    ModelAndView errorPage = new ModelAndView();  
    errorPage.setViewName("error");  
    errorPage.addObject("errormsg", exception.getMessage());  
    return errorPage;  
}
```

- And we can define the level of exception that we like to handler to intercept by changing the handler method argument:
```java
@ExceptionHandler(Exception.class)  
public ModelAndView exceptionHandler(RuntimeException exception){ // <<---
    ModelAndView errorPage = new ModelAndView();  
    errorPage.setViewName("error");  
    errorPage.addObject("errormsg", exception.getMessage());  
    return errorPage;  
}
```


















---
## Flash cards section
