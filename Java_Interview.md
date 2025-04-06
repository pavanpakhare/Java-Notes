# **Java Theory Notes**  

## **1. Object-Oriented Programming (OOP) Concepts**  

### **1.1 Four Pillars of OOP**  
1. **Encapsulation**  
   - Bundling data (variables) and methods (functions) into a single unit (class).  
   - Achieved using **private** variables and **public getters/setters**.  
   - Example:  
     ```java
     public class Person {
         private String name; // Encapsulated field
         public String getName() { return name; }
         public void setName(String name) { this.name = name; }
     }
     ```

2. **Abstraction**  
   - Hiding complex implementation details and exposing only necessary features.  
   - Achieved using **abstract classes** and **interfaces**.  
   - Example:  
     ```java
     abstract class Animal {
         abstract void sound(); // Abstract method (no implementation)
     }
     ```

3. **Inheritance**  
   - **IS-A** relationship where a subclass extends a superclass.  
   - Promotes **code reusability**.  
   - Example:  
     ```java
     class Dog extends Animal {
         void sound() { System.out.println("Bark!"); }
     }
     ```

4. **Polymorphism**  
   - **"Many forms"** – Same method behaves differently based on context.  
   - Types:  
     - **Compile-time (Method Overloading)**  
       ```java
       void add(int a, int b) { }
       void add(double a, double b) { }
       ```
     - **Runtime (Method Overriding)**  
       ```java
       @Override
       void sound() { System.out.println("Meow!"); }
       ```

---

## **2. Java Basics**  

### **2.1 Data Types**  
- **Primitives** (Stored in stack, faster):  
  `byte`, `short`, `int`, `long`, `float`, `double`, `char`, `boolean`  
- **Objects (Wrapper Classes)**:  
  `Integer`, `Double`, `String`, etc.  

### **2.2 String vs StringBuilder vs StringBuffer**  
| Feature        | String          | StringBuilder | StringBuffer |
|--------------|--------------|--------------|--------------|
| **Mutability** | Immutable | Mutable | Mutable |
| **Thread-Safe** | Yes | No | Yes (synchronized) |
| **Performance** | Slow (new object per change) | Fast | Slower than StringBuilder |

### **2.3 final Keyword**  
- **final variable**: Constant (cannot be modified).  
- **final method**: Cannot be overridden.  
- **final class**: Cannot be inherited.  

### **2.4 static Keyword**  
- Belongs to the **class** (not instance).  
- Used for **utility methods**, **constants**, and **singleton patterns**.  
- Example:  
  ```java
  class MathUtils {
      static final double PI = 3.14;
      static int add(int a, int b) { return a + b; }
  }
  ```

---

## **3. Exception Handling**  

### **3.1 Exception Hierarchy**  
```
Throwable  
├── **Error** (e.g., OutOfMemoryError)  
└── **Exception**  
    ├── **Checked** (Compile-time, must handle)  
    │   └── IOException, SQLException  
    └── **Unchecked** (Runtime)  
        └── NullPointerException, ArrayIndexOutOfBoundsException  
```

### **3.2 try-catch-finally**  
```java
try {
    // Risky code
} catch (IOException e) {
    // Handle exception
} finally {
    // Always executes (for cleanup)
}
```

### **3.3 try-with-resources**  
- Automatically closes resources (implements `AutoCloseable`).  
```java
try (FileInputStream fis = new FileInputStream("file.txt")) {
    // Use fis
} catch (IOException e) {
    e.printStackTrace();
}
```

---

## **4. Collections Framework**  

### **4.1 List (Ordered, Allows Duplicates)**  
- **ArrayList**: Dynamic array (fast random access).  
- **LinkedList**: Doubly-linked list (fast insertions/deletions).  

### **4.2 Set (No Duplicates)**  
- **HashSet**: Unordered, O(1) operations.  
- **LinkedHashSet**: Maintains insertion order.  
- **TreeSet**: Sorted (natural order / Comparator).  

