

----
Creation date: 2022-04-30 22:04
Modification date: Saturday 30th April 2022 22:04:03

----

#Selenium 

> One who gains strength by overcoming obstacles possesses the only strength which can overcome adversity.
> — <cite>Albert Schweitzer</cite>

In the Test Automation project, there are typically 2 types of layer: the framework layer and the test layer.

-   2 types of layers are mostly placed in the sources folder.
-   The Framework layer is in the Main folder, all of your interactions with the web or all the code that has been done under your application should be in your Framework.
-   The Test layer is in the Test folder and your Test file should be focused on the test itself.

And everything that has to do with your browsers like how that link be clicked, should be done in the Framework.

So we gonna use a **pattern** called the **Page Object Model** pattern. This is not the only pattern, but it is just the most popular pattern in Test Automation.

The way the **Page Object Model** works is that you create a Class in your Framework section of the project that represents of Page in your test application, and for every page, in your application, you create a new class in the Framework section of your project.

How to implement POM:

-   Create Class inside the main folder, under the java folder.
-   Each page creates a Class for it.
-   And create methods to interact with the elements.
-   It is recommended that you create what you need at that time and then add-on over time.
-   It's custom in the **Page Object Model** design pattern that if your action changes the page then you should return a handle to that new page.
    -   public LoginPage clickFormAuthentication(){ driver.findElement(formAuthenticationLink).click(); return new LoginPage(driver); }
-   It's like when you hanging on the monkey bars, if you let go then you will fall, but if you want to move on then you have to get the handle of the next bars.