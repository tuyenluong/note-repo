---
Creation_date: 2022-04-30 22:16
Modification_date: Saturday 30th April 2022 22:16:15
Indexes:
  - "[[webDriver]]"
---

----


> Our greatest glory is not in never falling, but in rising every time we fall.
> — <cite>Confucius</cite>

Disable infobars "Chrome is being controlled by automated software."

```java
options.setExperimentalOption("excludeSwitches", Collections._singletonList_("enable-automation")); options.setExperimentalOption("useAutomationExtension",false);
```

_// Use this approach from Chrome 76 or above_

And if you run your test on the Selenium Grid or un the cloud, then the ChromeOptions headless mode comes very handily.

**Handling Cookie**

Your browser stores cookies as data. It's basically a reliable way for websites to remember information about the state or record some type of browser activity that the user is doing.

In your automated test, if you're doing something very advanced, you might want to store cookies on the browser. Or you may even want to read cookies from your website to make sure that certain things are there.

This is how we can create a cookie on the website:

```java
private void setCookie(){ 
	Cookie cookie = new Cookie.Builder("TAU","123") 
		.domain("[the-internet.herokuapp.com](http://the-internet.herokuapp.com/)") 
		.build(); 
	driver.manage().addCookie(cookie); 
}
```

But we can have other methods to manage cookies as well:

-   getCookiesNamed() [getCookieNamed]
-   deleteCookiesNamed() [deleteCookieNamed]
-   getCookies() [getCookies]
-   deleteAllCookies() [deleteAllCookies]
-   deleteCookie() [deleteCookie]