### **4.3 Map (Key-Value Pairs)**  
- **HashMap**: O(1), no order, allows one `null` key.  
- **LinkedHashMap**: Maintains insertion order.  
- **TreeMap**: Sorted keys.  
- **ConcurrentHashMap**: Thread-safe alternative to `HashMap`.  

---

## **5. Multithreading & Concurrency**  

### **5.1 Thread Lifecycle**  
1. **New** → `new Thread()`  
2. **Runnable** → `start()`  
3. **Running** → Executing  
4. **Blocked/Waiting** → Waiting for lock/notify  
5. **Terminated** → Execution completed  

### **5.2 Creating Threads**  
1. **Extending `Thread` class**  
   ```java
   class MyThread extends Thread {
       public void run() { System.out.println("Thread running"); }
   }
   ```
2. **Implementing `Runnable`** (Preferred)  
   ```java
   class MyRunnable implements Runnable {
       public void run() { System.out.println("Runnable running"); }
   }
   ```

### **5.3 Synchronization**  
- **synchronized** methods/blocks prevent race conditions.  
- **volatile** ensures visibility across threads (no caching).  
- **Atomic classes** (`AtomicInteger`) provide lock-free thread safety.  

---

## **6. Java Memory Model (JMM)**  

### **6.1 Memory Areas**  
- **Heap**: Stores objects (shared across threads).  
- **Stack**: Stores method calls & local variables (thread-specific).  
- **Method Area**: Class metadata, static variables.  

### **6.2 Garbage Collection (GC)**  
- **Young Generation (Minor GC)**: Eden, Survivor spaces.  
- **Old Generation (Major GC)**: Long-lived objects.  
- **GC Algorithms**:  
  - **Mark-Sweep** (Identify & delete unreachable objects).  
  - **Mark-Compact** (Defragments memory).  
  - **G1 (Garbage-First)**: Default in Java 9+.  

---

## **7. Java 8+ Features**  

### **7.1 Lambda Expressions**  
```java
List<Integer> nums = Arrays.asList(1, 2, 3);
nums.forEach(n -> System.out.println(n));
```

### **7.2 Stream API**  
```java
List<String> filtered = names.stream()
    .filter(s -> s.startsWith("A"))
    .collect(Collectors.toList());
```

### **7.3 Optional (Avoid Null Checks)**  
```java
Optional<String> name = Optional.ofNullable(getName());
String result = name.orElse("Default");
```

---

## **8. Design Patterns**  

### **8.1 Singleton (One Instance Only)**  
```java
class Singleton {
    private static Singleton instance;
    private Singleton() { }
    public static Singleton getInstance() {
        if (instance == null) {
            instance = new Singleton();
        }
        return instance;
    }
}
```

### **8.2 Factory Pattern (Decouple Object Creation)**  
```java
interface Vehicle { void drive(); }
class Car implements Vehicle { ... }
class Bike implements Vehicle { ... }

class VehicleFactory {
    public Vehicle getVehicle(String type) {
        if (type.equals("car")) return new Car();
        else return new Bike();
    }
}
```

---

## **9. Common Interview Questions**  
1. **Difference between `==` and `.equals()`?**  
   - `==` checks reference equality.  
   - `.equals()` checks content equality (can be overridden).  

2. **How does `HashMap` work internally?**  
   - Uses **hashing** (key → hash → bucket).  
   - Handles collisions via **linked lists** (Java 8: converts to tree if large).  

3. **Why is `String` immutable?**  
   - Security, thread-safety, caching (String Pool).  

4. **`ArrayList` vs `LinkedList`?**  
   - **ArrayList**: Fast random access, slow insertions/deletions.  
   - **LinkedList**: Slow random access, fast insertions/deletions.  

5. **How to prevent deadlock?**  
   - Avoid nested locks, use timeouts, lock ordering.  

---

