---
Creation_date: 2022-04-30 22:07
Modification_date: Saturday 30th April 2022 22:07:29
Indexes:
  - "[[webDriver]]"
---

----

> Our kindness may be the most persuasive argument for that which we believe.
> — <cite>Gordon Hinckley</cite>

"**Keys**" Class

-   "Keys" class contains some method (_button)_ perform some keys like
-   Arrow down, left, right, and up
-   Alt key
-   Cancel and clear, command, control, decimal, delete… There are so many different keys here
-   Enter key
-   There are all of these function keys. So F1 through 12
-   There's help, home, insert...
-   Keys usage:
-   `Keys.BACK_SPACE`
-   The `.chord()` method allows us to send multiple keys, at one time.
-   Example: (_This will equal when you press ALT + p at the same time on your keyboard_)

```java
public void enterPi(){
    enterText(Keys.chord(Keys.ALT, "p"));
}
```






---
## Flash cards section

What Selenium Keys class method is used for performing keyboard actions like pressing the arrow or function keys? ;; Keys class
<!--SR:!2024-05-08,1,230-->
How do you simulate pressing multiple keys at once in Selenium, such as ALT and P? ;; Keys.chord()
<!--SR:!2024-07-11,1,210-->
What does `Keys.chord(Keys.ALT, "p")` in Selenium do when executed? ;; Simulates pressing ALT and 'p' simultaneously
<!--SR:!2024-05-08,1,230-->
Which Selenium Keys class constant is used to represent the backspace key? ;; Keys.BACK_SPACE
<!--SR:!2024-05-08,1,230-->
List some special keys supported by the Selenium Keys class. ;; Alt, Cancel, Clear, Command, Control, Decimal, Delete, Enter, Help, Home, Insert
<!--SR:!2024-05-08,1,230-->
What range of function keys can be simulated using the Selenium Keys class? ;; F1 through F12
<!--SR:!2024-05-08,1,230-->