---
Creation_date: 2024-03-26 00:44
Modification_date: Tuesday 26th March 2024 00:44:18
Indexes:
  - "[[array]]"
  - "[[java]]"
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

## `Arrays.binarySearch()` method
- This method only works on sorted arrays
	- If array is not sorted, the result is unpredictable
- Takes array and array element as arguments
	- If element is found, the index of the element is returned
	- If element is not found, the negative number is returned
		- `- (index_where_it_would_belong + 1)`
		- `nth place with '-' in front`
- Array elements are counted from 0

### Examples

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