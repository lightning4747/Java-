# Object-Oriented Programming (OOP) in Java - Comprehensive Study Guide

## Table of Contents
1. [Introduction to OOP](#introduction-to-oop)
2. [The Four Pillars of OOP](#the-four-pillars-of-oop)
   - [Encapsulation](#encapsulation)
   - [Inheritance](#inheritance)
   - [Polymorphism](#polymorphism)
   - [Abstraction](#abstraction)
3. [Key OOP Concepts in Java](#key-oop-concepts-in-java)
   - [Classes and Objects](#classes-and-objects)
   - [Constructors](#constructors)
   - [Access Modifiers](#access-modifiers)
4. [Practice Work](#practice-work)
5. [Code Challenges](#code-challenges)
6. [Next to Learn](#next-to-learn)

---

## Introduction to OOP

Object-Oriented Programming is a programming paradigm that organizes software design around **objects** rather than functions and logic. Java is fundamentally object-oriented, making OOP concepts crucial for Java developers.

---

## The Four Pillars of OOP

### Encapsulation

**Encapsulation** is the practice of bundling data (variables) and methods (functions) that operate on that data into a single unit called a **class**, while restricting direct access to some of the object's components.

```java
public class BankAccount {
    // Private data (encapsulated)
    private double balance;
    private String accountNumber;
    
    // Public methods to access private data
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

### Key Points:
- Protects data from unauthorized access
- Provides controlled access through public methods
- Promotes data integrity and security
- Makes code more maintainable and flexible

---

### Inheritance

**Inheritance** allows a class to inherit properties and behaviors from another class. The class being inherited from is called the **parent/superclass**, and the class that inherits is called the **child/subclass**.

```java
// Parent class
class Animal {
    String name;
    
    public void eat() {
        System.out.println(name + " is eating.");
    }
}

// Child class inheriting from Animal
class Dog extends Animal {
    String breed;
    
    public void bark() {
        System.out.println("Woof! Woof!");
    }
}
```

### Key Points:
- Promotes code reusability
- Establishes "is-a" relationships between classes
- Child classes can access parent class properties and methods
- Java supports single inheritance (one parent class only)

---

### Polymorphism

**Polymorphism** means "many forms" - it allows objects of different classes to be treated as objects of a common superclass.

```java
class Shape {
    public void draw() {
        System.out.println("Drawing a shape");
    }
}

class Circle extends Shape {
    @Override
    public void draw() {
        System.out.println("Drawing a circle");
    }
}

class Square extends Shape {
    @Override
    public void draw() {
        System.out.println("Drawing a square");
    }
}

// Using polymorphism
public class Main {
    public static void main(String[] args) {
        Shape[] shapes = new Shape[2];
        shapes[0] = new Circle();
        shapes[1] = new Square();
        
        for (Shape shape : shapes) {
            shape.draw(); // Calls the appropriate draw method
        }
    }
}
```

### Key Points:
- Enables method overriding and dynamic method dispatch
- Allows treating different objects uniformly through a common interface
- Runtime polymorphism is achieved through method overriding
- Compile-time polymorphism is achieved through method overloading

---

### Abstraction

**Abstraction** means hiding complex implementation details and showing only essential features. This is achieved using **abstract classes** and **interfaces**.

```java
// Abstract class
abstract class Vehicle {
    abstract void start(); // Abstract method (no implementation)
    
    public void stop() {
        System.out.println("Vehicle stopped");
    }
}

// Interface
interface Drivable {
    void drive(); // Interface method (automatically public and abstract)
}

class Car extends Vehicle implements Drivable {
    @Override
    void start() {
        System.out.println("Car started");
    }
    
    @Override
    public void drive() {
        System.out.println("Car is driving");
    }
}
```

### Key Points:
- Hides complex implementation details
- Focuses on what an object does rather than how it does it
- Abstract classes can have both abstract and concrete methods
- Interfaces define contracts that implementing classes must follow

---

## Key OOP Concepts in Java

### Classes and Objects

- **Class**: Blueprint/template for creating objects
- **Object**: Instance of a class

```java
// Class definition
public class Student {
    // Fields (attributes)
    String name;
    int age;
    
    // Constructor
    public Student(String name, int age) {
        this.name = name;
        this.age = age;
    }
    
    // Method
    public void study() {
        System.out.println(name + " is studying");
    }
}

// Creating objects
Student student1 = new Student("Alice", 20);
Student student2 = new Student("Bob", 22);
```

### Key Points:
- Classes define the structure and behavior of objects
- Objects are instances of classes created using the `new` keyword
- Each object has its own copy of instance variables
- Methods define the behavior of objects

---

### Constructors

Special methods called when an object is instantiated.

```java
public class Book {
    String title;
    String author;
    
    // Default constructor
    public Book() {
        title = "Unknown";
        author = "Unknown";
    }
    
    // Parameterized constructor
    public Book(String title, String author) {
        this.title = title;
        this.author = author;
    }
    
    // Copy constructor
    public Book(Book otherBook) {
        this.title = otherBook.title;
        this.author = otherBook.author;
    }
}
```

### Key Points:
- Constructors have the same name as the class
- They don't have a return type
- Default constructor is provided if no constructor is defined
- Constructor overloading allows multiple ways to create objects

---

### Access Modifiers

Access modifiers control the visibility and accessibility of classes, methods, and variables.

| Modifier | Class | Package | Subclass | World |
|----------|-------|---------|----------|-------|
| `public` | ✓ | ✓ | ✓ | ✓ |
| `protected` | ✓ | ✓ | ✓ | ✗ |
| Default | ✓ | ✓ | ✗ | ✗ |
| `private` | ✓ | ✗ | ✗ | ✗ |

```java
public class AccessExample {
    public String publicField;        // Accessible from anywhere
    protected String protectedField;  // Accessible within package and subclasses
    String defaultField;             // Accessible within package only
    private String privateField;     // Accessible within class only
    
    public void publicMethod() { }
    protected void protectedMethod() { }
    void defaultMethod() { }
    private void privateMethod() { }
}
```

### Key Points:
- `public`: Accessible from anywhere
- `private`: Accessible only within the same class
- `protected`: Accessible within the package and subclasses
- Default (no modifier): Accessible within the same package

---

## Practice Work

### Exercise 1: Student Management System
Create classes for `Student`, `Course`, and `University` with appropriate properties and methods. Implement encapsulation by making fields private and providing getter/setter methods.

**Requirements:**
- Student should have name, ID, age, and enrolled courses
- Course should have course code, name, credits, and enrolled students
- University should manage students and courses
- Implement methods to enroll/unenroll students, add/remove courses

### Exercise 2: Shape Hierarchy
Create an abstract class `Shape` with abstract methods `calculateArea()` and `calculatePerimeter()`. Create subclasses `Circle`, `Rectangle`, and `Triangle` that implement these methods.

**Requirements:**
- Shape should be abstract with common properties like color
- Each subclass should implement area and perimeter calculations
- Add a method to display shape information
- Test polymorphism by creating an array of different shapes

### Exercise 3: Bank Account Simulation
Create a `BankAccount` class with methods for deposit, withdrawal, and balance inquiry. Use encapsulation to protect the balance field. Create a `SavingsAccount` class that inherits from `BankAccount` and adds interest calculation functionality.

**Requirements:**
- BankAccount should have account number, holder name, and balance
- Implement deposit, withdraw, and getBalance methods with validation
- SavingsAccount should add interest rate and calculateInterest method
- Handle insufficient funds and negative amounts appropriately

### Exercise 4: Interface Implementation
Create an interface `Playable` with methods `play()`, `pause()`, and `stop()`. Implement this interface in classes `AudioPlayer` and `VideoPlayer` with appropriate implementations.

**Requirements:**
- Define Playable interface with common media control methods
- AudioPlayer should handle audio-specific functionality
- VideoPlayer should handle video-specific functionality
- Add additional methods specific to each player type

### Exercise 5: Polymorphism Challenge
Create a base class `Employee` and subclasses `Manager`, `Developer`, and `Designer`. Use polymorphism to create an array of employees and call a `work()` method that behaves differently for each type of employee.

**Requirements:**
- Employee base class with common properties (name, ID, salary)
- Each subclass implements work() method differently
- Add calculateBonus() method with different implementations
- Create a company class that manages different types of employees

---

## Code Challenges

### Challenge 1: Library Management System
Create a `Library` class that can store `Book` objects. Implement methods to add books, remove books, and search for books by title or author.

**Advanced Requirements:**
- Implement book borrowing and returning functionality
- Add Member class with borrowing history
- Implement late fee calculation
- Add book reservation system

### Challenge 2: Shopping Cart System
Design a `ShoppingCart` system with `Product` and `CartItem` classes. Implement methods to add products, remove products, calculate total price, and apply discounts.

**Advanced Requirements:**
- Implement different discount types (percentage, fixed amount)
- Add inventory management
- Implement tax calculation
- Add order history functionality

### Challenge 3: Vehicle Management System
Create a `Vehicle` hierarchy with classes `Car`, `Motorcycle`, and `Truck`. Use interfaces to implement common behaviors like `Drivable` and `Loadable`.

**Advanced Requirements:**
- Add fuel efficiency calculations
- Implement maintenance scheduling
- Add insurance and registration management
- Create a fleet management system

---

## Next to Learn

### Advanced OOP Concepts

#### Composition vs Inheritance
Understanding when to use each approach for better code design.

```java
// Composition example
class Engine {
    public void start() {
        System.out.println("Engine started");
    }
}

class Car {
    private Engine engine = new Engine(); // Has-a relationship
    
    public void startCar() {
        engine.start();
    }
}
```

#### Design Patterns
Common solutions to recurring problems:

- **Singleton Pattern**: Ensures only one instance of a class
- **Factory Pattern**: Creates objects without specifying exact classes
- **Observer Pattern**: Defines one-to-many dependency between objects
- **Strategy Pattern**: Defines family of algorithms and makes them interchangeable

### Java-Specific Features

#### Generics
Type-safe collections and methods that work with different data types.

```java
// Generic class
class Box<T> {
    private T content;
    
    public void setContent(T content) {
        this.content = content;
    }
    
    public T getContent() {
        return content;
    }
}
```

#### Collections Framework
- **Lists**: ArrayList, LinkedList, Vector
- **Sets**: HashSet, TreeSet, LinkedHashSet
- **Maps**: HashMap, TreeMap, LinkedHashMap

#### Exception Handling
Managing errors and exceptional conditions gracefully.

```java
try {
    // Code that might throw an exception
} catch (SpecificException e) {
    // Handle specific exception
} catch (Exception e) {
    // Handle general exception
} finally {
    // Code that always executes
}
```

### Modern Java Features

#### Lambda Expressions
Functional programming features for more concise code.

```java
// Lambda expression
List<String> names = Arrays.asList("Alice", "Bob", "Charlie");
names.forEach(name -> System.out.println(name));
```

#### Stream API
Processing collections functionally with operations like filter, map, and reduce.

```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);
List<Integer> evenNumbers = numbers.stream()
    .filter(n -> n % 2 == 0)
    .collect(Collectors.toList());
```

### Testing and Development

#### JUnit Testing
Writing unit tests to verify code functionality.

```java
@Test
public void testAddition() {
    Calculator calc = new Calculator();
    assertEquals(5, calc.add(2, 3));
}
```

#### Build Tools
- **Maven**: Project management and comprehension tool
- **Gradle**: Build automation tool with flexible scripting

### Recommended Learning Path

1. **Master OOP Fundamentals**: Complete all practice exercises
2. **Java Collections Framework**: Learn data structures implementation
3. **Exception Handling**: Understand error management
4. **Generics**: Type-safe programming
5. **Design Patterns**: Common programming solutions
6. **Modern Java Features**: Lambda expressions and Stream API
7. **Testing**: JUnit and test-driven development
8. **Build Tools**: Maven or Gradle
9. **Advanced Topics**: Multithreading, I/O, and Networking

---

## Conclusion

Object-Oriented Programming in Java provides a robust foundation for building scalable and maintainable applications. The four pillars of OOP - encapsulation, inheritance, polymorphism, and abstraction - work together to create clean, organized code that models real-world scenarios effectively.

Practice is essential for mastering these concepts. Start with simple examples and gradually work on more complex projects. Focus on understanding the "why" behind each concept, not just the "how." This will help you make better design decisions and write more effective Java code.

Remember: Good object-oriented design is about creating classes and objects that accurately represent the problem domain while maintaining clean, readable, and maintainable code.
