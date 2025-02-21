# Spring Boot Notes

## 1) Dependency Injection and IoC

### What is Dependency Injection and Inversion of Control (IoC)?
- In software applications, we organize code into components (classes in Java).
- Example:
  - `ProductDao` class handles database operations.
  - `ProductController` (Web layer) uses `ProductDao`.
- Instead of creating `ProductDao` inside `ProductController`, Spring dynamically creates and injects it.
- **Dependency Injection**: External components/modules create dependencies and inject them into required classes.
- **Inversion of Control (IoC)**:
  - Control of object creation is shifted from application code to an external framework (Spring).
  - A design pattern where object creation control is inverted.

---

## 2) Spring Bean Scopes

### Types of Bean Scopes
1. **Singleton** (Default)
   - Only one instance of the bean exists for the entire IoC container.
   - The same instance is injected wherever required.
2. **Prototype**
   - Multiple instances of the bean are created and injected as needed.

### Choosing Between Singleton and Prototype
- Use **Singleton** for stateless components (e.g., Controllers, DAOs).
- Use **Prototype** for stateful components to prevent data corruption across multiple threads.

---

## 3) Prototype in Singleton
- A **Prototype** bean can be injected into a **Singleton** bean.
- Once injected at runtime, the same instance of the prototype bean is used within the singleton bean.

---

## 4) HTTP Scopes
### Types of Spring Bean HTTP Context Scopes
1. **Request Scope**: A new bean instance is created for every HTTP request.
2. **Session Scope**: A single bean instance is used throughout a session (multiple requests/responses).
3. **Global Session Scope**: Applies when using portlets, sharing the same bean instance across portlets.

---

## 5) Problems with Traditional Spring
### Issues Faced Before Spring Boot
- Traditional Spring required extensive XML or Java-based configuration.
- Dependency management in `pom.xml` or `gradle.build` was complex.
- Ensuring compatibility between different Spring modules (Core, MVC, DAO, ORM) was challenging.
- Manual deployment to external servers (Tomcat, WebLogic, WebSphere) was required.

---

## 6) Why Use Spring Boot?
### Advantages of Spring Boot
1. **Auto Configuration**
   - Eliminates XML/Java-based configurations.
   - Automatically configures Dispatcher Servlet, Data Source, and Transaction Manager.
2. **Dependency Management**
   - Spring Boot Starters simplify adding dependencies.
   - Ensures version compatibility via a parent project.
3. **Embedded Server Support**
   - Comes with embedded **Tomcat**, **Jetty**, or **Undertow**.
   - Simplifies deployment (Run as Spring Boot Application).
4. **Spring Boot Actuators**
   - Provides health checks and application monitoring.
   - Displays auto-configuration details, mappings, and metrics.

---

## 7) `@SpringBootApplication`
### Role of `@SpringBootApplication`
- Marks the main class as the entry point for Spring Boot.
- Combines three annotations:
  1. `@SpringBootConfiguration`: Allows defining bean methods.
  2. `@EnableAutoConfiguration`: Enables auto-configuration based on classpath dependencies.
  3. `@ComponentScan`: Scans the current package and sub-packages for components (`@Component`, `@Service`, `@Repository`).

---

## 8) `@SpringBootTest`
### Purpose of `@SpringBootTest`
- Uses **Spring Extension Class** to run tests instead of standard JUnit Runner.
- Searches for a class annotated with `@SpringBootApplication` to load the Spring context.
- Ensures all dependencies and beans are available before running tests.

