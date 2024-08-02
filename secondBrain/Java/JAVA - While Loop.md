---
Creation_date: 2024-03-10 14:56
Modification_date: Sunday 10th March 2024 14:56:59
Indexes:
  - "[[flow_control]]"
---

----

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




---
## Flash cards section

**What is the syntax of a `while` loop in Java?** ;; `while (condition) { // body of the loop }`

**What is an infinite loop?** ;; An infinite loop is a loop that runs forever because its condition always evaluates to true.

**How can you prevent an infinite loop in Java?** ;; You can use a `break` statement or a sentinel condition to exit the loop.

**What is a sentinel condition?** ;; A sentinel condition is a specific value used to terminate a loop when reached.

What will this code do?
```java
int i = 0;
while (i < 10) {
    System.out.println(i);
    i++;
}
```
?
The code will print numbers from 0 to 9, each on a new line.

What will this code do?
```java
int a = 5, b = 7;
while (a > b) {
    System.out.println("Hello");
}
```
?
The code will never execute the `println` statement because `a` is always less than `b`.

What will happen with this code?
```java
int a = 5, b = 7;
while (a < b) {
    System.out.println("Hello");
}
```
?
The code will create an infinite loop because `a` is always less than `b`, and there is no code to change `a` or `b`.

What is the output of this code?
```java
int n = 0;
while (true) {
    System.out.println(n);
    if (n == 9) break;
    n++;
}
```
?
The code will print numbers from 0 to 9, each on a new line, and then terminate.

What will this code do?
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
```
?
The code will print pairs of numbers from 1 to 3 for both `i` and `j` in a nested loop format.

True or False: The following code will print "Hello" infinitely:
```java
while (true) {
    System.out.println("Hello");
}
```
?
True. This loop will print "Hello" indefinitely.

**True or False: The `break` statement in the inner loop of a nested loop breaks out of both the inner and outer loops.** ;; False. The `break` statement only exits the innermost loop unless labelled.

**True or False: You can use a `continue` statement to exit a loop entirely.** ;; False. The `continue` statement only skips the current iteration and proceeds with the next iteration of the loop.
<!--SR:!2024-08-06,4,270-->

**True or False: The `return` statement will terminate only the loop in which it is used.** ;; False. The `return` statement will exit the entire method, not just the loop.

True or False: The following code will compile and run correctly:
```java
int i = 0;
while (true) {
    if (i == 10) break;
    System.out.println(i);
}
```
?
True. The code will print numbers from 0 to 9 and then terminate due to the `break` statement.

What will this code print?
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
}
```
?
The code will print pairs of numbers from `(1, 1)` to `(1, 3)` and then terminate due to the labelled `break`.

What will be the result of this code?
```java
int i = 0;
while (true) {
    i++;
    if (i == 5) break;
}
System.out.println("Done");
```
?
The code will print "Done" after the `break` statement terminates the loop when `i` reaches 5.
