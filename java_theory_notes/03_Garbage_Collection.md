# Java Garbage Collection

# 1. what is Garbage in java
In java, garbage means unreferenced objects.

# 2. what is Garbage Collections

Garbage Collection is a process of reclaiming the runtime unused memory automatically. 
In other words, it is a way to destroy the unused objects.

To do so, we were using free() function in C language and delete() in C++. 
But, in java it is performed automatically. So, java provides better memory management.

Garbage Collection (GC) in Java is a process by which the Java Virtual Machine (JVM) automatically manages memory. 
It identifies and reclaims memory that is no longer in use, i.e., memory used by objects that are no longer 
reachable or referenced by any part of the program.

The primary goal of garbage collection is to automatically free up memory that is no longer needed, 
which preventing memory leaks and optimizing memory usage in Java applications. 

The JVM handles this process in the background and allowing developers to focus on application logic 
without manually managing memory.

Advantage of Garbage Collection
- It makes java memory efficient because garbage collector removes the unreferenced objects from heap memory.
- It is automatically done by the garbage collector(a part of JVM) so we don't need to make extra efforts.

# 3. How can an object be unreferenced?

There are many ways
- **By nulling the reference**
- **By assigning a reference to another**
- **By anonymous object etc**.

**By nulling a reference:**
~~~
Employee e = new Employee();  
e = null;
~~~

**By assigning a reference to another:**
~~~
Employee e1 = new Employee();  
Employee e2 = new Employee();  
e1 = e2; 
//now the first object referred by e1 is available for garbage collection
~~~

**By anonymous object:**
~~~
new Employee();  
~~~

# 4. finalize() method

The finalize() method is invoked each time before the object is garbage collected. 
This method can be used to perform cleanup processing.

Note: Neither finalization nor garbage collection is guaranteed.

This method is defined in Object class as:
~~~
protected void finalize(){}
~~~
**Note: The Garbage collector of JVM collects only those objects that are created by new keyword. 
So if you have created any object without new, you can use finalize method to perform cleanup processing 
(destroying remaining objects)**.
~~~
JVM ----> new Student();
~~~

# 5. gc() method

**The gc()** method is used to invoke or call the garbage collector to perform cleanup processing. 
The gc() method is found in System and Runtime classes.

Note: Neither finalization nor garbage collection is guaranteed.
~~~
public static void gc(){}
~~~

**Note: Garbage collection is performed by a daemon thread called Garbage Collector(GC). 
This thread calls the finalize() method before object is garbage collected.**
~~~
1. garbage collection done by daemon Thread.
2. Thid daemon Thread called GC (Garbage Collector).
3. Before the Object is collected, Thid daemon thread calls the finalize() method. 
~~~


**Simple Example of garbage collection in java**
~~~
public class TestGarbage1 {  
    
    public void finalize() {
        
        System.out.println("object is garbage collected");
    }

    public static void main(String args[]) {  
    
        TestGarbage1 s1=new TestGarbage1();  
        TestGarbage1 s2=new TestGarbage1();  
        
        s1=null;  
        s2=null;  
        
        System.gc();  
    }	  
}  

Output :
object is garbage collected
object is garbage collected
~~~

**Note: Neither finalization nor garbage collection is guaranteed.**

# 6. Important Points to Remember

1.	**Garbage Collection is Automatic**: You don’t need to manually manage memory in Java because the JVM handles 
    garbage collection for you.

2.	**Garbage Collection Pauses**: Although GC minimizes manual memory management, it introduces occasional pauses 
    (GC pause times). In some applications, long pauses can be detrimental, so tuning GC becomes crucial for 
     performance-sensitive applications.

3.	**No Guarantee of Immediate GC**: The JVM doesn’t guarantee when garbage collection will happen; 
    it only happens when needed. 
    You can manually invoke garbage collection using System.gc(), but it’s not recommended, as 
    it’s generally inefficient.


# 7. How Garbage Collection Works

Garbage collection occurs in the heap, and its process generally involves:

