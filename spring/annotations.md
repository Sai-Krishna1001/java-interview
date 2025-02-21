# **🔥 Java & Spring Boot Annotations List with Definitions 🔥**

## **1️⃣ Core Java Annotations**
| Annotation        | Definition |
|------------------|------------|
| `@Override` | Indicates that a method is overriding a superclass method. |
| `@Deprecated` | Marks a method, class, or field as deprecated (discouraged for use). |
| `@SuppressWarnings` | Suppresses compiler warnings for a specific code block. |
| `@FunctionalInterface` | Ensures that an interface has only one abstract method (for lambda expressions). |
| `@SafeVarargs` | Suppresses warnings for using varargs with generics. |
| `@Retention` | Specifies how long the annotation is retained (SOURCE, CLASS, or RUNTIME). |
| `@Target` | Defines where the annotation can be applied (METHOD, FIELD, CLASS, etc.). |

---

## **2️⃣ Spring Boot Core Annotations**
| Annotation        | Definition |
|------------------|------------|
| `@SpringBootApplication` | Main entry point of a Spring Boot application (combines `@Configuration`, `@EnableAutoConfiguration`, and `@ComponentScan`). |
| `@Component` | Generic annotation to register a class as a Spring bean. |
| `@Service` | Specialized version of `@Component`, used for service layer classes. |
| `@Repository` | Specialized version of `@Component`, used for DAO (Data Access Object) classes. |
| `@Bean` | Declares a Spring bean inside a `@Configuration` class. |
| `@Configuration` | Indicates that a class contains bean definitions for the application context. |
| `@ComponentScan` | Specifies the packages to scan for Spring beans. |
| `@Lazy` | Delays bean initialization until it is actually needed. |

---

## **3️⃣ Dependency Injection Annotations**
| Annotation        | Definition |
|------------------|------------|
| `@Autowired` | Automatically injects a bean by type. |
| `@Qualifier` | Specifies which bean should be injected when multiple beans of the same type exist. |
| `@Primary` | Specifies a default bean to be used when multiple beans of the same type exist. |
| `@Value` | Injects values from properties files or environment variables. |
| `@Scope` | Defines the scope of a bean (`singleton`, `prototype`, etc.). |

---

## **4️⃣ REST API Annotations**
| Annotation        | Definition |
|------------------|------------|
| `@RestController` | Combines `@Controller` and `@ResponseBody` to handle REST requests. |
| `@RequestMapping` | Maps a URL to a controller method (GET, POST, PUT, DELETE). |
| `@GetMapping` | Maps HTTP GET requests to a method. |
| `@PostMapping` | Maps HTTP POST requests to a method. |
| `@PutMapping` | Maps HTTP PUT requests to a method. |
| `@DeleteMapping` | Maps HTTP DELETE requests to a method. |
| `@PatchMapping` | Maps HTTP PATCH requests to a method. |
| `@RequestBody` | Maps the body of an HTTP request to a Java object. |
| `@RequestParam` | Maps query parameters from a URL. |
| `@PathVariable` | Maps URL path variables to method parameters. |
| `@ResponseBody` | Converts Java objects into JSON responses. |
| `@ResponseStatus` | Sets the HTTP status for a response. |

---

## **5️⃣ Exception Handling Annotations**
| Annotation        | Definition |
|------------------|------------|
| `@ExceptionHandler` | Defines a method to handle specific exceptions in a controller. |
| `@ControllerAdvice` | Defines global exception handling across multiple controllers. |
| `@ResponseStatus` | Specifies the HTTP status to return when an exception is thrown. |

---

## **6️⃣ Transaction Management Annotations**
| Annotation        | Definition |
|------------------|------------|
| `@Transactional` | Defines a method or class as transactional (ensures atomicity). |
| `@EnableTransactionManagement` | Enables transaction management in a Spring Boot application. |

---

## **7️⃣ Spring Security Annotations**
| Annotation        | Definition |
|------------------|------------|
| `@EnableWebSecurity` | Enables Spring Security configuration. |
| `@PreAuthorize` | Specifies security constraints before executing a method. |
| `@PostAuthorize` | Specifies security constraints after executing a method. |
| `@RolesAllowed` | Restricts access to users with specific roles. |
| `@Secured` | Specifies security constraints based on roles. |

---

## **8️⃣ Scheduling Annotations**
| Annotation        | Definition |
|------------------|------------|
| `@EnableScheduling` | Enables scheduling support in Spring Boot. |
| `@Scheduled` | Schedules a method to run at fixed intervals. |

---

## **9️⃣ Spring Boot Caching Annotations**
| Annotation        | Definition |
|------------------|------------|
| `@EnableCaching` | Enables caching in a Spring Boot application. |
| `@Cacheable` | Caches the result of a method call. |
| `@CachePut` | Updates a cached entry with a new value. |
| `@CacheEvict` | Removes entries from the cache. |

---

## **🔟 Testing Annotations**
| Annotation        | Definition |
|------------------|------------|
| `@SpringBootTest` | Loads the full application context for integration testing. |
| `@WebMvcTest` | Loads only the web layer (for testing controllers). |
| `@MockBean` | Mocks a Spring bean in tests. |
| `@DataJpaTest` | Configures an in-memory database for testing JPA repositories. |

---

## **1️⃣1️⃣ Actuator & Monitoring Annotations**
| Annotation        | Definition |
|------------------|------------|
| `@EnableActuatorEndpoints` | Enables Spring Boot Actuator endpoints. |
| `@Endpoint` | Creates a custom Actuator endpoint. |

---

## **1️⃣2️⃣ Custom Annotation Example**
### **Step 1: Define the Annotation**
```java
import java.lang.annotation.*;

@Retention(RetentionPolicy.RUNTIME)
@Target(ElementType.METHOD)
public @interface LogExecutionTime { }
```

### **Step 2: Implement Annotation Using AOP**
```java
@Aspect
@Component
public class LoggingAspect {
    @Around("@annotation(com.example.LogExecutionTime)")
    public Object logExecutionTime(ProceedingJoinPoint joinPoint) throws Throwable {
        long start = System.currentTimeMillis();
        Object result = joinPoint.proceed();
        long executionTime = System.currentTimeMillis() - start;
        System.out.println(joinPoint.getSignature() + " executed in " + executionTime + "ms");
        return result;
    }
}
```

### **Step 3: Use the Custom Annotation**
```java
@Service
public class OrderService {
    @LogExecutionTime
    public void placeOrder() {
        System.out.println("Order placed!");
    }
}
```


