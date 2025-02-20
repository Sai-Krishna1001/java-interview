# Spring Framework Interview Questions and Answers

## 1. What is the Spring Framework and what are its core features?
**Answer:**  
Spring is a **lightweight, modular** Java framework for building enterprise applications. It simplifies **Java EE** development with features like **dependency injection (DI)** and **aspect-oriented programming (AOP)**.

### **Core Features:**
1. **Spring Core** – Provides **IoC (Inversion of Control)** and **DI (Dependency Injection)**.  
2. **Spring AOP** – Enables **aspect-oriented programming** (logging, security).  
3. **Spring MVC** – Framework for **building web applications**.  
4. **Spring Security** – Handles **authentication & authorization**.  
5. **Spring Data JPA** – Simplifies **database access**.  
6. **Spring Boot** – Auto-configuration and **microservices support**.  
7. **Spring Cloud** – Provides **distributed system support** (Eureka, Hystrix).  

## 2. How do you create a simple Spring application?
**Answer:**  
To create a simple **Spring application**, follow these steps:

### **Step 1: Add Dependencies (Spring Boot)**
Use **Spring Boot** to simplify setup by adding dependencies in `pom.xml` (Maven):
```xml
<dependencies>
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter</artifactId>
    </dependency>
</dependencies>
```

### **Step 2: Create a Main Class**
```java
import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

@SpringBootApplication
public class MySpringApp {
    public static void main(String[] args) {
        SpringApplication.run(MySpringApp.class, args);
    }
}
```

### **Step 3: Create a Simple REST Controller**
```java
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
@RequestMapping("/api")
public class MyController {
    @GetMapping("/hello")
    public String sayHello() {
        return "Hello, Spring!";
    }
}
```

### **Step 4: Run the Application**
Run the main class, and access `http://localhost:8080/api/hello` to see the output.

## 3. What is Inversion of Control (IoC)? How does Spring facilitate IoC?
**Answer:**  
**Inversion of Control (IoC)** is a design principle where the control of object creation and dependency management is transferred from the programmer to the framework.

### **How Spring Facilitates IoC?**
Spring implements IoC through **Dependency Injection (DI)**, which allows objects to define their dependencies without creating them manually.

### **Types of Dependency Injection in Spring:**
1. **Constructor Injection**  
2. **Setter Injection**  
3. **Field Injection (via @Autowired annotation)**  

### **Example of Constructor Injection:**
```java
import org.springframework.stereotype.Component;
import org.springframework.beans.factory.annotation.Autowired;

@Component
class Service {
    public void serve() {
        System.out.println("Service is running");
    }
}

@Component
class Client {
    private final Service service;
    
    @Autowired
    public Client(Service service) {
        this.service = service;
    }
    
    public void perform() {
        service.serve();
    }
}
```
In this example, Spring **injects the `Service` dependency into `Client`** automatically.

## 4. What is the ApplicationContext in Spring?
**Answer:**  
The **ApplicationContext** is the central **IoC container** in Spring. It is responsible for managing beans, dependency injection, and lifecycle management.

### **Features of ApplicationContext:**
1. **Bean Factory** – Manages bean creation and lifecycle.  
2. **Message Source** – Supports internationalization.  
3. **Event Propagation** – Allows event-based communication between beans.  
4. **Resource Loading** – Provides access to files and classpath resources.  
5. **ApplicationEventPublisher** – Publishes events within the application.

### **Example Usage of ApplicationContext:**
```java
import org.springframework.context.ApplicationContext;
import org.springframework.context.annotation.AnnotationConfigApplicationContext;
import org.springframework.stereotype.Component;

@Component
class ExampleService {
    public void execute() {
        System.out.println("Executing service logic");
    }
}

public class MainApp {
    public static void main(String[] args) {
        ApplicationContext context = new AnnotationConfigApplicationContext(AppConfig.class);
        ExampleService service = context.getBean(ExampleService.class);
        service.execute();
    }
}
```

## 5. Explain Dependency Injection and its types in the Spring context.
**Answer:**  
**Dependency Injection (DI)** is a design pattern in which Spring **injects dependencies** into objects instead of creating them manually. DI improves code **loosely coupled**, **testable**, and **maintainable**.

### **Types of Dependency Injection in Spring:**
1. **Constructor Injection** – Dependencies are passed through the constructor.
2. **Setter Injection** – Dependencies are set using setter methods.
3. **Field Injection** – Dependencies are injected directly into fields using `@Autowired`.

