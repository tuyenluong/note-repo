

----
Creation date: 2022-04-30 22:00
Modification date: Saturday 30th April 2022 22:00:48

----

Tags: [[selenium]]

> Work like you don't need the money. Love like you've never been hurt. Dance like nobody's watching.
> — <cite>Satchel Paige</cite>

In the automation project, let's say we want to click on some of the links.

So we need to tell WebDriver: "I want you to find this element on the page".

**In order, for it to find this element, we need to give it the way to locate that element via what’s provided in the HTML or the DOM (Document Object Model).**

To find elements:

-   driver.findElement() it needs a By object.
-   driver.findElement**s**() it also needs a By object, but in plural.

After we finish that, the findElement() methods will return a WebElement, and it will return the first element that it finds.

In case you want to find multiple elements and you want to count them.

Let's write the code:

-   driver.findElement**s**(By.tagName("A")) the plural version and it will find all the tag name have A elements.
-   Make a variable to contain all the elements in a list:
-   List\<WebElement> variable = driver.findElement**s** (By.tagName("A"))
-   System.out.println(variable.size())

And if you want to find an element that does not exist, then you gonna get an exception: "NoSuchElementException"

In Automation Test, is a very common thing that you will encounter this exception.