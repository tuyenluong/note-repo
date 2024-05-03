---
Creation_date: 2022-05-26 17:02
Modification_date: Thursday 26th May 2022 17:02:53
Indexes: "[[selenium]]"
---

----


> If you want to go east, don't go west.
> — <cite>Ramakrishna</cite>

There is another approach that allows us to do Explicit Waits

When we use explicit waits, we use them only we need to.

So, if we know of examples where our application needs to wait, we can plug them in right there.

WebDriver has a class that's called [WebDriverWait](https://seleniumhq.github.io/selenium/docs/api/java/org/openqa/selenium/support/ui/WebDriverWait), and this is in the support UI package.

The WebDriverWait constructor takes two arguments — the driver and also timeout in seconds.

Let's say maybe 5 seconds.

WebDriverWait wait = new WebDriverWait(driver, 5);

The timeout in seconds will also do polling just like the implicit wait.

However, the implicit wait was for the entire app, where as this is only for this specific method. So, we're saying poll the application up until 5 seconds.

Now this statement in and of itself won't do anything — it's just a setup statement to create this wait object.

We then have to say wait.until and then we give it some expected condition.

There's this [ExpectedConditions](https://seleniumhq.github.io/selenium/docs/api/dotnet/html/T_OpenQA_Selenium_Support_UI_ExpectedConditions.htm) class that's also in support.ui package.

The ExpectedConditions class contains all sorts of methods that allow you to wait for some condition to be met before proceeding.

This class is really wonderful and provides lots and lots of different conditions to choose from.