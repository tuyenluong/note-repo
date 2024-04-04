

----
Creation date: 2022-04-30 22:05
Modification date: Saturday 30th April 2022 22:05:51

----

#Selenium  

> Sometimes it is better to lose and do the right thing than to win and do the wrong thing.
> — <cite>Tony Blair</cite>

So we want a handle for the dropdown elements.

And we need to create a method to select any of the options from the dropdown, not just the first or the second option of the dropdown.

But the Selenium we downloaded doesn't have the class that can solve our problem.

So we need another dependency called Selenium Support. So that we can use a class called Select.

There is a method in the Select Class is getAllSelectedOptions()

-   It will get all the elements in the dropdown for us and put it in a List<\WebElements\>
-   But we don't want it to return the elements, we want it to return a String.
-   Then you have to make 2 assertions
-   1 is to check if there is just 1 value has been selected
-   2 is to check if the selected option is the correct one