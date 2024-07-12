---
Creation_date: 2022-04-30 22:12
Modification_date: Saturday 30th April 2022 22:12:53
Indexes:
  - "[[webDriver]]"
---

----


> Better be ignorant of a matter than half know it.
> — <cite>Publilius Syrus</cite>

Web driver provides an Interface called "Navigation".

Docs: [](https://www.selenium.dev/selenium/docs/api/java/org/openqa/selenium/WebDriver.Navigation)[https://www.selenium.dev/selenium/docs/api/java/org/openqa/selenium/WebDriver.Navigation](https://www.selenium.dev/selenium/docs/api/java/org/openqa/selenium/WebDriver.Navigation)

This navigation interaction should go in the framework. It should not go on the package of the page.

Because interface Navigation is a utility method.

Because it's a util package, every method of the Navigation class return void. So it won't have the object to return

**Multiple Windows**

Method to switch between tabs.

Web Driver has a method `.getWindowHandles()` will get us all the opening windows or tasks.