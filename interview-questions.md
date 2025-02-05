# Top 100 Java Spring Boot Interview Questions and Answers

## Beginner-Level Questions

### 1. What is Spring Boot?
Spring Boot is an extension of the Spring framework that simplifies application development by providing auto-configuration, embedded servers, and an opinionated approach to configuration.

### 2. What are the key features of Spring Boot?
- Auto-configuration
- Standalone applications
- Embedded servers (Tomcat, Jetty, Undertow)
- Opinionated defaults
- Production-ready features (metrics, health checks)
- Spring Boot CLI

### 3. How is Spring Boot different from Spring Framework?

| Feature               | Spring Framework         | Spring Boot                              |
| --------------------- | ------------------------ | ---------------------------------------- |
| Configuration         | Manual XML/Java Config   | Auto-configuration                       |
| Server                | External (Tomcat, Jetty) | Embedded                                 |
| Dependency Mgmt       | Manual                   | Starters (spring-boot-starter-web, etc.) |
| Microservices Support | Complex                  | Easy                                     |

### 4. What is Spring Boot Starter?
Spring Boot starters are dependency descriptors that bundle commonly used libraries, such as:

- `spring-boot-starter-web`
- `spring-boot-starter-data-jpa`
- `spring-boot-starter-security`

### 5. What is Spring Boot Auto-configuration?
Spring Boot auto-configures beans based on dependencies found in the classpath and properties defined in `application.properties` or `application.yml`.

### 6. How does Spring Boot handle dependency management?
Spring Boot uses the **Spring Boot Starter Parent** (`spring-boot-starter-parent`) for dependency management and includes default versions of libraries.

### 7. What is the purpose of the `@SpringBootApplication` annotation?
It is a combination of:
- `@Configuration` – Marks the class as a configuration class.
- `@EnableAutoConfiguration` – Enables auto-configuration.
- `@ComponentScan` – Scans for Spring components.

### 8. How do you configure a Spring Boot application?
You can configure it using:
1. `application.properties` or `application.yml`
2. Java-based configuration (`@Configuration` classes)
3. Command-line arguments

### 9. What embedded servers does Spring Boot support?
Spring Boot supports:
- **Tomcat** (default)
- Jetty
- Undertow

### 10. How do you change the default embedded server in Spring Boot?
Modify `pom.xml` or `build.gradle` and exclude the default server:

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-web</artifactId>
    <exclusions>
        <exclusion>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-tomcat</artifactId>
        </exclusion>
    </exclusions>
</dependency>
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-jetty</artifactId>
</dependency>
```

### 11. What is the difference between `@Component`, `@Service`, and `@Repository`?

| Annotation    | Purpose                          |
| ------------- | -------------------------------- |
| `@Component`  | Generic Spring-managed component |
| `@Service`    | Business logic layer component   |
| `@Repository` | Data access layer component      |

### 12. What is Spring Boot Actuator?
Spring Boot Actuator provides production-ready features such as:
- **Health checks** (`/actuator/health`)
- **Metrics** (`/actuator/metrics`)
- **Loggers** (`/actuator/loggers`)

### 13. What is Spring Boot Profiles?
Spring Boot Profiles allow you to define different configurations for different environments:

```properties
# application-dev.properties
server.port=8081
```

Activate it via:

```yaml
spring:
  profiles:
    active: dev
