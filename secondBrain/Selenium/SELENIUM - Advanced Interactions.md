---
Creation_date: 2022-04-30 22:06
Modification_date: Saturday 30th April 2022 22:06:28
Indexes: "[[selenium]]"
---

----


> Nature gave us one tongue and two ears so we could hear twice as much as we speak.
> — <cite>Epictetus</cite>

**"Actions"** Class

Until now we have learned how to click on the elements, select elements from the dropdown, all types of interactions.

Today we learn some more advanced Interactions, Actions class.

-   Hover on the elements
-   When creating an Actions object, we need to pass in the driver that we have.
-   There are multiple methods we can use in the Actions class. But in this section, we just need the moveToElement() method to take the element.
-   In case multiple elements don't have a unique element, we can get all the elements then contain them in a List and then find the element that we want through an index. And the List index starts with 0 so we need to get that in mind or we can deal with that by changing it to start by 1.
-   But there is a catch that all the interactions in the Actions class will not execute just by calling them alone. Example: action.moveToElement().
-   Because Actions class belong to a Builder class, so for it to execute, after every interaction methods need a **perform()** method in the order to work.
-   In the previous section, we already said that we never that to return a WebElements object. In case we have found the element and we want to get it, but under that element also have 2 other elements, and we don't want to return that.
-   There is another approach, are you can create an inner class to deal with those elements.
-   Instead of returning a Web element, we can create an inner class for that method to start with, and from that, it can return the new inner class instead of the web element.
-   This is just one approach. Again, you could do other approaches if you like. For right now, this one seems to make the most sense, especially since this HoversPage doesn't have many actions. The only real thing that you can do on this page is to hover over a figure. This class is really small as it is, so it wouldn't really hurt to add this inner class here and then keep all of this in one place.
-   _if we look at this, this is under a figcaption div, so we could return this entire div. However, this is going to be a WebElement and remember we don't want to return WebElement objects to our test methods._

_-from Chapter 5 of TAU-_