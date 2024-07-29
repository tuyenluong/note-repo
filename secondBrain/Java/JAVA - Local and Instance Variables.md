---
Creation_date: 2024-07-08 20:20
Modification_date: Monday 8th July 2024 20:20:13
Indexes:
  - "[[methods]]"
---

----
## Local Variables

- Defined inside the block of code `{ }`, go out of scope
- Can have only one optional modifier: `final` for Local variable
	- Once final variable is assigned a value, it cannot be changed
- *"effectively final"*: doesn't change value in the scope
	- variable is *"effectively final"* if you you can put final in variable declaration and the code will still compile
- All local variables must be explicitly initialized before used.


## Instance Variables

- Defined on class level, belong to instance of the class
- Can have different access modifiers: `private`, `protected`, `public`
- Can be marked as `final`, `volatile`, `transient`
- If not initialized, they are assume default values depending on type

### `final` means that *reference* is constant, content of the *reference* can be modified

```run-java
import java.util.Arrays;
public class Test{
	public static void main(String[] args){
		final int[] a = {1, 3, 5};
		a[1] = 7; 
		System.out.println(Arrays.toString(a));
	}
}
```











---
## Flash cards section

Local variable is only able to defined one optional modifier only. It's true? ;; Yes, it's true
<!--SR:!2024-07-24,10,270-->

Once final local variable is assigned a value, it can be changed. It's true? ;; No , it's false
<!--SR:!2024-07-15,1,210-->

All local variables must be explicitly initialized before used. It's true? ;; Yes, it's true
<!--SR:!2024-07-30,16,290-->

All instance variables must be explicitly initialized before used. It's true? ;; No , it's false
<!--SR:!2024-07-24,10,272-->

Will I able to change the value of the a array below?
```java
public void printSomething(){
	final int[] a = {1, 3, 5};
	a[1] = 7; 
	System.out.prinln(Arrays.toString(a));
}
```
?
Yes, `final` means that *reference* is constant, content of the *reference* can be modified
Result: \[1, 7, 4]
```run-java
import java.util.Arrays;
public class Test{
	public static void main(String[] args){
		final int[] a = {1, 3, 5};
		a[1] = 7; 
		System.out.println(Arrays.toString(a));
	}
}
```
<!--SR:!2024-07-12,4,270-->