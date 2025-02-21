# Multithreading in Java - Interview Questions and Answers

## 1. What is Multithreading in Java?
Multithreading is the ability of a program to execute multiple threads concurrently to improve performance and responsiveness.

### Key Points:
- Java provides built-in support for multithreading using the `Thread` class and `Runnable` interface.
- Threads run independently but share the same process memory.
- JVM schedules threads using a priority-based preemptive scheduling algorithm.

## 2. What are the different ways to create a thread in Java?
1. **Extending the `Thread` class**: Override the `run()` method.
2. **Implementing the `Runnable` interface**: Pass an instance to `Thread`.
3. **Using `Callable` and `Future`**: Returns a result and handles exceptions.
4. **Using `ExecutorService`**: Manages thread execution more efficiently.

### Hidden Rules & Facts:
- Implementing `Runnable` is preferred over extending `Thread` to allow multiple inheritance.
- `Callable` is used when a task needs to return a result.
- `ExecutorService` manages thread pools for better performance and resource management.

## 3. What is the difference between Process and Thread?
| Feature    | Process | Thread |
|-----------|---------|--------|
| Memory    | Separate memory space | Shared memory space |
| Communication | Inter-process communication (IPC) required | Direct memory access |
| Creation  | Expensive | Lightweight |
| Execution | Independent | Can be interdependent |

## 4. What are the different thread states in Java?
Java threads go through six states:
1. **NEW** – Created but not started.
2. **RUNNABLE** – Ready to run or running.
3. **BLOCKED** – Waiting for a monitor lock.
4. **WAITING** – Waiting indefinitely for another thread.
5. **TIMED_WAITING** – Waiting for a specific time.
6. **TERMINATED** – Execution finished.

### Important Facts:
- A thread in `BLOCKED` state waits for a resource lock.
- `WAITING` and `TIMED_WAITING` states require another thread's intervention.

## 5. What is the difference between `synchronized` and `Lock`?
| Feature        | `synchronized` | `Lock` (ReentrantLock) |
|---------------|--------------|------------------|
| Flexibility   | Implicit locking | Explicit locking |
| Interruptible | No | Yes |
| Fairness      | No fairness guarantee | Can be fair |
| Try-Lock      | Not available | Available |
| Condition Variables | Not available | Available |

### Key Points:
- `synchronized` blocks or methods use intrinsic locks (monitor lock).
- `ReentrantLock` provides better control over locks with fairness policies.
- `Lock.tryLock()` allows acquiring locks without blocking.

## 6. What is the difference between `wait()`, `notify()`, and `notifyAll()`?
| Method    | Description |
|-----------|-------------|
| `wait()` | Releases lock and waits until notified. |
| `notify()` | Wakes up one waiting thread. |
| `notifyAll()` | Wakes up all waiting threads. |

### Hidden Rules:
- `wait()`, `notify()`, and `notifyAll()` must be called inside a `synchronized` block.
- `notify()` does not guarantee which thread gets woken up.

## 7. What is Thread Safety, and how do you achieve it?
Thread safety ensures that multiple threads can access shared resources without causing inconsistencies.

### Ways to Achieve Thread Safety:
1. **Synchronization (`synchronized`)** – Ensures mutual exclusion.
2. **Volatile Keyword** – Ensures visibility of changes across threads.
3. **Atomic Variables** – Provides lock-free thread safety (`AtomicInteger`, `AtomicBoolean`).
4. **Thread-safe Collections** – `ConcurrentHashMap`, `CopyOnWriteArrayList`.
5. **Thread-local Storage (`ThreadLocal`)** – Provides thread-confined variables.

### Important Facts:
- `volatile` does not guarantee atomicity, only visibility.
- `synchronized` can cause performance issues if overused.
- `ConcurrentHashMap` provides better performance than `synchronized` HashMap.

## 8. What is the difference between `volatile` and `synchronized`?
| Feature | `volatile` | `synchronized` |
|---------|------------|---------------|
| Atomicity | No | Yes |
| Visibility | Yes | Yes |
| Locking | No | Yes |
| Performance | Better | Can be slow |

## 9. What are `ExecutorService` and Thread Pools?
`ExecutorService` is a framework for managing a pool of worker threads efficiently.

### Key Implementations:
- `FixedThreadPool` – Fixed number of threads.
- `CachedThreadPool` – Creates threads as needed.
- `ScheduledThreadPool` – Supports scheduled execution.

### Limits & Facts:
- Using a thread pool is better than manually managing threads.
- A large thread pool can cause excessive memory usage.

## 10. What are Deadlock, Livelock, and Starvation?
| Concept | Description |
|---------|-------------|
| Deadlock | Circular dependency causes threads to block each other. |
| Livelock | Threads keep changing state but never proceed. |
| Starvation | Low-priority threads never execute due to high-priority threads. |

### Important Facts:
- Deadlocks occur when multiple threads hold locks in a circular manner.
- Livelock happens when threads respond to each other’s state but make no progress.
- Starvation can be prevented using fair locking mechanisms (`ReentrantLock(true)`).

## 11. What is Fork/Join Framework?
The **Fork/Join Framework** in Java 7+ is used for parallel computation by splitting tasks into subtasks.

### Key Points:
- Uses `ForkJoinPool` to execute recursive tasks.
- Splits tasks into smaller subtasks (Fork) and combines results (Join).
- Works well for divide-and-conquer problems.

## 12. What is a Daemon Thread?
A **Daemon Thread** runs in the background and terminates when all user threads finish execution.

### Key Points:
- Use `thread.setDaemon(true)` to make a thread a daemon.
- JVM terminates daemon threads automatically when no user thread is running.
- Garbage Collector (GC) runs as a daemon thread.

## 13. What is the `ThreadLocal` class?
`ThreadLocal` provides thread-specific storage of variables, ensuring each thread gets a unique copy.

### Important Facts:
- Useful for per-thread data like user sessions, database connections.
- Avoid memory leaks by calling `remove()` after usage.

## 14. How does `Future` and `CompletableFuture` differ?
| Feature | `Future` | `CompletableFuture` |
|---------|---------|----------------|
| Blocking | Yes | No |
| Chaining | No | Yes |
| Exception Handling | No | Yes |
| Parallel Execution | No | Yes |

### Key Points:
- `CompletableFuture` supports non-blocking async programming.
- `Future.get()` blocks until a result is available.

