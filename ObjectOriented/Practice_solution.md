# Object-Oriented Programming (OOP) in Java - Practice Solutions

## Exercise 1: Student Management System

```java
// Student.java
public class Student {
    private String name;
    private int id;
    private int age;
    private String major;
    
    public Student(String name, int id, int age, String major) {
        this.name = name;
        this.id = id;
        this.age = age;
        this.major = major;
    }
    
    // Getters and setters
    public String getName() { return name; }
    public void setName(String name) { this.name = name; }
    
    public int getId() { return id; }
    public void setId(int id) { this.id = id; }
    
    public int getAge() { return age; }
    public void setAge(int age) { this.age = age; }
    
    public String getMajor() { return major; }
    public void setMajor(String major) { this.major = major; }
    
    public void displayInfo() {
        System.out.println("Student ID: " + id);
        System.out.println("Name: " + name);
        System.out.println("Age: " + age);
        System.out.println("Major: " + major);
    }
}

// Course.java
public class Course {
    private String courseCode;
    private String courseName;
    private int credits;
    private String instructor;
    
    public Course(String courseCode, String courseName, int credits, String instructor) {
        this.courseCode = courseCode;
        this.courseName = courseName;
        this.credits = credits;
        this.instructor = instructor;
    }
    
    // Getters and setters
    public String getCourseCode() { return courseCode; }
    public void setCourseCode(String courseCode) { this.courseCode = courseCode; }
    
    public String getCourseName() { return courseName; }
    public void setCourseName(String courseName) { this.courseName = courseName; }
    
    public int getCredits() { return credits; }
    public void setCredits(int credits) { this.credits = credits; }
    
    public String getInstructor() { return instructor; }
    public void setInstructor(String instructor) { this.instructor = instructor; }
    
    public void displayCourseInfo() {
        System.out.println("Course Code: " + courseCode);
        System.out.println("Course Name: " + courseName);
        System.out.println("Credits: " + credits);
        System.out.println("Instructor: " + instructor);
    }
}

// University.java
import java.util.ArrayList;
import java.util.List;

public class University {
    private String name;
    private List<Student> students;
    private List<Course> courses;
    
    public University(String name) {
        this.name = name;
        this.students = new ArrayList<>();
        this.courses = new ArrayList<>();
    }
    
    public void addStudent(Student student) {
        students.add(student);
    }
    
    public void addCourse(Course course) {
        courses.add(course);
    }
    
    public void displayAllStudents() {
        System.out.println("Students at " + name + ":");
        for (Student student : students) {
            student.displayInfo();
            System.out.println("---------------");
        }
    }
    
    public void displayAllCourses() {
        System.out.println("Courses at " + name + ":");
        for (Course course : courses) {
            course.displayCourseInfo();
            System.out.println("---------------");
        }
    }
    
    // Main method to test
    public static void main(String[] args) {
        University university = new University("Tech University");
        
        // Create students
        Student student1 = new Student("Alice", 101, 20, "Computer Science");
        Student student2 = new Student("Bob", 102, 21, "Mathematics");
        
        // Create courses
        Course course1 = new Course("CS101", "Introduction to Programming", 3, "Dr. Smith");
        Course course2 = new Course("MATH201", "Calculus II", 4, "Prof. Johnson");
        
        // Add to university
        university.addStudent(student1);
        university.addStudent(student2);
        university.addCourse(course1);
        university.addCourse(course2);
        
        // Display information
        university.displayAllStudents();
        university.displayAllCourses();
    }
}
```

## Exercise 2: Shape Hierarchy

```java
// Shape.java
public abstract class Shape {
    public abstract double calculateArea();
    public abstract double calculatePerimeter();
    
    public void displayInfo() {
        System.out.println("Area: " + calculateArea());
        System.out.println("Perimeter: " + calculatePerimeter());
    }
}

// Circle.java
public class Circle extends Shape {
    private double radius;
    
    public Circle(double radius) {
        this.radius = radius;
    }
    
    @Override
    public double calculateArea() {
        return Math.PI * radius * radius;
    }
    
    @Override
    public double calculatePerimeter() {
        return 2 * Math.PI * radius;
    }
    
    public double getRadius() { return radius; }
    public void setRadius(double radius) { this.radius = radius; }
}

// Rectangle.java
public class Rectangle extends Shape {
    private double length;
    private double width;
    
    public Rectangle(double length, double width) {
        this.length = length;
        this.width = width;
    }
    
    @Override
    public double calculateArea() {
        return length * width;
    }
    
    @Override
    public double calculatePerimeter() {
        return 2 * (length + width);
    }
    
    public double getLength() { return length; }
    public void setLength(double length) { this.length = length; }
    
    public double getWidth() { return width; }
    public void setWidth(double width) { this.width = width; }
}

// Triangle.java
public class Triangle extends Shape {
    private double side1;
    private double side2;
    private double side3;
    
    public Triangle(double side1, double side2, double side3) {
        this.side1 = side1;
        this.side2 = side2;
        this.side3 = side3;
    }
    
    @Override
    public double calculateArea() {
        // Using Heron's formula
        double s = calculatePerimeter() / 2;
        return Math.sqrt(s * (s - side1) * (s - side2) * (s - side3));
    }
    
    @Override
    public double calculatePerimeter() {
        return side1 + side2 + side3;
    }
    
    // Main method to test
    public static void main(String[] args) {
        Shape[] shapes = new Shape[3];
        shapes[0] = new Circle(5);
        shapes[1] = new Rectangle(4, 6);
        shapes[2] = new Triangle(3, 4, 5);
        
        for (Shape shape : shapes) {
            shape.displayInfo();
            System.out.println("---------------");
        }
    }
}
```