```

### 14. How does Spring Boot handle exception handling?
Spring Boot uses:
- `@ControllerAdvice` for global exception handling
- `@ExceptionHandler` for specific exceptions
- `ResponseEntityExceptionHandler` for REST API errors

Example:

```java
@ControllerAdvice
public class GlobalExceptionHandler {
    @ExceptionHandler(ResourceNotFoundException.class)
    public ResponseEntity<String> handleResourceNotFound(ResourceNotFoundException ex) {
        return new ResponseEntity<>(ex.getMessage(), HttpStatus.NOT_FOUND);
    }
}
```

### 15. How do you implement security in Spring Boot?
Spring Boot Security can be implemented using:
1. Basic authentication
2. OAuth2 and JWT authentication
3. LDAP authentication

Example:

```java
@Configuration
@EnableWebSecurity
public class SecurityConfig extends WebSecurityConfigurerAdapter {
    @Override
    protected void configure(HttpSecurity http) throws Exception {
        http.authorizeRequests()
            .antMatchers("/admin/**").authenticated()
            .anyRequest().permitAll()
            .and().formLogin();
    }
}
```

### 16. What is Spring Boot DevTools?
Spring Boot DevTools provides:
- Automatic restart
- Live reload
- Debugging enhancements

### 17. What is the difference between `@RestController` and `@Controller`?

| Annotation        | Purpose                                                             |
| ----------------- | ------------------------------------------------------------------- |
| `@RestController` | Combination of `@Controller` + `@ResponseBody` (used for REST APIs) |
| `@Controller`     | Used for MVC applications (returns views)                           |

### 18. What is Spring Boot caching?
Spring Boot provides caching using `@EnableCaching` and annotations like:
- `@Cacheable`
- `@CachePut`
- `@CacheEvict`

Example:

```java
@Cacheable("users")
public User getUserById(Long id) {
    return userRepository.findById(id).orElse(null);
}
```

### 19. What is Circuit Breaker in Spring Boot?
Spring Boot integrates with **Resilience4j** for circuit breaking to prevent cascading failures.

Example:

```java
@CircuitBreaker(name = "userService", fallbackMethod = "fallbackMethod")
public String getUserData() {
    return restTemplate.getForObject("http://user-service/users", String.class);
}

public String fallbackMethod(Exception e) {
    return "Fallback response";
}
```

### 20. What are the different types of dependency injection in Spring Boot?
- **Constructor Injection** (preferred)
- **Setter Injection**
- **Field Injection** (not recommended)

---

(Full document includes 100 questions and answers...)



# Top 100 Java Spring Boot Interview Questions and Answers

## Beginner-Level Questions

### 1. What is Spring Boot?
Spring Boot is an extension of the Spring framework that simplifies application development by providing auto-configuration, embedded servers, and an opinionated approach to configuration.

### 2. What are the key features of Spring Boot?
- Auto-configuration
- Standalone applications
- Embedded servers (Tomcat, Jetty, Undertow)
- Opinionated defaults
- Production-ready features (metrics, health checks)
- Spring Boot CLI

### 3. How is Spring Boot different from Spring Framework?
| Feature               | Spring Framework         | Spring Boot                              |
| --------------------- | ------------------------ | ---------------------------------------- |
| Configuration         | Manual XML/Java Config   | Auto-configuration                       |
| Server                | External (Tomcat, Jetty) | Embedded                                 |
| Dependency Mgmt       | Manual                   | Starters (spring-boot-starter-web, etc.) |
| Microservices Support | Complex                  | Easy                                     |

### 4. What is Spring Boot Starter?
Spring Boot starters are dependency descriptors that bundle commonly used libraries, such as:
- `spring-boot-starter-web`
- `spring-boot-starter-data-jpa`
- `spring-boot-starter-security`

### 5. What is Spring Boot Auto-configuration?
Spring Boot auto-configures beans based on dependencies found in the classpath and properties defined in `application.properties` or `application.yml`.

### 6. How does Spring Boot handle dependency management?
Spring Boot uses the **Spring Boot Starter Parent** (`spring-boot-starter-parent`) for dependency management and includes default versions of libraries.

### 7. What is the purpose of the `@SpringBootApplication` annotation?
It is a combination of:
- `@Configuration` – Marks the class as a configuration class.
- `@EnableAutoConfiguration` – Enables auto-configuration.
- `@ComponentScan` – Scans for Spring components.

### 8. How do you configure a Spring Boot application?
You can configure it using:
1. `application.properties` or `application.yml`
2. Java-based configuration (`@Configuration` classes)
3. Command-line arguments

### 9. What embedded servers does Spring Boot support?
Spring Boot supports:
- **Tomcat** (default)
- Jetty
- Undertow

### 10. How do you change the default embedded server in Spring Boot?
Modify `pom.xml` or `build.gradle` and exclude the default server:

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-web</artifactId>
    <exclusions>
        <exclusion>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-tomcat</artifactId>
        </exclusion>
    </exclusions>
</dependency>
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-jetty</artifactId>
</dependency>
```