1.	**Marking**: The GC identifies which objects are still in use or not by tracing references from the root objects 
    (e.g., local variables, static fields, active threads).
2.	**Sweeping**: Once objects that are no longer reachable are identified, the garbage collector sweeps 
    through and frees the memory they occupy.
3.	**Compacting**: After sweeping, the remaining live objects may be scattered across the heap. 
    The GC may compact the heap to reduce fragmentation by moving live objects together,
    making space for new objects.

# 8. Generations in Java Garbage Collection

The Java heap is divided into several generations based on the age of objects:

**Heap Memory:**
The Java objects are stored in Heap Memory. It's divided into two main parts: 

1.	**Young Generation**.
2.	**Old Generation (Tenured Generation)**.


1. **Young Generation**: Where newly created objects are placed. It is further divided into:
   **Eden Space & Survivor Spaces (S0, S1)**

-	Young Generation, This is where most objects are created.
-	Objects that are newly created are placed in the Eden space.
-	After some time, surviving objects are promoted to the Survivor space (S0 and S1).
-	Minor GC occurs here, which is usually a shorter process.

**Eden Space**: This is where most new objects are created.
**Survivor Spaces (S0, S1)**: Where objects that survive from garbage collection in the Eden space are moved.

2. **Old Generation (Tenured Generation)**: Objects that have lived long enough in the young generation are promoted 
 here.

-	Objects that have survived multiple garbage collection cycles in the young generation are 
    promoted to the old generation.
-	Major GC or Full GC occurs in this space and is more expensive because it involves the entire heap, 
    not just the young generation.

3. **Permanent Generation (Before Java 8):**
- It was used to store metadata related to classes, methods, etc.
- From Java 8 onwards, it has been replaced by the Metaspace.


# 9. Garbage Collector (GC):
The garbage collector is responsible for identifying which objects are no longer in use (i.e., unreachable) 
and reclaiming their memory.

**Reachability**
An object is considered reachable if it can be accessed through any chain of references starting 
from active threads, static fields, or local variables.

If an object has no references pointing to it (means it’s unreachable), it is eligible for garbage collection.

# 10. Types of Garbage Collection Algorithms

Java provides different **garbage collection algorithms**, and the JVM can be configured to use different 
ones based on performance needs. 

**1. Serial Garbage Collector:** It is single threaded and performs garbage collection in a single thread. 
It is suitable for small application or environments with limited memory.

**2. Parallel Garbage Collector (also known as the throughput collector):**
It is Multi-threaded and performs garbage collection in a Multi-thread in the young generation, 
as uses multi-threaded which speeds up the process. It is suitable for applications where high throughput 
is required (e.g., batch processing).

**3. CMS (Concurrent Mark-Sweep) Collector:**
Low pause times: It aims to minimize application pauses during GC. 
Best suited for applications where low latency is critical (e.g., web servers)

**4. G1 (Garbage First) Collector:**
The G1 collector is designed for applications that handle large heaps. 
G1 divides the heap into regions, and garbage collection occurs in parallel across different region. 
G1 aims to balance low latency and high throughput.

**5. ZGC and Shenandoah GC (Java 11+):**
Low latency GCs designed to handle extremely large heaps (multi-terabyte scale). 
They aim for very short pause times (under 10ms).

# 11. About Finalization method

**Before GC**: Before an object is garbage collected, the finalize() method is called (if defined) 
to allow the object to clean up resources.

**Deprecated in Java 9**: The use of **finalize()** is discouraged because it leads to 
non-deterministic behavior and can cause issues with garbage collection. 
**java.lang.ref.Cleaner** and **java.lang.ref.PhantomReference** are better alternatives.


# 12. Tuning Garbage Collection

You can tune garbage collection by using different JVM flags to control various aspects of the process:

1. **Heap Size:**
~~~
-Xms: Initial heap size
-Xmx: Maximum heap size.