## Exercise 3: Bank Account Simulation

```java
// BankAccount.java
public class BankAccount {
    private String accountNumber;
    private String accountHolder;
    protected double balance; // protected for inheritance
    
    public BankAccount(String accountNumber, String accountHolder, double initialBalance) {
        this.accountNumber = accountNumber;
        this.accountHolder = accountHolder;
        this.balance = initialBalance;
    }
    
    public void deposit(double amount) {
        if (amount > 0) {
            balance += amount;
            System.out.println("Deposited: $" + amount);
        } else {
            System.out.println("Invalid deposit amount");
        }
    }
    
    public void withdraw(double amount) {
        if (amount > 0 && amount <= balance) {
            balance -= amount;
            System.out.println("Withdrew: $" + amount);
        } else {
            System.out.println("Invalid withdrawal amount or insufficient funds");
        }
    }
    
    public double getBalance() {
        return balance;
    }
    
    public void displayAccountInfo() {
        System.out.println("Account Number: " + accountNumber);
        System.out.println("Account Holder: " + accountHolder);
        System.out.println("Balance: $" + balance);
    }
}

// SavingsAccount.java
public class SavingsAccount extends BankAccount {
    private double interestRate;
    
    public SavingsAccount(String accountNumber, String accountHolder, 
                         double initialBalance, double interestRate) {
        super(accountNumber, accountHolder, initialBalance);
        this.interestRate = interestRate;
    }
    
    public void calculateInterest() {
        double interest = balance * interestRate / 100;
        deposit(interest);
        System.out.println("Interest added: $" + interest);
    }
    
    public double getInterestRate() { return interestRate; }
    public void setInterestRate(double interestRate) { this.interestRate = interestRate; }
    
    // Main method to test
    public static void main(String[] args) {
        SavingsAccount savings = new SavingsAccount("SAV123", "John Doe", 1000, 2.5);
        
        savings.displayAccountInfo();
        savings.deposit(500);
        savings.withdraw(200);
        savings.calculateInterest();
        savings.displayAccountInfo();
    }
}
```

## Exercise 4: Interface Implementation

```java
// Playable.java
public interface Playable {
    void play();
    void pause();
    void stop();
}

// AudioPlayer.java
public class AudioPlayer implements Playable {
    private String audioName;
    
    public AudioPlayer(String audioName) {
        this.audioName = audioName;
    }
    
    @Override
    public void play() {
        System.out.println("Playing audio: " + audioName);
    }
    
    @Override
    public void pause() {
        System.out.println("Pausing audio: " + audioName);
    }
    
    @Override
    public void stop() {
        System.out.println("Stopping audio: " + audioName);
    }
    
    public String getAudioName() { return audioName; }
    public void setAudioName(String audioName) { this.audioName = audioName; }
}

// VideoPlayer.java
public class VideoPlayer implements Playable {
    private String videoName;
    private int duration;
    
    public VideoPlayer(String videoName, int duration) {
        this.videoName = videoName;
        this.duration = duration;
    }
    
    @Override
    public void play() {
        System.out.println("Playing video: " + videoName + " (Duration: " + duration + " mins)");
    }
    
    @Override
    public void pause() {
        System.out.println("Pausing video: " + videoName);
    }
    
    @Override
    public void stop() {
        System.out.println("Stopping video: " + videoName);
    }
    
    // Main method to test
    public static void main(String[] args) {
        Playable[] players = new Playable[2];
        players[0] = new AudioPlayer("Song.mp3");
        players[1] = new VideoPlayer("Movie.mp4", 120);
        
        for (Playable player : players) {
            player.play();
            player.pause();
            player.stop();
            System.out.println("---------------");
        }
    }
}
```

## Exercise 5: Polymorphism Challenge

