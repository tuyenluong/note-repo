

----
Creation date: 2024-03-03 12:01
Modification date: Sunday 3rd March 2024 12:01:09

----

#Java  
#Done  

Unary operator requires only one [[JAVA - Operators in Java#^d8d14f|operand]].

| Operator          | Example  |
| ----------------- | -------- |
| Logical component | !b       |
| Bitwise component | ~a       |
| Plus              | +a       |
| Negation (minus)  | -a       |
| Increment         | ++a, a++ |
| Decrement         | --a, a-- |
| Cast              | (int)a   |
## Increment and decrement operators
- Based on the [[JAVA - Operators in Java#^5c4efa|operator associativity]], this is how the Increment and decrement operators works:
```java
++a ==>> increases value by 1 and then return the NEW value
a++ ==>> increases value by 1 and then return the OLD value
--a ==>> increases value by 1 and then return the NEW value
a-- ==>> increases value by 1 and then return the OLD value
```

- Example:
![[Pasted image 20240303141212.png]]

- A tricky example:
![[Pasted image 20240303135756.png]]

Here's what happens step by step:
1. The current value of `a` (which is 5) is stored temporarily.
2. `a` is incremented by 1 due to `a++`. So, `a` becomes 6.
3. The stored value (5) is assigned to `a` because of the assignment operation (`a =`).
4. As a result, after the statement `a = a++;`, `a` will still have the value 5.

- The reason behind this behavior is that the post-increment operator (`a++`) increments the value of `a`, but returns the original value before the increment. So, even though `a` is incremented, the incremented value is not stored in `a` until after the assignment operation is completed. Therefore, the assignment reverts `a` back to its original value before the increment.