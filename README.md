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