Example: java -Xms512m -Xmx1024m MyApp 
(sets initial heap size to 512MB and max to 1024MB).
~~~
2. **GC Algorithm Selection:**
~~~
-XX:+UseSerialGC:           Serial collector.
-XX:+UseG1GC:               G1 garbage collector.
-XX:+UseConcMarkSweepGC:    CMS garbage collector.
-XX:+UseZGC:                Z Garbage Collector.
~~~
3. **GC Logging:**
~~~
-XX:+PrintGCDetails: Print GC details.
-XX:+PrintGCDateStamps: Print GC timestamps.
~~~
4. **GC Pause Time:**
~~~
-XX:MaxGCPauseMillis=<time_in_ms>: Control the maximum pause time.
~~~


# 13. What is Garbage Collection in Java?
Garbage Collection (GC) is the process by which Java automatically reclaims memory by deleting objects 
that are no longer referenced by any part of the program. 
The JVM performs this task in the background, freeing up memory for new objects, to avoiding memory leaks.

# 14. How does Garbage Collection work in Java?
Garbage collection works by identifying and reclaiming memory occupied by objects that are no longer reachable. 
It typically involves the following steps:

1.	**Marking**: Identifying the live objects by tracing references from the root.
2.	**Sweeping**: Releasing the memory occupied by unreachable objects.
3.	**Compacting**: (Optional) Moving live objects together to reduce fragmentation and free up contiguous memory space.

# 15. What is the difference between Minor GC and Major GC in Java?

**Minor GC occur**s in the young generation (**Eden and Survivor spaces**). 
It happens when the Eden space fills up and involves reclaiming memory from the young generation. 
It is usually quick and frequent.

**Major GC (Full GC) occurs** in the old generation (**tenured generation**). 
It involves reclaiming memory from both the young and old generations and is more time-consuming 
than Minor GC because it processes the entire heap.

# 16. What is the role of finalize() method in Garbage Collection?

The **finalize()** method in Java allows an object to clean up resources 
(like closing files or releasing network connections) before it is garbage collected. 
It is called just before the garbage collector reclaims the object's memory. 
However, finalize() is **deprecated in Java 9** and is generally avoided because it introduces unpredictable behavior. 
Instead, the **java.lang.ref.Cleane**r or **PhantomReference** is recommended for resource cleanup

# 17. What are the different types of Garbage Collectors in Java?

Java provides several types of garbage collectors, which can be selected based on the application needs:

**Serial Garbage Collector:** Uses a single thread for garbage collection. 
Suitable for single-threaded applications or small heaps.

**Parallel Garbage Collector:** Uses multiple threads for garbage collection in the young generation, 
optimizing throughput. It is suitable for multi-threaded applications.

**CMS (Concurrent Mark-Sweep) Collector:** Aims to minimize pause times by performing most of the garbage collection
work concurrently with application threads. Suitable for applications requiring low-latency.

**G1 Garbage Collector:** Aimed at large heap sizes with low-latency requirements. 
It divides the heap into regions and performs GC in a way that optimizes both pause time and throughput.

**ZGC (Z Garbage Collector):** A low-latency garbage collector introduced in Java 11, 
designed for large heaps (multi-terabyte scale) with very short pause times (under 10ms).

**Shenandoah GC:** Another low-latency garbage collector designed for large heaps with reduced pause times.

# 18. What is the significance of serialVersionUID in Serialization and Garbage Collection?

The **serialVersionUID** is a unique identifier for serialized classes. 
It is not directly related to garbage collection but can be important if a class is serialized.

During deserialization, if the **serialVersionUID** does not match between the serialized object and 
the current class, an **InvalidClassException** is thrown. 
It helps maintain backward compatibility during versioning.

# 19. What are the GC roots in Java?

GC roots are objects that are directly accessible by the garbage collector. 

These include:

**Active threads:** All objects referenced by the thread stack.

**Static fields:** Objects referenced by static variables.

**JNI (Java Native Interface) references:** References from native code.

**Active Stack Frames:** Variables and objects in the stack of active methods.

**Method Area**: Objects referenced by the method area (e.g., class definitions).


