# MCX India Java Developer Interview Prep Guide (Technical Only)

This guide covers the **top 5 technical areas** frequently asked in MCX India Java backend interviews, based on actual interview experiences and patterns. Behavioral/domain questions are skipped as per request.

---

## 1. Core Java & Linked List

### Q1: Explain Runtime vs Compile-Time Polymorphism in Java

**Answer:**

- **Compile-time polymorphism**: Achieved via **method overloading** (same method name, different parameters).
- **Runtime polymorphism**: Achieved via **method overriding** using inheritance and dynamic binding.

**Example:**

```java
class Animal {
    void sound() {
        System.out.println("Animal sound");
    }
}

class Dog extends Animal {
    void sound() {
        System.out.println("Dog barks");
    }
}

Animal a = new Dog();
a.sound(); // Runtime polymorphism
```

---

### Q2: Find the Midpoint in a Singly Linked List

**Pattern:** Fast and Slow Pointer

**Code:**

```java
class ListNode {
    int val;
    ListNode next;
    ListNode(int x) { val = x; }
}

public ListNode findMiddle(ListNode head) {
    ListNode slow = head, fast = head;
    while (fast != null && fast.next != null) {
        slow = slow.next;
        fast = fast.next.next;
    }
    return slow; // Midpoint
}
```

---

## 2. Java 8 Features

### Q3: What are Streams in Java 8?

**Answer:** Streams are used to perform functional-style operations on sequences of elements (Collections).

**Example:**

```java
List<String> names = Arrays.asList("Rahul", "Ravi", "Ramesh");
names.stream()
     .filter(name -> name.startsWith("Ra"))
     .forEach(System.out::println);
```

---

### Q4: What are Lambda Expressions?

**Answer:** Lambda expressions provide a clear and concise way to represent functional interfaces using an anonymous function.

**Example:**

```java
List<Integer> list = Arrays.asList(1, 2, 3, 4);
list.forEach(n -> System.out.println(n * n));
```

---

## 3. Algorithmic Logic

### Q5: Check if a number is Prime without using %, /, or \* operators

**Logic:** Subtract all possible divisors and check if remainder ever becomes zero.

**Code:**

```java
public boolean isPrime(int n) {
    if (n <= 1) return false;
    for (int i = 2; i < n; i++) {
        int num = n;
        int count = 0;
        while (num >= i) {
            num = num - i;
            count++;
        }
        if (num == 0) return false; // evenly divisible
    }
    return true;
}
```

---

## 4. Recursion

### Q6: Print numbers from 1 to N using recursion

**Code:**

```java
public void printNumbers(int n) {
    if (n == 0) return;
    printNumbers(n - 1);
    System.out.print(n + " ");
}
```

---

### Q7: Explain base case and recursion stack

**Answer:**

- **Base case**: Stops recursion (prevents infinite loop).
- **Recursive call**: Pushes current state onto stack.

In the above example, numbers are printed after returning from recursion (LIFO).

---

## 5. Multithreading & OOP Comparison

### Q8: What is thread safety? How do you achieve it?

**Answer:** Thread safety means shared data remains consistent when accessed by multiple threads. Achieved using:

- `synchronized` methods/blocks
- `volatile` keyword
- Concurrent collections (e.g., `ConcurrentHashMap`)

---

### Q9: Synchronized vs Volatile

**synchronized**: Ensures only one thread can execute a block/method at a time.

**volatile**: Ensures visibility of changes to variables across threads.

---

### Q10: Difference between OOP in C++ vs Java

| Feature              | C++                 | Java                          |
| -------------------- | ------------------- | ----------------------------- |
| Multiple Inheritance | Yes (via classes)   | No (only via interfaces)      |
| Memory Management    | Manual (new/delete) | Automatic (Garbage Collector) |
| Pointers             | Yes                 | No direct pointer support     |

---

### Q11: Runnable vs Thread

**Runnable**: Interface to implement task logic. **Thread**: Class to represent a thread.

```java
// Runnable implementation
class MyTask implements Runnable {
    public void run() {
        System.out.println("Task running");
    }
}

Thread t = new Thread(new MyTask());
t.start();
```

---

This is your complete technical prep set based on real MCX India Java developer interviews. Focus on these and you’re ready for battle! 💪

