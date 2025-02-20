# Java Core Concepts:

## 1. Java Components Overview
### Key Components for Compiling and Running Java Programs:
- **Java Development Kit (JDK):** Includes Java Runtime Environment (JRE) and essential tools like the Java compiler and Java command.
- **Java Runtime Environment (JRE):** Contains libraries and JVM necessary to run Java applications.
- **Java Virtual Machine (JVM):** Executes bytecode and ensures platform independence.
- **Just-In-Time (JIT) Compiler:** Optimizes bytecode translation for better performance.
- **Bytecode:** Compiled Java code, interpreted by JVM, making Java platform-independent.

### Execution Flow:
1. Java code is compiled into bytecode using the Java compiler.
2. The JVM interprets bytecode and translates it into machine code for the OS.
3. The JIT compiler optimizes bytecode execution.

## 2. Constructors in Java
### Definition and Characteristics:
- A **constructor** initializes object properties when an instance is created.
- It has the **same name as the class**.
- Unlike regular methods, constructors execute **only once at object creation**.

### Key Features:
- **Constructor Overloading:** Multiple constructors with different parameters.
- **Calling Another Constructor:** Use `this()` within the same class.
- **Calling Superclass Constructor:** Use `super()` to invoke the parent class constructor.

## 3. Abstract Class vs Interface
### Abstract Class:
- Can contain both **abstract methods (without body)** and **concrete methods**.
- Requires `abstract` keyword.
- A class can extend **only one** abstract class.

### Interface:
- Contains **only abstract methods** (before Java 8).
- A class can **implement multiple interfaces**.
- Uses `interface` keyword, and methods are implicitly `public abstract`.

## 4. Why Multiple Inheritance is Not Supported in Java
- If a class extends **two parent classes** with the same method, ambiguity arises.
- Leads to **diamond problem** (if a common ancestor has the same method).
- Java prevents multiple inheritance to avoid confusion and inconsistency.

## 5. Implementing Multiple Interfaces with the Same Method
- A class **can implement multiple interfaces** even if they have the same method signature.
- No ambiguity since the implementing class **provides its own method implementation**.
- Unlike multiple inheritance in classes, this does not lead to the **diamond problem**.

### Example:
```java
interface Car { void go(); }
interface Driverless { void go(); }
class Honda implements Car, Driverless {
    public void go() { System.out.println("Honda is moving"); }
}
```

### 6. Object Class Methods
Every class in Java inherits methods from the `Object` class. The key methods include:
- `equals()`
- `hashCode()`
- `finalize()`
- `clone()`
- `toString()`
- `wait()`, `notify()`, `notifyAll()` (used in multithreading, cannot be overridden)
- The first five methods can be overridden to provide custom implementations.

---

### 7. Default `hashCode()` Implementation
- If a class does not override `hashCode()`, it returns a number that represents the memory location of the object.
- Custom implementations of `hashCode()` help maintain object uniqueness in hash-based collections.

---

### 8. Default `toString()` Implementation
- If `toString()` is not overridden, it returns a string in the format:
  ```java
  ClassName@HexadecimalMemoryAddress
  ```
- Overriding `toString()` allows customization of object representation.

---

### 9. `equals()` Method vs `==` Operator
- `==` compares **memory references** (shallow comparison).
- `equals()` by default also compares references but can be overridden for **content-based comparison** (deep comparison).
- By default, `equals()` does a reference check (`==`) in `Object` class.
- `String`, primitive, wrapper classes (`Integer`, `Double`, etc.), and `Enum` override `equals()` to compare actual values instead of memory locations.
- For custom classes, we must override `equals()` to ensure deep comparison.
- Example:
  ```java
  String s1 = new String("ABC");
  String s2 = new String("ABC");
  System.out.println(s1 == s2);       // false (different memory locations)
  System.out.println(s1.equals(s2));  // true (content is same)
  ```

---

### 10. `final`, `finally`, and `finalize()`
| Keyword     | Purpose |
|------------|---------|
| `final`    | Prevents modification (variables), inheritance (classes), and overriding (methods). |
| `finally`  | Used in exception handling; always executes after `try-catch` blocks. |
| `finalize()` | Called by the JVM garbage collector before reclaiming an object (not reliable for resource cleanup). |
- Example of `finally` usage:
  ```java
  try {
      int x = 5 / 0;
  } catch (ArithmeticException e) {
      System.out.println("Exception caught");
  } finally {
      System.out.println("Finally block executed");
  }
  ```

---

### 11. Generics and Type Erasure
- Before Java 5, collections did not enforce type safety.
- Generics allow specifying data types at compile time.
- Example:
  ```java
  List<Integer> numbers = new ArrayList<>();
  numbers.add(10);  // Allowed
  numbers.add("text");  // Compile-time error
  ```
- **Type Erasure**: Generics exist only at compile time; type information is removed to maintain backward compatibility with older Java versions.



