---
Creation_date: 2024-03-26 00:44
Modification_date: Tuesday 26th March 2024 00:44:18
Indexes:
  - "[[array]]"
---

----

## Declaring an Array

```java
int[] nums = new int[3];
```

**Key elements in the syntax**
- [] (*read the array elements*)
- naming (*nums*)
- **new** keyword ^2960c3
- size: \[3]

## Initializing an Array

- First declare, then initialize
```java
int[] nums = new int[3];
nums = new int[]{3, -1, 17};
```

- initialization can be done without **new** keyword
```java
int[] nums = {3, -1, 17};
```

- Declaring and initializing at once
```java
int[] nums = new int[]{3, -1, 17};
int[] array = {2, 0, 107};
```

## There are more allowed ways to declare an array
- Allowed space between the data type and square bracket and the name.
```java
int[] nums;
int [] nums;
int []nums;
int nums[];
int nums [];
```

- NOTE: The size of the array can only be on the right-hand side!!
```java
int[3] nums = ... // THIS WILL NOT COMPILE
```

- You can have multiple values in one declaration (*Not recommend, but possible*)
```java
int[] nums1, nums2;
```

- You can even declare int number and int array in the same line
```java
int nums[], a; // The 'nums' is an array, and 'a' is just a integer
```

#### NOTE: arrays don't implement `equals()`method
- Since arrays don't implement `equals()`method, that means that the `equals()`method is the same as the double sign. 
- As we have mentioned in [[JAVA - Garbage Collector|Garbage Collector lesson]], although these two may similar in content but they are 2 different objects in the memory. Because each one is declared with a **new** keyword
- Or in [[JAVA - String pool#^663b55|String Pool lesson]], two equals sign compares references
```run-java
public class Test{
	public static void main(String[] args){
		int[] nums1 = new int[]{3, -1, 17};
		int[] nums2 = new int[]{3, -1, 17};
		System.out.print(nums1.equals(nums2));
		//==>> false
	}
}
```

## Printing out the array

- If you try to print the array directly with the print statement, then you will get a "Hash code" of the reference in return, not the value, and this is not very friendly.
```run-java
public class Test{
	public static void main(String[] args){
		int[] nums1 = new int[]{3, -1, 17};
		System.out.print(nums1);
		//==>> [I@f7f7f9f5 >> this is the Hash code of the reference
	}
}
```

- You need to import the `import java.util.Arrays;`class to be able to use the `toString()` method to make the printing statement works.
```run-java
import java.util.Arrays;
public class Test{
	public static void main(String[] args){
		int[] nums1 = new int[]{3, -1, 17};
		System.out.print(Arrays.toString(nums1));
		//==>> [3, -1, 17]
	}
}
```

- Every array has a property called `length`, note that it's not a method!!
```run-java
public class Test{
	public static void main(String[] args){
		int[] nums1 = new int[]{3, -1, 17};
		System.out.print(nums1.length);
		//==>> 3
	}
}
```


---
## Flash cards section

How do you first declare and then initialize an array in Java?
?
```java
int[] nums = new int[3];
nums = new int[]{3, -1, 17};
```
<!--SR:!2024-08-06,4,270-->

How do you initialize an array without using the **new** keyword?
?
```java
int[] nums = {3, -1, 17};
```

How do you declare and initialize an array at once using the **new** keyword?
?
```java
int[] nums = new int[]{3, -1, 17};
int[] array = {2, 0, 107};
```

List the allowed ways to declare an array in Java.
?
```java
int[] nums;
int [] nums;
int []nums;
int nums[];
int nums [];
```

Where can the size of an array be specified in the declaration? ;; The size of the array can only be on the right-hand side, e.g., `int[] nums = new int[3];`

Why will the following declaration not compile:
?
Because the size of the array cannot be specified on the left-hand side.
```java
int[3] nums = ...
```

How can you declare multiple arrays in one declaration?
?
```java
int[] nums1, nums2;
```

How can you declare an integer and an integer array in the same line?
?
`nums` is an array, and `a` is just an integer
```java
int nums[], a;
```

Do arrays in Java implement the `equals()` method? ;; No, arrays in Java do not implement the `equals()` method, so using `equals()` is the same as using the double equals sign ==

What will the following code print:
```java
public class Test{
    public static void main(String[] args){
        int[] nums1 = new int[]{3, -1, 17};
        int[] nums2 = new int[]{3, -1, 17};
        System.out.print(nums1.equals(nums2));
    }
}
```
?
False
```run-java
public class Test{
    public static void main(String[] args){
        int[] nums1 = new int[]{3, -1, 17};
        int[] nums2 = new int[]{3, -1, 17};
        System.out.print(nums1.equals(nums2));
    }
}
```

What happens if you try to print an array directly with the `print` statement? ;; You will get the "hash code" of the reference, not the value, e.g., `[I@f7f7f9f5`.

How can you print the values of an array instead of the hash code?
?
By importing `java.util.Arrays` and using the `toString()` method, e.g.,
```run-java
import java.util.Arrays;
public class Test{
    public static void main(String[] args){
        int[] nums1 = new int[]{3, -1, 17};
        System.out.print(Arrays.toString(nums1));
    }
}
```

What will the following code print:
```java
import java.util.Arrays;
public class Test{
    public static void main(String[] args){
        int[] nums1 = new int[]{3, -1, 17};
        System.out.print(Arrays.toString(nums1));
    }
}
```
?
`[3, -1, 17]`

What property do all arrays in Java have that gives their size? ;; `length` (note: it's not a method).
<!--SR:!2024-08-06,4,270-->

What will the following code print:
```java
public class Test{
    public static void main(String[] args){
        int[] nums1 = new int[]{3, -1, 17};
        System.out.print(nums1.length);
    }
}
```
?
3








