---
Creation_date: 2024-06-11 11:29
Modification_date: Tuesday 11th June 2024 11:29:35
Indexes:
  - "[[webDriver]]"
---
----
- Should use Ctrl + Click to open new tab, rather then open new window.
- Open new window will result in windows have to handles more to get to the correct window context.

```java
new Actions(driver)
.keyDown(Keys.CONTROL).click(webElement).keyUp(Keys.CONTROL)
.build().perform();
```






---
## Flash cards section
