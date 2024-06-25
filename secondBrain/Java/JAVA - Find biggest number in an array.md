---
Creation_date: 2024-06-25 20:53
Modification_date: Tuesday 25th June 2024 20:53:10
Indexes:
  - "[[data_and_algo]]"
  - "[[array]]"
---

----

```run-java
public static void main(String[] args){
	int[] arr = new int[]{1,2,3,4,5,6,7};
	int biggest = Integer.MIN_VALUE;
	for(int i = 0; i < arr.length; i++){
		if(arr[i] > biggest){
			biggest = arr[i];
		}
	}
	System.out.println(biggest);
}
```


















---
## Flash cards section
