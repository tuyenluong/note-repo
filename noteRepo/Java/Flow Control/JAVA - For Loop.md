

----
Creation date: 2024-03-10 14:57
Modification date: Sunday 10th March 2024 14:57:43

----

#Java 
#Done 

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


- It's possible to [[List of keywords#^bc73e2|omit]] any one of the statements, but you still have to keep your `;`'s in place
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