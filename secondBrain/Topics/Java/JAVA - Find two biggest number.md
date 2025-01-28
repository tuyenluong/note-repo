---
Creation_date: 2024-07-09 14:57
Modification_date: Tuesday 9th July 2024 14:57:03
Indexes:
  - "[[data_structure_algo]]"
  - "[[array]]"
---


----


```run-java
public class Test{
	public static void main(String... args){
		int[] arr = {14,15,346,64,756};
		twoLargest(arr);
	}
	public static void twoLargest(int values[]){

	int largestA = values[0];
	int largestB = -1;

		for(int i = 0; i < values.length; i++){
			if(values[i] > largestA){
				largestB = largestA;
				largestA = values[i];
			}
			else if (values[i] > largestB && values[i] != largestA) {
				largestB = values[i];
			}
		}
	System.out.println("Largest - " + largestA);
	System.out.println("2nd largest Largest - " + largestB);
	}
}

```

















---
## Flash cards section