### **Example of Constructor Injection:**
```java
import org.springframework.stereotype.Component;
import org.springframework.beans.factory.annotation.Autowired;

@Component
class Engine {
    public void start() {
        System.out.println("Engine started");
    }
}

@Component
class Car {
    private final Engine engine;
    
    @Autowired
    public Car(Engine engine) {
        this.engine = engine;
    }
    
    public void drive() {
        engine.start();
        System.out.println("Car is moving");
    }
}
```

## 6. What are Bean Scopes in Spring? Name them.
**Answer:**  
Bean scope defines the **lifecycle and visibility** of a bean in the Spring container.

### **Types of Bean Scopes in Spring:**
1. **Singleton** – A single instance per Spring container (default scope).  
2. **Prototype** – A new instance is created every time it is requested.  
3. **Request** – A new instance is created for each HTTP request (only in web applications).  
4. **Session** – A new instance is created for each HTTP session (only in web applications).  
5. **Application** – A single instance is shared across the entire web application.  

### **Example of Singleton and Prototype Scopes:**
```java
import org.springframework.context.annotation.Scope;
import org.springframework.stereotype.Component;

@Component
@Scope("singleton")
class SingletonBean {
    // Single instance across the application
}

@Component
@Scope("prototype")
class PrototypeBean {
    // New instance every time
}
```
By default, all beans are **Singleton** in Spring.

### 7. How do you configure a bean in Spring?
In Spring, a bean is an object managed by the Spring IoC (Inversion of Control) container. There are three main ways to configure a bean:

1. **XML Configuration:**
   - Beans can be defined in an XML configuration file using the `<bean>` tag.
   ```xml
   <bean id="myBean" class="com.example.MyBean"/>
   ```

2. **Java-based Configuration:**
   - Beans can be configured using Java classes with `@Configuration` and `@Bean` annotations.
   ```java
   @Configuration
   public class AppConfig {
       @Bean
       public MyBean myBean() {
           return new MyBean();
       }
   }
   ```

3. **Annotation-based Configuration:**
   - Using annotations like `@Component`, `@Service`, `@Repository`, and `@Controller` along with `@ComponentScan` to automatically detect beans.
   ```java
   @Component
   public class MyBean {
   }
   ```

### 8. Describe the role of the Spring Core container.
The Spring Core container is responsible for managing the lifecycle and dependencies of beans. It is built on the principles of Dependency Injection (DI) and Inversion of Control (IoC). The core container consists of several modules:

- **BeanFactory:** The simplest container that provides basic dependency injection.
- **ApplicationContext:** A more advanced container with additional features like event propagation, declarative mechanisms, and integration with AOP.
- **Context Modules:** Support for internationalization, event propagation, and resource loading.

The core container ensures that dependencies are resolved and managed efficiently, promoting a loosely coupled architecture.

### 9. What is a Spring configuration file?
A Spring configuration file is an XML or Java-based file that provides metadata for configuring the Spring container. It defines beans, their dependencies, and application-specific settings.

- **XML-based Configuration:**
  ```xml
  <beans xmlns="http://www.springframework.org/schema/beans"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://www.springframework.org/schema/beans
         http://www.springframework.org/schema/beans/spring-beans.xsd">
      <bean id="myBean" class="com.example.MyBean"/>
  </beans>
  ```

- **Java-based Configuration:**
  ```java
  @Configuration
  public class AppConfig {
      @Bean
      public MyBean myBean() {
          return new MyBean();
      }
  }
  ```

### 10. How do you create an ApplicationContext in a Spring application?
The `ApplicationContext` is the central interface for accessing Spring container functionalities. It can be created in multiple ways:

1. **Using ClassPathXmlApplicationContext (XML-based Configuration):**
   ```java
   ApplicationContext context = new ClassPathXmlApplicationContext("applicationContext.xml");
   MyBean myBean = context.getBean(MyBean.class);
   ```

2. **Using AnnotationConfigApplicationContext (Java-based Configuration):**
   ```java
   ApplicationContext context = new AnnotationConfigApplicationContext(AppConfig.class);
   MyBean myBean = context.getBean(MyBean.class);
   ```

3. **Using FileSystemXmlApplicationContext:**
   ```java
   ApplicationContext context = new FileSystemXmlApplicationContext("C:/config/applicationContext.xml");
   ```

These approaches allow Spring to manage and inject dependencies dynamically, ensuring flexibility and modularity in applications.



