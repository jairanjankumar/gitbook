# Garbage Collection

There are many garbage collection algorithms which run in the background.

1\) Mark and Sweep Algorithm

```
Mark and Sweep Algorithm in two phases:
1) Mark phase - Traces Reachable Object
    Every object has extra bit - the mark bit 
    When an object is created, its mark bit is set to 0. 
    In the Mark phase, we set the marked bit for all the reachable objects to 1.
2) Sweep phase - Collect the Garbage Objects
    it clears the heap memory for all the unreachable objects.
```

Advantages:

```
It handles the case with cyclic references, 
even in case of a cycle, this algorithm never ends up in an infinite loop.
There are no additional overheads incurred during the execution of the algorithm.
```

Disadvantages :

```
Normal program execution is suspended while the garbage collection algorithm runs.
After the Mark and Sweep Algorithm is run several times on a program, reachable 
objects end up being separated by many, small unused memory regions. 
Mark and Sweep Algorithm Fragment the memory
```

2\) Stop And Copy Algorithm

```
Stop and copy is another technique for GarbageCollection that also removes any 
fragmentation.
It works by splitting the available memory in half. One half is designated as 
the current half (where all allocations take place) and the other half is designated 
as the idle half (nothing happens to it).

Because this technique eliminates fragmentation, there is no free list to maintain 
or search. So, when memory must be allocated, it can simply be taken from the free 
space immediately after the last object allocated in the current half of the heap.

When the end of the current half of the heap is reached, a garbage collection must 
be performed. As with MarkAndSweep garbage collection, the collector traverses the 
heap by starting at the root pointers (conventionally, stored in the stack and registers).

When the copy is complete (all reachable nodes have been copied into the idle heap), 
the designations of the heaps are switched, the idle heap becomes the current heap 
and the current heap becomes the idle heap.
In the process, all the unreachable nodes are left in the idle heap at this point.
```

3\) Reference Counting Algorithm

```
keep a count in each record of the number of records pointing to it. 
When a count reaches zero, put the record on the free list. 
Reference counting requires the mutator to explicitly discard records it no longer needs.

(allocate)      // return record with count 1
(set-box! a b)  // discard (unbox a), increment count of b
(discard a)     // decrement count of A and if 0, add a to free list

The problem with reference counting is that cycles are never reclaimed
```

!!! There are more advance garbage collection Algorithm

```
Concurrent : Allow the program to run while the collection is happening
Generational : Do not scan log-lived objects at every collection
Real time : Bound the length of pauses
Parallel : Several collector working at once
```

'## Introduction to Garbage Collection is a mostly theoretical one. When things come to practice, numerous adjustments need to be done to accommodate for real-world scenarios and needs

Java heap terminology:

The Heap is divided into young and old generations.

permanent generation" is not part of heap area, it is part of non-heap area which is used by JVM to internal purpose like JIT optimization, method areas etc.

**Young generation:**

The Young Generation is where all new objects are allocated and aged. When the young generation fills up, **this causes a minor garbage** collection. A young generation full of dead objects is collected very quickly. Some surviving objects are aged and eventually move to the old generation.

This divided into two spaces:

```
Eden Space : When object created using new keyword memory allocated on this space.
Survivor Space : This is the pool which contains objects which have survived after 
java garbage collection from Eden space.
```

**Old generation :**

The Old Generation is used to store long surviving objects. Typically, a threshold is set for young generation object and when that age is met, the object gets moved to the old generation. Eventually the old generation needs to be collected. **This event is called a major garbage collection**.

```
Tenured Space: This memory pool contains objects which survived after multiple garbage 
collection means object which survived after garbage collection from Survivor space.
```

**Permanent generation :**

Permanent generation contains metadata required by the JVM to describe the classes and those that is tied to the classes for example static members. The permanent generation is populated by the JVM at runtime based on classes in use by the application.

PermGen has been replaced with Metaspace since Java 8 release.

**Code Cache :**

(Virtual or reserved) : If you are using HotSpot Java VM this includes code cache area that containing memory which will be used for compilation and storage of native code.

![](https://i2.wp.com/javahonk.com/wp-content/uploads/2014/03/JVM\_Structure.png)

Courtesy:

[https://www.youtube.com/watch?v=p9lmJVmsSH0\&list=PLO9y7hOkmmSGTy5z6HZ-W4k2y8WXF7Bff\&index=0](https://www.youtube.com/watch?v=p9lmJVmsSH0\&list=PLO9y7hOkmmSGTy5z6HZ-W4k2y8WXF7Bff\&index=0)

[https://plumbr.io/handbook/garbage-collection-in-java](https://plumbr.io/handbook/garbage-collection-in-java)

[http://javahonk.com/how-many-types-memory-areas-allocated-by-jvm/](http://javahonk.com/how-many-types-memory-areas-allocated-by-jvm/)
