---
Creation_date: 2022-04-30 22:11
Modification_date: Saturday 30th April 2022 22:11:40
Indexes:
  - "[[webDriver]]"
---

----


> He who lives in harmony with himself lives in harmony with the world.
> — <cite>Marcus Aurelius</cite>

When we test, we may encounter some type of test that needs to wait a certain amount of time to find an element or wait for a function to load.

**Implicit Waits**

We can use it like this:

"_driver.manage().timeouts(). **implicitWait(30, TimeUnit.SECONDS);**"_

What this is saying is that any time WebDriver needs to interact with an element, it should poll the website for _up to_ 30 seconds until it finds that element.

-   If it finds the element before 30 seconds, then it will interact with it then.
-   If not, then it will wait and continue to poll until it finds the element, or until the 30 seconds are up.
-   If the 30 seconds are up and it has not found the element, then it will throw a NoSuchElementException.

**Caution**

Be careful when using implicit waits because you're setting this at the project level, meaning it will wait up until this amount of time for all interactions, and this could slow down your project if you're not careful.