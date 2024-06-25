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