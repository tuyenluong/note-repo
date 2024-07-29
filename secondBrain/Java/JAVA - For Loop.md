---
Creation_date: 2024-03-10 14:57
Modification_date: Sunday 10th March 2024 14:57:43
Indexes:
  - "[[flow_control]]"
---

----

## The syntax of the For Loop

```java
for (initialization; condition; update){
	// executes while the condition is true
}
```
#### Order of the execution
1. Execute initialization statement (*only once*)
2. Check the condition
3. If condition is true execute the code, otherwise exit the loop
4. Execute update statement
5. Repeat next iteration
### Compare between two syntax

| While loop                  | For loop                                                                          |
| --------------------------- | --------------------------------------------------------------------------------- |
| Simplest way to make a loop | Initialize, condition, [[JAVA - While Loop#^e2c84a\|sentinel]] all in a same line |
|                             | More convenient, easier to read, compact                                          |


![[Pasted image 20240325234802.png]]


- It's possible to [[ENG - List of keywords or phrases#^bc73e2|omit]] any one of the statements, but you still have to keep your `;`'s in place
```java
for ( ; ; ){ } ==>> This is valid 
```

- You can use more than one index in a for loop, separated by comma 
```java
for (int i = 0, j = 0; (i + j) < 5; i++, j++){
	System.out.println("i=" + i + ", j=" + j);
}
==>> Result:
i=0, j=0
i=1, j=1
i=2, j=2
```

### Everything else works the same as in while loop
- break, continue, nested loops, unreachable code, breaking with return, etc.



---
## Flash cards section

What is the syntax of a for loop in Java?
?
```java
for (initialization; condition; update) {
    // executes while the condition is true
}
```

What is the first step in the execution order of a for loop? ;; Execute the initialization statement (only once).

What is the second step in the execution order of a for loop? ;; Check the condition.

What happens if the condition in a for loop is true? ;; Execute the code inside the loop.

What happens if the condition in a for loop is false? ;; Exit the loop.

What is the fourth step in the execution order of a for loop? ;; Execute the update statement.

How does a for loop compare to a while loop in terms of syntax? ;; A for loop initializes, checks the condition, and updates in the same line, making it more convenient, easier to read, and compact.

Can you omit any statements in a for loop? ;; Yes, you can omit any one of the statements, but you must keep the semicolons in place.

What is the result of this code?
```java
for ( ; ; ) { }
```
?
This creates an infinite loop and is valid.

How can you use multiple indices in a for loop?
?
```java
for (int i = 0, j = 0; (i + j) < 5; i++, j++) {
    System.out.println("i=" + i + ", j=" + j);
}
```

What will the output of this code be?
```java
for (int i = 0, j = 0; (i + j) < 5; i++, j++) {
    System.out.println("i=" + i + ", j=" + j);
}

```
?
Plain text
```java
i=0, j=0
i=1, j=1
i=2, j=2
```

Do break, continue, nested loops, unreachable code, and breaking with return work the same way in for loops as in while loops? ;; Yes, they work the same way in both for loops and while loops.




