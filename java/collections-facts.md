### Hidden Facts of Java Collections

1. **ArrayList’s Default Capacity Growth**  
   - When an `ArrayList` exceeds its current capacity, it increases by **50%** of its size (`newCapacity = oldCapacity + (oldCapacity >> 1)`).  
   - Example: Initial capacity 10 → Grows to 15 → 22 → 33, and so on.

2. **HashMap’s Load Factor & Resize Mechanism**  
   - Default load factor = **0.75** (i.e., rehashing occurs when 75% of capacity is filled).  
   - Initial capacity = 16 → Grows to 32 → 64, etc., doubling each time.  
   - Uses **linked list before Java 8**, **balanced tree (Red-Black) from Java 8+** for better performance.

3. **LinkedHashMap Maintains Insertion Order**  
   - Unlike `HashMap`, `LinkedHashMap` maintains **insertion order** using a doubly linked list.

4. **TreeMap Uses Red-Black Tree**  
   - Implements `NavigableMap`, sorts keys in **natural order** (or via `Comparator`).  
   - Average time complexity for insert/search/delete = **O(log n)**.

5. **ConcurrentHashMap Uses Segments (Before Java 8)**  
   - Prior to Java 8, it divided the map into **segments** for better concurrency.  
   - From Java 8 onwards, it uses **fine-grained locks** (CAS operations) instead of segments.

6. **Vector & Stack Are Legacy Synchronized Classes**  
   - `Vector` is similar to `ArrayList` but **synchronized**.  
   - `Stack` extends `Vector` but is rarely used in favor of `Deque`.

7. **CopyOnWriteArrayList for Thread-Safety**  
   - All modification operations (add, remove, etc.) create a **new copy** of the array.  
   - Best for **read-heavy** operations (e.g., caching use cases).

8. **PriorityQueue Doesn't Guarantee Sorted Order**  
   - Implements a **min-heap** (by default), so only the **head** is the smallest.  
   - The entire queue is **not** fully sorted.

9. **HashSet Internally Uses HashMap**  
   - `HashSet` is backed by a `HashMap`, storing values as **keys** and a dummy `Boolean.TRUE` as **value**.

10. **EnumSet Is More Efficient Than HashSet**  
   - `EnumSet` is implemented using **bitwise operations**, making it much faster than `HashSet`.

