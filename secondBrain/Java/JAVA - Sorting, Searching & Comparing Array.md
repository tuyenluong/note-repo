---
Creation_date: 2024-03-26 00:44
Modification_date: Tuesday 26th March 2024 00:44:40
Indexes:
  - "[[array]]"
---

----

## `Arrays.sort()` method
- Sort the array in alphabetical order
- Arrays are [[JAVA - What is mutable and immutable means|mutable]], `sort()` changes the original array! 
```run-java
import java.util.Arrays;
public class Test{
	public static void main(String[] args){
		int[] nums = new int[]{3, 17, -1};
		Arrays.sort(nums);
		System.out.println(Arrays.toString(nums));
		//==>> [-1, 3, 17]
	}
}
```

## `Arrays.binarySearch(arr[], elementOfTheArr)` method
- This method only works on sorted arrays
	- If array is not sorted, the result is unpredictable
- Takes array and array element as arguments
	- If element is found, the index of the element is returned
	- If element is not found, the negative number is returned
		- `-(index_where_the_element_would_belong + 1)`
		- `nth place with '-' in front`
- Array elements are counted from 0
### Examples

- Sorted array
```run-java
import java.util.Arrays;
public class Test{
	public static void main(String[] args){
		int[] nums = new int[]{3, 17, -1};
		Arrays.sort(nums); // [-1, 3, 17]
		System.out.println(Arrays.binarySearch(nums, -1));
		//==>> 0
		System.out.println(Arrays.binarySearch(nums, 17));
		//==>> 2
		System.out.println(Arrays.binarySearch(nums, 0));
		//==>> -2
	}
}
```

- Unsorted array
```run-java
import java.util.Arrays;
public class Test{
	public static void main(String[] args){
		int[] nums = new int[]{3, 17, -1};
		System.out.println(Arrays.binarySearch(nums, -1));
		//==>> unpredictable result
	}
}
```

## `Arrays.compare(fistArr, secondArr)` method

- How to determines which array is `smaller` and returns?
	- Negative number if `first` is smaller then the `second`
	- Zero if the arrays are equal in content
	- Positive number if `first` is larger then the `second`
```run-java
import java.util.Arrays;
public class Test{
	public static void main(String[] args){
		System.out.println("Return positive number: " + Arrays.compare(new int[]{3, 7}, new int[]{3}) );
		System.out.println("Return number zero: " + Arrays.compare(new int[]{3, 7}, new int[]{3, 7}));
		System.out.println("Return negative number: "+Arrays.compare(new int[]{3, 3}, new int[]{7}));
	}
}
```
### What is consider `smaller`?

- If one array has less number of elements, it's `smaller`
- If both arrays have the same number of elements
	- The `smaller` array is determent by the first different member of the arrays.
- Null is `smaller` than any other values
- For Strings:
	- One is `smaller` if it's a prefix of another
	- Numbers are `smaller` than letters
	- Uppercase is `smaller` than lowercase
	- Alphabetical order is applied

```run-java
import java.util.Arrays;
public class Test{
	public static void main(String[] args){
		System.out.println("1. " + Arrays.compare(new int[]{3, 7}, new int[]{3}) );
		System.out.println("2. " + Arrays.compare(new int[]{3, 7}, new int[]{3, 7}));
		System.out.println("3. " + Arrays.compare(new String[]{"ab", "John Wayne"}, new String[]{"abc", "Hey!"}));
		System.out.println("4. " + Arrays.compare(new String[]{"xy", "John Wayne"}, new String[]{"abc", "Hey!"}));
		System.out.println("5. " + Arrays.compare(new String[]{"John", "Wayne"}, new String[]{"john", "Hey!"}));
		System.out.println("6. " + Arrays.compare(new String[]{"3", "7"}, new String[]{"john", "Hey!"}));
		System.out.println("7. " + Arrays.compare(new String[]{"ab", "John Wayne"}, null));
	}
}
```

## `Arrays.mismatch(fistArr, secondArr)`method

- The method will return `-1` if the arrays are equal, otherwise it will return the first index where they differ.

```run-java
import java.util.Arrays;
public class Test{
	public static void main(String[] args){
		System.out.println("1. " + Arrays.mismatch(new String[]{"John", "Wayne"}, new String[]{"John", "Doe"}) );
		System.out.println("2. " + Arrays.mismatch(new int[]{3, 7}, new int[]{3, 7}));

	String[] arr1 = new String[]{"John", "Wayne"};
	String[] arr2 = new String[]{"John", "Wayne", "The Duke"};
	System.out.println("3. " + Arrays.mismatch(arr1, arr2));
	}
}
```



