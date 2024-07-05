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