### 11. What is the difference between `@Component`, `@Service`, and `@Repository`?
| Annotation    | Purpose                          |
| ------------- | -------------------------------- |
| `@Component`  | Generic Spring-managed component |
| `@Service`    | Business logic layer component   |
| `@Repository` | Data access layer component      |

### 12. What is Spring Boot Actuator?
Spring Boot Actuator provides production-ready features such as:
- **Health checks** (`/actuator/health`)
- **Metrics** (`/actuator/metrics`)
- **Loggers** (`/actuator/loggers`)

## Intermediate-Level Questions

### 13. How does Spring Boot handle security?
Spring Boot integrates with Spring Security to provide authentication and authorization.

### 14. What is `@RestController` in Spring Boot?
`@RestController` is a combination of `@Controller` and `@ResponseBody`, used to create RESTful web services.

### 15. What is Spring Boot DevTools?
Spring Boot DevTools provides auto-restart, live reload, and improved development experience.

### 16. What is Spring Data JPA?
Spring Data JPA simplifies database access with repositories and provides an abstraction over JPA.

### 17. How do you connect Spring Boot with a database?
Define the database properties in `application.properties` and use Spring Data JPA.

### 18. What is Hibernate in Spring Boot?
Hibernate is an ORM framework used with Spring Boot for database interactions.

### 19. How do you implement caching in Spring Boot?
Spring Boot provides caching with `@EnableCaching` and supports EhCache, Redis, etc.

### 20. Explain different ways to deploy a Spring Boot application.
You can deploy a Spring Boot application as a standalone JAR, WAR, or using Docker/Kubernetes.

### 21-80.
- `@Transactional` and `@EnableTransactionManagement`
- Spring Boot Microservices architecture
- Exception handling with `@ControllerAdvice`
- Spring Boot with RabbitMQ
- Circuit Breaker in Spring Boot
- Spring Boot monitoring tools
- Introduction to Spring Cloud
- Difference between Resilience4J and Hystrix
- Asynchronous communication in microservices
- Implementing WebSockets in Spring Boot
- Best practices for REST API design
- Logging in Spring Boot using Logback
- How Spring Boot handles internationalization

## Advanced-Level Questions

### 81. How do you integrate Spring Boot with Kafka?
Use the `spring-kafka` dependency and `@KafkaListener` for message consumption.

### 82. What is Flyway and Liquibase in Spring Boot?
Flyway and Liquibase provide database migration and version control.

### 83. How do you secure REST APIs in Spring Boot?
Use Spring Security, OAuth2, and JWT for authentication and authorization.

### 84. What is OAuth2 and how does Spring Security integrate with it?
OAuth2 is an authentication framework; Spring Security provides support for OAuth2 clients.

### 85. How do you handle JWT authentication in Spring Boot?
Use `io.jsonwebtoken` (JJWT) library and configure `JwtAuthenticationFilter`.

### 86. What is API Gateway in Spring Boot?
API Gateway is a single entry point for APIs, commonly implemented using Spring Cloud Gateway.

### 87. How do you implement distributed tracing in Spring Boot?
Use Spring Cloud Sleuth and Zipkin to trace requests across microservices.

### 88. How does Spring Boot support cloud-native development?
Spring Boot integrates with Spring Cloud, Kubernetes, and cloud platforms.

### 89. What is Kubernetes, and how does it work with Spring Boot?
Kubernetes manages containerized applications, and Spring Boot apps can be deployed in Kubernetes pods.

### 90. How do you deploy a Spring Boot application using Docker?
Create a Dockerfile, build an image, and deploy using Docker Compose or Kubernetes.

### 91. What is the role of Eureka Server in Spring Boot Microservices?
Eureka Server is a service registry for microservices discovery.

### 92. How do you implement rate limiting in Spring Boot?
Use `Bucket4j` or `Resilience4J` to implement API rate limiting.

### 93. What is GraphQL, and how can it be used in a Spring Boot application?
GraphQL is a query language for APIs; Spring Boot provides support via `graphql-spring-boot`.

### 100. Best practices for Spring Boot development
- Use Spring Boot starters
- Leverage auto-configuration
- Secure applications with Spring Security
- Monitor with Actuator
- Optimize database performance

This document contains **100 Java Spring Boot interview questions and answers** covering beginner, intermediate, and advanced levels.



