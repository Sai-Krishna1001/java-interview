# Java 8 Interview Questions and Answers

## 1. What are the key features of Java 8?
Java 8 introduced several new features, including:
- **Lambda Expressions** – Enables functional programming.
- **Functional Interfaces** – Introduces interfaces with a single abstract method.
- **Streams API** – Facilitates bulk operations on collections.
- **Optional Class** – Reduces `NullPointerException` occurrences.
- **Default and Static Methods in Interfaces** – Supports method implementations in interfaces.
- **New Date and Time API** – Provides a modern date-time handling mechanism.
- **Collectors** – Helps in collecting stream elements efficiently.
- **CompletableFuture** – Enables asynchronous programming.

### Hidden Rules & Facts:
- Lambdas and method references are implemented using invokedynamic at runtime.
- Streams do not store elements; they process them on demand (lazy evaluation).
- The default methods in interfaces do not affect implementing classes unless explicitly overridden.
- Java 8 removed the **Permanent Generation (PermGen)** space and replaced it with **Metaspace** to improve memory management.

## 2. What are Functional Interfaces in Java 8?
A Functional Interface is an interface with a single abstract method (SAM). Java 8 provides built-in functional interfaces such as `Predicate`, `Consumer`, `Function`, and `Supplier`.

### Key Points:
- Functional interfaces can have multiple default and static methods but only one abstract method.
- The `@FunctionalInterface` annotation is optional but recommended.

## 3. What is the purpose of the Streams API in Java 8?
The Streams API allows functional-style operations on collections, enabling operations like filtering, mapping, and reducing data efficiently.

### Limits & Facts:
- Streams do not modify the original data source; they generate new streams.
- Operations on streams are either **intermediate (lazy)** or **terminal (eager)**.

## 4. What is Optional in Java 8?
`Optional` is a container object used to represent nullable values. It helps avoid `NullPointerException` and promotes safer code by providing methods to handle absence of values.

### Important Key Points:
- Use `orElseGet()` instead of `orElse()` to avoid unnecessary object creation.
- `Optional` should not be used as method parameters; use it only for return types.

## 5. What is the difference between `map()` and `flatMap()` in Java 8?
- `map()` applies a function to each element and returns a stream of the results.
- `flatMap()` applies a function and flattens the resulting streams into a single stream.

## 6. What are default and static methods in interfaces?
- **Default Methods** – Allow interfaces to provide method implementations, ensuring backward compatibility.
- **Static Methods** – Define utility methods in interfaces without requiring instantiation.

### Limits:
- Default methods cannot override `Object` class methods like `equals()`, `hashCode()`, and `toString()`.
- Static methods in interfaces cannot access instance variables of implementing classes.

## 7. What is the new Date and Time API in Java 8?
Java 8 introduced `java.time` package, which includes classes like `LocalDate`, `LocalTime`, `LocalDateTime`, `ZonedDateTime`, and `Duration` for better date-time handling.

## 8. How does `forEach` work in Java 8?
The `forEach` method is used to iterate over collections using lambda expressions, making code more readable and concise.

### Hidden Fact:
- `forEach()` does not guarantee order in parallel streams. Use `forEachOrdered()` if ordering is required.

## 9. What is the significance of Collectors in Java 8?
Collectors are used to accumulate elements from a stream into a collection, string, or other representations, supporting operations like grouping and joining.

### Important Fact:
- `Collectors.toList()` may return an unmodifiable list depending on the implementation.

## 10. What is the purpose of `CompletableFuture` in Java 8?
`CompletableFuture` is used for asynchronous programming, allowing tasks to be executed in parallel without blocking the main thread.

### Limits & Key Points:
- Unlike `Future`, `CompletableFuture` allows multiple dependent computations.
- Be cautious of deadlocks when combining multiple async tasks.

## 11. What is the advantage of using method references in Java 8?
Method references simplify lambda expressions by referring to existing methods, improving code readability and reusability.

## 12. What are Predicate, Consumer, Function, and Supplier in Java 8?
- **Predicate** – Represents a boolean-valued function.
- **Consumer** – Represents an operation that takes a single input and returns no result.
- **Function** – Represents a function that takes one argument and produces a result.
- **Supplier** – Represents a supplier of results without input parameters.

### Hidden Rules:
- `Predicate` can be chained using `and()`, `or()`, and `negate()`.
- `Function` can be composed using `compose()` and `andThen()`.

## 13. What is the difference between `findFirst()` and `findAny()`?
- `findFirst()` returns the first element in the stream.
- `findAny()` returns any element, optimized for parallel streams.

## 14. How does Java 8 improve memory management?
Java 8 optimizes memory usage by introducing features like:
- **Metaspace** – Eliminates the memory constraints of the old `PermGen`.
- **StringJoiner** – Efficient string concatenation without creating multiple String objects.
- **Compact Strings** – Uses byte arrays instead of char arrays in certain cases.

## 15. How does Java 8 support backward compatibility?
By introducing default methods in interfaces, Java 8 allows older interfaces to be extended without breaking existing implementations.

