
----
Creation date: 2022-04-30 22:08
Modification date: Saturday 30th April 2022 22:08:51

----

#Selenium 
#Done 

> True friendship is a plant of slow growth, and must undergo and withstand the shocks of adversity, before it is entitled to the appellation.
> — <cite>George Washington</cite>

If a pop-up alert doesn't have a result in the DOM, it is because the alert doesn't attach to the DOM.

Today I know some new method was able to interact with that kind of alert

-   **switchTo():** Send future commands to a different frame or window.
-   **alert():** Switches to the currently active modal dialog for this particular driver instance.
-   **accept() :** Accept that pop-up
-   **dismiss() :** Dismiss that pop-up
-   And in this chapter, we have 3 Test methods is interact with differences Pop up alerts and results. So we need to quit the driver and open a new one after a Test method.
-   So we need to configure the BaseTest, create a new @BeforeMethod call goHome() to get the homepage URL. And in the @BeforeClass **setup()**, we delete the "**driver.get()**" method and use the **goHome()** method. This way we don't need to have called the "**driver.get()**" twice.

**Upload**

To test the Upload file function, we can use the **.sendKeys()** method to pass in the absolute path of the file. So that it can work at any local machine.

**Modals**

A modal window is a pop-up inside the DOM. It can interact with, but when the modal window pop-up. The main page in the background is dimmed. Cause of the, you just only interact with the modal pop-up only when it appear.