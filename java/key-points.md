# Java - Important One-Liners for Interview

## **1️⃣ Core Java Basics**
- **Java is platform-independent** due to the JVM (Write Once, Run Anywhere).
- **JVM (Java Virtual Machine)** executes Java bytecode.
- **JRE (Java Runtime Environment)** provides libraries for running Java programs.
- **JDK (Java Development Kit)** contains JRE + development tools.
- **Object-Oriented Programming (OOP)** concepts: Encapsulation, Inheritance, Polymorphism, Abstraction.
- **Java is pass-by-value** (reference values are passed for objects).

## **2️⃣ Java Data Types & Memory**
- **Primitive types**: int, float, double, char, boolean, long, short, byte.
- **Wrapper classes**: Integer, Float, Double, Character, Boolean, etc.
- **Heap Memory** stores objects, **Stack Memory** stores method calls & variables.
- **Garbage Collection** reclaims unused objects automatically.
- **final, finally, and finalize()**:
  - `final` = constant or method override prevention.
  - `finally` = executes regardless of exceptions.
  - `finalize()` = garbage collector hook.

## **3️⃣ Java Collections Framework (JCF)**
- **List (ArrayList, LinkedList)** - ordered, allows duplicates.
- **Set (HashSet, LinkedHashSet, TreeSet)** - unique elements only.
- **Map (HashMap, LinkedHashMap, TreeMap, ConcurrentHashMap)** - key-value pairs.
- **Queue (PriorityQueue, LinkedList, ArrayDeque)** - FIFO/LIFO structures.
- **Vector & Stack** - synchronized legacy classes.

## **4️⃣ Java Multithreading & Concurrency**
- **Thread Lifecycle**: New → Runnable → Running → Blocked/Waiting → Terminated.
- **Thread creation**:
  - Extend `Thread` class.
  - Implement `Runnable` interface.
  - Use `ExecutorService` for thread management.
- **Synchronized block & methods** prevent race conditions.
- **volatile keyword** ensures variable visibility across threads.
- **CountDownLatch, Semaphore, CyclicBarrier** handle thread synchronization.

## **5️⃣ Java Exception Handling**
- **Checked Exceptions**: IOException, SQLException (handled at compile-time).
- **Unchecked Exceptions**: NullPointerException, ArithmeticException (runtime errors).
- **try-catch-finally** ensures proper resource cleanup.
- **throws vs throw**:
  - `throws` declares exceptions.
  - `throw` is used to explicitly throw an exception.
- **Custom Exceptions** extend `Exception` or `RuntimeException`.

## **6️⃣ Java Functional Programming (Java 8+)**
- **Lambda Expressions** simplify function syntax (`(a, b) -> a + b`).
- **Functional Interfaces**: `Predicate<T>`, `Consumer<T>`, `Supplier<T>`, `Function<T, R>`.
- **Stream API**:
  - `map()`, `filter()`, `reduce()` for collection processing.
  - `parallelStream()` enables parallel execution.
- **Default & Static Methods** in interfaces allow method definitions.
- **Optional<T>** prevents `NullPointerException`.

## **7️⃣ Java Design Patterns**
- **Singleton**: Ensures a single instance.
- **Factory Pattern**: Creates objects dynamically.
- **Builder Pattern**: Simplifies complex object creation.
- **Observer Pattern**: Handles event-driven programming.
- **Strategy Pattern**: Selects algorithms at runtime.

## **8️⃣ Java I/O & Serialization**
- **BufferedReader vs Scanner**: `BufferedReader` is faster.
- **Serialization**: Converts objects to byte streams (`implements Serializable`).
- **Deserialization**: Restores objects from byte streams.
- **transient keyword** prevents field serialization.
- **Files API (Java NIO)**: `Paths.get()`, `Files.readAllBytes()`.

## **9️⃣ Java Database Connectivity (JDBC)**
- **JDBC Steps**:
  1. Load driver (`Class.forName()`).
  2. Establish connection (`DriverManager.getConnection()`).
  3. Create statement (`Statement`, `PreparedStatement`).
  4. Execute query (`executeQuery()`, `executeUpdate()`).
  5. Close connection (`close()`).
- **Connection Pooling** improves performance (HikariCP, C3P0).

## **🔟 Java Best Practices**
- Use `StringBuilder` instead of `String` for mutable strings.
- Prefer `List<>` over `ArrayList<>` for flexibility.
- Close resources using `try-with-resources` (`AutoCloseable`).
- Avoid memory leaks using WeakReference, SoftReference.
- Use `enum` instead of constants for better readability.
- Write clean and modular code following SOLID principles.

