---
Creation_date: 2024-03-03 12:01
Modification_date: Sunday 3rd March 2024 12:01:09
Indexes:
  - "[[operator]]"
---


----

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

- The reason behind this behaviour is that the post-increment operator (`a++`) increments the value of `a`, but returns the original value before the increment. So, even though `a` is incremented, the incremented value is not stored in `a` until after the assignment operation is completed. Therefore, the assignment reverts `a` back to its original value before the increment.



---
## Flash cards section

**What is the result of the expression `-a` when `a` is 5?** ;; The result is `-5`.

**What does the operator `++a` do?** ;; It increments the value of `a` by 1 and then returns the new value.

**What does the operator `a++` do?** ;; It increments the value of `a` by 1 but returns the old value before the increment.

**What is the effect of the `--a` operator?** ;; It decrements the value of `a` by 1 and then returns the new value.

**What happens when you use the `a--` operator in an expression?** ;; The value of `a` is decremented by 1, but the expression returns the old value before the decrement.

**Given `int a = 5; a = a++;`, what is the value of `a` after execution?** ;; The value of `a` will be `5`. The post-increment operation `a++` increments `a` to `6`, but the assignment `a =` uses the old value `5`.

What will be the output of the following code?
```java
int a = 10;
System.out.println(++a);
```
?
The output will be `11`. The `++a` operator increments `a` by 1 before printing.

What will be the output of the following code?
```java
int a = 10;
System.out.println(a++);
```
?
The output will be `10`. The `a++` operator prints the old value before incrementing `a` to `11`.

**What is the result of the expression `--a + a++` where `a` is initially 7?** ;; The result is `13`. The `--a` operation decrements `a` to `6` and returns `6`. The `a++` operation returns the old value `6`, then increments `a` to `7`. So, `6 + 7 = 13`.

**In the following code snippet, what will the final value of `x` be?**
```java
int x = 5;
x = x-- + --x;
```
?
The final value of `x` will be `9`. The expression `x--` uses the old value `5`, and `--x` decrements `x` to `4`, so `5 + 4 = 9`. The final value of `x` will be `9`.

**True or False: The expression `a = ++a` will always result in `a` being incremented by 1.** ;; False. The expression is not valid because `++a` increments `a` and returns the new value, so `a` cannot be assigned the same new value.

**True or False: The `a++` operator will affect the original value of `a` before returning it.** ;; False. The `a++` operator returns the original value of `a` before incrementing it.

**True or False: The `--a` operator will increment the value of `a`.** ;; False. The `--a` operator will decrement the value of `a`.

**True or False: If `a = 5;` and you use `a = a++`, `a` will be incremented to `6`.** ;; False. The value of `a` will remain `5` because the assignment `a =` uses the old value before incrementing.

**True or False: The `a++` operator returns the incremented value of `a` immediately.** ;; False. The `a++` operator returns the value of `a` before it is incremented.