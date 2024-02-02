

----
Creation date: 2022-04-30 22:04
Modification date: Saturday 30th April 2022 22:04:55

----


#Selenium 
#Done 

> He who experiences the unity of life sees his own Self in all beings, and all beings in his own Self, and looks on everything with an impartial eye.
> — <cite>Buddha</cite>

Write the Test

-   Create a package test the function
-   Class name end with the "Tests" word
-   The test class extends from the "BaseTest" so every test doesn't have to do the set-up part again and again.
-   Selenium WebDriver is not a verification tool it's only used to automate the action on the browsers.
-   So we need a verification tool to do that
-   Go to [](https://mvnrepository.com/)[https://mvnrepository.com/](https://mvnrepository.com/)
-   Download the TestNG dependency
-   And add the dependency to the pom.xml file
-   We gonna use:
-   assertEquals("actual", "expected", "error message");
-   assertTrue(getText.contains("actual","message");
-   (_import static org.testng.Assert._;)* this line of the code will import any other method of the Assert class
-   Now we can remove the main method and we gonna use these annotations:
-   @Test
-   @AfterClass
-   @BeforeClass
-   Check TestNG section Chapter 3