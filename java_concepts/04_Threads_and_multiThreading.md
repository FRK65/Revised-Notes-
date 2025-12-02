# 1. Why we need Threads?

Thread allows multiple tasks to be executed simultaneously and improve the overall performance 
and responsiveness of applications.  
Threads enable multitasking within a single process, allowing different parts of a program 
to run in parallel.
In summary, threads enhance performance, responsiveness, and efficiency in Java applications 
by enabling concurrent execution of multiple tasks.

# 2. How we can create Thread in java

There are 2 main ways to create a thread
1.	**By Extending the Thread class**
2.	**By Implementing the Runnable Interface**

**Extending Thread class** : 
Simpler but limits you to only one inheritance, as Java allows single inheritance only.
      
**Implementing Runnable:** 
More flexible, as it allows your class to extend another class and implement Runnable interface.

# 2.1 By Extending the Thread class
You can create a thread by extending the Thread class and overriding its run() method.

**run()**: Contains the code to be executed in the thread.

**start()**: Begins the execution of the thread and calls run() internally.
~~~
class MyThread extends Thread {

    @Override
    public void run() {
        // Code to be executed by the thread
        System.out.println("Thread is running.");
    }
}
~~~
~~~
public class Main
{
    public static void main(String[] args) {
        MyThread thread = new MyThread();
        thread.start();  // Start the thread
    }
}
~~~

# 2.2 By Implementing the Runnable Interface

Alternatively, you can create a thread by implementing the Runnable interface and passing it to a 
Thread object.

**run():** Contains the task to be executed.

**Thread(Runnable Class object):** The Thread constructor takes a Runnable class  object.

**start():** Starts the thread and invokes the run() method.

~~~
class MyRunnable implements Runnable {
    
    @Override
    public void run() {
        
        // Code to be executed by the thread
        System.out.println("Thread is running.");
    }
}
~~~
~~~
public class Main {
    public static void main(String[] args) {
        
        MyRunnable myclassObj = new MyRunnable();
        Thread thread = new Thread(myclassObj);
        thread.start();  // Start the thread
    }
}
~~~



# 3. Common Method used in Thread.

-	**thread.start()** : It start the thread and invokes the run() method in a new thread of execution. 
                         Can only be called once on a thread.
-	**run()** : Method to override with the task to be executed when the thread is started. 
                It Contains the code to be executed by the thread.
-	**Thread.sleep(1000)** : Pauses the thread for a specified time.

-	**thread.isAlive()** : Returns true if the thread has been started and is still running or 
                         has not yet completed its execution.
-	**thread.setPriority(Thread.MAX_PRIORITY)** : Sets the thread’s priority to a value between Thread.MIN_PRIORITY (1) 
       and Thread.MAX_PRIORITY (10). Default is Thread.NORM_PRIORITY (5).
-	**int priority = thread.getPriority()** : returns the current priority of the thread.
-	**long id = thread.getId()** : Returns the unique ID assigned to the thread by the JVM.
-	**String name = thread.getName()** : Returns the name of the thread
-	**thread.setName("MyThread")** : Allows you to assign a custom name to the thread.





# 4. What is daemon Thread?

The **Thread.setDaemon(true);** method in the Thread class is used to mark a thread as a daemon thread.

A daemon thread is a type of thread that runs in the background to perform certain tasks 
but does not prevent the JVM from exiting when all user (non-daemon) threads have finished executing.
Daemon Thread should not prevent the JVM from exiting.

**Daemon Thread**: A thread that runs in the background, typically used for background tasks like garbage collection, 
logging, or monitoring. It is not critical to the application’s core logic.

**User Thread**: A thread that is typically part of the main logic of an application, 
and the JVM waits for all user threads to finish before it exits.

_Key Points:_
1.	**Automatic Termination**: When the JVM detects that there are no user threads remaining 
    (i.e., all user threads have finished), it will terminate all daemon threads, even if they are still running.
2.	**Set Daemon before start()**: The setDaemon() method must be called before starting the thread using start(). 
    If it is called after the thread has already started, it will throw an IllegalThreadStateException.
3.	**Default Behavior**: By default, all threads are user threads (i.e., non-daemon). 
    Only threads that explicitly call setDaemon(true) become daemon threads.

# 5. State of Threads 
| State	| Description	| Transition |
| :---         |:-----------------------:|          ---: |
| New	| Thread is created but not yet started.	| Created using the Thread constructor but start() has not been called. |
| Runnable	| Thread is eligible to run, but the thread scheduler has not yet assigned it CPU time.	| Thread is in New state and start() is called, or it was blocked or waiting and is now ready to run. |
| Blocked	| Thread is waiting to acquire a lock.	| Thread is attempting to access a synchronized resource but is blocked by another thread holding the lock. |
| Waiting	| Thread is waiting indefinitely for another thread to perform a particular action.	| Thread is waiting on wait(), join(), or sleep() without a timeout. |
| Timed Waiting	| Thread is waiting for a specified amount of time before it becomes runnable again.	| Thread is waiting for a specific time limit on sleep(), join(), wait(), or yield(). |
| Terminated	| Thread has finished executing.	| run() method has completed, or thread was terminated due to an exception. Once terminated, it cannot be restarted. |




