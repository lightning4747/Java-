# Java Basics Study Notes

## Table of Contents
1. [Introduction to Java](#introduction-to-java)
2. [Setting Up Java](#setting-up-java)
3. [Basic Syntax](#basic-syntax)
4. [Data Types](#data-types)
5. [Variables](#variables)
6. [Operators](#operators)
7. [Control Flow](#control-flow)
8. [Arrays](#arrays)
9. [Methods](#methods)
10. [Object-Oriented Programming](#object-oriented-programming)
11. [Exception Handling](#exception-handling)
12. [File I/O Basics](#file-io-basics)

---

## Introduction to Java

Java is a high-level, object-oriented programming language designed for cross-platform compatibility and robust application development.

### Key Characteristics
- **High-level programming language** - Easy to read and write
- **Object-oriented** - Based on objects and classes
- **Platform independent** - "Write Once, Run Anywhere" (WORA)

### Key Features
- **Simple** - Clean syntax, automatic memory management
- **Secure** - Built-in security features, no pointers
- **Portable** - Runs on any platform with JVM
- **Robust** - Strong error handling and memory management
- **Multithreaded** - Built-in support for concurrent execution

---

## Setting Up Java

### Installation Steps
1. **Install JDK (Java Development Kit)**
   - Download from Oracle or OpenJDK
   - Choose appropriate version for your operating system

2. **Set PATH environment variable**
   - Add JDK bin directory to system PATH
   - Set JAVA_HOME environment variable

3. **Verify installation**
   ```bash
   java -version
   javac -version
   ```

Expected output should show Java version information.

---

## Basic Syntax

### Basic Program Structure

```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello, World!");
    }
}
```

### Key Rules
- Class name must match filename
- `main` method is the entry point
- Case-sensitive language
- Statements end with semicolon
- Code blocks use curly braces `{}`

---

## Data Types

Java has two categories of data types: primitive and reference types.

### Primitive Types

| Type | Size | Description |
|------|------|-------------|
| `byte` | 8-bit | Integer (-128 to 127) |
| `short` | 16-bit | Integer (-32,768 to 32,767) |
| `int` | 32-bit | Integer (most commonly used) |
| `long` | 64-bit | Integer (large numbers) |
| `float` | 32-bit | Floating point number |
| `double` | 64-bit | Double precision floating point |
| `boolean` | 1-bit | true or false |
| `char` | 16-bit | Unicode character |

### Reference Types
- **Objects** - Instances of classes
- **Arrays** - Collections of elements
- **Strings** - Sequences of characters

---

## Variables

Variables are containers that store data values.

### Variable Declaration Examples

```java
// Primitive variables
int age = 25;
double price = 19.99;
char grade = 'A';
boolean isJavaFun = true;

// Reference variable
String name = "John";

// Multiple variables
int x = 5, y = 10, z = 15;

// Constants
final double PI = 3.14159;
```

### Naming Rules
- Start with letter, underscore, or dollar sign
- Can contain letters, digits, underscores
- Cannot be Java keywords
- Use camelCase convention

---

## Operators

### Arithmetic Operators
```java
int a = 10, b = 3;
int sum = a + b;        // Addition: 13
int diff = a - b;       // Subtraction: 7
int product = a * b;    // Multiplication: 30
int quotient = a / b;   // Division: 3
int remainder = a % b;  // Modulus: 1
a++;                   // Increment
b--;                   // Decrement
```

### Assignment Operators
```java
int x = 10;
x += 5;  // x = x + 5
x -= 3;  // x = x - 3
x *= 2;  // x = x * 2
x /= 4;  // x = x / 4
x %= 3;  // x = x % 3
```

### Comparison Operators
```java
int a = 5, b = 3;
boolean result = a == b;  // Equal to: false
result = a != b;          // Not equal: true
result = a > b;           // Greater than: true
result = a < b;           // Less than: false
result = a >= b;          // Greater or equal: true
result = a <= b;          // Less or equal: false
```

### Logical Operators
```java
boolean x = true, y = false;
boolean and = x && y;     // AND: false
boolean or = x || y;      // OR: true
boolean not = !x;         // NOT: false
```

### Bitwise Operators
- `&` - AND
- `|` - OR
- `^` - XOR
- `~` - NOT
- `<<` - Left shift
- `>>` - Right shift
- `>>>` - Unsigned right shift

---

## Control Flow

### If-Else Statements

```java
if (condition) {
    // Execute if condition is true
} else if (anotherCondition) {
    // Execute if another condition is true
} else {
    // Execute if all conditions are false
}
```

### Switch Statement

```java
switch(expression) {
    case value1:
        // Code for value1
        break;
    case value2:
        // Code for value2
        break;
    default:
        // Default case
        break;
}
```

### Loops

#### For Loop
```java
for (int i = 0; i < 10; i++) {
    System.out.println(i);
}
```

#### While Loop
```java
while (condition) {
    // Code to execute
    // Update condition to avoid infinite loop
}
```

#### Do-While Loop
```java
do {
    // Code to execute
} while (condition);
```

#### Enhanced For Loop
```java
int[] numbers = {1, 2, 3, 4, 5};
for (int num : numbers) {
    System.out.println(num);
}
```

---

## Arrays

Arrays store multiple values of the same type in a single variable.

### Array Declaration and Initialization

```java
// Declaration
int[] numbers;

// Initialization
numbers = new int[5];

// Combined declaration and initialization
int[] numbers = {1, 2, 3, 4, 5};

// Alternative syntax
int[] numbers = new int[]{1, 2, 3, 4, 5};
```

### Working with Arrays

```java
// Accessing elements
int first = numbers[0];    // First element
numbers[1] = 10;           // Modify element

// Array length
int size = numbers.length;

// Iterate through array
for (int i = 0; i < numbers.length; i++) {
    System.out.println(numbers[i]);
}

// Enhanced for loop
for (int num : numbers) {
    System.out.println(num);
}
```

### Multidimensional Arrays

```java
// 2D Array
int[][] matrix = {
    {1, 2, 3},
    {4, 5, 6},
    {7, 8, 9}
};

// Access element
int element = matrix[1][2]; // Row 1, Column 2
```

---

## Methods

Methods are reusable blocks of code that perform specific tasks.

### Method Structure

```java
accessModifier static returnType methodName(parameters) {
    // Method body
    return value; // if returnType is not void
}
```

### Method Examples

```java
// Method with return value
public static int add(int a, int b) {
    return a + b;
}

// Method without return value
public static void printMessage(String message) {
    System.out.println(message);
}

// Method call
int result = add(5, 3);
printMessage("Hello World");
```

### Method Overloading

```java
public class Calculator {
    // Different parameter types
    public static int add(int a, int b) {
        return a + b;
    }
    
    public static double add(double a, double b) {
        return a + b;
    }
    
    // Different number of parameters
    public static int add(int a, int b, int c) {
        return a + b + c;
    }
}
```

---

## Object-Oriented Programming

### Classes and Objects

```java
// Class definition
public class Car {
    // Fields (attributes)
    String color;
    String model;
    
    // Method (behavior)
    void start() {
        System.out.println("Car started");
    }
    
    void displayInfo() {
        System.out.println("Color: " + color + ", Model: " + model);
    }
}

// Object creation and usage
Car myCar = new Car();
myCar.color = "Red";
myCar.model = "Toyota";
myCar.start();
myCar.displayInfo();
```

### Constructors

Constructors are special methods that initialize objects when they're created.

```java
public class Car {
    String color;
    String model;
    
    // Constructor
    public Car(String carColor, String carModel) {
        color = carColor;
        model = carModel;
    }
    
    // Default constructor
    public Car() {
        color = "Unknown";
        model = "Unknown";
    }
}

// Using constructors
Car myCar = new Car("Blue", "Honda");
Car defaultCar = new Car();
```

### Inheritance

Inheritance allows a class to inherit properties and methods from another class.

```java
// Parent class
public class Vehicle {
    void move() {
        System.out.println("Vehicle is moving");
    }
}

// Child class
public class Car extends Vehicle {
    void honk() {
        System.out.println("Beep beep!");
    }
}

// Usage
Car myCar = new Car();
myCar.move();  // Inherited method
myCar.honk();  // Own method
```

### Encapsulation

```java
public class BankAccount {
    private double balance;  // Private field
    
    // Public methods to access private field
    public double getBalance() {
        return balance;
    }
    
    public void deposit(double amount) {
        if (amount > 0) {
            balance += amount;
        }
    }
    
    public void withdraw(double amount) {
        if (amount > 0 && amount <= balance) {
            balance -= amount;
        }
    }
}
```

---

## Exception Handling

Exception handling manages runtime errors gracefully.

### Try-Catch-Finally

```java
try {
    // Code that may throw an exception
    int result = 10 / 0;  // This will throw ArithmeticException
} catch (ArithmeticException e) {
    // Handle specific exception
    System.out.println("Cannot divide by zero!");
} catch (Exception e) {
    // Handle any other exception
    System.out.println("An error occurred: " + e.getMessage());
} finally {
    // Code that always executes
    System.out.println("Cleanup code here");
}
```

### Common Exception Types

- `ArithmeticException` - Division by zero
- `NullPointerException` - Accessing null reference
- `ArrayIndexOutOfBoundsException` - Invalid array index
- `NumberFormatException` - Invalid number format
- `IOException` - Input/Output errors

### Throwing Exceptions

```java
public static void checkAge(int age) {
    if (age < 0) {
        throw new IllegalArgumentException("Age cannot be negative");
    }
}
```

---

## File I/O Basics

Java provides several ways to read from and write to files.

### Writing to a File

```java
import java.io.FileWriter;
import java.io.IOException;

try {
    FileWriter writer = new FileWriter("file.txt");
    writer.write("Hello Java");
    writer.write("\nThis is line 2");
    writer.close();
    System.out.println("File written successfully");
} catch (IOException e) {
    System.out.println("An error occurred: " + e.getMessage());
}
```

### Reading from a File

```java
import java.io.File;
import java.io.FileNotFoundException;
import java.util.Scanner;

try {
    File file = new File("file.txt");
    Scanner scanner = new Scanner(file);
    
    while (scanner.hasNextLine()) {
        String line = scanner.nextLine();
        System.out.println(line);
    }
    scanner.close();
} catch (FileNotFoundException e) {
    System.out.println("File not found: " + e.getMessage());
}
```

### Using Try-with-Resources

```java
import java.io.FileWriter;
import java.io.IOException;

// Automatically closes resources
try (FileWriter writer = new FileWriter("file.txt")) {
    writer.write("Hello Java");
    System.out.println("File written successfully");
} catch (IOException e) {
    System.out.println("An error occurred: " + e.getMessage());
}
```

---

## Summary

This document covers the fundamental concepts of Java programming:

- **Language Basics** - Syntax, data types, and variables
- **Control Structures** - Conditional statements and loops
- **Methods** - Code organization and reusability
- **Arrays** - Data structure for multiple values
- **OOP Principles** - Classes, objects, inheritance, and encapsulation
- **Error Handling** - Exception management
- **File Operations** - Basic I/O operations

These concepts form the foundation for more advanced Java programming topics. Practice with coding exercises and projects to reinforce these fundamentals.

---

*This study guide provides a comprehensive overview of Java basics. Continue practicing and exploring more advanced topics to become proficient in Java programming.*
