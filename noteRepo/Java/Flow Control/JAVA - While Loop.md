

----
Creation date: 2024-03-10 14:56
Modification date: Sunday 10th March 2024 14:56:59

----

#Java 
## The Syntax of While Loop

```java
while (condition){
	// executes while condition is true
}
```

- First example, print out numbers from 0 to 9
```java
int i = 0;
while (i < 10){
	System.out.println(i);
	i++;
}
```

- It's possible that the body inside the while loop is never executed
```java
int a = 5, b = 7;
while (a > b){  ==>> this condition will never be true because a is smaller then b
	System.out.println("Hello");
	// never executes
}
```

- Infinite loop
```java
int a = 5, b = 7;
while (a <  b){  ==>> this condition will go on forever because a is always 
				==>> smaller than b
	System.out.println("Hello");
	// never executes
}
```

- Simplest infinite loop
```java
while (true){  ==>> this condition will go on forever 
			==>> because the condition is always true
	System.out.println("Hello");
	// never executes
}
```

### To prevent infinite loop, we can use `break` statement or [sentinel condition](https://en.wikipedia.org/wiki/Sentinel_value)

^e2c84a

```java
int n = 0;
while (true){  ==>> It seem that this loop will run forever
	System.out.println(n);
	if (n == 9) break; ==>> but at iteration 9, n will meets his condition
					   ==>>  and break out of the loop
	n++;
}
```

## Nested Loop

```java
int i = 0, j = 0;
while (i < 3) {
	i++;
	j = 0;
	while (j < 3) { 
		j++;
		System.out.print("(" + i + ", " + j + ") ");
	}
}
==>> Result: (1, 1) (1, 2) (1, 3) (2, 1) (2, 2) (2, 3) (3, 1) (3, 2) (3, 3) 
```

### Using `break` in nested loops

- Here we have a case nested infinite loops  
- Instead of using a sentinel condition for termination the loop, we use a `true` condition
- This will lead to infinite loop on both of them, but we will use the `break` statement inside the 2nd loop.

```java
int i = 0, j = 0;
while (true) { ==>> This time we use true instead of sentinel condition
	i++;
	j = 0;
	while (true) { ==>> This time we use true instead of sentinel condition
		j++;
		System.out.print("(" + i + ", " + j + ") ");
		if (j == 3) break;  ==>> Only break the inner loop on this program
	}
}
```
- Although we do used the `break` statement, but it's only `break` out of current loop which is the inner loop.
- Due to it only `break` the inner loop, the outer loop is still an infinite loop.

### Using `break` in nested loops, but with labels

- Label is when you give your loop a name by adding it before the line in which your loop begins. 
- Label can be written like any other Java identifier, but it's a convention to write this in all uppercase.
	- Used SNAKE_CASE naming convention.
- Thank to label, now we can point out which loop does the `break` statement should `break`
```java
int i = 0, j = 0;
OUTER_LOOP: while (true) { 
	i++;
	j = 0;
	INNER_LOOP: while (true) { 
		j++;
		System.out.print("(" + i + ", " + j + ") ");
		if (j == 3) break OUTER_LOOP;  ==>> Thank to label, the `break` statement
		                              ==>> can identify which loop it should break
	}
}
==>> Result: (1, 1) (1, 2) (1, 3)
```

### But be careful about the unreachable code

- [Example about unreachable code.](https://www.baeldung.com/java-unreachable-statements)

```java
int i = 0, j = 0;
OUTER_LOOP: while (true) { 
	i++;
	j = 0;
	INNER_LOOP: while (true) { 
		j++;
		System.out.print("(" + i + ", " + j + ") ");
		if (j == 3) break OUTER_LOOP;
	}
	System.out.print("Hello");  ==>> Due to the `break` statement above
		                       ==>> the command print "Hello" is unreachable
}
==>> Result: DOES NOT COMPILE
```

![[Pasted image 20240319010455.png]]
![[Pasted image 20240319010508.png]]

### Continue statement skips one iteration of the loop

- Task: print all even numbers between 0 and 20
```java
int i = -1;
while (i < 20) {
	i++;
	if (i % 2 == 1) continue;
	System.out.print("Hello " + i);  ==>> This is not reachable if
		                            ==>> the number is odd
}
```

### Return statement breaks the execution of the loop (*exits the method*)

- In this example, the `return` statement is placed inside the inner loop. 
- And you can see, again we using a `while (true)` loop, but it doesn't matter.
- Because the `return` statement will exists the method completely once the return command is called.
- It just exists the method, doesn't matter it's inner loop or outer loop.

```java
public void printPairs(){
	int i = 0, j = 0;
	while (true) { 
		i++;
		while (true) { 
			j++;
			System.out.print("(" + i + ", " + j + ") ");
			if (j == 4)
				return;
		}	
	}
}
```