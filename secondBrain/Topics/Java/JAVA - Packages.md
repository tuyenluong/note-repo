---
Creation_date: 2024-02-07 17:35
Modification_date: Wednesday 7th February 2024 17:35:56
Indexes:
  - "[[java_building_block]]"
---

----

> People are so constituted that everybody would rather undertake what they see others do, whether they have an aptitude for it or not.
> — <cite>Johann Wolfgang von Goethe</cite>

- Java classes are stored in different *packages*.
- You can think of them as folders in which classes are stored.
- In order to use a class, you must *import* a package in your program.
- Name of the package usually look something like:
	- com.udemy.javacourse.ocp
	- this mean that there is a folder "com", in which there is a subfolder "udemy", with subfolder "javacourse", with subfolder "ocp" containing classes.
	- exem creators like to use more generic names like a.b.c

Example:
```java
import java.unti.*;

public class NumberGenerator {
	public static void main(String[] args){
		Random randomNumber = new Random();
		System.out.println(randomNumber.nextint(100));
	}
}
```

- Another option without using import is to use a fully qualified name of the class: ^49fc75
	- But this is not practical.
```java
java.util.Radom randomNumber = new java.util.Random();
```

- Using wildcards *
```java
import java.util.Random  -->> imports class Random
import java.util.*       -->> imports all classes in java.util package
                        -->> but not in subpackges (subfolders) !!
import java.util.*.*     -->> DOES NOT COMPILE
```

- Be aware of conflicts
```java
import java.util.Date; -->> import the same class name will result in conflicts
import java.sql.Date; -->> DOES NOT COMPILE
```

- Solution if you what to use 2 classes that have the same name at 2 different packages:
	- The Java class now will automatically use java.util.Date because it's imported explicitly.
	- And if you need to use java.sql.Date, then you will have to use [[JAVA - Packages#^49fc75|fully qualified]] name like we
```java
import java.util.Date; -->> One using explicit class name
import java.sql.*; -->> One using a wildcard sign *
```

- Using custom packages
	- Custom packages is the current package of the class 
```java
package com.udemy.oca -->> corresponds to a folder (must be in the first line!)
public class Oca { }

package com.udemy.ocp -->> another folder

import com.udemy.oca; -->> if you want to use Oca class then you have to import it
public class Ocp {
	OCa myOcaInstance = new Oca();
}
```




---
## Flash cards section

What is a package in Java, and why is it used? ;; A package in Java is a namespace that organizes classes into folders. It helps in managing the code, avoiding name conflicts, and controlling access.

What is the purpose of the `import` statement in Java? ;; The `import` statement is used to bring other classes or entire packages into the current file so that you can use them without specifying their fully qualified names.

Given the following code, what will be the output if you use `import java.util.*`?
```java
import java.util.*;

public class NumberGenerator {
    public static void main(String[] args){
        Random randomNumber = new Random();
        System.out.println(randomNumber.nextInt(100));
    }
}
```
?
The code will compile and run successfully, printing a random number between 0 and 99. The wildcard import `java.util.*` includes all classes in the `java.util` package, which allows the use of `Random`.

What happens if you use `import java.util.*.*` in your Java code? ;; The code will not compile. Java does not support importing sub-packages or classes within sub-packages using wildcards.

If you have `import java.util.Date;` and `import java.sql.Date;` in the same file, what will happen? ;; The code will not compile due to a naming conflict. Java does not allow two classes with the same name to be imported from different packages in the same file.

How can you resolve conflicts when using classes with the same name from different packages?
?
Use fully qualified names for one of the conflicting classes. For example:
```java
import java.util.Date; // imports java.util.Date
import java.sql.*;     // imports all classes from java.sql package

public class Test {
    java.sql.Date sqlDate = new java.sql.Date(System.currentTimeMillis());
    java.util.Date utilDate = new java.util.Date();
}
```

What is the correct way to import a specific class from a package?
?
Use the `import` statement followed by the fully qualified class name. For example:
```java
import java.util.Random;
```

How do you use a class from a custom package?
?
You need to import the class using its fully qualified name or use a fully qualified name when creating an instance. For example:
```java
import com.udemy.oca.Oca;

public class Ocp {
    Oca myOcaInstance = new Oca();
}
```

If you create a class in a custom package, how should you declare the package in the source file?
?
The package declaration should be the first line in the source file. For example:
```java
package com.udemy.oca;

public class Oca { }
```
<!--SR:!2024-08-05,3,250-->

What will be the result of this code if you try to compile it?
```java
package com.udemy.oca;

import com.udemy.ocp.Ocp;

public class Test {
    Oca myOcaInstance = new Oca();
    Ocp myOcpInstance = new Ocp();
}
```
?
The code will compile if the `com.udemy.ocp.Ocp` and `com.udemy.oca.Oca` classes exist and are accessible. The `import` statement is used to bring the `Ocp` class from the `com.udemy.ocp` package into the current file.

