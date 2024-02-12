
----
Creation date: 2024-02-07 17:35
Modification date: Wednesday 7th February 2024 17:35:56

----
#Java 
#Done 

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
