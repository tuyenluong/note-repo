---
Creation_date: 2024-07-12 11:36
Modification_date: Friday 12th July 2024 11:36:12
Indexes:
  - "[[data_structure_algo]]"
  - "[[array]]"
---

----
## Steps for insert algorithm:
1. Create a new array with larger size
2. Insert elements from the old array to the new array
3. Shift the elements to the right until insert index is available for insert
	1. To doing so, we need to start the loop at the end of the array, but since array started with index zero. We need to minus 1 when calling the array length. (`int i = newArr.lenght -1;`)
		1. Otherwise, when we interacted with the new array index, we will result in `ArrayOutOfBoundException`error. 
		2.  Let say that the `newArray` length was 6, but when calling `newArr[i]`, the `i` is 6 when it should be 5 only since the array started with zero.
	2. Condition for loop to stop was, when the index is still larger then `indexK` then it will continue the loop
	3. Inside the loop it will get the previous index of the `newArr` element and assign it to the current index of the loop.
	4. After the assignment is finished, the loop index will decrement by one, and go on.
4. Assign value to the insert index
5. Print out the result.
```run-java
import java.util.Arrays;
public class Test{
	public static void main(String... args){
		int[] arr = {1, 3, 5, 6 ,7};
		int indexK = 2;
		int valueInsert = 123;
		insertInt(indexK, valueInsert, arr);  
	}
	public static void insertInt(int indexK, int value, int[] arr){
		int[] newArr = new int[arr.length+1];
		for(int i = 0; i < arr.length; i++){
		    newArr[i] = arr[i];
		}
		for(int i = newArr.length - 1; i > indexK; i--){
			newArr[i] = newArr[(i-1)];
		}
		newArr[indexK] = value;
		System.out.println(Arrays.toString(newArr));
	}
}
```

## Better algorithm
The algorithm above is still valid, but still able encounter potential issues involve with indexes.
### Potential Issue:
1. **Index Handling**:
    - The loop `for(int i = newArr.length - 1; i > indexK; i--)` correctly shifts elements, but the issue is not ensuring that the `newArr` indices are handled properly when shifting elements.
### Why It May Fail:
- When `indexK = 0`, the logic for copying and shifting the elements works as expected.
- However, if `indexK` were set to a different value, such as `arr.length` or other values, careful handling of indices is required to avoid any unexpected behavior.
### Corrected Version:
The logic of your method is correct for the provided `indexK = 0`, but it can be made more robust for general use. Here's a slight adjustment to ensure clarity and correctness for any index value:

```run-java
import java.util.Arrays;
public class Test {
    public static void main(String... args) {
        int[] arr = {1, 3, 5, 6, 7};
        int indexK = 0;
        int valueInsert = 123;
        insertInt(indexK, valueInsert, arr);
    }

    public static void insertInt(int indexK, int value, int[] arr) {
        int[] newArr = new int[arr.length + 1];

        // Copy elements up to indexK
        for (int i = 0; i < indexK; i++) {
            newArr[i] = arr[i];
        }

        // Insert the new value at indexK
        newArr[indexK] = value;

        // Copy the remaining elements, shifted to the right
        for (int i = indexK; i < arr.length; i++) {
            newArr[i + 1] = arr[i];
        }

        System.out.println(Arrays.toString(newArr));
    }
}
```

### Explanation:

- **Copy Elements Before the Insert Point**: 
	- The first loop copies elements from the original array to the new array up to the insertion index.
```java
for (int i = 0; i < indexK; i++) {
    newArr[i] = arr[i];
}
```
- **Insert the New Value**:
	- The new value is inserted at the specified index.
```java
newArr[indexK] = value;
```
- **Shift Elements to the Right**:
	- The second loop starts at the insertion index and copies the remaining elements, shifted to the right by one position.
```java
for (int i = indexK; i < arr.length; i++) {
    newArr[i + 1] = arr[i];
}
```

This version ensures correct element shifting and value insertion for any `indexK` within the valid range.







---
## Flash cards section
