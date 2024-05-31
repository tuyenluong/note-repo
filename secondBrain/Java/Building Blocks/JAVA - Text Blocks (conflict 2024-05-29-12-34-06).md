

----
Creation date: 2024-02-23 00:41
Modification date: Friday 23rd February 2024 00:41:19

----

 Tags: [[java]]

- Introduced as standard feature in Java 15
- It has triple quote
- And be careful when you put the triple quotes in the beginning, it must be followed by the new line.
	- Otherwise it will not compile.
	- This is the starting delimiter and the ending delimiter can be in the new line or in the same line.   
- There is 2 type of [[JAVA - Text Blocks#^4d9e81|white spaces]] 
	- One is Incidental whitespace -->> This will be ignored by the compiler
	- Second is Essential whitespace -->> The compiler looks the first non-empty character and everything before that is just Incidental whitespace and it's ignored. But once the compiler finds the first non-empty character, then these spaces are called essential white.
- ![[Pasted image 20240223004254.png]] ^4d9e81
- Even the quotation marks inside the triple quotes is treated as part of the String. 
	- So you don't have to worry about escape sign anymore.
	- The output will look like [[JAVA - Text Blocks#^588409|THIS]]

![[Pasted image 20240223004301.png]] ^588409

- [[JAVA - Text Blocks#^774077|The old way]]
	- Must remember the escape sign for the quotation marks
	- Must have sequence n for new line
	- Have to handle space manually

![[Pasted image 20240223004354.png]] ^774077

- Another point is that when you try to concatenate with other String like [[JAVA - Text Blocks#^b6468d|THIS]] 
	- So you can see since this ending, Delimiter is in the same line as as the rest of the text, Java doesn't insert this new line.
	- So we wanted that after after the name that you have the new line and then the next print will be in its own line.
	- So to achieve this, you can write the same thing, but just put the delimiter. In the separate line. 
	- Like [[JAVA - Text Blocks#^533f33|THIS]] for the [[JAVA - Text Blocks#^7c5cac|OUTPUT]] And this is want we want.

![[Pasted image 20240223010703.png]] ^b6468d


![[Pasted image 20240223010710.png]] ^bad0b4

![[Pasted image 20240223012141.png]] ^533f33

![[Pasted image 20240223012227.png]] ^7c5cac

### Text Block Methods
Java introduced **text blocks** (also known as **multiline strings**) in Java 13 as a preview feature, and they became a standard feature in Java 15. Text blocks simplify writing multiline string literals in Java. They are particularly useful for working with JSON, HTML, or SQL queries directly embedded in Java code. Text blocks are defined by triple double quotes (`"""`), and any content within the triple quotes is considered part of the string, including newlines and any leading whitespace common to all lines.
#### Key Methods for Text Blocks
Text blocks in Java come with several useful methods that help manage and manipulate the content effectively:
1. [[JAVA - String methods#^3062c7|stripIndent()]]:
    - This method removes incidental white space from the beginning of every line in the string.
    - It is useful for correcting indentation when your string literals need to align with your code's formatting.
2. [[JAVA - String methods#^71eb32|translateEscapes()]]:
    - Processes escape sequences in the text block, such as `\n`, `\t`, and Unicode escapes like `\uXXXX`.
    - This allows for dynamic interpretation of escape sequences that are part of the text block data.
3. **`formatted(Object... args)`**:
    - This method is an instance method equivalent to `String.format()`. It allows you to format the text block using provided arguments, making it easier to embed variables or perform formatting directly within the string.
    - It supports the same format specifiers as `String.format()`.