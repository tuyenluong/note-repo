---
Creation_date: 2022-04-30 22:09
Modification_date: Saturday 30th April 2022 22:09:31
Indexes: "[[selenium]]"
---

----


> All men have a sweetness in their life. That is what helps them go on. It is towards that they turn when they feel too worn out.
> — <cite>Albert Camus</cite>

A frame is an HTML document, which is embedded inside another HTML document.

A-frame embedded inside another HTML document is called a child frame.

We can use the **switchTo()** method in the previous chapter and we will see 3 kinds of "frame":

1.  Switch to a frame by the WebElement
2.  Switch to a frame by index (_int_)
3.  Switch to a frame by ID (_String_)

-   **So** this will switch the context from the paged DOM to this iframe DOM.
-   **But** after we are inside the iframe DOM, we only can interact with the HTML within the iframe DOM.
-   **And** after we are done executing on the iframe HTML, we need to exit that iframe and switch back to the main DOM. So that we do not get stuck at the iframe level.
-   To switch to the parent frame, we can call this method to get back to the main DOM:
-   "driver.**switchTo().parentFrame()**"