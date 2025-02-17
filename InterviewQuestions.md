# Java, Spring Boot, and Microservices Interview Questions and Answers

---

## 1. How to make sure that your microservice is secured?

- **Authentication & Authorization:** Implement OAuth2, JWT, or use API Gateway security to ensure only authenticated users access your services.
- **Transport Security:** Use HTTPS to encrypt data in transit.
- **Input Validation:** Validate all incoming data to prevent injection attacks (e.g., SQL injection, XSS).
- **Rate Limiting:** Apply rate limiting/throttling to mitigate denial-of-service attacks.
- **Role-Based Access Control (RBAC):** Enforce fine-grained permissions.
- **Logging & Monitoring:** Continuously log and monitor for suspicious behavior.
- **Dependency Management:** Regularly update libraries to avoid known vulnerabilities.

> **Example:**  
> In Spring Security, you can configure JWT filters that intercept requests and verify tokens before they reach your endpoints.

---

## 2. Difference between `map` and `flatMap` in Java Streams

- **`map()`:** Applies a function to each element of the stream and returns a new stream of the results.
- **`flatMap()`:** Similar to `map()`, but each element is replaced with a stream, and then those streams are flattened into a single stream.

### Example:
```java
List<String> words = Arrays.asList("Hello", "World");
List<String> letters = words.stream()
    .map(word -> word.split(""))       // Returns Stream<String[]>
    .flatMap(Arrays::stream)             // Flattens into Stream<String>
    .collect(Collectors.toList());
System.out.println(letters); // [H, e, l, l, o, W, o, r, l, d]
