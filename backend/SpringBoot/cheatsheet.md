# Spring Boot Cheatsheet

## 🚀 What is Spring Boot?
Spring Boot is a framework built on top of the Spring Framework to simplify the setup, configuration, and deployment of Spring applications. It allows you to create standalone, production-ready apps with minimal boilerplate.

## 🧱 Core Concepts You'll Find Familiar
Since you already know Django/Express/FastAPI, here's how Spring Boot concepts map:

| Concept | Django / Node | Spring Boot Equivalent |
|---------|---------------|------------------------|
| Routing | urls.py, app.get() | @RestController, @GetMapping, @PostMapping |
| ORM | Django ORM / Sequelize / Mongoose | JPA (with Hibernate as default) |
| Dependency Injection | Built-in / lightweight in Node | Core to Spring (@Autowired) |
| Middleware | Middleware / Middleware classes | Filters, Interceptors |
| Config | settings.py, .env | application.properties or application.yml |
| API Documentation | Swagger/FastAPI docs | SpringDoc OpenAPI / Swagger |

## 🔧 Key Annotations to Know
- `@SpringBootApplication` – Entry point of the app (like main.py)
- `@RestController` – Defines a REST controller
- `@GetMapping("/api")` – Maps GET request to a function
- `@PostMapping`, `@PutMapping`, etc. – Same as above but for other HTTP methods
- `@Service`, `@Repository`, `@Component` – Used for component scanning and DI
- `@Autowired` – Injects dependencies
- `@Entity` – Declares a JPA model
- `@Id`, `@GeneratedValue` – Primary key annotations

## 🗃️ Database Handling (JPA & Hibernate)
Spring Boot uses Spring Data JPA, usually with Hibernate.

Define a model:
```java
@Entity
public class User {
  @Id
  @GeneratedValue
  private Long id;
  private String name;
}
```

Repository:
```java
public interface UserRepository extends JpaRepository<User, Long> {}
```

Service Layer (Optional but good practice):
```java
@Service
public class UserService {
  @Autowired
  private UserRepository userRepository;
}
```

## ⚙️ Project Structure
```
crudapp/
├── src/
│   └── main/
│       ├── java/
│       │   └── com/
│       │       └── vishwa/
│       │           └── crudapp/
│       │               ├── CrudAppApplication.java  <- main class
│       │               ├── controller/
│       │               ├── model/
│       │               ├── repository/
│       │               └── service/
│       └── resources/
│           ├── application.properties  <- config file
│           └── static/                 <- for frontend assets (if any)
├── pom.xml                             <- Maven dependency file
```

## 🛠️ Build Tool
Mostly uses Maven or Gradle. You'll see:
- `pom.xml` for Maven
- `build.gradle` for Gradle

These manage dependencies, like requirements.txt or package.json.

## 📦 Running the App
Just run the main class containing `@SpringBootApplication`:
```java
@SpringBootApplication
public class MyApp {
  public static void main(String[] args) {
    SpringApplication.run(MyApp.class, args);
  }
}
```
Use `mvn spring-boot:run` or `./gradlew bootRun`.

## 📄 application.properties / application.yml
Used to configure database URLs, server ports, etc.
```properties
server.port=8081
spring.datasource.url=jdbc:mysql://localhost:3306/mydb
spring.datasource.username=root
spring.datasource.password=secret
```

## ✅ What You Should Focus On Initially
- Project structure and routing (@RestController, @Service, @Repository)
- JPA for DB interactions
- How DI (@Autowired) works
- How to configure app with application.properties
- Build tool (Maven vs Gradle – just understand the basics of the one in use)
- How error handling is done using @ControllerAdvice

## 🔍 Optional Extras (If You Need Them)
- Spring Security – For auth
- Spring Cloud – For microservices patterns (service discovery, config, etc.)
- Spring Boot Actuator – For health checks, metrics, etc.
- Swagger – For API docs

## 🚦 REST Controller Example
```java
@RestController
@RequestMapping("/api/users")
public class UserController {
    
    @Autowired
    private UserService userService;
    
    @GetMapping
    public List<User> getAllUsers() {
        return userService.findAll();
    }
    
    @GetMapping("/{id}")
    public ResponseEntity<User> getUserById(@PathVariable Long id) {
        User user = userService.findById(id);
        return ResponseEntity.ok(user);
    }
    
    @PostMapping
    public ResponseEntity<User> createUser(@RequestBody User user) {
        User savedUser = userService.save(user);
        return ResponseEntity.status(HttpStatus.CREATED).body(savedUser);
    }
    
    @PutMapping("/{id}")
    public ResponseEntity<User> updateUser(@PathVariable Long id, @RequestBody User user) {
        user.setId(id);
        User updatedUser = userService.update(user);
        return ResponseEntity.ok(updatedUser);
    }
    
    @DeleteMapping("/{id}")
    public ResponseEntity<Void> deleteUser(@PathVariable Long id) {
        userService.deleteById(id);
        return ResponseEntity.noContent().build();
    }
}
```

