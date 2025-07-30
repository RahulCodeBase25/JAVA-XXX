
# 🧾 J2EE Interview Q&A (Servlets, JSP, Filters, Listeners)

---

### 21. What is a Servlet? Servlet Lifecycle?

A **Servlet** handles HTTP requests and responses in a Java web application.

**Lifecycle Methods**:
1. `init()` — Called once at startup  
2. `service()` — Called for each request  
3. `destroy()` — Called before removal

📦 **Example**:
```java
public void doGet(HttpServletRequest req, HttpServletResponse res) {
    res.getWriter().println("Hello!");
}
```

🎮 **Analogy**: NPC in a multiplayer game — loaded once, interacts repeatedly, and removed cleanly.

---

### 22. Difference between doGet() and doPost()

| Aspect         | `doGet()`                          | `doPost()`                         |
|----------------|------------------------------------|-------------------------------------|
| Data in URL    | Yes                                | No                                  |
| Data Limit     | Limited                            | Large                               |
| Caching        | Allowed                            | Not cached                          |
| Use case       | Fetch data                         | Submit data                         |
| Idempotent     | Yes                                | No                                  |

🎮 **Analogy**:  
- `doGet()` = watching a game  
- `doPost()` = sending input in-game

---

### 23. What is a Filter in J2EE? Use Case?

A **Filter** intercepts requests/responses before they reach servlets.

✅ **Used for**:
- Authentication
- Logging
- Response compression

📦 **Example**:
```java
chain.doFilter(request, response);
```

🎮 **Analogy**: Like a **bouncer** checking players before letting them enter the game.

---

### 24. What are Listeners in J2EE?

Listeners monitor **application, session, or request** events.

✅ **Types**:
- `ServletContextListener`
- `HttpSessionListener`
- `ServletRequestListener`

📦 **Example**:
```java
public void contextInitialized(...) {
    System.out.println("App Started");
}
```

🎮 **Analogy**: Game observer — tracks when a player joins or leaves.

---

### 25. JSP vs Servlet — When to use which?

| Feature    | Servlet               | JSP                          |
|------------|------------------------|-------------------------------|
| Role       | Business logic         | UI rendering                  |
| Language   | Java                   | HTML + Java                   |
| Compiles   | Manually or precompiled| Compiled to servlet internally|

🎮 **Analogy**:  
- Servlet = Game engine  
- JSP = Game UI screen

---

### 26. How is session maintained in Java web apps?

Java uses a **session ID** (often in cookies) to identify users.

✅ **Methods**:
- Cookies (default)
- URL Rewriting
- Hidden Fields

📦 **Example**:
```java
HttpSession session = request.getSession();
```

🎮 **Analogy**: Like a player token that keeps your state when you rejoin a multiplayer game.

---

### 27. Cookies vs Session vs URL Rewriting

| Feature      | Cookies            | Session           | URL Rewriting              |
|--------------|--------------------|--------------------|-----------------------------|
| Stored in    | Browser            | Server             | URL                        |
| Security     | Less secure        | More secure        | Visible in URL             |
| Size Limit   | 4KB                | Server-dependent   | No strict limit            |

🎮 **Analogy**:  
- Cookies = name tag  
- Session = saved profile  
- URL Rewriting = info in URL query

---

### 28. What is a RequestDispatcher and how does it work?

Used to **forward** or **include** requests between servlets/JSPs.

📦 **Example**:
```java
RequestDispatcher rd = request.getRequestDispatcher("dashboard.jsp");
rd.forward(request, response);
```

🎮 **Analogy**: Like handing over the controller to a teammate (`forward`) or asking them to assist you (`include`).
