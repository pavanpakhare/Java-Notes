# Java-Notes
# Java Basic Tutorial

Java is one of the most popular programming languages, known for its "write once, run anywhere" capability. This tutorial covers the fundamentals of Java programming.

## Table of Contents
1. [Introduction to Java](#introduction-to-java)
2. [Setting Up Java](#setting-up-java)
3. [Basic Syntax](#basic-syntax)
4. [Variables and Data Types](#variables-and-data-types)
5. [Operators](#operators)
6. [Control Flow Statements](#control-flow-statements)
7. [Arrays](#arrays)
8. [Methods](#methods)
9. [Object-Oriented Programming](#object-oriented-programming)
10. [Exception Handling](#exception-handling)

## Introduction to Java

Java is:
- Object-oriented
- Platform-independent (thanks to JVM)
- Strongly typed
- Multi-threaded
- Used for web, mobile, desktop, and enterprise applications

## Setting Up Java

1. Download and install JDK from [Oracle's website](https://www.oracle.com/java/technologies/javase-downloads.html)
2. Set up JAVA_HOME environment variable
3. Verify installation with:
   ```bash
   java -version
   javac -version
   ```

## Basic Syntax

```java
// HelloWorld.java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello, World!");
    }
}
```

To compile and run:
```bash
javac HelloWorld.java
java HelloWorld
```

## Variables and Data Types

Java has two categories of data types:
1. Primitive types:
   - `byte`, `short`, `int`, `long` (integers)
   - `float`, `double` (floating-point)
   - `char` (single character)
   - `boolean` (true/false)

2. Reference types:
   - Objects
   - Arrays
   - Strings

Example:
```java
int age = 25;
double price = 19.99;
char grade = 'A';
boolean isJavaFun = true;
String name = "John Doe";
```

## Operators

Java supports various operators:
- Arithmetic: `+`, `-`, `*`, `/`, `%`
- Assignment: `=`, `+=`, `-=`, etc.
- Comparison: `==`, `!=`, `>`, `<`, `>=`, `<=`
- Logical: `&&`, `||`, `!`
- Bitwise: `&`, `|`, `^`, `~`, `<<`, `>>`, `>>>`

Example:
```java
int a = 10, b = 20;
int sum = a + b;
boolean isEqual = (a == b);
```

## Control Flow Statements

### If-else
```java
if (condition) {
    // code
} else if (anotherCondition) {
    // code
} else {
    // code
}
```

### Switch
```java
switch (variable) {
    case value1:
        // code
        break;
    case value2:
        // code
        break;
    default:
        // code
}
```

### Loops
```java
// for loop
for (int i = 0; i < 10; i++) {
    System.out.println(i);
}

// while loop
int j = 0;
while (j < 10) {
    System.out.println(j);
    j++;
}

// do-while loop
int k = 0;
do {
    System.out.println(k);
    k++;
} while (k < 10);
```

## Arrays

```java
// Declaration and initialization
int[] numbers = new int[5];
int[] numbers = {1, 2, 3, 4, 5};

// Accessing elements
int first = numbers[0];

// Length
int length = numbers.length;

// Multi-dimensional arrays
int[][] matrix = new int[3][3];
```

## Methods

```java
// Method definition
public static int add(int a, int b) {
    return a + b;
}

// Method call
int result = add(5, 3);
```

## Object-Oriented Programming

### Classes and Objects
```java
// Class definition
public class Dog {
    // Fields
    String breed;
    int age;
    
    // Constructor
    public Dog(String breed, int age) {
        this.breed = breed;
        this.age = age;
    }
    
    // Method
    public void bark() {
        System.out.println("Woof!");
    }
}

// Creating objects
Dog myDog = new Dog("Labrador", 3);
myDog.bark();
```

### Inheritance
```java
public class Animal {
    public void eat() {
        System.out.println("Eating...");
    }
}

public class Cat extends Animal {
    public void meow() {
        System.out.println("Meow!");
    }
}

Cat myCat = new Cat();
myCat.eat();  // Inherited method
myCat.meow(); // Own method
```

### Polymorphism
```java
Animal myAnimal = new Cat();  // Upcasting
myAnimal.eat();
```

### Encapsulation
```java
public class Person {
    private String name;
    
    public String getName() {
        return name;
    }
    
    public void setName(String name) {
        this.name = name;
    }
}
```

## Exception Handling

```java
try {
    // Code that might throw an exception
    int result = 10 / 0;
} catch (ArithmeticException e) {
    System.out.println("Cannot divide by zero!");
} finally {
    System.out.println("This always executes");
}
```

### Throwing exceptions
```java
public void checkAge(int age) throws Exception {
    if (age < 18) {
        throw new Exception("Age must be 18+");
    }
}
```

# Java Intermediate Tutorial

This intermediate Java tutorial builds on the basics and covers more advanced concepts that are essential for becoming a proficient Java developer.

## Table of Contents
1. [Collections Framework](#collections-framework)
2. [Generics](#generics)
3. [Input/Output (I/O) Streams](#inputoutput-io-streams)
4. [Multithreading](#multithreading)
5. [Lambda Expressions](#lambda-expressions)
6. [Stream API](#stream-api)
7. [Java Date and Time API](#java-date-and-time-api)
8. [Annotations](#annotations)
9. [Java Database Connectivity (JDBC)](#java-database-connectivity-jdbc)
10. [Unit Testing with JUnit](#unit-testing-with-junit)

## Collections Framework

The Java Collections Framework provides implementations of common data structures.

### Main Interfaces
- `List` - Ordered collection (ArrayList, LinkedList)
- `Set` - Unique elements (HashSet, TreeSet)
- `Queue` - FIFO (LinkedList, PriorityQueue)
- `Map` - Key-value pairs (HashMap, TreeMap)

### Examples
```java
// ArrayList
List<String> names = new ArrayList<>();
names.add("Alice");
names.add("Bob");
names.get(0); // "Alice"

// HashSet
Set<Integer> numbers = new HashSet<>();
numbers.add(1);
numbers.add(1); // Duplicate ignored

// HashMap
Map<String, Integer> ages = new HashMap<>();
ages.put("Alice", 25);
ages.put("Bob", 30);
ages.get("Alice"); // 25
```

## Generics

Generics provide type safety and eliminate the need for casting.

```java
// Generic class
public class Box<T> {
    private T content;
    
    public void setContent(T content) {
        this.content = content;
    }
    
    public T getContent() {
        return content;
    }
}

// Usage
Box<String> stringBox = new Box<>();
stringBox.setContent("Hello");
String value = stringBox.getContent(); // No casting needed

// Generic methods
public <T> void printArray(T[] array) {
    for (T element : array) {
        System.out.println(element);
    }
}
```

## Input/Output (I/O) Streams

Java I/O is used for reading from and writing to files, network connections, etc.

### File I/O
```java
// Writing to a file
try (BufferedWriter writer = new BufferedWriter(new FileWriter("file.txt"))) {
    writer.write("Hello, World!");
} catch (IOException e) {
    e.printStackTrace();
}

// Reading from a file
try (BufferedReader reader = new BufferedReader(new FileReader("file.txt"))) {
    String line;
    while ((line = reader.readLine()) != null) {
        System.out.println(line);
    }
} catch (IOException e) {
    e.printStackTrace();
}
```

### Serialization
```java
public class Person implements Serializable {
    private String name;
    private int age;
    // constructors, getters, setters
}

// Serialize
try (ObjectOutputStream oos = new ObjectOutputStream(new FileOutputStream("person.ser"))) {
    oos.writeObject(new Person("Alice", 25));
}

// Deserialize
try (ObjectInputStream ois = new ObjectInputStream(new FileInputStream("person.ser"))) {
    Person person = (Person) ois.readObject();
    System.out.println(person.getName());
}
```

## Multithreading

Java supports multithreading for concurrent programming.

### Creating Threads
```java
// Extending Thread class
class MyThread extends Thread {
    public void run() {
        System.out.println("Thread is running");
    }
}

// Implementing Runnable interface
class MyRunnable implements Runnable {
    public void run() {
        System.out.println("Runnable is running");
    }
}

// Usage
Thread thread1 = new MyThread();
Thread thread2 = new Thread(new MyRunnable());
thread1.start();
thread2.start();
```

### Synchronization
```java
class Counter {
    private int count = 0;
    
    public synchronized void increment() {
        count++;
    }
    
    public int getCount() {
        return count;
    }
}
```

### Executor Framework
```java
ExecutorService executor = Executors.newFixedThreadPool(5);
for (int i = 0; i < 10; i++) {
    executor.execute(() -> {
        System.out.println("Task executed by " + Thread.currentThread().getName());
    });
}
executor.shutdown();
```

## Lambda Expressions

Lambda expressions provide a concise way to implement functional interfaces.

```java
// Before Java 8
Runnable r = new Runnable() {
    public void run() {
        System.out.println("Hello");
    }
};

// With lambda
Runnable r = () -> System.out.println("Hello");

// Functional interfaces
interface MathOperation {
    int operate(int a, int b);
}

MathOperation add = (a, b) -> a + b;
System.out.println(add.operate(5, 3)); // 8
```

## Stream API

The Stream API provides functional-style operations on streams of elements.

```java
List<String> names = Arrays.asList("Alice", "Bob", "Charlie", "David");

// Filter and map
List<String> result = names.stream()
    .filter(name -> name.startsWith("A"))
    .map(String::toUpperCase)
    .collect(Collectors.toList());

// forEach
names.stream().forEach(System.out::println);

// reduce
int sum = IntStream.range(1, 5).reduce(0, (a, b) -> a + b);
```

## Java Date and Time API

Java 8 introduced a new Date and Time API in the `java.time` package.

```java
// Current date
LocalDate today = LocalDate.now();

// Specific date
LocalDate birthday = LocalDate.of(1990, Month.JANUARY, 1);

// Date arithmetic
LocalDate nextWeek = today.plusWeeks(1);

// Formatting
DateTimeFormatter formatter = DateTimeFormatter.ofPattern("dd/MM/yyyy");
String formattedDate = today.format(formatter);

// Parsing
LocalDate parsedDate = LocalDate.parse("25/12/2023", formatter);

// Duration and Period
Duration duration = Duration.between(LocalTime.now(), LocalTime.now().plusHours(2));
Period period = Period.between(LocalDate.now(), LocalDate.now().plusDays(10));
```

## Annotations

Annotations provide metadata about the code.

### Built-in Annotations
```java
@Override
public String toString() {
    return "Custom toString";
}

@Deprecated
public void oldMethod() {}

@SuppressWarnings("unchecked")
List list = new ArrayList();
```

### Custom Annotations
```java
@Retention(RetentionPolicy.RUNTIME)
@Target(ElementType.METHOD)
public @interface TestAnnotation {
    String value() default "default";
    int count() default 1;
}

// Usage
@TestAnnotation(value = "test", count = 5)
public void annotatedMethod() {}
```

## Java Database Connectivity (JDBC)

JDBC is used to connect to databases.

```java
// Connection setup
String url = "jdbc:mysql://localhost:3306/mydb";
String username = "user";
String password = "pass";

try (Connection connection = DriverManager.getConnection(url, username, password)) {
    // Statement
    Statement statement = connection.createStatement();
    ResultSet rs = statement.executeQuery("SELECT * FROM users");
    
    // PreparedStatement (prevents SQL injection)
    PreparedStatement ps = connection.prepareStatement("INSERT INTO users VALUES (?, ?)");
    ps.setString(1, "Alice");
    ps.setInt(2, 25);
    ps.executeUpdate();
    
    // Processing ResultSet
    while (rs.next()) {
        String name = rs.getString("name");
        int age = rs.getInt("age");
        System.out.println(name + ": " + age);
    }
} catch (SQLException e) {
    e.printStackTrace();
}
```

## Unit Testing with JUnit

JUnit is a popular testing framework for Java.

```java
import org.junit.jupiter.api.Test;
import static org.junit.jupiter.api.Assertions.*;

class CalculatorTest {
    
    @Test
    void testAdd() {
        Calculator calculator = new Calculator();
        assertEquals(5, calculator.add(2, 3));
    }
    
    @Test
    void testDivide() {
        Calculator calculator = new Calculator();
        assertThrows(ArithmeticException.class, () -> calculator.divide(1, 0));
    }
}

class Calculator {
    public int add(int a, int b) {
        return a + b;
    }
    
    public int divide(int a, int b) {
        if (b == 0) {
            throw new ArithmeticException("Division by zero");
        }
        return a / b;
    }
}
```


