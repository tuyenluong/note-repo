
----
Creation date: 2022-04-30 21:55
Modification date: Saturday 30th April 2022 21:55:32

----

Tags: [[selenium]]

> It is common sense to take a method and try it. If it fails, admit it frankly and try another. But above all, try something.
> — <cite>Franklin D. Roosevelt</cite>

**Set-Up**

The thing is needed for our Automation Test:

-   Java 8 or above
    -   _(It's LTS (Long Time Support) version, but if you use it for production. You need to read the message carefully)_
-   IntelliJ
    -   _(It has 2 options: Community and Enterprise. But in this case, you just need the Community version to practice and it is free as well)_
-   Chrome browser
    -   _(Selenium can support multiple browsers, but in here we just focus on Chrome only)_
-   Chrome driver
    -   _(Chome driver version need to match with the Chrome browser on your machine)_

**Create A New Project**

-   Create a Maven project
-   Project SDK should be the path that your Java 8 JDK just downloaded.
-   Name GroupID and ArtijactID _(Need to be investigated on the convention of the GroupID and ArtijactID)_
-   Choose a path/location for your project. You can type in of location that you want your project to be or you can browse the location.
-   Enable auto-import in Maven
-   The next thing you need to do is open the Maven pom.xml file and add the Java 8 properties into the file, so IntelliJ knows that to compile our code using Java 8.
```java
<properties>
        <maven.compiler.target>8</maven.compiler.target>
        <maven.compiler.source>8</maven.compiler.source> 
</properties>
```
-   The next thing is dependency, the first dependency we need is Selenium Chrome. You can find the dependency on this link: [](https://mvnrepository.com/)[https://mvnrepository.com/](https://mvnrepository.com/)
-   After that, you just copy-paste the Maven code on the Maven tab of the dependency
    - <dependency><groupId>org.seleniumhq.selenium</groupId>
    - <artifactId>selenium-chrome-driver</artifactId>
    - <version>3.141.59</version></dependency>
-   After you paste the Selenium Chrome onto the pom.xml file you need to create a "dependencies" section to contain all dependencies.
-   You just need to put all dependencies in between \<dependencies>\<here>\</dependencies>
-  And you have to make sure that the dependency is imported, is in the "Maven" tab on the middle right of the IntelliJ.
    -   Click on it and open the "Dependency" folder to check.
    -   If it's not there, you can re-import it on the menu tab.
    - And the last thing on the set-up step, you need to create a "resources" directory and move the ChromeDriver executable to the "resources" directory so that your project be able to use it.