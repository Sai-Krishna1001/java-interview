# Microservices - Important One-Liners for Interview

## **1️⃣ Microservices Basics**
- Microservices follow **Single Responsibility Principle (SRP)**, ensuring each service handles a specific function.  
- Services communicate via **REST, gRPC, Kafka, or RabbitMQ**.  
- Each microservice has **its own database (Database Per Service pattern)** to ensure loose coupling.  
- **API Gateway** (e.g., **Spring Cloud Gateway, Kong, Zuul**) is used for request routing, authentication, and load balancing.  
- **Service Discovery** (e.g., **Eureka, Consul, Zookeeper**) helps services dynamically locate each other.  

## **2️⃣ Spring Boot & Spring Cloud**
- `@SpringBootApplication` combines `@Configuration`, `@EnableAutoConfiguration`, and `@ComponentScan`.  
- `@FeignClient` simplifies inter-service communication without `RestTemplate`.  
- `@LoadBalanced` enables client-side load balancing with **Ribbon** or **Spring Cloud LoadBalancer**.  
- `@CircuitBreaker` (from **Resilience4j**) prevents repeated failures when a service is down.  
- `@Retry` (from **Resilience4j**) retries failed requests for transient failures.  

## **3️⃣ Service Communication**
- **Synchronous** communication uses **REST APIs** (blocking calls).  
- **Asynchronous** communication uses **Kafka, RabbitMQ, or WebSockets** (non-blocking).  
- **Event-Driven Architecture** (using Kafka) enables **loose coupling** between services.  

## **4️⃣ Database & Transactions**
- Use **Saga Pattern** for distributed transactions across microservices.  
- **Choreography Saga** relies on **events**, while **Orchestration Saga** uses a central controller.  
- **CQRS (Command Query Responsibility Segregation)** improves performance by separating read and write operations.  

## **5️⃣ Resilience & Fault Tolerance**
- **Circuit Breaker Pattern** (Resilience4j) prevents cascading failures.  
- **Bulkhead Pattern** isolates resources to prevent overloading.  
- **Rate Limiting** (via **API Gateway**) prevents service abuse and overload.  

## **6️⃣ Security in Microservices**
- **JWT (JSON Web Token)** secures inter-service communication.  
- **OAuth2.0** and **Keycloak** are used for authentication and authorization.  
- **Spring Security** with `@PreAuthorize` ensures role-based access control (RBAC).  

## **7️⃣ Logging & Monitoring**
- **Centralized logging** is implemented using **ELK (Elasticsearch, Logstash, Kibana)**.  
- **Distributed tracing** (Zipkin, Jaeger) helps track requests across microservices.  
- **Spring Cloud Sleuth** adds trace IDs to logs for debugging.  

## **8️⃣ Deployment & Scaling**
- **Docker** is used to containerize microservices.  
- **Kubernetes (K8s)** automates deployment, scaling, and management of microservices.  
- **Blue-Green Deployment** reduces downtime during updates.  
- **Canary Deployment** rolls out new versions gradually to a small subset of users.  

## **9️⃣ API Versioning & Backward Compatibility**
- Use **URL versioning (`/api/v1/resource`)** or **Header versioning (`Accept-Version: v1`)**.  
- **Feature flags** help in rolling out new functionalities safely.  

## **🔟 Real-Time Scenario Handling**
- If a microservice is down, **API Gateway** handles fallbacks and reroutes traffic.  
- If a database is unavailable, **Retry Mechanism** ensures smooth recovery.  
- In case of high traffic, **Load Balancers (Nginx, AWS ALB)** distribute requests across instances.  