# 20. What is the difference between WeakReference, SoftReference, and PhantomReference in Java?

**WeakReference:** Objects referenced by a WeakReference can be collected by the garbage collector 
at the next GC cycle, regardless of memory availability.

**SoftReference**: Objects referenced by a SoftReference are **only garbage collected** when 
the JVM is running out of memory, making it useful for caching.

**PhantomReference**: Objects referenced by a PhantomReference are never automatically finalized. 
It is used for post-mortem cleanup after an object is about to be garbage collected.

# 21. What is the -Xms and -Xmx JVM option?

**-Xms:** Specifies the initial heap size (memory) for the JVM. 
For example, -Xms512m sets the initial heap size to 512 MB.

**-Xmx:** Specifies the maximum heap size the JVM can use. 
For example, -Xmx1024m sets the maximum heap size to 1024 MB.

# 22. What is the role of -XX:+UseG1GC JVM option?

The **-XX:+UseG1GC** option tells the JVM to use the Garbage First (G1) garbage collector, 
which is designed for large heap sizes and aims to minimize pause times while still providing good throughput. 
It is a good choice for applications that need predictable low-latency garbage collection.

# 23. What is Metaspace in Java and how does it relate to Garbage Collection?

**Metaspace** is where the JVM stores class metadata (e.g. class definitions, method information) 
starting from **Java 8**.

Prior to Java 8, this area was called the **Permanent Generation (PermGen)**. 
The main difference is that **Metaspace grows dynamically** and is not limited by the size of the heap, 
unlike PermGen, which could run into OutOfMemoryError. 

The garbage collection of Metaspace is separate from the heap's garbage collection process.

# 24. What are the disadvantages of using the finalize() method in garbage collection?

The finalize() method introduces unpredictable behavior because it is called by the garbage collector, 
and there is no guarantee of when it will be executed.

- It can delay the reclaiming of memory, as the JVM waits for finalize() to complete before reclaiming the object.
- It can result in performance overhead and potential memory leaks if finalize() fails to release resources properly.
- It can lead to non-deterministic finalization. 
  For reliable cleanup, **java.lang.ref.Cleaner or PhantomReference are recommended.**

# 25. What happens when the JVM runs out of heap memory and garbage collection cannot reclaim enough space?
If the JVM runs out of heap memory and garbage collection cannot reclaim sufficient space, 
it will throw an **OutOfMemoryError**. 
This typically occurs when the heap size is too small for the application's needs, 
or when objects are being allocated too quickly and the garbage collector cannot keep up.

# 26. Can you trigger garbage collection manually in Java?

**No**, But You can suggest garbage collection using **System.gc()**.

But it is not guaranteed to actually trigger a GC. It merely makes a request to the JVM to run garbage collection, 
and the JVM may ignore this request or defer it to a later time.

Manual GC invocation is discouraged, as it disrupts the JVM’s automatic memory management and 
could lead to performance issues.

# 27. How can you tune garbage collection to improve application performance?

Tuning garbage collection involves adjusting JVM options and choosing the right garbage collector 
based on your application's needs. 

Some common tuning techniques include:

- Adjusting heap sizes (-Xms, -Xmx) to avoid frequent garbage collections.
- Using the appropriate garbage collector (e.g., G1, CMS, or ZGC for low-latency requirements).
- Using GC logging options (-XX:+PrintGCDetails, -XX:+PrintGCDateStamps) to analyze GC performance.
- Optimizing object allocation patterns to reduce the frequency of GC.
- Using -XX:MaxGCPauseMillis to set desired GC pause times.

# 27. What are the potential problems caused by Garbage Collection?

**GC Pauses:** While GC frees memory, it introduces pauses, which can affect application performance, 
especially in low-latency applications.

**Memory Leaks:** If objects are inadvertently retained (e.g., through strong references), 
they won't be garbage collected, leading to memory leaks.

**Overhead:** The garbage collector itself requires CPU resources, which can increase the overhead 
on the application.

**Full GC:**
