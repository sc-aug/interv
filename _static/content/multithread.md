# Multithreading

* What is the difference between Process and Thread?
    + application >> process >> thread
    + A process = an executing program.
    + A Java application 1 process (default). Within a Java application you work with several threads to achieve parallel processing or asynchronous behavior.
    + **isolation**
        - Process: runs independently, isolated from others. cannot directly access shared data in other processes
        - Thread: share the context of the process. own call stack, and can access shared data of other threads in the same process.
    + **context switch**
        - Process: slow
        - Thread: fast 
    + **communication**
        - Process: specific communication technique
        - Thread: is easier as thread shares common address space 
* What are the benefits of multi-threaded programming?
    + fast / efficient / reduce cpu idle time 
    + when two or more thread running simultaneously, you can create multifunctoinal app
    + appilcation response fast, and no I/O blocking
* What is difference between user Thread and daemon Thread? [ref](https://javaconceptoftheday.com/difference-between-used-threads-vs-daemon-threads-in-java/)
    + Daemon Thread
        - perform some background tasks like garbage collection.
        - Daemon thread is to provide services to user thread for background supporting task.
        - Daemon Threads are threads that do not prevent the JVM from shutting down.
        - `setDaemon(true)` to set a thread as a daemon thread
        - `isDaemon()`
    + User Thread
        - User threads are threads use in your application to achieve user task
        - User threads are designed to do user defined tasks
        - User threads are high priority threads
    + JVM:
        - JVM will wait for user threads to finish their tasks. JVM will not exit until all user threads finish their tasks. On the other side, JVM will not wait for daemon threads to finish their tasks. It will exit as soon as all user threads finish their tasks.
        - JVM will not force the user threads to terminate. It will wait for user threads to terminate themselves. On the other hand, JVM will force the daemon threads to terminate if all the user threads have finished their task.
* What is multi-tasking and multi-threading?
    + multi-tasking = multiple processes 
    + multi-threading = multiple threads (faster context swicher)
* How can we create a Thread in Java?
    + create Thread object, passing Runnable Object, start()
    + create class extends Thread, create object of that class, start()
* What are different states in lifecycle of Thread? ?? block ->runnable ?? start & run
    + [new] thread is not alive and it’s a state internal to Java programming.
    + [runnable] call `start()`, it’s state is changed to Runnable. The **thread scheduler** will take control of the thread, and finish execution of the thread. the thread may run immediately, or it may keep in runnable thread pool.
    + [running] Thread scheduler picks one of the thread from the runnable thread pool and change it’s state to Running. When thread is executing, it’s state is changed to Running.
        - running -> runnable : yield
        - running -> terminate : finish
        - running -> block : sleep(), wait()
    + [block/wait] sleep, wait/notify, consumer/producer, i/o / (suspend/resume ??)
        - block -> runnable -> running 
    + [terminate] Once the thread finished executing

![thread states](/images/thread-states.jpg)

* Can we call run() method of a Thread class?
    + No. it's just a common method, call `run()` directly won't create new 
* How can we pause the execution of a Thread for specific time?
    + 
* What do you understand about Thread Priority? ?? always highest first ??
    + priorities [min-max] = [1-10], default = 5
    + In most cases, thread schedular schedules the threads according to their priority (known as preemptive scheduling).
* What is Thread Scheduler and Time Slicing?
    + Thread scheduler in java **is the part of the JVM** that decides which thread should run.
    + There is no guarantee that which runnable thread will be chosen to run by the thread scheduler.
    + Only one thread at a time can run in a single process.
    + Time slicing schedulling is the one of preemptive based scheduling algorithm
    + A task executes for a predefined slice of time and then reenters a pool of ready tasks.
    + Time slicing [**predefine**] [**time window**]
* What is context-switching in multi-threading?
    + in multi-threading. At a time point, for each processor, there would be only one thread running.
    + so if multiple thread is assign to a same processor, the processor need to schedule threads.
    + during the context switching OS kernel has to save the the state of the cpu registers for the current thread, then load these registers with the correct state for the next thread that is next to be executed
* what is join()
    + the joined thread will execute first, until then current thread will run the code after that `join()` method
    + current thread block, wait the thread execution which use join()
* How can we make sure main() is the last thread to finish in Java Program?
    + all the thread should use `join()` method to join in `main()` thread.
    + daemon_main() & thread.setDaemon(true);thread.start() ??
* How does thread communicate with each other?
    - wait()/notify()/notifyAll()
* Why thread communication methods wait(), notify() and notifyAll() are in Object class?
    - because `wait`, `notify`, `notifyAll()` they apply on lock, and the lock is based on Object not Thread.
* Why wait(), notify() and notifyAll() methods have to be called from synchronized method or block?
    - because `wait`, `notify`, `notifyAll()` they apply on lock, the lock is from `synchronized`. If `w n na` is used, then `synchronized` should go along with them
* Why Thread sleep() and yield() methods are static?
    - sleep() not associate with perticular thread. [in t1 cannot call t2.sleep()]
    - yield(), The thread which executes the yield method will enter in the [runnable] from [running].
* How can we achieve thread safety in Java?
    - make sure that shared object is thread safe
    - if shared object is not thread safe, apply `synchronized` `Lock` should be used, so only one thread can access the object at a time point.
* What is `volatile` keyword in Java
    + `volatile` keyword disables cpu cache
    + `volatile` make sure the object is stored in main memory where it can be seen by diff threads.
* Which is more preferred – Synchronized method or Synchronized block?
    + synch static method: lock on class => synchronizing to class of the object 
    + synch non-static method: lock on class => synchronizing to the object
    + synch block: better control of synchronization by using a lock object, you can synchronizing a part of method to a lock object and without lock the whole object/class.
* How to create daemon thread in Java?
    + create a common thread -> setDaemon(true) -> start()
* What is ThreadLocal? [ref](http://tutorials.jenkov.com/java-concurrency/threadlocal.html)
    + The ThreadLocal class in Java enables you to create variables that can only be read and written by the same thread. Thus, even if two threads are executing the same code, and the code has a reference to a ThreadLocal variable, then the two threads cannot see each other's ThreadLocal variables.
* What is `ThreadGroup`? Why it’s advised not to use it?
    + The instance of `ThreadGroup` class contains `Thread` and `ThreadGroup`.
    + The `ThreadGroup` offers a convenient way to manage groups of threads as a unit. 
    + Manage a number of related Threads easily and manipulate them at the same time (suspend & resume).
* What is Java Thread Dump, How can we get Java Thread dump of a Program?
    + 
* What is Deadlock? How to analyze and avoid deadlock situation?
    + >2 threads asking for resources which acuqired by other thread    
    + avoid nested Lock
    + tryLock()
* ?? Scheduled Thread Pool
    + schedule a thread 

```
ScheduledExecutorService scheduledThreadPool = Executors.newScheduledThreadPool(5);
Thread t= new Thread();
scheduledThreadPool .schedule(t, 50, TIMEUNIT.SECONDS);
```
?? ScheduledExecutorService scheduleAtFixedRate(Runnable command,long initialDelay,long period,TimeUnit unit)

What is Java Timer Class? How to schedule a task to run after specific interval?
* What is Thread Pool?
    + is a collection of worker threads (execute asynchronous) on behalf of the application.
    + is primarily used to (reduce the number of threads) and (provide threads' management).
    + use Executor framework
* How can we create Thread Pool in Java?
    + single/cache/fix/schdule
* What will happen if we don’t override Thread class run() method?
    + `start()` internally calling `run()`, so if `run()` is not overrided then nothing will happen.
* What is atomic operation? What are atomic classes in Java Concurrency API?
    + 
* What is Lock interface in Java Concurrency API? What are it’s benefits over synchronization?
    + Fairness ReentrantLock(true)
    + increase performance
    + tryLock avoid deadlock
    + ReentrantLock / Read/Write Lock
    + concurrentHashMap - Read/Write Lock
    + What is ReentrantLock  ???
* What is Executors Framework?
    + 
* What is BlockingQueue? How can we implement Producer-Consumer problem using Blocking Queue?
    + ?? blockingqueue no null value & thread safe & 
* What is Callable and Future?
    + Callable 
* What is FutureTask class?
    + Implementation
* What are Concurrent Collection Classes?
    + copyAndWriteArrayList / BlockingQueue / ConcurrentHashMap
    + ArrayBlockingQueue, ConcurrentHashMap, or ExecutorService.
What is Executors Class?
What are some of the improvements in Concurrency API in Java 8?
Object Class notify,notifyAll,wait ?
What is 

* object lock & class lock??

* nested sync method ??

* executor shutdown ??

* ConcurrentModificationException?? ??
    - how to avoid (when use copy first) (sync block) ()
* ConcurrentMidification ??
failFast failSafe
https://www.geeksforgeeks.org/fail-fast-fail-safe-iterators-java/
iterator fail fast

* CompleteFuture ??
    + chain
    + exception handling
    + complete() manual terminate

* where used in project ?? executorframework

* ?? semaphore ?? mutex ??

* Iterator only call remove() and no add()

* terminated thread start IlleagalThreadState 

Question1. What Do You Understand By Executor Framework In Java?
Question2. What Is The Role Of Executorservice In Java?

Question3. What Is Executors In Java Executor Framework?


Question4. What Is The Role Of Futuretask And Future In Java?

Question5. What Is Difference Between Shutdownnow() And Shutdown() In Executor 
Question6. How To Terminate A Thread In Executor Framework In Java?


Question7. What Is The Role Of Executors.privileged Threadfactory() In Executor Framework?


Question8. What Is The Role Of Executors.unconfigurable Executorservice In Executor 

Question9. What Are The Different Policy In Executor Framework?

Question10. How To Get Return Value Of A Callable Thread In Java Executor Framework?


Question11. Write A Program Using Executor In Java Or Example Of Thread Pool In Java?


Question12. What Is Semaphore?


Question13. What Is Cyclicbarrier And Countdownlatch?
Answer :

Question14. How Countdownlatch Work In Java?

Question15. What Is Difference Between Lock Interface And Synchronized Keyword?

Question16. What Is Condition?

Question17. What Is Readwritelock?



Lab Work

Q1) Write a program to do the following operations using Thread:
Create an user defined Thread class called as “CopyDataThread .java” .
This class will be designed to copy the content from one file “source.txt ” to another file “target.txt” and after every 10 characters copied, “10 characters are copied” message will be shown to user.(Keep delay of 5 seconds after every 10 characters read.)
Create another class “FileProgram.java” which will create above thread. Pass required File Stream classes to CopyDataThread constructor and implement the above functionality.

Q2) Write a thread program to display timer where timer will get refresh after every 10seconds.( Use Runnable implementation )

