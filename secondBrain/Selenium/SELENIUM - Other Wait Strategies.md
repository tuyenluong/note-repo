---
Creation_date: 2022-05-26 17:06
Modification_date: Thursday 26th May 2022 17:06:36
Indexes:
  - "[[webDriver]]"
---

----


> Before we acquire great power, we must acquire wisdom to use it well.
> — <cite>Ralph Waldo Emerson</cite>

Other Wait Strategies

If we do the driver.Manage.timeouts again, let's see what else is here.

There's also the pageLoadTimeout.

The pageLoadTimeout allows you to set the amount of time to wait for a page load to complete before it throws an error.

This is also something that you can add to your script at the project level to say, "I would like to wait a certain amount of time for my pages to load."

Then there's also this setScriptTimeout.

This will allow you to set the amount of time to wait for asynchronous scripts to finish executing.

Lots of applications are written in JavaScript and there may be some asynchronous actions happening in the background. So, you can set some timeouts using this.