## 📊 Validation
```java
@Entity
public class Product {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    
    @NotBlank(message = "Name is required")
    private String name;
    
    @Positive(message = "Price must be positive")
    private BigDecimal price;
    
    @Min(value = 0, message = "Stock cannot be negative")
    private Integer stock;
    
    // Getters and setters
}

// In controller:
@PostMapping
public ResponseEntity<Product> createProduct(@Valid @RequestBody Product product) {
    // ...
}
```

## 🔒 Basic Spring Security Configuration
```java
@Configuration
@EnableWebSecurity
public class SecurityConfig {
    
    @Bean
    public SecurityFilterChain filterChain(HttpSecurity http) throws Exception {
        http
            .authorizeHttpRequests(auth -> auth
                .requestMatchers("/api/public/**").permitAll()
                .requestMatchers("/api/admin/**").hasRole("ADMIN")
                .anyRequest().authenticated()
            )
            .httpBasic(withDefaults());
        return http.build();
    }
    
    @Bean
    public UserDetailsService userDetailsService() {
        UserDetails user = User.withDefaultPasswordEncoder()
            .username("user")
            .password("password")
            .roles("USER")
            .build();
            
        UserDetails admin = User.withDefaultPasswordEncoder()
            .username("admin")
            .password("admin")
            .roles("ADMIN")
            .build();
            
        return new InMemoryUserDetailsManager(user, admin);
    }
}
```

## 📝 Exception Handling
```java
@ControllerAdvice
public class GlobalExceptionHandler {
    
    @ExceptionHandler(ResourceNotFoundException.class)
    public ResponseEntity<ErrorResponse> handleResourceNotFound(ResourceNotFoundException ex) {
        ErrorResponse error = new ErrorResponse(
            HttpStatus.NOT_FOUND.value(),
            ex.getMessage()
        );
        return ResponseEntity.status(HttpStatus.NOT_FOUND).body(error);
    }
    
    @ExceptionHandler(ValidationException.class)
    public ResponseEntity<ErrorResponse> handleValidationErrors(ValidationException ex) {
        ErrorResponse error = new ErrorResponse(
            HttpStatus.BAD_REQUEST.value(),
            ex.getMessage()
        );
        return ResponseEntity.status(HttpStatus.BAD_REQUEST).body(error);
    }
    
    @ExceptionHandler(Exception.class)
    public ResponseEntity<ErrorResponse> handleGenericException(Exception ex) {
        ErrorResponse error = new ErrorResponse(
            HttpStatus.INTERNAL_SERVER_ERROR.value(),
            "An unexpected error occurred"
        );
        return ResponseEntity.status(HttpStatus.INTERNAL_SERVER_ERROR).body(error);
    }
}
```

## 🧪 Testing in Spring Boot
```java
@SpringBootTest
class UserServiceTests {
    
    @MockBean
    private UserRepository userRepository;
    
    @Autowired
    private UserService userService;
    
    @Test
    void testFindById() {
        // Arrange
        User mockUser = new User();
        mockUser.setId(1L);
        mockUser.setName("Test User");
        
        when(userRepository.findById(1L)).thenReturn(Optional.of(mockUser));
        
        // Act
        User foundUser = userService.findById(1L);
        
        // Assert
        assertNotNull(foundUser);
        assertEquals("Test User", foundUser.getName());
    }
}
```

## 📋 Common Spring Boot Starters
- `spring-boot-starter-web` - Web applications with Spring MVC
- `spring-boot-starter-data-jpa` - Spring Data JPA with Hibernate
- `spring-boot-starter-security` - Spring Security
- `spring-boot-starter-test` - Testing utilities
- `spring-boot-starter-validation` - Java Bean Validation
- `spring-boot-starter-actuator` - Production-ready features
- `spring-boot-starter-thymeleaf` - Thymeleaf template engine
- `spring-boot-starter-jdbc` - Basic JDBC support
- `spring-boot-starter-data-rest` - Expose repositories as REST
- `spring-boot-starter-cache` - Caching support