---
Creation_date: 2024-03-26 00:44
Modification_date: Tuesday 26th March 2024 00:44:18
Indexes:
  - "[[array]]"
---

----
## `Arrays.sort()` method
- Creating a new array
- Arrays are [[JAVA - What is mutable and immutable means|mutable]], `sort()` changes the original array! 
```java
int[] nums = new int[]{3, -1, 17}
Arrays.sort(nums);
System.out.println(Arrays.toString(nums));
==>> [-1, 3, 17]
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
```java
int[] nums = new int[]{3, -1, 17}
Arrays.sort(nums); // [-1, 3, 17]
System.out.println(Arrays.binarySearch(nums, -1));
==>> 0
System.out.println(Arrays.binarySearch(nums, 17));
==>> 2
System.out.println(Arrays.binarySearch(nums, 0));
==>> -2
```

- Unsorted array
```java
int[] nums = new int[]{3, -1, 17}
System.out.println(Arrays.binarySearch(nums, -1));
==>> unpredictable result
```

## `Arrays.compare(fistArr, secondArr)` method

- Determines which array is `smaller` and returns:
	- Negative number if `first` is smaller then the `second`
	- Zero if the arrays are equal in content
	- Positive number if `first` is larger then the `second`

### What is consider `smaller`?

- If one array has less number of elements, it's `smaller`
- If both arrays have the same number of elements
	- The `smaller` array is the one whose first different member is `smaller`
- Null is `smaller` than any other values
- For Strings:
	- One is `smaller` if it's a prefix of another
	- Numbers are `smaller` than letters
	- Uppercase is `smaller` than lowercase
	- Alphabetical order is applied
https://onecompiler.com/java/42ha4j96y