# 5.1 . New (Thread is in the "new" state)

A thread is in the New state when it is created but has not yet started means 
the start() method has not been called yet. 
The thread remains in this state until the start() method is invoked.
~~~
Thread thread = new Thread();
// Thread is in "New" state until start() is called
~~~
# 5.2 Runnable (Thread is in the "runnable" state

A thread enters the Runnable state after the start() method is called. 
In this state, the thread is eligible to run, but it may not immediately get the CPU time. 
The thread scheduler decides when the thread will actually execute.

The thread can enter the runnable state from the New state via start() method. 
It can also return/reverse to the runnable state from other states like Blocked or Waiting.
~~~
thread.start();  // Now thread is in "Runnable" state
~~~

# 5.3 Blocked (Thread is in the "blocked" state)
A thread enters the Blocked state when it is waiting to acquire a lock (monitor) on an object, 
and it is unable to proceed until the lock is released by another thread.
The thread moves to the blocked state when trying to access a synchronized (block or method) 
and the lock is already held by another thread.

# 5.4 Waiting (Thread is in the "waiting" state)

A thread enters the Waiting state when it is waiting indefinitely for another thread to perform a 
particular action. 
A thread can enter this state by calling methods like Object.wait() or Thread.join(), without a specified timeout.

The thread moves to the Waiting state when calling methods like:
~~~
•	Thread.sleep()
•	Object.wait() (without timeout)
•	Thread.join() (without timeout)
~~~
The thread will remain in the Waiting state until it is awakened by another thread.
~~~
synchronized (lock) {
    
    lock.wait();  // Thread enters "Waiting" state
}
~~~
# 5.5 Timed Waiting (Thread is in the "timed waiting" state)

A thread enters the Timed Waiting state when it is waiting for a specified period of time to expire, 
after which it will automatically return to the Runnable state.

The thread enters this state when it calls methods like
~~~
Thread.sleep(long millis),
Object.wait(long millis),
Thread.join(long millis), or
Thread.yield().
~~~

# 5.6 Terminated (Thread is in the " Terminated " state)
A thread enters the Terminated state when it has finished executing its run() method or if it 
terminates due to an exception.
The thread moves to this state once the run() method completes, or if an unhandled exception occurs 
during execution. Once a thread is in the Terminated state, it cannot be restarted.
~~~
// After the run() method completes, the thread is terminated
~~~

# 5.7 Waiting on IO / Blocking (Special state for IO operations)

In certain environments, when a thread is performing input/output operations, it may be waiting for 
resources to become available. This is often considered an extension of the Blocked or Waiting state.
This is often handled by the JVM and might not appear as a distinct state in all contexts, 
but you can think of it as being related to the Blocked state.


# 6. What is a thread in Java?
A thread is a lightweight sub-process, the smallest unit of processing. 
In Java, a thread is represented by the Thread class, and it allows concurrent execution of two or more parts of 
a program. Threads in Java can be created either by extending the Thread class or by implementing 
the Runnable interface.

# 7. How can you create a thread in Java?
In Java, you can create a thread in two ways:

**By extending the Thread class**: Override the run() method and call start() to begin the execution.

**By implementing the Runnable interface**: Implement the run() method and pass it to a Thread object, 
then start the thread.

# 8. What is the difference between start() and run() methods in Java?

**start()**: This method is used to begin the execution of a thread. It invokes the run() method 
in a new thread of execution.

**run():** This method contains the code that defines the task to be executed by the thread. 
If you directly call run() (instead of start()), it will not start a new thread but will execute the code on 
the current thread.

# 9. What is the sleep() method in Java?
The **sleep(long millis)** method is a static method of the Thread class that pauses the current thread for 
a specified amount of time (in milliseconds). 
During this time, the thread remains inactive, and other threads can execute. 
It can throw an **InterruptedException** if the thread is interrupted during sleep.

# 10. What is the difference between sleep() and wait() in Java?

**sleep()**: The sleep() method is used to pause the execution of the current thread for a specified period. 
It does not release any locks.

**wait()**: The wait() method is used for inter-thread communication. 
It can be called on an object to make the current thread release the lock and wait until another thread sends 
a notification **notify() or notifyAll().**

# 11. What is the join() method in Java?
The join() method is used to make one thread wait for the completion of another thread. 
If thread A calls join() on thread B, thread A will pause until thread B finishes execution.
~~~
threadA.join();  // Waits for threadA to finish before continuing
~~~

# 12. What is the difference between Runnable and Thread in Java?

