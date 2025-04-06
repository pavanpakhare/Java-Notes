# **Microservices Patterns with Spring Boot – Complete Guide**

This tutorial covers **essential microservices patterns** implemented using **Spring Boot, Spring Cloud, and Docker**. Learn how to build **scalable, resilient, and maintainable** microservices architectures.

---

## **Table of Contents**
1. [**Introduction to Microservices**](#1-introduction-to-microservices)
2. [**Decomposition Patterns**](#2-decomposition-patterns)
   - Domain-Driven Design (DDD)
   - Strangler Pattern
3. [**Communication Patterns**](#3-communication-patterns)
   - API Gateway
   - REST vs gRPC
   - Event-Driven (Kafka)
4. [**Resiliency Patterns**](#4-resiliency-patterns)
   - Circuit Breaker
   - Retry/Fallback
   - Bulkhead
5. [**Data Management**](#5-data-management-patterns)
   - Database per Service
   - Saga Pattern
   - CQRS
6. [**Service Discovery & Load Balancing**](#6-service-discovery--load-balancing)
   - Eureka
   - Spring Cloud LoadBalancer
7. [**Distributed Tracing**](#7-distributed-tracing)
   - Sleuth + Zipkin
8. [**Security Patterns**](#8-security-patterns)
   - JWT/OAuth2
   - API Gateway Security
9. [**Deployment Patterns**](#9-deployment-patterns)
   - Docker + Kubernetes
   - Blue-Green Deployment

---

## **1. Introduction to Microservices**
Microservices are **small, independent services** that:
✅ Run in their own process  
✅ Communicate via APIs  
✅ Can be deployed independently  
✅ Own their own database  

### **Spring Boot + Spring Cloud for Microservices**
| **Technology**       | **Purpose**                          |
|----------------------|--------------------------------------|
| Spring Boot          | Build individual microservices       |
| Spring Cloud Gateway | API Gateway                          |
| Eureka               | Service Discovery                    |
| Resilience4j         | Circuit Breaker, Retry, Rate Limiter |
| Kafka/RabbitMQ       | Event-Driven Communication           |
| Sleuth + Zipkin      | Distributed Tracing                  |

---

## **2. Decomposition Patterns**
### **Domain-Driven Design (DDD)**
- Break down services by **business domains** (e.g., `OrderService`, `PaymentService`).
- Use **Bounded Contexts** to define service boundaries.

### **Strangler Pattern**
- Gradually replace a **monolith** with microservices.
- Route new features to microservices while keeping legacy code.

---

## **3. Communication Patterns**
### **API Gateway (Spring Cloud Gateway)**
```yaml
# application.yml
spring:
  cloud:
    gateway:
      routes:
        - id: order-service
          uri: lb://ORDER-SERVICE
          predicates:
            - Path=/api/orders/**
```

### **Synchronous (REST)**
```java
@FeignClient(name = "payment-service")
public interface PaymentClient {
    @PostMapping("/payments")
    Payment processPayment(PaymentRequest request);
}
```

### **Asynchronous (Kafka)**
```java
@KafkaListener(topics = "order-events")
public void handleOrderEvent(OrderEvent event) {
    // Process event
}
```

---

## **4. Resiliency Patterns**
### **Circuit Breaker (Resilience4j)**
```java
@CircuitBreaker(name = "paymentService", fallbackMethod = "processPaymentFallback")
public Payment processPayment(PaymentRequest request) {
    return paymentClient.processPayment(request);
}

public Payment processPaymentFallback(PaymentRequest request, Exception e) {
    return new Payment("FALLBACK");
}
```

### **Retry Mechanism**
```java
@Retry(name = "paymentService", fallbackMethod = "processPaymentFallback")
public Payment retryPayment(PaymentRequest request) {
    return paymentClient.processPayment(request);
}
```

### **Bulkhead (Thread Isolation)**
```yaml
resilience4j:
  thread-pool-bulkhead:
    paymentService:
      maxThreadPoolSize: 5
      coreThreadPoolSize: 3
```

---

## **5. Data Management Patterns**
### **Database per Service**
- Each microservice **owns its database** (SQL/NoSQL).
- Avoid shared databases.

### **Saga Pattern (Event Choreography)**
```java
public class OrderSaga {
    @Transactional
    public void createOrder(Order order) {
        orderRepository.save(order);
        eventPublisher.publish(new OrderCreatedEvent(order.getId()));
    }
}
```

### **CQRS (Command Query Responsibility Segregation)**
- Separate **reads** (Query) and **writes** (Command).
- Example:  
  ```java
  @RestController
  @RequestMapping("/orders")
  public class OrderController {
      @GetMapping("/{id}") // Query
      public Order getOrder(@PathVariable Long id) { ... }
      
      @PostMapping // Command
      public void createOrder(@RequestBody Order order) { ... }
  }
  ```

---

## **6. Service Discovery & Load Balancing**
### **Eureka Server (Service Registry)**
```java
@SpringBootApplication
@EnableEurekaServer
public class EurekaServerApplication { ... }
```

### **Eureka Client (Microservice Registration)**
```yaml
# application.yml
eureka:
  client:
    service-url:
      defaultZone: http://localhost:8761/eureka
```

### **Spring Cloud LoadBalancer**
```java
@Bean
@LoadBalanced
public WebClient.Builder loadBalancedWebClientBuilder() {
    return WebClient.builder();
}
```

---

## **7. Distributed Tracing (Sleuth + Zipkin)**
### **Add Dependencies**
```xml
<dependency>
    <groupId>org.springframework.cloud</groupId>
    <artifactId>spring-cloud-starter-sleuth</artifactId>
</dependency>
<dependency>
    <groupId>org.springframework.cloud</groupId>
    <artifactId>spring-cloud-sleuth-zipkin</artifactId>
</dependency>
```

### **View Traces in Zipkin**
1. Run Zipkin:  
   ```bash
   docker run -d -p 9411:9411 openzipkin/zipkin
   ```
2. Access: `http://localhost:9411`

---

## **8. Security Patterns**
### **JWT Authentication**
```java
@Bean
public SecurityFilterChain securityFilterChain(HttpSecurity http) throws Exception {
    http
        .authorizeHttpRequests(auth -> auth
            .requestMatchers("/api/auth/**").permitAll()
            .anyRequest().authenticated()
        )
        .oauth2ResourceServer(oauth2 -> oauth2.jwt(Customizer.withDefaults()));
    return http.build();
}
```

### **API Gateway Security**
```yaml
spring:
  cloud:
    gateway:
      routes:
        - id: secure-route
          uri: lb://user-service
          predicates:
            - Path=/api/users/**
          filters:
            - TokenRelay
```

---

## **9. Deployment Patterns**
### **Dockerize Microservices**
```dockerfile
FROM openjdk:17
COPY target/user-service.jar app.jar
ENTRYPOINT ["java", "-jar", "app.jar"]
```

### **Kubernetes Deployment**
```yaml
# deployment.yml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: order-service
spec:
  replicas: 3
  selector:
    matchLabels:
      app: order-service
  template:
    spec:
      containers:
        - name: order-service
          image: order-service:1.0
          ports:
            - containerPort: 8080
```

### **Blue-Green Deployment**
1. Deploy **v2** alongside **v1**.
2. Switch traffic using **Kubernetes Ingress**.

---

## **Conclusion**
This tutorial covered **essential microservices patterns** with Spring Boot:
✅ **Decomposition** (DDD, Strangler)  
✅ **Communication** (API Gateway, Kafka)  
✅ **Resiliency** (Circuit Breaker, Retry)  
✅ **Data Management** (Saga, CQRS)  
✅ **Observability** (Sleuth, Zipkin)  

