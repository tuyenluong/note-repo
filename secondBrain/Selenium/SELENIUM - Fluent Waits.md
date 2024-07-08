---
Creation_date: 2022-05-26 17:04
Modification_date: Thursday 26th May 2022 17:04:24
Indexes:
  - "[[webDriver]]"
---

----


> Friendship may, and often does, grow into love, but love never subsides into friendship.
> — <cite>Lord Byron</cite>

There's also the concept of [Fluent Waits](https://seleniumhq.github.io/selenium/docs/api/java/org/openqa/selenium/support/ui/FluentWait.html).

Let's look at this same example with a FluentWait.

We'll create a new instance of FluentWait and this takes a driver.

FluentWait wait = new FluentWait(driver)

As opposed to putting a semicolon, we're going to put a . and now we can specify any of these methods.

You see we have:

-   ignoring
    
-   pollingEveryignoreAll
    
-   withMessage
    

Let's set the timeout first.

We can say .withTimeout, we still want to do the 5 seconds.

-   withTimeout
    
-   We would say Duration. because this takes a Duration object and then we'll say .ofSeconds.
    

And then specify how many seconds. In addition to seconds, there's also nano, milli, minutes, et cetera. So, you can choose the unit that you'd like.

We're going to stick with the same example, so let's say 5 seconds and then we can do another . to keep going.

FluentWait wait = new FluentWait(driver)
     .withTimeout(Duration.ofSeconds(5))

Then we can say, “okay, I want you to poll every maybe 1 second”. So, we can say duration of 1 second.

FluentWait wait = new FluentWait(driver)
    .withTimeout(Duration.ofSeconds(5))
    .pollingEvery(Duration.ofSeconds(1))

And then another . to say “ignore the NoSuchElementException”.

So, let's say that the element was not present in the DOM. If we tried to find it before it was there, then it would throw this NoSuchElementException.

So, to ignore that exception, we say:

FluentWait wait = new FluentWait(driver)
    .withTimeout(Duration.ofSeconds(5))
    .pollingEvery(Duration.ofSeconds(1))
    .ignoring(NoSuchElementException.class);

You can specify any other exceptions that you wanted in there.

Okay, so again, this is equivalent to the creation of the object for the explicit wait.

In order for it to actually do something, we need to do a wait.until and then we'd go ahead and give it that same expected condition.

And now we have a fluent wait.

FluentWait wait = new FluentWait(driver)
    .withTimeout(Duration.ofSeconds(5))
     .pollingEvery(Duration.ofSeconds(1))
     .ignoring(NoSuchElementException.class);

wait.until(ExpectedConditions.invisibilityOf(
        driver.findElement(loadingIndicator)));

So, this gives you a little bit more control. In addition to just setting the timeout, you can also say how often it should check for this and any exceptions to ignore.
