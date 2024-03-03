

----
Creation date: 2022-04-30 22:07
Modification date: Saturday 30th April 2022 22:07:29

----

#Selenium 
#Done 

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
-   Keys.BACK_SPACE
-   The _"**.chord()**"_ method allows us to send multiple keys, at one time.
-   Example: (_This will equal when you press ALT + p at the same time on your keyboard_)

public void enterPi(){
    enterText(Keys.chord(Keys.ALT, "p"));
}