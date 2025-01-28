---
Creation_date: 2024-03-26 00:45
Modification_date: Tuesday 26th March 2024 00:45:11
Indexes:
  - "[[array]]"
---

----
Multidimensional Arrays is just array within array.
\
- You could use [[JAVA - For Loop|traditional for loop]] to accessing elements

```run-java
public class Test{
	public static void main(String[] args){
		int[][] nums = {{-1, 17}, {3}, {5, 103, 11}, {4, 9, -6, 8}};
		for(int i = 0; i < nums.length; i++){
			for(int j = 0; j < nums[i].length; j++){
				System.out.println("nums(%d, %d) = %d".formatted(i, j, nums[i][j]));
			}
		}
	}
}
```


- You can using [[JAVA - For-Each Loop| for each loop]] as well, but the drawback was it has no control over the indexes.

```run-java
public class Test{
	public static void main(String[] args){
		int[][] nums = {{-1, 17}, {3}, {5, 103, 11}, {4, 9, -6, 8}};
		for(int[] row : nums){
			for(int element : row){
				System.out.println("element = " + element);
			}
		}
	}
}
```



---
## Flash cards section

What is a multidimensional array in Java? ;; A multidimensional array is an array of arrays. It allows you to create arrays with more than one dimension, such as 2D or 3D arrays.

Given this code, what will be the output?
```java
public class Test {
    public static void main(String[] args) {
        int[][] nums = {{-1, 17}, {3}, {5, 103, 11}, {4, 9, -6, 8}};
        for (int i = 0; i < nums.length; i++) {
            for (int j = 0; j < nums[i].length; j++) {
                System.out.println("nums(" + i + ", " + j + ") = " + nums[i][j]);
            }
        }
    }
}
```
?
The output will be:
```java
nums(0, 0) = -1
nums(0, 1) = 17
nums(1, 0) = 3
nums(2, 0) = 5
nums(2, 1) = 103
nums(2, 2) = 11
nums(3, 0) = 4
nums(3, 1) = 9
nums(3, 2) = -6
nums(3, 3) = 8
```

How can you access elements of a 2D array using a traditional for loop? ;; You can access elements of a 2D array using nested traditional for loops. The outer loop iterates over rows, and the inner loop iterates over columns.

Given this code, what is the output?
```java
public class Test {
    public static void main(String[] args) {
        int[][] nums = {{-1, 17}, {3}, {5, 103, 11}, {4, 9, -6, 8}};
        for (int[] row : nums) {
            for (int element : row) {
                System.out.println("element = " + element);
            }
        }
    }
}
```
?
The output will be:
```java
element = -1
element = 17
element = 3
element = 5
element = 103
element = 11
element = 4
element = 9
element = -6
element = 8
```

What is a drawback of using the for-each loop with multidimensional arrays? ;; The drawback of using the for-each loop with multidimensional arrays is that you do not have control over the indices.

Analyse the following code. What will be the output?
```java
public class Test {
    public static void main(String[] args) {
        int[][] nums = {{1, 2, 3}, {4, 5, 6}, {7, 8, 9}};
        for (int i = 0; i < nums.length; i++) {
            for (int j = 0; j < nums[i].length; j++) {
                System.out.print(nums[i][j] + " ");
            }
            System.out.println();
        }
    }
}
```
?
The output will be:
```java
1 2 3 
4 5 6 
7 8 9 
```
The code prints each row of the 2D array on a new line.

What is the difference between accessing elements with a traditional for loop versus a for-each loop in a multidimensional array? ;; A traditional for loop allows access to indices and provides control over the iteration process, while a for-each loop simplifies access to elements but does not provide control over the indices.

Given this code, what will be the output?
```java
public class Test {
    public static void main(String[] args) {
        int[][] nums = {{10, 20}, {30, 40, 50}};
        System.out.println(nums[0][1]);
        System.out.println(nums[1][2]);
    }
}
```
?
The output will be:
```java
20
50
```
This code accesses and prints specific elements from the 2D array `nums`.













