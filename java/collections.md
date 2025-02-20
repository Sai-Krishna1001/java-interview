# Java Collections - Interview Questions & Explanations

## 1) What are the Different Collection Types?

Java Collections Framework provides various interfaces and classes for handling collections of objects efficiently. The primary collection types include:

- **List**: Ordered collection that allows duplicates.
  - Implementations: `ArrayList`, `LinkedList`
- **Set**: Unordered collection that does not allow duplicates.
  - Implementations: `HashSet`, `LinkedHashSet`, `TreeSet`
- **Queue**: FIFO (First-In-First-Out) structure for elements.
  - Implementations: `PriorityQueue`
- **BlockingQueue**: Special queue designed for concurrent processing (useful in Producer-Consumer patterns).
- **Map**: Stores data as key-value pairs.
  - Implementations: `HashMap`, `LinkedHashMap`, `TreeMap` (sorted map)

## 2) ArrayList vs LinkedList

| Feature          | ArrayList | LinkedList |
|-----------------|-----------|------------|
| Internal Structure | Uses a dynamic array | Uses a doubly linked list |
| Element Access | Fast (O(1) for index-based access) | Slow (O(n) as traversal is needed) |
| Insertion/Deletion | Expensive (O(n) due to shifting) | Efficient (O(1) if pointer manipulation is done) |
| Best Use Case | Read-heavy applications | Insert/delete-heavy applications |

## 3) Vector vs ArrayList

- `Vector` and `ArrayList` both use a dynamic array but **Vector is synchronized**, meaning it is thread-safe but slower.
- `ArrayList` is not synchronized and provides better performance in single-threaded environments.

## 4) HashMap vs LinkedHashMap

- `HashMap` does **not** maintain the insertion order of elements.
- `LinkedHashMap` maintains insertion order using a **doubly-linked list**.

## 5) How to Create a Generic Class in Java?

To create a generic class:

```java
class Box<T> {
    private T item;
    public void setItem(T item) { this.item = item; }
    public T getItem() { return item; }
}

Box<String> stringBox = new Box<>();
stringBox.setItem("Hello");
System.out.println(stringBox.getItem());
```

- `<T>` denotes a generic type parameter that can be replaced with actual types like `String`, `Integer`, etc.
- Generics provide **type safety** and eliminate the need for type casting.

## 6) Fail-Fast vs Fail-Safe Iterators

| Feature | Fail-Fast Iterator | Fail-Safe Iterator |
|---------|------------------|------------------|
| Behavior | Throws `ConcurrentModificationException` if modified during iteration | Allows modification during iteration |
| Example Collections | `ArrayList`, `HashSet`, `HashMap` | `CopyOnWriteArrayList`, `ConcurrentHashMap` |
| Working Mechanism | Directly accesses the collection | Works on a cloned copy of the collection |

## 7) Producer-Consumer Pattern

- `BlockingQueue` is the best choice for implementing the **Producer-Consumer pattern**.
- It provides:
  - `put()` - Adds an item, blocking if the queue is full.
  - `take()` - Removes an item, blocking if the queue is empty.

Example:

```java
BlockingQueue<Integer> queue = new ArrayBlockingQueue<>(5);

// Producer
new Thread(() -> {
    try { queue.put(1); } catch (InterruptedException e) {}
}).start();

// Consumer
new Thread(() -> {
    try { queue.take(); } catch (InterruptedException e) {}
}).start();
```

## 8) Comparable vs Comparator

| Feature | Comparable | Comparator |
|---------|------------|------------|
| Package | `java.lang` | `java.util` |
| Implementation | Implemented within the class itself (`compareTo` method) | Implemented externally (`compare` method) |
| Sorting Order | Defines **natural ordering** | Allows multiple custom sorting orders |
| Example Usage | `Collections.sort(list)` | `Collections.sort(list, new ComparatorClass())` |

Example:

```java
class Student implements Comparable<Student> {
    int age;
    public int compareTo(Student s) { return this.age - s.age; }
}

class AgeComparator implements Comparator<Student> {
    public int compare(Student s1, Student s2) { return s2.age - s1.age; }
}
```

## 9) What are Concurrent Collections?

- **Traditional collections (`ArrayList`, `HashMap`)** are not thread-safe.
- **Concurrent collections (`ConcurrentHashMap`, `CopyOnWriteArrayList`)** provide:
  - Thread safety without blocking the entire collection.
  - Fail-safe iterators that allow modifications during iteration.

Example of `ConcurrentHashMap`:

```java
ConcurrentHashMap<Integer, String> map = new ConcurrentHashMap<>();
map.put(1, "A");
map.put(2, "B");
```

### Key Takeaways:
- Use `ArrayList` for **fast access** and `LinkedList` for **frequent insertions/deletions**.
- Prefer `ConcurrentHashMap` over `synchronized HashMap` for **multi-threaded environments**.
- `BlockingQueue` simplifies **Producer-Consumer pattern** implementation.
- `Comparable` defines **natural sorting**, while `Comparator` provides **custom sorting**.
