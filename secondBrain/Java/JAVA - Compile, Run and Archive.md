---
Creation_date: 2024-02-08 15:56
Modification_date: Thursday 8th February 2024 15:56:53
Indexes:
  - "[[java_building_block]]"
---


----


> Ceasing to do evil, Cultivating the good, Purifying the heart: This is the teaching of the Buddhas.
> — <cite>The Buddha</cite>
> 
- Compile
	- Compiling code with packages
		- Declaring class path for Java class on different OS: 
			- First class:
				- C:\\com\\udemy\\ocppackage\Ocp.java (*Windows*)
				- \/com\/udemy\/ocppackage\/Ocp.java (*Unix*)
			- Second class: 
				- C:\\com\\udemy\\ocapackage\Oca.java (*Windows*)
				- \/com\/udemy\/ocapackage\/Oca.java (*Unix*)
			- Take the common-ground position:
				- cd C:\\com\\udemy\\ (*Windows*)
				- cd  \/com\/udemy (*Unix*)
	- [[JAVA - main() method#^33c6b8|Compiling note for prior Java 11]]
		- javac ocppackage/Ocp.java ocapackage/Oca.java
			- output: .class files
	- Alternatively, you can compile multiple Java files in one package at once using wild cards sign (*\**)
		- javac ocppackage/\*.java ocapackage/\*.java
- Run
	- Run Ocp application
		- java ocppackage.Ocp
	- What if we want classes in another directory?
		- java -d classes ocppackage/Ocp.java ocapackage/Oca.java
			- The -d \<directory\> is specify a directory to interact with if required
	- Three ways to run Ocp application:
		- java -cp classes ecpackage.Ocp
		- java -classpath classes ecpackage.Ocp
		- java --class-path classes ecpackage.Ocp
			- \<classpath\>  option can be used with javac command to specify location of classes needed to compile the program.
	- And If we have a application that depends on other files to run, like some of the files are in package "deps", and some are in myJar.jar then we will have a syntax like this.
		- java -cp ".;C:\comudemy\deps;C:\comudemy\myJar.jar" myPackage.myApp
		- The dot is including the current folder, next is the "deps" package that will be separated by a semi colon. And the last one is a jar file.
		- You also can use the wildcards sign for many jar files as well.
- Archive
	-  Create your own jar file
		- [Documentation](https://docs.oracle.com/javase/tutorial/deployment/jar/view.html).
		- jar -cvf \<yourNewJarFileName\>.jar . 
		- jar -cvf stand for --create --verbose --file 
		- The dot at the and is your current directory or you can specify the custom folder to be archive
		- jar -cvf \<yourNewJarFileName\>.jar  \<yourCustomFolderToBeArchive\> 



---
## Flash cards section

What command to creates a jar file of desired project with the Java command?;; jar -cvf \<yourNewJarFileName\>.jar .
<!--SR:!2024-06-06,2,190-->

What is the option -cvf stands for in the jar command?;; -cvf stand for --create --verbose --file
<!--SR:!2024-06-07,3,212-->

How can you choose which folder to be archive with the jar command?
?
By identifying the custom folder to be archive after you defined your jar file name
jar -cvf \<yourNewJarFileName\>.jar  \<yourCustomFolderToBeArchive\>
<!--SR:!2024-06-06,2,192--> 