**Thread**: The Thread class represents a thread of execution. 
You can create a thread by extending the Thread class and overriding the run() method.

**Runnable**: The Runnable interface represents a task that can be executed by a thread. 
By implementing Runnable, you can pass the task to a Thread object. 
Using Runnable allows more flexibility because Java supports multiple inheritance of interfaces.

# 13. What are daemon threads in Java?
A daemon thread is a background thread that does not prevent the JVM from exiting. 
When all user threads (non-daemon threads) finish, the JVM will terminate any running daemon threads. 
You can mark a thread as a daemon using the setDaemon(true) method before starting the thread.
~~~
thread.setDaemon(true);
~~~

# 14. What happens if you call start() method multiple times on the same thread?
You can only call start() once on a thread. Calling start() multiple times on the same thread will result 
in an **IllegalThreadStateException**.

# 15. What is thread synchronization?
Thread synchronization is a mechanism that ensures that multiple threads do not access shared resources 
concurrently, which could lead to data corruption or inconsistent results. 
In Java, synchronization can be achieved using the synchronized keyword, 
which locks an object to allow only one thread to access it at a time.
~~~
synchronized (lock) {

        // Critical section of code
}
~~~

# 16. What is the difference between synchronized and volatile in Java?
**synchronized**: Ensures that only one thread can access a synchronized block or method at a time, 
preventing data inconsistency in shared resources.

**volatile**: The volatile keyword is used to ensure that a variable’s value is always 
read from and written to the main memory, not from a thread's local cache. 
This is used for flags or variables that may be shared between multiple threads.

# 17. What is the thread lifecycle in Java?

The thread lifecycle consists of several states:

- **New**: Thread is created but not started.
- **Runnable**: Thread is eligible to run but may not be running yet.
- **Blocked**: Thread is waiting to acquire a lock.
- **Waiting**: Thread is waiting for another thread to perform a specific action.
- **Timed Waiting**: Thread is waiting for a specific period.
- **Terminated**: Thread has finished executing.

# 18. What is ThreadPoolExecutor in Java?
**ThreadPoolExecutor** is a class in Java that provides a pool of worker threads for executing tasks concurrently. 
It is part of the java.util.concurrent package. 
It manages the threads, reducing the overhead of creating and destroying threads repeatedly. 
A common use case is in server applications where many short-lived tasks need to be handled
~~~
ExecutorService executor = Executors.newFixedThreadPool(10);
executor.submit(new MyTask());
~~~

# 19. What is the difference between wait() and notify() in Java?
**wait()**: Makes the current thread release the lock and wait until it is notified by another thread.
**notify():** Wakes up a single thread that is waiting on the same object. 
If multiple threads are waiting, one of them is selected at random.

# 20. Explain deadlock in Java.
A deadlock occurs when two or more threads are blocked forever, each waiting for the other to 
release a resource. 
It happens when threads acquire locks in different orders, and each thread holds a lock while waiting 
for the other to release a lock.

# 21. What is a Thread Pool in Java?
A Thread Pool in Java is a collection of pre-instantiated, reusable worker threads that are used to execute tasks. 
Instead of creating new threads for every task, which can be inefficient and resource-heavy, 
a thread pool reuses threads to handle multiple tasks concurrently. 
This approach improves performance by reducing the overhead associated with thread creation and destruction.

# 22. What is ExecutorService in Java?
ExecutorService is a powerful interface for managing thread execution and concurrency in Java.
It simplifies the handling of thread pools, task submission, scheduling, and graceful shutdowns.
It supports both Runnable (no result) and Callable (with result) tasks and provides additional features 
like managing task queues, thread pooling, and more.

# 23. What is Callable in Java?
In Java, the Callable interface is part of the **java.util.concurrent** package, and it represents a task that 
can be executed by multiple threads. It is similar to the Runnable interface, but with two key differences:

1.	**Return Value**: Unlike Runnable, which does not return any result, Callable can return a result of a specific type.
2.	**Exception Handling**: A Callable can throw exceptions during execution, whereas Runnable cannot.

The Callable interface is used primarily for tasks that need to return a result or may throw a checked exception.

Key Methods of Callable: **call()**

**Usage of Callable**:
1.	**Returning a Result**: The call() method returns a result, which is captured by a Future object 
    when the task is submitted.
2.	**Exception Handling**: The call() method can throw exceptions 
    (such as **InterruptedException** or **ExecutionException**), allowing more flexibility in handling errors 
    during execution. 

# 24. Key Differences Between Runnable and Callable:


|Feature |                   	Runnable                   |	Callable |
| :---         |:---------------------------------------------:|          ---: |
|Return Value |   Does not return any result. (void run())    | Returns a result of type V. (V call()) |
|Exception Handling	|       Cannot throw checked exceptions.        | 	Can throw checked exceptions. |
| Usage | 	For tasks that don't need to return a value. | For tasks that return a value or may throw an exception. |
