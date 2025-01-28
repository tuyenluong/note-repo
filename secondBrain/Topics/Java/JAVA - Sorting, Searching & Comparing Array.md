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
^dea931

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




---
## Flash cards section

What does `Arrays.sort(nums)` do if `nums` is an array of integers {3, 17, -1}? ;; Sorts the array `nums` in ascending order, resulting in `[-1, 3, 17]`.

Explain the behaviour of `Arrays.binarySearch(nums, -1)` on a sorted array `nums` {-1, 3, 17}. ;; Returns the index 0, indicating that `-1` is found at the first position in the sorted array `nums`.

What happens if you use `Arrays.binarySearch(nums, 0)` on an array `nums` {-1, 3, 17} that is not sorted? ;; The result is unpredictable due to the requirement that the array must be sorted for `binarySearch()` to work correctly.

What does `Arrays.compare(new int[]{3, 7}, new int[]{3, 7})` return? ;; Returns 0, indicating that the arrays are equal in content.

Explain the result of `Arrays.compare(new int[]{3, 3}, new int[]{7})`. ;; Returns a negative number (-4), indicating that the first array `{3, 3}` is smaller than the second array `{7}`.

Describe the behaviour of `Arrays.mismatch(new String[]{"John", "Wayne"}, new String[]{"John", "Doe"})`. ;; Returns the index 1, indicating the first mismatch between the two arrays `{John, Wayne}` and `{John, Doe}` occurs at index 1 (*Wayne vs. Doe*).

What does `Arrays.mismatch(new int[]{3, 7}, new int[]{3, 7})` return? ;; Returns -1, indicating that the arrays are equal and have no mismatches.

Explain the result of `Arrays.mismatch(new String[]{"John", "Wayne"}, new String[]{"John", "Wayne", "The Duke"})`. ;; Returns 2, indicating the first mismatch between the two arrays `{John, Wayne}` and `{John, Wayne, The Duke}` occurs at index 2 (additional element in the second array).

What does the `Arrays.sort()` method do to an array? ;; It sorts the array in ascending order and modifies the original array.

Given the following code, what will be the output of `Arrays.toString(nums)`?
```java
import java.util.Arrays;

public class Test {
    public static void main(String[] args) {
        int[] nums = new int[]{3, 17, -1};
        Arrays.sort(nums);
        System.out.println(Arrays.toString(nums));
    }
}
```
?
The output will be:
```java
[-1, 3, 17]
```

How does the `Arrays.binarySearch()` method work on a sorted array? ;; It returns the index of the element if found. If the element is not found, it returns `-(index_where_the_element_would_belong + 1)`.

Given the following code, what will be the result of `Arrays.binarySearch(nums, 0)`?
```java
import java.util.Arrays;

public class Test {
    public static void main(String[] args) {
        int[] nums = new int[]{3, 17, -1};
        Arrays.sort(nums); // Sorted: [-1, 3, 17]
        System.out.println(Arrays.binarySearch(nums, 0));
    }
}
```
?
The result will be `-2`, indicating that `0` would be at index `1` if it were present in the array.

What will happen if you use `Arrays.binarySearch()` on an unsorted array? ;; The result is unpredictable and cannot be relied upon.

Given the following code, what will be the output of `Arrays.compare()`?
```java
import java.util.Arrays;

public class Test {
    public static void main(String[] args) {
        System.out.println(Arrays.compare(new int[]{3, 7}, new int[]{3}));
        System.out.println(Arrays.compare(new int[]{3, 7}, new int[]{3, 7}));
        System.out.println(Arrays.compare(new int[]{3, 3}, new int[]{7}));
    }
}
```
?
The output will be:
```java
1
0
-1
```
Explanation:
- The first comparison returns `1` because `[3, 7]` is larger than `[3]` (due to the extra `7`).
- The second comparison returns `0` because both arrays are equal.
- The third comparison returns `-1` because `[3, 3]` is smaller than `[7]` (the first element `3` is smaller than `7`).

How does `Arrays.compare()` determine which array is smaller? ;; It determines size first. If the sizes are equal, it compares elements from the beginning until a difference is found. Null is considered smaller than any value.

Given the following code, what will be the output of `Arrays.compare()` for strings?
```java
import java.util.Arrays;

public class Test {
    public static void main(String[] args) {
        System.out.println(Arrays.compare(new String[]{"ab", "John Wayne"}, new String[]{"abc", "Hey!"}));
        System.out.println(Arrays.compare(new String[]{"xy", "John Wayne"}, new String[]{"abc", "Hey!"}));
        System.out.println(Arrays.compare(new String[]{"John", "Wayne"}, new String[]{"john", "Hey!"}));
        System.out.println(Arrays.compare(new String[]{"3", "7"}, new String[]{"john", "Hey!"}));
        System.out.println(Arrays.compare(new String[]{"ab", "John Wayne"}, null));
    }
}
```
?
The output will be:
```java
-1
-1
-1
-1
1
```
Explanation:
- The first comparison returns `-1` because `"ab"` is smaller than `"abc"`.
- The second comparison returns `-1` because `"xy"` is smaller than `"abc"`.
- The third comparison returns `-1` because `"John"` is smaller than `"john"` (uppercase vs. lowercase).
- The fourth comparison returns `-1` because `"3"` is smaller than `"john"` (numbers vs. letters).
- The fifth comparison returns `1` because the first array is not null, and the second array is null.

What does the `Arrays.mismatch()` method return if the arrays are equal? ;; It returns `-1` if the arrays are equal.

Given the following code, what will be the result of `Arrays.mismatch()`?
```java
import java.util.Arrays;

public class Test {
    public static void main(String[] args) {
        System.out.println(Arrays.mismatch(new String[]{"John", "Wayne"}, new String[]{"John", "Doe"}));
        System.out.println(Arrays.mismatch(new int[]{3, 7}, new int[]{3, 7}));
        System.out.println(Arrays.mismatch(new String[]{"John", "Wayne"}, new String[]{"John", "Wayne", "The Duke"}));
    }
}
```
?
The output will be:
```java
1
-1
2
```
Explanation:
- The first comparison returns `1` because the first mismatch is at index `1` where `"Wayne"` is not equal to `"Doe"`.
- The second comparison returns `-1` because the arrays are equal.
- The third comparison returns `2` because the arrays differ at index `2` (the first array is shorter).