

----
Creation date: 2022-04-30 22:15
Modification date: Saturday 30th April 2022 22:15:38

----

#Selenium 

> We may encounter many defeats, but we must not be defeated.
> — <cite>Maya Angelou</cite>

**Event Listeners**

1.  WebDriverEventListener is an interface containing methods that listen for Selenium event
2.  EventFiringWebDriver is a class that allows you to register an implementation of WebDriverEventListener
3.  The method of the WebDriverEventListener is called before or after the action is taken.

Usage:

**For example, what if we want to write reports that capture the actions that were taken on the UI during our test?**

We could do that by implementing the WebDriverEventListener interface.

Let's see how we add this to our project.

In our BaseTests class, we're going to change our driver type from a WebDriver to a specific instance of WebDriver called the EventFiringWebDriver.

Then instead of this being an instance of ChromeDriver, we're going to make it an instance of the EventFiringWebDriver, which takes another instance of WebDriver.

So, we can say it is a ChromeDriver, but we want to wrap this in this EventFiringWebDriver.

This EventFiringWebDriver is the one that will listen out for events.

The way that we tell it to listen for events is we have to actually register a class that is implementing the WebDriverEventListener interface.

So, we say driver.register, and then we provide the instance of the listener class, which we haven't created yet.

**Let's go and create this class — in our project we want to create this listener.**

Let's put this under the framework part, so in the “main” section.

It isn't a page, of course. We can put it in the “utils” package.

So, let's make a new class here and we'll call this class EventReporter.

Now in order for this to be a listener, it has to implement the WebDriverEventListener interface.

Let's go ahead and add that