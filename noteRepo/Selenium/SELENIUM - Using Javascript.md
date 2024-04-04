

----
Creation date: 2022-04-30 22:12
Modification date: Saturday 30th April 2022 22:12:13

----


#Selenium 

> Never apologize for showing feeling. When you do so, you apologize for truth.
> — <cite>Benjamin Disraeli</cite>

**Scroll down**

To scroll down, we can write a method using Javascript in able to "scroll" on the web.

We can use "JavascriptExecutor" in the Selenium package like this:

-   ((JavasciptExecutor)driver).executeScript("JS-code-within-of-String",)

**Infinity Scroll**

Sometimes there are situations that the web element does not appear on the web right away. For example, when a user scrolls to a certain paragraph. The website will automatically add a number of paragraphs.

We can use a script that helps us scroll to the elements that we want.

-   We need the script inside a variable:
-   **String script = "window.scrollTo('horizontal','vertically')"**

The whole method will be:

-   **public void scrollToParagragh(int index){**
-   **String script = "window.scrollTo('horizontal','vertically')";**
-   **var jsExecutor = (JavascriptExecutor)driver;**
-   **while(getNumberOfParagraghPresent() < index){**
-   **jsExecutor.executeSxript(script);}}**
-   **private int getNumberOfParagraghPresent(){ return driver.finElements(textBlocks).size();}**