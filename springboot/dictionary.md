# Spring Boot Basic Terminology for Revision

## A - C

### Actuator
A set of tools to monitor and manage Spring Boot applications (`/actuator` endpoints).

### Application Context
The central container that holds all Spring beans and their configurations.

### Autoconfiguration
A feature that automatically configures Spring Boot applications based on classpath dependencies.

### Bean
An object managed by the Spring IoC container, defined using `@Component`, `@Service`, or `@Repository`.

### BeanFactory
A lightweight container that provides the basic mechanism for managing beans.

### Configuration
Defines application settings using `@Configuration` annotated classes.

### Controller
A Spring MVC component that handles web requests (`@Controller` or `@RestController`).

## D - F

### Dependency Injection (DI)
A design pattern that injects dependencies into a class rather than creating them inside.

### DevTools
A Spring Boot module that provides live reload and automatic application restart during development.

### Embedded Server
Spring Boot supports embedded web servers like Tomcat, Jetty, and Undertow for running applications without external deployment.

### Endpoints
Actuator-provided URLs that expose operational information (`/actuator/health`, `/actuator/metrics`).

### Filter
A component that intercepts HTTP requests and responses for processing (`@Component`).

### Flyway
A database migration tool used for version-controlled schema changes.

## G - I

### HATEOAS
A principle that enhances REST APIs with navigational links (`spring-boot-starter-hateoas`).

### Hibernate
A popular ORM framework used in Spring Boot applications with JPA (`spring-boot-starter-data-jpa`).

### Initialization
Application startup processes, including bean instantiation and dependency resolution.

### Interceptor
A mechanism to process requests before they reach the controller (`HandlerInterceptor`).

## J - M

### JDBC
A Java API for database connectivity, often used with Spring Boot’s `JdbcTemplate`.

### JPA (Java Persistence API)
A specification for ORM frameworks like Hibernate to map Java objects to database tables.

### Logging
Spring Boot uses SLF4J with Logback as the default logging framework.

### Microservices
A software architecture pattern where applications are divided into small, independent services.

### Model
Represents application data used by the view layer (`@Entity`, `@Table`).

### MyBatis
An alternative to JPA for database interactions, using XML or annotation-based SQL queries.

## N - P

### Pagination
A technique to retrieve large datasets in smaller chunks (`Pageable` in Spring Data).

### Profiles
Spring Boot allows environment-specific configurations using `@Profile` and `application-{profile}.properties`.

### Properties
Configuration settings stored in `application.properties` or `application.yml`.

### Proxy
Spring uses dynamic proxies for AOP features like `@Transactional` and `@Cacheable`.

## Q - S

### Query Methods
Spring Data JPA provides query generation based on method names (`findByName(String name)`).

### REST
A software architecture style for building APIs that use HTTP for communication.

### Repository
A layer that interacts with the database, typically using `@Repository`.

### Security
Spring Security provides authentication and authorization mechanisms for applications.

### Service
A class containing business logic, marked with `@Service`.

### Spring Boot Starter
A pre-configured dependency set for specific functionalities (`spring-boot-starter-web`).

### Swagger
A tool for documenting and testing REST APIs (`springdoc-openapi`).

## T - Z

### Testing
Spring Boot provides `@SpringBootTest` and `MockMvc` for integration and unit testing.

### Transaction Management
Spring Boot uses `@Transactional` for handling database transactions automatically.

### Thymeleaf
A modern server-side Java template engine for dynamic HTML generation.

### YAML
An alternative to `.properties` for configuration files (`application.yml`).

### Zuul
A Netflix OSS API Gateway for routing requests in microservices architectures.

