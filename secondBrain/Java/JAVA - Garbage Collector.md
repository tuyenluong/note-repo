---
Creation_date: 2024-02-24 16:39
Modification_date: Saturday 24th February 2024 16:39:36
Indexes:
  - "[[java_building_block]]"
---


----

Garbage Collector (*GC*) is a very important and very convenient Java feature called Garbage Collector (*GC*).
## What is Garbage Collection?
- All Java objects are stored in programs memory **heap** (*a.k.a free store*)
- **GC is a process automatically freeing memory on the heap.**
	- By removing objects which are no longer reachable in the program
- These object are said to be eligible for GC.
- Once the object is eligible for GC, Java can remove it from the heap (*and free memory*)
### Garbage Collection process is out of your control !!!
- You cannot know if ad when the memory will be feed.
## System.gc()
- This method you can suggest Java to clean the heap
```java
System.gc();
```
- But it's not guaranteed to do anything !!
- So be careful with this kind of question in the exam.

## Eligibility for Garbage Collection

- Two scenarios which can happen that when a object is eligible for GC once it is no longer reachable by the program:
	- The object has no reference pointing to it
	- All references of the object have gone out of scope
```java
public class GcExample {
	public static void main(String[] args){
		String a, b;
		// Reference a is pointing to object "Emperor"
		a = new String("Emperor");
		// Reference b is pointing to object "King"
		b = new String("King");
		// Two thing happens in this line
		// Reference a now poting to object "King" as well
		// Since refence a point to "King" which means object "Emperor"
		// now is ELIGIBIABLE for garbage collection
		// because the object has no reference pointing to it
		a = b;
		// Reference c point to object "King" also
		String c = a;
		// Now reference a is pointing to null which means nothing
		// So now a is not pointing at "King" anymore
		// Because of that, reference a is ELIGIBIABLE for garbage collection
		a = null;
	}
}
```
### Remember! It's objects (HEAP), not references, which are collected by the G.C !!


---
## Flash cards section

What does the following code illustrate about Garbage Collection?
```java
public class GcExample {
    public static void main(String[] args) {
        String a = new String("Hello");
        String b = new String("World");
        a = b;
        b = null;
    }
}
```
?
The object `"Hello"` is eligible for garbage collection because there are no references pointing to it after the assignment `a = b`. The object `"World"` is also eligible for garbage collection after `b = null` because the only reference to it was removed.

How does this code affect Garbage Collection?
```java
public class GcExample {
    public static void main(String[] args) {
        String a = "Java";
        String b = "Java";
        a = null;
    }
}
```
?
The string `"Java"` might not be eligible for garbage collection because it is a string literal, which is usually interned and managed by the Java String Pool. Thus, it is still referenced and not removed.

What happens to objects in memory in this code example?
```java
public class GcExample {
    public static void main(String[] args) {
        String a = new String("Test");
        String b = a;
        a = null;
    }
}
```
?
The object `"Test"` is not eligible for garbage collection because `b` still references it. The reference `a` being set to `null` does not affect the object's eligibility for garbage collection since `b` still holds a reference to it.

Analyse the following code snippet and determine the Garbage Collection outcome:
```java
public class GcExample {
    public static void main(String[] args) {
        String a = new String("Sample");
        String b = new String("Example");
        a = b;
        b = new String("New");
    }
}
```
?
The original object `"Sample"` is eligible for garbage collection because the reference `a` is now pointing to a new object `"Example"`, and the reference `b` now points to yet another new object `"New"`. The object `"Sample"` no longer has any references.

What will be the result of Garbage Collection in this code?
```java
public class GcExample {
    public static void main(String[] args) {
        String a = new String("Old");
        String b = new String("New");
        b = a;
        a = null;
    }
}
```
?
The object `"New"` is eligible for garbage collection because the reference `b` is reassigned to `a`, which holds a reference to the object `"Old"`. The object `"New"` no longer has any references.

Given this code, which objects are eligible for Garbage Collection?
```java
public class GcExample {
    public static void main(String[] args) {
        String a = "Alpha";
        String b = "Beta";
        a = b;
        b = null;
    }
}
```
?
The string literal `"Alpha"` might not be eligible for garbage collection because it's a string literal in the String Pool. However, the object `"Beta"` is not eligible for garbage collection because it is still referenced by `a`.

What does this code demonstrate about Garbage Collection?
```java
public class GcExample {
    public static void main(String[] args) {
        String a = "Java";
        String b = "Java";
        String c = new String("Java");
        a = null;
        c = null;
    }
}
```
?
The string literal `"Java"` in the String Pool is not eligible for garbage collection because string literals are typically interned and managed by the pool. The object referenced by `c`, which is a new `String` instance, is eligible for garbage collection since `c` is set to `null`.

