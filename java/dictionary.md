# Java Basic Terminology for Revision

## A - C

### Abstract Class
A class that **cannot be instantiated** and may have both abstract and concrete methods.

### Abstraction
Hiding implementation details and exposing only the functionality.

### Access Modifiers
Control the visibility of classes, methods, and variables (`private`, `protected`, `public`, default).

### Autoboxing
Automatic conversion of primitive types into their wrapper classes (`int` → `Integer`).

### Checked Exception
Exceptions that must be handled using `try-catch` or `throws` in the method signature.

### ClassLoader
A part of JVM that loads `.class` files into memory.

### Constructor
A special method that initializes objects. It has the same name as the class.

### Compile-Time Polymorphism
Method overloading where multiple methods have the same name but different parameters.

## D - F

### Default Constructor
A constructor with no parameters, automatically provided if no constructor is defined.

### Deep Copy
A cloning process where all objects are **fully copied**, not just references.

### Dependency Injection (DI)
A design pattern where dependencies are injected rather than created inside a class.

### Encapsulation
Wrapping data (fields) and methods into a single unit (class) with controlled access.

### Enum
A special class used to define constants (`enum Days {MON, TUE, WED}`).

### Exception Propagation
The process of passing an exception up the call stack if not handled.

### Factory Pattern
A design pattern that provides a method to create objects without specifying their exact class.

## G - I

### Garbage Collection
Automatic memory management that removes unused objects.

### Generics
A feature that allows writing **type-safe** and reusable code (`List<String>` instead of `List<Object>`).

### HashCode
A method that returns an integer representing an object’s memory address for fast lookups.

### Heap Memory
A runtime memory area where objects are allocated.

### Immutable Class
A class whose objects **cannot be modified** after creation (e.g., `String`).

### Instance Variable
A variable defined inside a class but outside any method, unique to each object.

### Interface
A blueprint for a class with only **abstract methods** (before Java 8) and **default/static methods** (after Java 8).

## J - M

### JIT Compiler
Converts bytecode into native machine code for faster execution.

### JVM (Java Virtual Machine)
A runtime environment that executes Java bytecode.

### Lambda Expression
A concise way to represent anonymous functions (`(a, b) -> a + b`).

### Lazy Initialization
Deferring object creation until it’s needed to improve performance.

### Local Variable
A variable declared within a method or block, accessible only within that scope.

### Marker Interface
An empty interface (like `Serializable`) used to signal metadata to the JVM.

### Method Overloading
Defining multiple methods with the **same name but different parameters** in the same class.

### Method Overriding
Redefining a method from the parent class in a subclass to change its behavior.

## N - P

### Native Method
A method implemented in **C or C++** using the `native` keyword.

### NullPointerException (NPE)
A runtime error that occurs when trying to access an object reference that is `null`.

### Object Pooling
Reusing objects instead of creating new ones to improve performance (e.g., `Integer.valueOf()`).

### Optional
A wrapper class introduced in Java 8 to **avoid null checks** (`Optional.ofNullable(obj)`).

### Polymorphism
The ability of an object to take **multiple forms** (method overriding and method overloading).

### Primitive Type
Basic data types (`int`, `char`, `boolean`) that are **not objects**.

## Q - S

### Reflection
A mechanism to **inspect and modify** a class at runtime.

### Serialization
The process of converting an object into a byte stream to **save or transfer** it.

### Shallow Copy
A cloning process where only object references are copied, not the actual data.

### Singleton Pattern
A design pattern ensuring that **only one instance** of a class exists.

### Stack Memory
Memory used for storing **method calls and local variables**.

### Static Keyword
Used to define class-level fields or methods that belong to the class, not instances.

### Stream API
A Java 8 feature that allows functional-style operations on collections (`list.stream().map(x -> x * 2)`).

### Strictfp
A keyword that ensures floating-point calculations are consistent across platforms.

## T - Z

### Ternary Operator
A shorthand for `if-else` (`condition ? value1 : value2`).

### Thread Safety
Ensuring that multiple threads do not cause inconsistent data (`synchronized` helps achieve this).

### Transient Keyword
Prevents a field from being **serialized**.

### Try-With-Resources
A Java 7 feature that automatically closes resources (`try (BufferedReader br = new BufferedReader(...))`).

### Unchecked Exception
Exceptions **not checked** at compile-time (e.g., `NullPointerException`).

### Volatile Keyword
Ensures visibility of variable changes across threads but does **not** guarantee atomicity.

### WeakReference
A reference that **does not prevent garbage collection** (`WeakReference<MyObject> ref = new WeakReference<>(obj)`).