```java
// Employee.java
public class Employee {
    private String name;
    private int id;
    
    public Employee(String name, int id) {
        this.name = name;
        this.id = id;
    }
    
    public void work() {
        System.out.println(name + " is working");
    }
    
    public String getName() { return name; }
    public int getId() { return id; }
}

// Manager.java
public class Manager extends Employee {
    private String department;
    
    public Manager(String name, int id, String department) {
        super(name, id);
        this.department = department;
    }
    
    @Override
    public void work() {
        System.out.println(getName() + " is managing the " + department + " department");
    }
    
    public void conductMeeting() {
        System.out.println(getName() + " is conducting a meeting");
    }
}

// Developer.java
public class Developer extends Employee {
    private String programmingLanguage;
    
    public Developer(String name, int id, String programmingLanguage) {
        super(name, id);
        this.programmingLanguage = programmingLanguage;
    }
    
    @Override
    public void work() {
        System.out.println(getName() + " is coding in " + programmingLanguage);
    }
    
    public void debugCode() {
        System.out.println(getName() + " is debugging code");
    }
}

// Designer.java
public class Designer extends Employee {
    private String designTool;
    
    public Designer(String name, int id, String designTool) {
        super(name, id);
        this.designTool = designTool;
    }
    
    @Override
    public void work() {
        System.out.println(getName() + " is designing with " + designTool);
    }
    
    public void createPrototype() {
        System.out.println(getName() + " is creating a prototype");
    }
}

// Company.java
public class Company {
    public static void main(String[] args) {
        Employee[] employees = new Employee[4];
        employees[0] = new Manager("Sarah", 101, "Engineering");
        employees[1] = new Developer("Mike", 102, "Java");
        employees[2] = new Designer("Emma", 103, "Figma");
        employees[3] = new Developer("Alex", 104, "Python");
        
        System.out.println("Company Work Day:");
        for (Employee employee : employees) {
            employee.work();
            
            // Demonstrate specific behaviors using instanceof
            if (employee instanceof Manager) {
                ((Manager) employee).conductMeeting();
            } else if (employee instanceof Developer) {
                ((Developer) employee).debugCode();
            } else if (employee instanceof Designer) {
                ((Designer) employee).createPrototype();
            }
            
            System.out.println("---------------");
        }
    }
}
```

## Code Challenge Solutions

### Challenge 1: Library System

```java
import java.util.ArrayList;
import java.util.List;

class Book {
    private String title;
    private String author;
    private String isbn;
    
    public Book(String title, String author, String isbn) {
        this.title = title;
        this.author = author;
        this.isbn = isbn;
    }
    
    public String getTitle() { return title; }
    public String getAuthor() { return author; }
    public String getIsbn() { return isbn; }
    
    @Override
    public String toString() {
        return "Book: " + title + " by " + author + " (ISBN: " + isbn + ")";
    }
}

class Library {
    private List<Book> books;
    
    public Library() {
        books = new ArrayList<>();
    }
    
    public void addBook(Book book) {
        books.add(book);
        System.out.println("Added: " + book);
    }
    
    public void removeBook(String isbn) {
        books.removeIf(book -> book.getIsbn().equals(isbn));
        System.out.println("Removed book with ISBN: " + isbn);
    }
    
    public List<Book> searchByTitle(String title) {
        List<Book> results = new ArrayList<>();
        for (Book book : books) {
            if (book.getTitle().toLowerCase().contains(title.toLowerCase())) {
                results.add(book);
            }
        }
        return results;
    }
    
    public List<Book> searchByAuthor(String author) {
        List<Book> results = new ArrayList<>();
        for (Book book : books) {
            if (book.getAuthor().toLowerCase().contains(author.toLowerCase())) {
                results.add(book);
            }
        }
        return results;
    }
    
    public void displayAllBooks() {
        System.out.println("Library Collection:");
        for (Book book : books) {
            System.out.println(book);
        }
    }
    
    public static void main(String[] args) {
        Library library = new Library();
        
        library.addBook(new Book("Java Programming", "John Smith", "123-456"));
        library.addBook(new Book("Python Basics", "Jane Doe", "789-012"));
        library.addBook(new Book("Advanced Java", "John Smith", "345-678"));
        
        System.out.println("\nSearch by author 'Smith':");
        for (Book book : library.searchByAuthor("Smith")) {
            System.out.println(book);
        }
        
        System.out.println("\nSearch by title 'Java':");
        for (Book book : library.searchByTitle("Java")) {
            System.out.println(book);
        }
        
        library.removeBook("789-012");
        library.displayAllBooks();
    }
}
```

These solutions demonstrate practical implementations of OOP concepts. Try modifying them, adding new features, or creating your own variations to deepen your understanding!
