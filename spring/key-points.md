# Spring Boot - Important One-Liners for Interview

## **1️⃣ Spring Boot Basics**
- `@SpringBootApplication` = `@Configuration` + `@EnableAutoConfiguration` + `@ComponentScan`.
- **Auto-Configuration** eliminates manual configuration using `spring-boot-starter` dependencies.
- **Embedded Servers** (Tomcat, Jetty, Undertow) allow standalone applications.
- **Spring Boot Profiles** enable environment-specific configurations (`application-{profile}.properties`).
- **Spring Boot Actuator** provides built-in health checks, metrics, and monitoring endpoints.
- **Spring Boot DevTools** improves development efficiency with auto-reload.

## **2️⃣ Spring Boot Annotations**
- `@RestController` combines `@Controller` and `@ResponseBody`.
- `@RequestMapping`, `@GetMapping`, `@PostMapping` handle HTTP requests.
- `@PathVariable` extracts values from the URL.
- `@RequestParam` extracts query parameters.
- `@Transactional` ensures method execution within a transaction.
- `@Component`, `@Service`, `@Repository` define Spring beans.
- `@Autowired` injects dependencies automatically.
- `@Qualifier` resolves multiple bean conflicts.
- `@Value` injects property values from `application.properties`.

## **3️⃣ Spring Boot Service Layer**
- **Service Layer** handles business logic (`@Service`).
- **DAO Layer** interacts with the database (`@Repository`).
- **Controller Layer** handles incoming requests (`@RestController`).

## **4️⃣ Spring Boot Security**
- `@EnableWebSecurity` enables Spring Security.
- **JWT (JSON Web Token)** secures APIs using token-based authentication.
- **OAuth2.0** manages authorization via identity providers.
- **Spring Security Filters** handle authentication and authorization.
- **Role-Based Access Control (RBAC)** restricts API access using `@PreAuthorize`.

## **5️⃣ Spring Boot Database & Transactions**
- **Spring Data JPA** simplifies database access using `JpaRepository`.
- **HikariCP** is the default connection pool for efficient database access.
- **Flyway & Liquibase** manage database migrations.
- **Spring Transaction Management** ensures atomicity (`@Transactional`).

## **6️⃣ Spring Boot Testing**
- **Spring Boot Test** provides integration testing support.
- `@SpringBootTest` loads the full application context for testing.
- `@MockBean` and `@Autowired` assist in unit testing.
- **Mockito & JUnit** are commonly used for testing Spring Boot applications.

## **7️⃣ Spring Boot Logging**
- **Spring Boot uses SLF4J with Logback** by default.
- Logging configuration is managed via `application.properties` or `logback.xml`.
- `logger.info()`, `logger.debug()` help in debugging.

## **8️⃣ Spring Boot Deployment & Scaling**
- **Docker** packages Spring Boot applications into containers.
- **Kubernetes (K8s)** automates deployment and scaling.
- **Spring Boot in Cloud** (AWS, GCP, Azure) deploys applications using services like AWS Elastic Beanstalk.
- **Spring Boot with CI/CD** automates build and deployment using Jenkins, GitHub Actions.

## **9️⃣ Real-Time Scenario Handling**
- **Memory leaks** are resolved using proper garbage collection tuning.
- **Slow API responses** are optimized with caching (Redis, Ehcache).
- **High traffic handling** is achieved via load balancers (Nginx, AWS ALB).
- **Database failures** are managed using retry mechanisms (Resilience4j, Retryable).

