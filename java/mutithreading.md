# Java Threads and Synchronization

## 1) How to Create Threads

### Different Ways to Create a Thread:
There are two ways to create a thread in Java:

1. **Extending the `Thread` class**
2. **Implementing the `Runnable` interface**

### 1.1 Extending the `Thread` Class
- A class extends `Thread` and overrides the `run()` method where the thread's logic resides.
- Create an instance of the class and invoke `start()` to begin execution.

#### Example:
```java
class MyThread extends Thread {
    public void run() {
        System.out.println("Thread is running...");
    }

    public static void main(String[] args) {
        MyThread t1 = new MyThread();
        t1.start(); // Starts a new thread
    }
}
```

### 1.2 Implementing the `Runnable` Interface
- Implements `Runnable` to allow class extension flexibility (Java doesn’t support multiple inheritance).
- Implement the `run()` method and pass an instance of the class to a `Thread` object.

#### Example:
```java
class MyRunnable implements Runnable {
    public void run() {
        System.out.println("Runnable thread is running...");
    }

    public static void main(String[] args) {
        MyRunnable runnable = new MyRunnable();
        Thread t1 = new Thread(runnable);
        t1.start();
    }
}
```

**Hidden Fact:** 
- Directly calling `run()` instead of `start()` will execute the method on the main thread rather than a new thread.

---

## 2) What is Synchronization?

### 2.1 Thread Synchronization
- When multiple threads access shared resources, data inconsistency may occur.
- Synchronization prevents multiple threads from modifying the same data simultaneously.
- Java provides the `synchronized` keyword to ensure only one thread executes a synchronized method or block at a time.

#### Example:
```java
class Counter {
    private int count = 0;
    
    public synchronized void increment() {
        count++;
    }
    
    public int getCount() {
        return count;
    }
}

public class SyncExample {
    public static void main(String[] args) throws InterruptedException {
        Counter counter = new Counter();
        
        Thread t1 = new Thread(() -> {
            for (int i = 0; i < 1000; i++) counter.increment();
        });
        
        Thread t2 = new Thread(() -> {
            for (int i = 0; i < 1000; i++) counter.increment();
        });
        
        t1.start();
        t2.start();
        t1.join();
        t2.join();
        
        System.out.println("Final count: " + counter.getCount());
    }
}
```

**Hidden Fact:**
- Synchronization introduces performance overhead due to context switching.

---

## 3) Class-Level Locks

### 3.1 What is a Class-Level Lock?
- A lock associated with the class instead of an object.
- If a thread acquires a class-level lock, no other thread can access synchronized static methods.

#### Example:
```java
class SharedResource {
    public static synchronized void staticMethod() {
        System.out.println(Thread.currentThread().getName() + " is executing staticMethod");
        try { Thread.sleep(1000); } catch (InterruptedException e) {}
    }
}

public class ClassLevelLockExample {
    public static void main(String[] args) {
        Thread t1 = new Thread(SharedResource::staticMethod, "Thread 1");
        Thread t2 = new Thread(SharedResource::staticMethod, "Thread 2");
        
        t1.start();
        t2.start();
    }
}
```

**Hidden Fact:**
- Even if different objects are created, synchronized static methods will still share the same class-level lock.

---

## 4) Synchronized Blocks

### 4.1 What are Synchronized Blocks?
- Instead of synchronizing an entire method, we can synchronize only the critical section.
- This improves performance by allowing multiple threads to execute non-critical parts simultaneously.

#### Example:
```java
class SyncBlock {
    public void printNumbers() {
        synchronized (this) { // Lock only this block
            for (int i = 1; i <= 5; i++) {
                System.out.println(Thread.currentThread().getName() + " - " + i);
                try { Thread.sleep(500); } catch (InterruptedException e) {}
            }
        }
    }
}

public class SyncBlockExample {
    public static void main(String[] args) {
        SyncBlock obj = new SyncBlock();
        
        Thread t1 = new Thread(obj::printNumbers, "Thread 1");
        Thread t2 = new Thread(obj::printNumbers, "Thread 2");
        
        t1.start();
        t2.start();
    }
}
```

**Hidden Fact:**
- Using `this` in a synchronized block locks the current instance, whereas using a class reference (`ClassName.class`) locks the entire class.

---

## 5) Thread Communication

### 5.1 How Do Threads Communicate?
- Threads use `wait()`, `notify()`, and `notifyAll()` for communication.
- `wait()`: Releases the lock and moves the thread to the waiting state.
- `notify()`: Wakes up one waiting thread.
- `notifyAll()`: Wakes up all waiting threads.

#### Example:
```java
class Message {
    private String msg;
    private boolean hasMessage = false;
    
    public synchronized void write(String message) {
        while (hasMessage) {
            try { wait(); } catch (InterruptedException e) {}
        }
        this.msg = message;
        hasMessage = true;
        notify();
    }
    
    public synchronized String read() {
        while (!hasMessage) {
            try { wait(); } catch (InterruptedException e) {}
        }
        hasMessage = false;
        notify();
        return msg;
    }
}

public class ThreadCommunicationExample {
    public static void main(String[] args) {
        Message message = new Message();
        
        Thread writer = new Thread(() -> {
            message.write("Hello from Writer");
        });
        
        Thread reader = new Thread(() -> {
            System.out.println("Reader got message: " + message.read());
        });
        
        writer.start();
        reader.start();
    }
}
```

**Hidden Fact:**
- `wait()`, `notify()`, and `notifyAll()` must be used inside a synchronized block; otherwise, an `IllegalMonitorStateException` will be thrown.

