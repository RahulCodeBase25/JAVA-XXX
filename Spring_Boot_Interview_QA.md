
# 🌱 Spring & Spring Boot Interview Q&A

---

### 29. What is Spring Framework? Why use it?

Spring is a powerful Java framework for building enterprise applications. It provides features like Dependency Injection (DI), AOP, and simplifies development with modular components.

✅ Benefits:
- Loose coupling
- Testability
- Modular and layered architecture

🎮 **Analogy**: Spring is like a **game engine** — handles all background systems so you focus on game logic.

---

### 30. What is Spring Boot? How is it different from Spring?

Spring Boot is built on top of Spring — it removes boilerplate by:
- Auto-configuring beans
- Embedding web servers
- No XML needed

✅ Think of it as “Spring with batteries included.”

🎮 **Analogy**: Spring Boot is like using **Unity with default assets loaded** — less setup, quicker dev.

---

### 31. What is Dependency Injection? Types?

Dependency Injection (DI) lets you inject required objects into a class, instead of creating them inside.

✅ Types:
- Constructor Injection
- Setter Injection
- Field Injection

🎮 **Analogy**: Like receiving your gear kit from a sponsor — you don’t go buying each item yourself.

---

### 32. Difference between @Component, @Service, @Repository, @Controller

| Annotation     | Use Case                      |
|----------------|-------------------------------|
| `@Component`   | Generic bean                  |
| `@Service`     | Business logic layer          |
| `@Repository`  | DAO (Database Access Layer)   |
| `@Controller`  | Web layer controller (MVC)    |

🎮 **Analogy**: Like roles in a team — player, coach, analyst, captain.

---

### 33. What is Spring Bean Lifecycle?

1. Instantiate bean
2. Populate properties
3. Call `@PostConstruct` / `InitializingBean.afterPropertiesSet()`
4. Use bean
5. Call `@PreDestroy` / `DisposableBean.destroy()`

🎮 **Analogy**: Like player onboarding — registered, equipped, trained, played, retired.

---

### 34. Difference between Singleton and Prototype scopes?

| Scope       | Behavior                                |
|-------------|------------------------------------------|
| Singleton   | One instance per Spring container        |
| Prototype   | New instance each time it’s requested    |

🎮 **Analogy**: Singleton = team captain shared in every match. Prototype = new substitute every game.

---

### 35. What is @Autowired and how does it work internally?

`@Autowired` tells Spring to inject dependencies automatically.

- It checks by type first (`ApplicationContext`)
- Can also work with qualifiers for multiple beans

🎮 **Analogy**: Like assigning auto-loot to your inventory — Spring gives you what you need, when you need it.

---

### 36. Field vs Constructor vs Setter Injection — which is preferred?

✅ **Constructor Injection** is preferred:
- Ensures immutability
- Better for testing
- Helps in circular dependency detection

🎮 **Analogy**:
- Constructor = getting all weapons at spawn
- Setter = adding them later
- Field = magically appearing, not test-friendly

---

### 37. How do you handle exceptions in Spring Boot? (Global Exception Handling)

Use `@ControllerAdvice` with `@ExceptionHandler` to handle exceptions globally.

📦 Example:
```java
@ControllerAdvice
public class GlobalHandler {
    @ExceptionHandler(CustomException.class)
    public ResponseEntity<?> handleCustom(CustomException ex) {
        return ResponseEntity.status(400).body(ex.getMessage());
    }
}
```

🎮 **Analogy**: Like having a universal error screen in a game when anything fails.

---

### 38. What is a RestController? Difference with Controller?

- `@RestController` = `@Controller` + `@ResponseBody`
- Used for REST APIs that return JSON/XML, not views

🎮 **Analogy**: Controller = game menu screen, RestController = game API backend sending live data.

---

### 39. What is ResponseEntity and when to use it?

`ResponseEntity` lets you control:
- HTTP status codes
- Headers
- Response body

📦 Example:
```java
return new ResponseEntity<>("OK", HttpStatus.CREATED);
```

🎮 **Analogy**: Like choosing how your server responds to game clients — success, error, data type, etc.

---

### 40. What is Spring Boot Starter and AutoConfiguration?

- **Starter**: Predefined dependencies for common use cases (e.g., `spring-boot-starter-web`)
- **AutoConfiguration**: Spring auto-configures beans based on classpath and config

🎮 **Analogy**: Starters = pre-built loadouts. AutoConfig = game auto-adjusting settings for best performance.

---

### 41. Key Spring Boot Annotations in REST API

- `@SpringBootApplication`
- `@RestController`
- `@GetMapping`, `@PostMapping`, etc.
- `@Autowired`
- `@Service`, `@Repository`

🎮 **Analogy**: Like equipping all roles, tools, and powerups before starting a mission.

---

### 42. How do you connect Spring Boot with a Database?

1. Add DB dependency in `pom.xml`
2. Configure in `application.properties`
3. Use Spring Data JPA (`@Repository`)

🎮 **Analogy**: Like plugging your game into an online leaderboard — link established.

---

### 43. What is Spring Data JPA? Repositories?

Spring Data JPA helps avoid boilerplate by auto-implementing DB access methods via interfaces.

📦 Example:
```java
public interface UserRepo extends JpaRepository<User, Long> {}
```

🎮 **Analogy**: Like auto-aim in a shooter — just define target, framework handles the action.

---

### 44. What is Hibernate? Difference with JDBC?

- **Hibernate** is an ORM — maps Java objects to DB tables
- **JDBC** is low-level, manual SQL execution

🎮 **Analogy**: Hibernate = auto-drive mode. JDBC = manual steering.

---

### 45. Lazy vs Eager loading in Hibernate?

| Type     | Behavior                               |
|----------|----------------------------------------|
| Lazy     | Loads related data only when accessed  |
| Eager    | Loads related data immediately         |

🎮 **Analogy**: Lazy = loading maps on-demand. Eager = loading all maps at game start.

---

### 46. How do you handle transactions in Spring? (@Transactional)

Use `@Transactional` to manage DB operations atomically.

📦 Example:
```java
@Transactional
public void transferMoney() {
    // withdraw + deposit = one atomic operation
}
```

🎮 **Analogy**: Like a combo move — if one part fails, entire move gets canceled.

---

### 47. How do you validate incoming request bodies in Spring Boot?

Use `@Valid` or `@Validated` with bean validation annotations like `@NotNull`, `@Size`, etc.

📦 Example:
```java
public ResponseEntity<?> create(@Valid @RequestBody User u) { ... }
```

🎮 **Analogy**: Like checking player stats before letting them join a tournament.

---
