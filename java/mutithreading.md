## Java Threads and Synchronization

### 1) How to Create Threads
There are two ways to create a thread in Java:

- **Extending the `Thread` class**: Override the `run` method and define the threading logic inside it. Then, create an instance of the class and invoke the `start` method.
- **Implementing the `Runnable` interface**: Override the `run` method to provide the implementation. Create an instance of this class, pass it to a `Thread` object, and then invoke `start`.
- Implementing `Runnable` allows the class to extend another Java class, unlike extending `Thread`, which restricts multiple inheritance.

### 2) What is Synchronization?
Synchronization is used when multiple threads access the same object or data to prevent data corruption.

- By marking a method with the `synchronized` keyword, the first thread that enters the method attains a lock on it and all synchronized methods in the class.
- Other threads must wait until the first thread finishes its execution before accessing synchronized methods.
- Synchronization can be applied to instance methods, static methods, and at a block level.

### 3) What are Class-Level Locks?
- Every Java class has a unique lock associated with it.
- When a thread executes a synchronized static method, it attains the **class-level lock**.
- Other threads must wait to access any static synchronized methods of that class until the first thread releases the lock.

### 4) What are Synchronized Blocks?
- Using the `synchronized` keyword on a method locks the entire method, allowing only one thread to execute it at a time.
- If only specific lines of code need synchronization, use a **synchronized block** instead of locking the entire method.
- When using a synchronized block, you can specify an object or class on which to attain the lock.

### 5) How Do Threads Communicate?
Threads communicate using the `wait`, `notify`, and `notifyAll` methods.

- A thread calling `wait()` releases its lock on an object, allowing another thread to take over.
- After completing its task, the second thread calls `notify()` to wake up the waiting thread so it can resume execution.
- `notifyAll()` wakes up all threads waiting for the lock.
- These methods must be used within a synchronized context (inside a synchronized block or method), or an `IllegalMonitorStateException` will be thrown.

