# Java and OOP Cheatsheet

## Table of Contents
1. [Basic Java Syntax](#1-basic-java-syntax)
   - [Data Types](#data-types)
   - [Variables and Constants](#variables-and-constants)
   - [Operators](#operators)
   - [Control Flow](#control-flow)
   - [Arrays](#arrays)
   - [Strings](#strings)
   - [Input and Output](#input-and-output)
   
2. [Object-Oriented Programming Concepts](#2-object-oriented-programming-concepts)
   - [Classes and Objects](#classes-and-objects)
   - [Constructors](#constructors)
   - [Methods](#methods)
   - [Encapsulation](#encapsulation)
   - [Inheritance](#inheritance)
   - [Polymorphism](#polymorphism)
   - [Abstraction](#abstraction)
   - [Interfaces](#interfaces)
   
3. [Advanced OOP Concepts](#3-advanced-oop-concepts)
   - [Abstract Classes](#abstract-classes)
   - [Final Keyword](#final-keyword)
   - [Static Members](#static-members)
   - [Method Overloading and Overriding](#method-overloading-and-overriding)
   - [Access Modifiers](#access-modifiers)
   - [Packages](#packages)
   
4. [Exception Handling](#4-exception-handling)
   - [Try-Catch Blocks](#try-catch-blocks)
   - [Throw and Throws](#throw-and-throws)
   - [Custom Exceptions](#custom-exceptions)
   
5. [Collections Framework](#5-collections-framework)
   - [Lists](#lists)
   - [Sets](#sets)
   - [Maps](#maps)
   - [Iterators](#iterators)
   
6. [Generics](#6-generics)
   - [Generic Classes](#generic-classes)
   - [Generic Methods](#generic-methods)
   - [Bounded Type Parameters](#bounded-type-parameters)
   
7. [Multithreading](#7-multithreading)
   - [Thread Creation](#thread-creation)
   - [Synchronization](#synchronization)
   - [Thread States](#thread-states)
   
8. [Lambda Expressions and Functional Interfaces](#8-lambda-expressions-and-functional-interfaces)
   - [Lambda Syntax](#lambda-syntax)
   - [Functional Interfaces](#functional-interfaces)
   - [Stream API](#stream-api)
   
9. [Java I/O](#9-java-io)
   - [File Handling](#file-handling)
   - [Serialization](#serialization)
   
10. [Design Patterns](#10-design-patterns)
    - [Creational Patterns](#creational-patterns)
    - [Structural Patterns](#structural-patterns)
    - [Behavioral Patterns](#behavioral-patterns)

---

## 1. Basic Java Syntax

### Data Types

**Primitive Data Types:**
```java
byte myByte = 127;             // 8-bit, -128 to 127
short myShort = 32767;         // 16-bit, -32,768 to 32,767
int myInt = 2147483647;        // 32-bit, -2,147,483,648 to 2,147,483,647
long myLong = 9223372036854775807L; // 64-bit, -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807
float myFloat = 3.14f;         // 32-bit, requires 'f' suffix
double myDouble = 3.14159;     // 64-bit
boolean myBoolean = true;      // true or false
char myChar = 'A';             // 16-bit Unicode character
```

**Reference Data Types:**
```java
String myString = "Hello Java";
Integer myIntObj = 42;
Double myDoubleObj = 3.14;
```

### Variables and Constants

**Variable Declaration:**
```java
// Declaration
int count;

// Declaration and initialization
int count = 10;

// Multiple variables of the same type
int x = 10, y = 20, z = 30;
```

**Constants:**
```java
// Using final keyword
final double PI = 3.14159;

// Constant naming convention
final int MAX_USERS = 100;
```

### Operators

**Arithmetic Operators:**
```java
int a = 10, b = 3;
int sum = a + b;      // Addition (13)
int diff = a - b;     // Subtraction (7)
int product = a * b;  // Multiplication (30)
int quotient = a / b; // Division (3)
int remainder = a % b; // Modulus (1)
a++;                  // Increment (a becomes 11)
b--;                  // Decrement (b becomes 2)
```

**Comparison Operators:**
```java
boolean isEqual = (a == b);     // Equal to (false)
boolean isNotEqual = (a != b);  // Not equal to (true)
boolean isGreater = (a > b);    // Greater than (true)
boolean isLess = (a < b);       // Less than (false)
boolean isGreaterEqual = (a >= b); // Greater than or equal (true)
boolean isLessEqual = (a <= b); // Less than or equal (false)
```

**Logical Operators:**
```java
boolean condition1 = true, condition2 = false;
boolean andResult = condition1 && condition2; // Logical AND (false)
boolean orResult = condition1 || condition2;  // Logical OR (true)
boolean notResult = !condition1;              // Logical NOT (false)
```

**Assignment Operators:**
```java
int x = 10;
x += 5;  // x = x + 5 (15)
x -= 3;  // x = x - 3 (12)
x *= 2;  // x = x * 2 (24)
x /= 4;  // x = x / 4 (6)
x %= 4;  // x = x % 4 (2)
```

**Bitwise Operators:**
```java
int a = 5;  // Binary: 0101
int b = 3;  // Binary: 0011
int bitwiseAnd = a & b;  // Bitwise AND (1)
int bitwiseOr = a | b;   // Bitwise OR (7)
int bitwiseXor = a ^ b;  // Bitwise XOR (6)
int bitwiseComplement = ~a; // Bitwise NOT (-6)
int leftShift = a << 1;  // Left shift (10)
int rightShift = a >> 1; // Right shift (2)
```

### Control Flow

**Conditional Statements:**
```java
// If statement
if (condition) {
    // code to execute if condition is true
}

// If-else statement
if (condition) {
    // code to execute if condition is true
} else {
    // code to execute if condition is false
}

// If-else if-else statement
if (condition1) {
    // code for condition1
} else if (condition2) {
    // code for condition2
} else {
    // code if no conditions match
}

// Ternary operator
int result = (condition) ? valueIfTrue : valueIfFalse;

// Switch statement
switch (variable) {
    case value1:
        // code for value1
        break;
    case value2:
        // code for value2
        break;
    default:
        // default code
        break;
}

// Enhanced switch statement (Java 12+)
switch (variable) {
    case value1 -> // code for value1
    case value2 -> // code for value2
    default -> // default code
}
```

**Loops:**
```java
// For loop
for (int i = 0; i < 10; i++) {
    // code to repeat
}

// Enhanced for loop (for-each)
for (String item : itemsList) {
    // process each item
}

// While loop
while (condition) {
    // code to repeat while condition is true
}

// Do-while loop
do {
    // code to execute at least once
} while (condition);

// Break and continue
for (int i = 0; i < 10; i++) {
    if (i == 5) break;    // Exit the loop
    if (i == 3) continue; // Skip current iteration
}
```

### Arrays

**Array Declaration and Initialization:**
```java
// Declaration
int[] numbers;

// Initialization
numbers = new int[5];

// Declaration and initialization
int[] numbers = new int[5];

// Declaration with values
int[] numbers = {1, 2, 3, 4, 5};

// Accessing elements
int firstElement = numbers[0]; // Arrays are zero-indexed
numbers[1] = 10; // Assign value to element

// Array length
int arrayLength = numbers.length;
```

**Multidimensional Arrays:**
```java
// 2D array
int[][] matrix = new int[3][3];

// Initialize 2D array
int[][] matrix = {
    {1, 2, 3},
    {4, 5, 6},
    {7, 8, 9}
};

// Access element
int element = matrix[1][2]; // Value is 6

// Irregular/jagged arrays
int[][] irregular = new int[3][];
irregular[0] = new int[2];
irregular[1] = new int[3];
irregular[2] = new int[4];
```

### Strings

**String Declaration and Operations:**
```java
// Declaration
String greeting = "Hello";

// String concatenation
String fullGreeting = greeting + " World!";
String concat = greeting.concat(" World!");

// String methods
int length = greeting.length();
char firstChar = greeting.charAt(0);
String upper = greeting.toUpperCase();
String lower = greeting.toLowerCase();
boolean startsWith = greeting.startsWith("He");
boolean endsWith = greeting.endsWith("lo");
int indexOfL = greeting.indexOf("l");
String subString = greeting.substring(1, 4); // "ell"
boolean equal = greeting.equals("Hello");
boolean equalIgnoreCase = greeting.equalsIgnoreCase("hello");
String trimmed = "  Hello  ".trim();
String replaced = greeting.replace('l', 'w');
String[] split = "Hello,World".split(",");
```

**StringBuilder/StringBuffer:**
```java
// StringBuilder (not thread-safe)
StringBuilder sb = new StringBuilder();
sb.append("Hello");
sb.append(" ");
sb.append("World");
String result = sb.toString();

// StringBuffer (thread-safe)
StringBuffer buffer = new StringBuffer();
buffer.append("Hello");
buffer.insert(5, " Java");
buffer.reverse();
String buffResult = buffer.toString();
```

### Input and Output

**Console Input:**
```java
import java.util.Scanner;

Scanner scanner = new Scanner(System.in);

System.out.print("Enter your name: ");
String name = scanner.nextLine();

System.out.print("Enter your age: ");
int age = scanner.nextInt();

scanner.close(); // Important to close the scanner
```

**Console Output:**
```java
// Print with newline
System.out.println("Hello World!");

// Print without newline
System.out.print("Hello ");
System.out.print("World!");

// Formatted output
System.out.printf("Name: %s, Age: %d%n", name, age);
```

---

## 2. Object-Oriented Programming Concepts

### Classes and Objects

**Class Definition:**
```java
public class Person {
    // Fields (instance variables)
    private String name;
    private int age;
    
    // Constructor
    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }
    
    // Methods
    public void sayHello() {
        System.out.println("Hello, my name is " + name);
    }
    
    // Getters and Setters
    public String getName() {
        return name;
    }
    
    public void setName(String name) {
        this.name = name;
    }
    
    public int getAge() {
        return age;
    }
    
    public void setAge(int age) {
        this.age = age;
    }
}
```

**Object Creation:**
```java
// Creating an object
Person person1 = new Person("John", 25);

// Accessing methods
person1.sayHello();

// Using getters and setters
String name = person1.getName();
person1.setAge(26);
```

### Constructors

**Types of Constructors:**
```java
public class Student {
    private String name;
    private int id;
    
    // Default constructor
    public Student() {
        name = "Unknown";
        id = 0;
    }
    
    // Parameterized constructor
    public Student(String name, int id) {
        this.name = name;
        this.id = id;
    }
    
    // Constructor overloading
    public Student(String name) {
        this.name = name;
        this.id = 0;
    }
    
    // Copy constructor
    public Student(Student other) {
        this.name = other.name;
        this.id = other.id;
    }
}
```

**Constructor Chaining:**
```java
public class Person {
    private String name;
    private int age;
    private String address;
    
    public Person() {
        this("Unknown", 0, "Unknown");
    }
    
    public Person(String name) {
        this(name, 0, "Unknown");
    }
    
    public Person(String name, int age) {
        this(name, age, "Unknown");
    }
    
    public Person(String name, int age, String address) {
        this.name = name;
        this.age = age;
        this.address = address;
    }
}
```

### Methods

**Method Definition:**
```java
public class Calculator {
    // Method with no parameters and no return value
    public void displayInfo() {
        System.out.println("Simple Calculator");
    }
    
    // Method with parameters and return value
    public int add(int a, int b) {
        return a + b;
    }
    
    // Method with variable arguments
    public int sum(int... numbers) {
        int total = 0;
        for (int num : numbers) {
            total += num;
        }
        return total;
    }
    
    // Method overloading
    public double add(double a, double b) {
        return a + b;
    }
    
    // Method with object parameters
    public boolean isEqual(Calculator other) {
        // comparison logic
        return true;
    }
}
```

**Method Invocation:**
```java
Calculator calc = new Calculator();

calc.displayInfo();
int result = calc.add(5, 3);
int total = calc.sum(1, 2, 3, 4, 5);
double doubleResult = calc.add(2.5, 3.5);
```

### Encapsulation

**Encapsulation Implementation:**
```java
public class BankAccount {
    // Private variables (data hiding)
    private String accountNumber;
    private double balance;
    private String owner;
    
    // Constructor
    public BankAccount(String accountNumber, String owner) {
        this.accountNumber = accountNumber;
        this.owner = owner;
        this.balance = 0;
    }
    
    // Public getters
    public String getAccountNumber() {
        return accountNumber;
    }
    
    public String getOwner() {
        return owner;
    }
    
    public double getBalance() {
        return balance;
    }
    
    // Public methods for controlled access
    public void deposit(double amount) {
        if (amount > 0) {
            balance += amount;
        }
    }
    
    public boolean withdraw(double amount) {
        if (amount > 0 && balance >= amount) {
            balance -= amount;
            return true;
        }
        return false;
    }
}
```

**Using Encapsulated Class:**
```java
BankAccount account = new BankAccount("123456", "John Doe");

// Using public methods to interact with private data
account.deposit(1000);
boolean success = account.withdraw(500);
double currentBalance = account.getBalance();

// Direct access to private fields is not allowed
// account.balance = 5000; // This would cause a compilation error
```

### Inheritance

**Base Class (Superclass):**
```java
public class Animal {
    protected String name;
    protected int age;
    
    public Animal(String name, int age) {
        this.name = name;
        this.age = age;
    }
    
    public void eat() {
        System.out.println(name + " is eating");
    }
    
    public void sleep() {
        System.out.println(name + " is sleeping");
    }
    
    public String getName() {
        return name;
    }
}
```

**Derived Class (Subclass):**
```java
public class Dog extends Animal {
    private String breed;
    
    public Dog(String name, int age, String breed) {
        super(name, age); // Call to parent constructor
        this.breed = breed;
    }
    
    public void bark() {
        System.out.println(name + " is barking");
    }
    
    // Override parent method
    @Override
    public void eat() {
        System.out.println(name + " the dog is eating dog food");
    }
    
    public String getBreed() {
        return breed;
    }
}
```

**Using Inheritance:**
```java
// Create an object of the subclass
Dog dog = new Dog("Buddy", 3, "Golden Retriever");

// Access methods from the parent class
dog.sleep();

// Access overridden methods
dog.eat();

// Access methods specific to the subclass
dog.bark();

// Parent class reference can point to subclass object
Animal animal = new Dog("Rex", 2, "German Shepherd");
animal.eat(); // Calls the overridden method in Dog
// animal.bark(); // Error: Animal reference cannot access Dog-specific methods
```

### Polymorphism

**Method Overriding:**
```java
// Parent class
public class Shape {
    public double calculateArea() {
        return 0;
    }
    
    public void display() {
        System.out.println("This is a shape");
    }
}

// Child classes
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
    public void display() {
        System.out.println("This is a circle with radius " + radius);
    }
}

public class Rectangle extends Shape {
    private double width;
    private double height;
    
    public Rectangle(double width, double height) {
        this.width = width;
        this.height = height;
    }
    
    @Override
    public double calculateArea() {
        return width * height;
    }
    
    @Override
    public void display() {
        System.out.println("This is a rectangle with width " + width + " and height " + height);
    }
}
```

**Polymorphic Behavior:**
```java
// Array of Shape references
Shape[] shapes = new Shape[3];
shapes[0] = new Circle(5);
shapes[1] = new Rectangle(4, 6);
shapes[2] = new Shape();

// Polymorphic method calls
for (Shape shape : shapes) {
    shape.display(); // Calls the appropriate overridden method
    System.out.println("Area: " + shape.calculateArea());
}
```

### Abstraction

**Abstract Class:**
```java
public abstract class Vehicle {
    protected String make;
    protected String model;
    
    public Vehicle(String make, String model) {
        this.make = make;
        this.model = model;
    }
    
    // Abstract method (no implementation)
    public abstract void start();
    
    // Concrete method (with implementation)
    public void stop() {
        System.out.println("Vehicle stopped");
    }
    
    public String getInfo() {
        return make + " " + model;
    }
}
```

**Concrete Subclass:**
```java
public class Car extends Vehicle {
    private int numDoors;
    
    public Car(String make, String model, int numDoors) {
        super(make, model);
        this.numDoors = numDoors;
    }
    
    // Implementing abstract method
    @Override
    public void start() {
        System.out.println("Car started with key");
    }
    
    public int getNumDoors() {
        return numDoors;
    }
}
```

**Using Abstract Classes:**
```java
// Cannot instantiate abstract class
// Vehicle vehicle = new Vehicle("Generic", "Model"); // Error

// Create concrete subclass
Car car = new Car("Toyota", "Camry", 4);
car.start(); // Uses implemented method
car.stop();  // Uses inherited method

// Use abstract class reference
Vehicle vehicle = new Car("Honda", "Civic", 4);
vehicle.start(); // Calls Car's implementation
```

### Interfaces

**Interface Definition:**
```java
public interface Playable {
    // Constants (implicitly public, static, final)
    int MAX_VOLUME = 100;
    
    // Abstract methods (implicitly public and abstract)
    void play();
    void pause();
    void stop();
    
    // Default method (Java 8+)
    default void increaseVolume() {
        System.out.println("Volume increased");
    }
    
    // Static method (Java 8+)
    static boolean isPlayable(Object obj) {
        return obj instanceof Playable;
    }
}
```

**Implementing Interface:**
```java
public class MusicPlayer implements Playable {
    private String currentTrack;
    private boolean isPlaying;
    
    public MusicPlayer(String track) {
        this.currentTrack = track;
        this.isPlaying = false;
    }
    
    @Override
    public void play() {
        isPlaying = true;
        System.out.println("Playing: " + currentTrack);
    }
    
    @Override
    public void pause() {
        isPlaying = false;
        System.out.println("Paused: " + currentTrack);
    }
    
    @Override
    public void stop() {
        isPlaying = false;
        System.out.println("Stopped: " + currentTrack);
    }
    
    // Class can override default methods
    @Override
    public void increaseVolume() {
        System.out.println("Music player volume increased");
    }
}
```

**Multiple Interface Implementation:**
```java
public interface Chargeable {
    void charge();
    int getBatteryLevel();
}

public class SmartPhone implements Playable, Chargeable {
    private int batteryLevel;
    
    // Implement methods from Playable
    @Override
    public void play() { /* implementation */ }
    
    @Override
    public void pause() { /* implementation */ }
    
    @Override
    public void stop() { /* implementation */ }
    
    // Implement methods from Chargeable
    @Override
    public void charge() {
        batteryLevel = 100;
        System.out.println("Phone charged to 100%");
    }
    
    @Override
    public int getBatteryLevel() {
        return batteryLevel;
    }
}
```

**Using Interfaces:**
```java
// Interface reference can reference implementing object
Playable player = new MusicPlayer("Song.mp3");
player.play();
player.increaseVolume(); // Using default method

// Static method is called on the interface itself
boolean result = Playable.isPlayable(player);

// Object implementing multiple interfaces
SmartPhone phone = new SmartPhone();
phone.play();   // From Playable
phone.charge(); // From Chargeable
```

---

## 3. Advanced OOP Concepts

### Abstract Classes

**Extended Abstract Class Example:**
```java
public abstract class DatabaseConnection {
    protected String connectionString;
    protected boolean isConnected;
    
    public DatabaseConnection(String connectionString) {
        this.connectionString = connectionString;
        this.isConnected = false;
    }
    
    // Abstract methods
    public abstract boolean connect();
    public abstract void executeQuery(String query);
    public abstract void disconnect();
    
    // Concrete methods
    public boolean isConnected() {
        return isConnected;
    }
    
    public void setConnectionString(String connectionString) {
        if (!isConnected) {
            this.connectionString = connectionString;
        }
    }
}

// Concrete implementation
public class MySQLConnection extends DatabaseConnection {
    public MySQLConnection(String connectionString) {
        super(connectionString);
    }
    
    @Override
    public boolean connect() {
        // MySQL-specific connection logic
        System.out.println("Connecting to MySQL database...");
        isConnected = true;
        return true;
    }
    
    @Override
    public void executeQuery(String query) {
        if (isConnected) {
            System.out.println("Executing MySQL query: " + query);
        }
    }
    
    @Override
    public void disconnect() {
        if (isConnected) {
            System.out.println("Disconnecting from MySQL database...");
            isConnected = false;
        }
    }
}
```

### Final Keyword

**Final Applications:**
```java
// Final class (cannot be extended)
public final class Utility {
    // Final method (cannot be overridden)
    public final void helperMethod() {
        // implementation
    }
}

// Class with final field
public class Circle {
    // Final variable (must be initialized, cannot be changed)
    private final double PI = 3.14159;
    
    // Final variable initialized in constructor
    private final double radius;
    
    public Circle(double radius) {
        this.radius = radius; // Can only be assigned once
    }
    
    public double calculateArea() {
        return PI * radius * radius;
    }
    
    // Method with final parameter
    public void display(final String prefix) {
        // prefix = prefix + ": "; // Error: cannot modify final parameter
        System.out.println(prefix + " Circle with radius " + radius);
    }
}
```

### Static Members

**Static Variables and Methods:**
```java
public class MathUtils {
    // Static variable (shared across all instances)
    public static final double PI = 3.14159;
    
    // Static counter
    private static int operationCount = 0;
    
    // Static method
    public static double square(double num) {
        operationCount++;
        return num * num;
    }
    
    // Static method accessing static variable
    public static int getOperationCount() {
        return operationCount;
    }
    
    // Static initialization block
    static {
        System.out.println("MathUtils class loaded");
    }
}
```

**Static Inner Class:**
```java
public class OuterClass {
    private static int outerStaticVar = 10;
    private int outerInstanceVar = 20;
    
    // Static inner class
    public static class StaticNestedClass {
        private int nestedVar = 30;
        
        public void display() {
            // Can access static members of outer class
            System.out.println("Outer static variable: " + outerStaticVar);
            
            // Cannot access instance variables of outer class
            // System.out.println(outerInstanceVar); // Error
        }
    }
    
    // Non-static inner class
    public class InnerClass {
        public void display() {
            // Can access both static and instance members of outer class
            System.out.println("Outer static variable: " + outerStaticVar);
            System.out.println("Outer instance variable: " + outerInstanceVar);
        }
    }
}

// Usage
OuterClass.StaticNestedClass staticNested = new OuterClass.StaticNestedClass();
OuterClass outer = new OuterClass();
OuterClass.InnerClass inner = outer.new InnerClass();
```

### Method Overloading and Overriding

**Method Overloading:**
```java
public class Calculator {
    // Overloaded methods (different parameter types)
    public int add(int a, int b) {
        return a + b;
    }
    
    public double add(double a, double b) {
        return a + b;
    }
    
    // Overloaded methods (different number of parameters)
    public int add(int a, int b, int c) {
        return a + b + c;
    }
    
    // Overloaded methods (different parameter order)
    public double calculate(int a, double b) {
        return a + b;
    }
    
    public double calculate(double a, int b) {
        return a * b;
    }
}
```

**Method Overriding Details:**
```java
class Parent {
    // Method to be overridden
    public void display() {
        System.out.println("Parent's display method");
    }
    
    // Final method cannot be overridden
    public final void cannotOverride() {
        System.out.println("Cannot override this method");
    }
    
    // Method with return type
    public Number getValue() {
        return 10;
    }
    
    // Protected method
    protected void showDetails() {
        System.out.println("Parent details");
    }
}

class Child extends Parent {
    // Overriding method
    @Override
    public void display() {
        System.out.println("Child's display method");
        super.display(); // Call parent method
    }
    
    // Overridden method with covariant return type
    @Override
    public Integer getValue() { // Integer is a subclass of Number
        return 20;
    }
    
    // Overridden method with same or more accessible modifier
    @Override
    public void showDetails() { // changed from protected to public
        System.out.println("Child details");
    }
}
```

## Access Modifiers

Access modifiers control the visibility and accessibility of classes, methods, and fields.

| Modifier | Same Class | Same Package | Subclasses | Other Packages |
|----------|-------|---------|----------|-------|
| `public` | ✅ | ✅ | ✅ | ✅ |
| `protected` | ✅ | ✅ | ✅ | ❌ |
| `default` (no modifier) | ✅ | ✅ | ❌ | ❌ |
| `private` | ✅ | ❌ | ❌ | ❌ |

```java

public class AccessModifierExample {
    public String publicVar = "Accessible everywhere";
    protected String protectedVar = "Accessible in package and subclasses";
    String defaultVar = "Accessible only in package";
    private String privateVar = "Accessible only in this class";
    
    public void publicMethod() {
        System.out.println("Can be accessed from anywhere");
    }
    
    protected void protectedMethod() {
        System.out.println("Can be accessed from the same package and subclasses");
    }
    
    void defaultMethod() {
        System.out.println("Can be accessed only from the same package");
    }
    
    private void privateMethod() {
        System.out.println("Can be accessed only within this class");
    }
}
```

**Access Levels:**
```java
public class AccessExample {
    // Accessible from any class
    public int publicVar;
    
    // Accessible from classes within same package and subclasses
    protected int protectedVar;
    
    // Accessible only from classes within same package (default)
    int defaultVar;
    
    // Accessible only within this class
    private int privateVar;
    
    // Access modifiers for methods follow same rules
    public void publicMethod() { }
    protected void protectedMethod() { }
    void defaultMethod() { }
    private void privateMethod() { }
    
    // Inner class showing access to outer class variables
    public class InnerClass {
        public void accessTest() {
            // Can access all variables of the outer class
            System.out.println(publicVar);
            System.out.println(protectedVar);
            System.out.println(defaultVar);
            System.out.println(privateVar);
        }
    }
}

// Access in same package
class SamePackageClass {
    public void accessTest(AccessExample obj) {
        System.out.println(obj.publicVar);      // OK
        System.out.println(obj.protectedVar);   // OK
        System.out.println(obj.defaultVar);     // OK
        // System.out.println(obj.privateVar);  // Error: not accessible
    }
}

// Access in different package
package different;
import original.AccessExample;

class DifferentPackageClass {
    public void accessTest(AccessExample obj) {
        System.out.println(obj.publicVar);      // OK
        // System.out.println(obj.protectedVar);  // Error: not accessible

```

## Packages

Packages are used to organize classes and avoid naming conflicts.

```java
// Declaring a package
package com.example.myapp;

// Importing specific classes
import java.util.ArrayList;
import java.util.List;

// Importing all classes from a package
import java.util.*;

// Static import (import static members)
import static java.lang.Math.PI;
import static java.lang.Math.*;
```

**Creating and using packages:**
1. Declare package at the top of the file: `package com.example.myapp;`
2. Place your files in the appropriate directory structure (com/example/myapp/)
3. Compile with: `javac -d . YourClass.java`
4. Run with: `java com.example.myapp.YourClass`

---

## 4. Exception Handling

### Try-Catch Blocks

Exception handling helps manage runtime errors gracefully.

```java
try {
    // Code that might throw an exception
    int result = 10 / 0; // ArithmeticException
    
} catch (ArithmeticException e) {
    // Handle specific exception
    System.out.println("Cannot divide by zero: " + e.getMessage());
    
} catch (Exception e) {
    // Handle any other exceptions
    System.out.println("An error occurred: " + e.getMessage());
    
} finally {
    // Code that always executes (optional)
    System.out.println("This always executes");
}
```

**Multiple catch blocks:** Specific exceptions should come before general ones.

**Try-with-resources:** Automatically closes resources that implement AutoCloseable.

```java
try (
    FileInputStream fis = new FileInputStream("file.txt");
    BufferedReader br = new BufferedReader(new InputStreamReader(fis))
) {
    String line;
    while ((line = br.readLine()) != null) {
        System.out.println(line);
    }
} catch (IOException e) {
    e.printStackTrace();
}
// Resources automatically closed
```

### Throw and Throws

```java
// Using throws to declare that a method might throw exceptions
public void readFile(String filename) throws FileNotFoundException, IOException {
    FileReader fr = new FileReader(filename);
    // Code that reads the file
}

// Using throw to explicitly throw an exception
public void validateAge(int age) {
    if (age < 0) {
        throw new IllegalArgumentException("Age cannot be negative");
    }
}
```

### Custom Exceptions

```java
// Creating a custom exception
public class InsufficientFundsException extends Exception {
    private double amount;
    
    public InsufficientFundsException(double amount) {
        super("Insufficient funds: shortage of $" + amount);
        this.amount = amount;
    }
    
    public double getAmount() {
        return amount;
    }
}

// Using the custom exception
public class BankAccount {
    private double balance;
    
    public void withdraw(double amount) throws InsufficientFundsException {
        if (amount > balance) {
            throw new InsufficientFundsException(amount - balance);
        }
        balance -= amount;
    }
}
```

**Exception Hierarchy:**
- `Throwable` (root)
  - `Error` (serious problems, shouldn't catch)
  - `Exception` (catchable problems)
    - `RuntimeException` (unchecked exceptions)
    - Other exceptions (checked exceptions)

---

## 5. Collections Framework

The Java Collections Framework provides interfaces and classes for storing and manipulating groups of objects.

### Lists

Lists are ordered collections that can contain duplicate elements.

```java
// ArrayList (dynamic array implementation)
List<String> arrayList = new ArrayList<>();
arrayList.add("Apple");              // Add element
arrayList.add(0, "Banana");          // Add at index
String item = arrayList.get(1);      // Access by index
arrayList.set(1, "Cherry");          // Replace element
arrayList.remove("Banana");          // Remove by object
arrayList.remove(0);                 // Remove by index
int size = arrayList.size();         // Get size
boolean exists = arrayList.contains("Cherry"); // Check if exists

// LinkedList (doubly-linked list implementation)
List<String> linkedList = new LinkedList<>();
linkedList.add("Apple");
// Better for frequent insertions/deletions

// Common operations
for (String fruit : arrayList) {     // Enhanced for loop
    System.out.println(fruit);
}

// Sorting a list
Collections.sort(arrayList);         // Natural order
Collections.sort(arrayList, Collections.reverseOrder()); // Reverse order

// Custom sort with Comparator
Collections.sort(personList, new Comparator<Person>() {
    @Override
    public int compare(Person p1, Person p2) {
        return p1.getAge() - p2.getAge();
    }
});

// Lambda expression for sorting
Collections.sort(personList, (p1, p2) -> p1.getAge() - p2.getAge());
```

### Sets

Sets contain no duplicate elements.

```java
// HashSet (hash table implementation, unordered)
Set<String> hashSet = new HashSet<>();
hashSet.add("Apple");
hashSet.add("Banana");
hashSet.add("Apple");    // Ignored (duplicate)
hashSet.remove("Apple");
boolean contains = hashSet.contains("Banana");

// TreeSet (balanced tree implementation, sorted)
Set<String> treeSet = new TreeSet<>();
treeSet.add("Cherry");
treeSet.add("Apple");
treeSet.add("Banana");
// Elements will be stored in sorted order: Apple, Banana, Cherry

// LinkedHashSet (maintains insertion order)
Set<String> linkedHashSet = new LinkedHashSet<>();
```

### Maps

Maps store key-value pairs.

```java
// HashMap (unordered)
Map<String, Integer> hashMap = new HashMap<>();
hashMap.put("Apple", 10);            // Add or update
hashMap.put("Banana", 20);
Integer value = hashMap.get("Apple"); // Retrieve value
hashMap.remove("Apple");             // Remove by key
boolean hasKey = hashMap.containsKey("Banana");
boolean hasValue = hashMap.containsValue(20);
int size = hashMap.size();

// Iterating through a Map
for (Map.Entry<String, Integer> entry : hashMap.entrySet()) {
    System.out.println(entry.getKey() + ": " + entry.getValue());
}

// TreeMap (sorted by keys)
Map<String, Integer> treeMap = new TreeMap<>();

// LinkedHashMap (maintains insertion order)
Map<String, Integer> linkedHashMap = new LinkedHashMap<>();
```

### Iterators

```java
List<String> list = new ArrayList<>();
list.add("Apple");
list.add("Banana");
list.add("Cherry");

// Using Iterator
Iterator<String> iterator = list.iterator();
while (iterator.hasNext()) {
    String element = iterator.next();
    if (element.equals("Banana")) {
        iterator.remove(); // Safe way to remove during iteration
    }
}

// Using ListIterator (bidirectional)
ListIterator<String> listIterator = list.listIterator();
while (listIterator.hasNext()) {
    int index = listIterator.nextIndex();
    String element = listIterator.next();
    listIterator.set(element.toUpperCase()); // Replace current element
}
```

---

## 6. Generics

Generics enable types (classes and interfaces) to be parameters when defining classes, interfaces, and methods.

### Generic Classes

```java
// Generic class with one type parameter
public class Box<T> {
    private T content;
    
    public void set(T content) {
        this.content = content;
    }
    
    public T get() {
        return content;
    }
}

// Usage
Box<String> stringBox = new Box<>();
stringBox.set("Hello Generics");
String greeting = stringBox.get();

Box<Integer> integerBox = new Box<>();
integerBox.set(42);
Integer number = integerBox.get();

// Generic class with multiple type parameters
public class Pair<K, V> {
    private K key;
    private V value;
    
    public Pair(K key, V value) {
        this.key = key;
        this.value = value;
    }
    
    public K getKey() { return key; }
    public V getValue() { return value; }
}

// Usage
Pair<String, Integer> pair = new Pair<>("Age", 30);
```

### Generic Methods

```java
// Generic method
public static <T> void printArray(T[] array) {
    for (T element : array) {
        System.out.println(element);
    }
}

// Usage
Integer[] intArray = {1, 2, 3};
String[] strArray = {"Hello", "World"};

printArray(intArray);
printArray(strArray);

// Generic method with multiple type parameters
public static <K, V> boolean compare(Pair<K, V> p1, Pair<K, V> p2) {
    return p1.getKey().equals(p2.getKey()) && 
           p1.getValue().equals(p2.getValue());
}
```

### Bounded Type Parameters

```java
// Upper bound - T must be or extend Number
public static <T extends Number> double sum(List<T> list) {
    double total = 0;
    for (T element : list) {
        total += element.doubleValue(); // Can call Number methods
    }
    return total;
}

// Multiple bounds - T must implement both Comparable and Serializable
public static <T extends Comparable & Serializable> void process(T item) {
    // Can use methods from both Comparable and Serializable
}

// Wildcard - unknown type
public static void printList(List<?> list) {
    for (Object elem : list) {
        System.out.println(elem);
    }
}

// Upper bounded wildcard - any List of type that extends Number
public static double sumOfList(List<? extends Number> list) {
    double s = 0.0;
    for (Number n : list) {
        s += n.doubleValue();
    }
    return s;
}

// Lower bounded wildcard - any List of type that is a superclass of Integer
public static void addNumbers(List<? super Integer> list) {
    for (int i = 1; i <= 10; i++) {
        list.add(i);
    }
}
```

---

## 7. Multithreading

Multithreading allows concurrent execution of two or more parts of a program.

### Thread Creation

**Method 1: Extending Thread class**
```java
public class MyThread extends Thread {
    @Override
    public void run() {
        for (int i = 0; i < 5; i++) {
            System.out.println("Thread " + Thread.currentThread().getId() + ": " + i);
            try {
                Thread.sleep(500); // Pause for 500 milliseconds
            } catch (InterruptedException e) {
                System.out.println("Thread interrupted");
            }
        }
    }
}

// Usage
MyThread thread1 = new MyThread();
thread1.start(); // Important: call start(), not run()
```

**Method 2: Implementing Runnable interface**
```java
public class MyRunnable implements Runnable {
    @Override
    public void run() {
        for (int i = 0; i < 5; i++) {
            System.out.println("Thread " + Thread.currentThread().getId() + ": " + i);
            try {
                Thread.sleep(500);
            } catch (InterruptedException e) {
                System.out.println("Thread interrupted");
            }
        }
    }
}

// Usage
Thread thread2 = new Thread(new MyRunnable());
thread2.start();

// Or using lambda expression (Java 8+)
Thread thread3 = new Thread(() -> {
    for (int i = 0; i < 5; i++) {
        System.out.println("Lambda Thread: " + i);
        try {
            Thread.sleep(500);
        } catch (InterruptedException e) {
            System.out.println("Thread interrupted");
        }
    }
});
thread3.start();
```

### Synchronization

```java
// Synchronized method
public synchronized void synchronizedMethod() {
    // Only one thread can execute this method on the same instance at a time
}

// Synchronized block
public void someMethod() {
    // Non-synchronized code
    
    synchronized(this) {
        // Synchronized code block - only one thread can execute this block at a time
    }
    
    // More non-synchronized code
}

// Static synchronization (class lock)
public static synchronized void staticSyncMethod() {
    // Only one thread can execute this method across all instances
}
```

**Volatile Keyword:** Ensures that a variable is read directly from main memory, not from thread cache.

```java
private volatile boolean flag = false;
```

**Thread Safety Using Locks:**

```java
import java.util.concurrent.locks.Lock;
import java.util.concurrent.locks.ReentrantLock;

public class BankAccount {
    private double balance;
    private Lock lock = new ReentrantLock();
    
    public void deposit(double amount) {
        lock.lock();
        try {
            balance += amount;
        } finally {
            lock.unlock(); // Always unlock in finally block
        }
    }
    
    public void withdraw(double amount) {
        lock.lock();
        try {
            if (balance >= amount) {
                balance -= amount;
            }
        } finally {
            lock.unlock();
        }
    }
}
```

### Thread States

1. **NEW**: Thread is created but not started
2. **RUNNABLE**: Thread is executing or ready to execute
3. **BLOCKED**: Thread is waiting to acquire a monitor lock
4. **WAITING**: Thread is waiting indefinitely for another thread
5. **TIMED_WAITING**: Thread is waiting for a specified time
6. **TERMINATED**: Thread has completed execution

**Common Thread Methods:**

```java
Thread thread = new Thread(() -> {
    // Thread code
});

thread.start();                      // Start the thread
thread.join();                       // Wait for thread to finish
thread.join(1000);                   // Wait up to 1000 ms for thread to finish
thread.interrupt();                  // Interrupt the thread
thread.isAlive();                    // Check if thread is still running
Thread.sleep(1000);                  // Static method to pause current thread
Thread.yield();                      // Yield to other threads
thread.setPriority(Thread.MAX_PRIORITY); // Set thread priority (1-10)
```

**Thread Pools:**

```java
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;

public class ThreadPoolExample {
    public static void main(String[] args) {
        // Create a thread pool with 5 threads
        ExecutorService executor = Executors.newFixedThreadPool(5);
        
        // Submit tasks to the thread pool
        for (int i = 0; i < 10; i++) {
            final int taskId = i;
            executor.submit(() -> {
                System.out.println("Task " + taskId + " executed by " + 
                                   Thread.currentThread().getName());
            });
        }
        
        // Shutdown the executor
        executor.shutdown();
    }
}
```

---

## 8. Lambda Expressions and Functional Interfaces

Lambda expressions provide a concise way to express instances of single-method interfaces (functional interfaces).

### Lambda Syntax

```java
// Basic syntax: (parameters) -> expression
// or (parameters) -> { statements; }

// No parameters
Runnable runnable = () -> System.out.println("Hello from lambda");

// One parameter (parentheses optional for single parameter with no type)
Consumer<String> consumer = message -> System.out.println(message);

// Multiple parameters
BiFunction<Integer, Integer, Integer> add = (a, b) -> a + b;

// With parameter types
Comparator<String> comparator = (String s1, String s2) -> s1.compareTo(s2);

// Multiple statements
Runnable complexTask = () -> {
    System.out.println("Task started");
    performTask();
    System.out.println("Task completed");
};
```

### Functional Interfaces

Functional interfaces have exactly one abstract method and can be implemented using lambda expressions.

**Built-in Functional Interfaces:**

```java
// Function<T, R> - takes T, returns R
Function<String, Integer> length = s -> s.length();
Integer len = length.apply("Hello"); // 5

// Predicate<T> - takes T, returns boolean
Predicate<String> isEmpty = s -> s.isEmpty();
boolean result = isEmpty.test(""); // true

// Consumer<T> - takes T, returns nothing
Consumer<String> print = s -> System.out.println(s);
print.accept("Hello"); // Prints: Hello

// Supplier<T> - takes nothing, returns T
Supplier<Double> random = () -> Math.random();
Double value = random.get(); // Random value between 0.0 and 1.0

// BiFunction<T, U, R> - takes T and U, returns R
BiFunction<String, String, String> concat = (s1, s2) -> s1 + s2;
String combined = concat.apply("Hello, ", "world!"); // Hello, world!

// UnaryOperator<T> - takes T, returns T (specialization of Function)
UnaryOperator<String> toUpperCase = s -> s.toUpperCase();
String upper = toUpperCase.apply("hello"); // HELLO

// BinaryOperator<T> - takes two T, returns T (specialization of BiFunction)
BinaryOperator<Integer> multiply = (a, b) -> a * b;
Integer product = multiply.apply(5, 7); // 35
```

**Creating Custom Functional Interfaces:**

```java
@FunctionalInterface // Optional but recommended annotation
public interface TriFunction<T, U, V, R> {
    R apply(T t, U u, V v);
}

// Using the custom interface
TriFunction<Integer, Integer, Integer, Integer> addThree = 
    (a, b, c) -> a + b + c;
Integer sum = addThree.apply(1, 2, 3); // 6
```

### Stream API

The Stream API provides a modern approach to process collections of objects.

```java
import java.util.Arrays;
import java.util.List;
import java.util.stream.Collectors;

public class StreamExample {
    public static void main(String[] args) {
        List<String> names = Arrays.asList("John", "Jane", "Jack", "Joe", "Jill");
        
        // Filter names starting with "Jo"
        List<String> filteredNames = names.stream()
                                         .filter(name -> name.startsWith("Jo"))
                                         .collect(Collectors.toList());
        // [John, Joe]
        
        // Map names to their lengths
        List<Integer> nameLengths = names.stream()
                                       .map(String::length)
                                       .collect(Collectors.toList());
        // [4, 4, 4, 3, 4]
        
        // Sort names
        List<String> sortedNames = names.stream()
                                      .sorted()
                                      .collect(Collectors.toList());
        // [Jack, Jane, Jill, Joe, John]
        
        // Find any name with length 3
        String anyNameLength3 = names.stream()
                                   .filter(name -> name.length() == 3)
                                   .findAny()
                                   .orElse("None");
        // Joe
        
        // Check if all names have length >= 3
        boolean allLengthAtLeast3 = names.stream()
                                       .allMatch(name -> name.length() >= 3);
        // true
        
        // Get distinct lengths
        List<Integer> distinctLengths = names.stream()
                                          .map(String::length)
                                          .distinct()
                                          .collect(Collectors.toList());
        // [4, 3]
        
        // Sum of all name lengths
        int totalLength = names.stream()
                             .mapToInt(String::length)
                             .sum();
        // 19
    }
}
```

**Additional Stream Operations:**

```java
// Creating streams
Stream<String> streamFromArray = Arrays.stream(new String[]{"a", "b", "c"});
Stream<Integer> streamFromCollection = List.of(1, 2, 3).stream();
Stream<Integer> streamGenerated = Stream.generate(() -> 1).limit(5); // [1, 1, 1, 1, 1]
Stream<Integer> streamIterated = Stream.iterate(1, n -> n + 2).limit(5); // [1, 3, 5, 7, 9]

// Intermediate operations (return a stream)
.filter(predicate)     // Filter elements based on predicate
.map(function)         // Transform elements using function
.flatMap(function)     // Transform and flatten elements
.distinct()            // Remove duplicates
.sorted()              // Sort elements
.peek(consumer)        // Perform action on elements and pass them along
.limit(n)              // Limit to n elements
.skip(n)               // Skip n elements

// Terminal operations (produce a result or side-effect)
.forEach(consumer)     // Perform action on each element
.toArray()             // Convert to array
.collect(collector)    // Collect results into a collection
.reduce(identity, accumulator) // Reduce elements to a single value
.min(comparator)       // Find minimum element
.max(comparator)       // Find maximum element
.count()               // Count elements
.anyMatch(predicate)   // Returns true if any element matches
.allMatch(predicate)   // Returns true if all elements match
.noneMatch(predicate)  // Returns true if no elements match
.findFirst()           // Find first element
.findAny()             // Find any element
```

---

## 9. Java I/O

### File Handling

```java
import java.io.*;
import java.nio.file.*;

public class FileExample {
    public static void main(String[] args) {
        // Working with File class
        File file = new File("example.txt");
        
        boolean exists = file.exists();
        boolean isFile = file.isFile();
        boolean isDir = file.isDirectory();
        long length = file.length();
        boolean created = file.createNewFile();
        boolean deleted = file.delete();
        File[] files = new File("directory").listFiles();
        
        // Reading file line by line
        try (BufferedReader reader = new BufferedReader(new FileReader("input.txt"))) {
            String line;
            while ((line = reader.readLine()) != null) {
                System.out.println(line);
            }
        } catch (IOException e) {
            e.printStackTrace();
        }
        
        // Writing to a file
        try (BufferedWriter writer = new BufferedWriter(new FileWriter("output.txt"))) {
            writer.write("Hello, world!");
            writer.newLine();
            writer.write("Another line");
        } catch (IOException e) {
            e.printStackTrace();
        }
        
        // Java NIO (New I/O)
        Path path = Paths.get("example.txt");
        byte[] bytes = Files.readAllBytes(path);
        List<String> lines = Files.readAllLines(path);
        Files.write(path, "Content".getBytes());
        Files.write(path, lines);
        
        // File copy
        Path source = Paths.get("source.txt");
        Path destination = Paths.get("destination.txt");
        Files.copy(source, destination, StandardCopyOption.REPLACE_EXISTING);
        
        // Directory operations
        Path dirPath = Paths.get("newdir");
        Files.createDirectory(dirPath);
        Files.createDirectories(Paths.get("dir1/dir2/dir3"));
        
        // Stream directory contents
        try (Stream<Path> pathStream = Files.list(Paths.get("."))) {
            pathStream.forEach(System.out::println);
        }
    }
}
```

### Serialization

Serialization is the process of converting an object into a byte stream.

```java
import java.io.*;

// Class must implement Serializable interface
public class Person implements Serializable {
    // The serialVersionUID is used during deserialization to verify compatibility
    private static final long serialVersionUID = 1L;
    
    private String name;
    private int age;
    // transient fields are not serialized
    private transient String tempData;
    
    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }
    
    @Override
    public String toString() {
        return "Person{name='" + name + "', age=" + age + "}";
    }
}

public class SerializationExample {
    public static void main(String[] args) {
        // Serializing an object
        try (ObjectOutputStream oos = new ObjectOutputStream(
                new FileOutputStream("person.ser"))) {
            Person person = new Person("John Doe", 30);
            oos.writeObject(person);
            System.out.println("Person serialized");
        } catch (IOException e) {
            e.printStackTrace();
        }
        
        // Deserializing an object
        try (ObjectInputStream ois = new ObjectInputStream(
                new FileInputStream("person.ser"))) {
            Person person = (Person) ois.readObject();
            System.out.println("Person deserialized: " + person);
        } catch (IOException | ClassNotFoundException e) {
            e.printStackTrace();
        }
    }
}
```

---

## 10. Design Patterns

Design patterns are standard solutions to common problems in software design.

### Creational Patterns

**Singleton Pattern:** Ensures a class has only one instance and provides a global point of access to it.

```java
public class Singleton {
    // Private static instance - initialized when class is loaded
    private static final Singleton INSTANCE = new Singleton();
    
    // Private constructor prevents external instantiation
    private Singleton() {
        // Initialization code
    }
    
    // Public static getter method
    public static Singleton getInstance() {
        return INSTANCE;
    }
    
    // Business methods
    public void doSomething() {
        System.out.println("Singleton is doing something");
    }
}

// Usage
Singleton singleton = Singleton.getInstance();
singleton.doSomething();
```

**Lazy Initialization Singleton (thread-safe):**

```java
public class LazySingleton {
    // Volatile ensures visibility across threads
    private static volatile LazySingleton instance;
    
    private LazySingleton() {
        // Private constructor
    }
    
    // Double-checked locking pattern
    public static LazySingleton getInstance() {
        if (instance == null) {
            synchronized (LazySingleton.class) {
                if (instance == null) {
                    instance = new LazySingleton();
                }
            }
        }
        return instance;
    }
}
```

**Factory Method Pattern:** Defines an interface for creating an object, but lets subclasses decide which class to instantiate.

```java
// Product interface
interface Product {
    void use();
}

// Concrete Products
class ConcreteProductA implements Product {
    @Override
    public void use() {
        System.out.println("Using Product A");
    }
}

class ConcreteProductB implements Product {
    @Override
    public void use() {
        System.out.println("Using Product B");
    }
}

// Creator abstract class with factory method
abstract class Creator {
    // Factory method
    public abstract Product createProduct();
    
    // Common operations using the product
    public void doSomething() {
        Product product = createProduct();
        product.use();
    }
}

// Concrete Creators
class ConcreteCreatorA extends Creator {
    @Override
    public Product createProduct() {
        return new ConcreteProductA();
    }
}

class ConcreteCreatorB extends Creator {
    @Override
    public Product createProduct() {
        return new ConcreteProductB();
    }
}

// Usage
Creator creator = new ConcreteCreatorA();
creator.doSomething(); // Creates and uses Product A
```

**Builder Pattern:** Separates the construction of a complex object from its representation.

```java
public class Person {
    // Required parameters
    private final String firstName;
    private final String lastName;
    
    // Optional parameters
    private final int age;
    private final String address;
    private final String phone;
    
    private Person(Builder builder) {
        this.firstName = builder.firstName;
        this.lastName = builder.lastName;
        this.age = builder.age;
        this.address = builder.address;
        this.phone = builder.phone;
    }
    
    // Getters...
    
    // Builder class
    public static class Builder {
        // Required parameters
        private final String firstName;
        private final String lastName;
        
        // Optional parameters with default values
        private int age = 0;
        private String address = "";
        private String phone = "";
        
        public Builder(String firstName, String lastName) {
            this.firstName = firstName;
            this.lastName = lastName;
        }
        
        public Builder age(int age) {
            this.age = age;
            return this;
        }
        
        public Builder address(String address) {
            this.address = address;
            return this;
        }
        
        public Builder phone(String phone) {
            this.phone = phone;
            return this;
        }
        
        public Person build() {
            return new Person(this);
        }
    }
}

// Usage
Person person = new Person.Builder("John", "Doe")
        .age(30)
        .address("123 Main St")
        .phone("555-1234")
        .build();
```

### Structural Patterns

**Adapter Pattern:** Allows objects with incompatible interfaces to collaborate.

```java
// Target interface
interface Target {
    void request();
}

// Adaptee (has incompatible interface)
class Adaptee {
    public void specificRequest() {
        System.out.println("Specific request from Adaptee");
    }
}

// Adapter (implements Target, composes Adaptee)
class Adapter implements Target {
    private Adaptee adaptee;
    
    public Adapter(Adaptee adaptee) {
        this.adaptee = adaptee;
    }
    
    @Override
    public void request() {
        adaptee.specificRequest(); // Calls the adaptee's method
    }
}

// Usage
Target target = new Adapter(new Adaptee());
target.request(); // Outputs: Specific request from Adaptee
```

**Decorator Pattern:** Attaches additional responsibilities to an object dynamically.

```java
// Component interface
interface Component {
    void operation();
}

// Concrete Component
class ConcreteComponent implements Component {
    @Override
    public void operation() {
        System.out.println("Basic operation");
    }
}

// Decorator base class
abstract class Decorator implements Component {
    protected Component component; // Reference to wrapped component
    
    public Decorator(Component component) {
        this.component = component;
    }
    
    @Override
    public void operation() {
        component.operation(); // Delegate to component
    }
}

// Concrete Decorators
class ConcreteDecoratorA extends Decorator {
    public ConcreteDecoratorA(Component component) {
        super(component);
    }
    
    @Override
    public void operation() {
        super.operation();
        addedBehavior();
    }
    
    private void addedBehavior() {
        System.out.println("Added behavior A");
    }
}

class ConcreteDecoratorB extends Decorator {
    public ConcreteDecoratorB(Component component) {
        super(component);
    }
    
    @Override
    public void operation() {
        super.operation();
        addedBehavior();
    }
    
    private void addedBehavior() {
        System.out.println("Added behavior B");
    }
}

// Usage
Component component = new ConcreteComponent();
Component decoratedA = new ConcreteDecoratorA(component);
Component decoratedB = new ConcreteDecoratorB(decoratedA);

decoratedB.operation();
// Output:
// Basic operation
// Added behavior A
// Added behavior B
```

**Composite Pattern:** Composes objects into tree structures to represent part-whole hierarchies.

```java
// Component
interface Graphic {
    void draw();
}

// Leaf
class Circle implements Graphic {
    @Override
    public void draw() {
        System.out.println("Draw a circle");
    }
}

class Rectangle implements Graphic {
    @Override
    public void draw() {
        System.out.println("Draw a rectangle");
    }
}

// Composite
class CompositeGraphic implements Graphic {
    private List<Graphic> childGraphics = new ArrayList<>();
    
    public void add(Graphic graphic) {
        childGraphics.add(graphic);
    }
    
    public void remove(Graphic graphic) {
        childGraphics.remove(graphic);
    }
    
    @Override
    public void draw() {
        System.out.println("Draw composite:");
        for (Graphic graphic : childGraphics) {
            graphic.draw();
        }
    }
}

// Usage
Circle circle = new Circle();
Rectangle rectangle = new Rectangle();

CompositeGraphic group = new CompositeGraphic();
group.add(circle);
group.add(rectangle);

CompositeGraphic canvas = new CompositeGraphic();
canvas.add(group);
canvas.add(new Circle());

canvas.draw();
```

**Proxy Pattern:** Provides a surrogate or placeholder for another object to control access to it.

```java
// Subject interface
interface Image {
    void display();
}

// Real Subject
class RealImage implements Image {
    private String fileName;
    
    public RealImage(String fileName) {
        this.fileName = fileName;
        loadFromDisk();
    }
    
    private void loadFromDisk() {
        System.out.println("Loading " + fileName + " from disk");
    }
    
    @Override
    public void display() {
        System.out.println("Displaying " + fileName);
    }
}

// Proxy
class ProxyImage implements Image {
    private String fileName;
    private RealImage realImage; // Reference to real subject
    
    public ProxyImage(String fileName) {
        this.fileName = fileName;
    }
    
    @Override
    public void display() {
        if (realImage == null) {
            // Create real subject only when needed
            realImage = new RealImage(fileName);
        }
        realImage.display();
    }
}

// Usage
Image image = new ProxyImage("test.jpg");
// Image not loaded at this point

image.display(); // Now image is loaded and displayed
image.display(); // Image already loaded, only displayed
```

### Behavioral Patterns

**Observer Pattern:** Defines a one-to-many dependency between objects.

```java
import java.util.ArrayList;
import java.util.List;

// Subject interface
interface Subject {
    void registerObserver(Observer observer);
    void removeObserver(Observer observer);
    void notifyObservers();
}

// Observer interface
interface Observer {
    void update(String message);
}

// Concrete Subject
class NewsPublisher implements Subject {
    private List<Observer> observers = new ArrayList<>();
    private String latestNews;
    
    @Override
    public void registerObserver(Observer observer) {
        observers.add(observer);
    }
    
    @Override
    public void removeObserver(Observer observer) {
        observers.remove(observer);
    }
    
    @Override
    public void notifyObservers() {
        for (Observer observer : observers) {
            observer.update(latestNews);
        }
    }
    
    public void setNews(String news) {
        this.latestNews = news;
        notifyObservers();
    }
}

// Concrete Observer
class NewsSubscriber implements Observer {
    private String name;
    
    public NewsSubscriber(String name) {
        this.name = name;
    }
    
    @Override
    public void update(String message) {
        System.out.println(name + " received news: " + message);
    }
}

// Usage
NewsPublisher publisher = new NewsPublisher();
Observer subscriber1 = new NewsSubscriber("Subscriber 1");
Observer subscriber2 = new NewsSubscriber("Subscriber 2");

publisher.registerObserver(subscriber1);
publisher.registerObserver(subscriber2);

publisher.setNews("Breaking news!");
// Output:
// Subscriber 1 received news: Breaking news!
// Subscriber 2 received news: Breaking news!
```

**Strategy Pattern:** Defines a family of algorithms, encapsulates each one, and makes them interchangeable.

```java
// Strategy interface
interface PaymentStrategy {
    void pay(int amount);
}

// Concrete Strategies
class CreditCardPayment implements PaymentStrategy {
    private String cardNumber;
    private String name;
    
    public CreditCardPayment(String cardNumber, String name) {
        this.cardNumber = cardNumber;
        this.name = name;
    }
    
    @Override
    public void pay(int amount) {
        System.out.println(amount + " paid with credit card " + cardNumber);
    }
}

class PayPalPayment implements PaymentStrategy {
    private String email;
    
    public PayPalPayment(String email) {
        this.email = email;
    }
    
    @Override
    public void pay(int amount) {
        System.out.println(amount + " paid using PayPal account " + email);
    }
}

// Context
class ShoppingCart {
    private PaymentStrategy paymentStrategy;
    
    public void setPaymentStrategy(PaymentStrategy paymentStrategy) {
        this.paymentStrategy = paymentStrategy;
    }
    
    public void checkout(int amount) {
        paymentStrategy.pay(amount);
    }
}

// Usage
ShoppingCart cart = new ShoppingCart();

cart.setPaymentStrategy(new CreditCardPayment("1234-5678-9012-3456", "John Doe"));
cart.checkout(100);

cart.setPaymentStrategy(new PayPalPayment("john@example.com"));
cart.checkout(200);
```

**Command Pattern:** Encapsulates a request as an object.

```java
// Command interface
interface Command {
    void execute();
}

// Receiver
class Light {
    public void turnOn() {
        System.out.println("Light is on");
    }
    
    public void turnOff() {
        System.out.println("Light is off");
    }
}

// Concrete Commands
class LightOnCommand implements Command {
    private Light light;
    
    public LightOnCommand(Light light) {
        this.light = light;
    }
    
    @Override
    public void execute() {
        light.turnOn();
    }
}

class LightOffCommand implements Command {
    private Light light;
    
    public LightOffCommand(Light light) {
        this.light = light;
    }
    
    @Override
    public void execute() {
        light.turnOff();
    }
}

// Invoker
class RemoteControl {
    private Command command;
    
    public void setCommand(Command command) {
        this.command = command;
    }
    
    public void pressButton() {
        command.execute();
    }
}

// Usage
Light light = new Light();
Command lightOn = new LightOnCommand(light);
Command lightOff = new LightOffCommand(light);

RemoteControl remote = new RemoteControl();
remote.setCommand(lightOn);
remote.pressButton(); // Light is on

remote.setCommand(lightOff);
remote.pressButton(); // Light is off
```

**Template Method Pattern:** Defines the skeleton of an algorithm, deferring some steps to subclasses.

```java
// Abstract class with template method
abstract class Beverage {
    // Template method
    public final void prepareRecipe() {
        boilWater();
        brew();
        pourInCup();
        if (customerWantsCondiments()) {
            addCondiments();
        }
    }
    
    // Methods implemented by the abstract class
    private void boilWater() {
        System.out.println("Boiling water");
    }
    
    private void pourInCup() {
        System.out.println("Pouring into cup");
    }
    
    // Methods to be implemented by subclasses
    protected abstract void brew();
    protected abstract void addCondiments();
    
    // Hook method - subclasses can override
    protected boolean customerWantsCondiments() {
        return true; // Default implementation
    }
}

// Concrete subclasses
class Coffee extends Beverage {
    @Override
    protected void brew() {
        System.out.println("Dripping coffee through filter");
    }
    
    @Override
    protected void addCondiments() {
        System.out.println("Adding sugar and milk");
    }
    
    @Override
    protected boolean customerWantsCondiments() {
        return false; // Override hook method
    }
}

class Tea extends Beverage {
    @Override
    protected void brew() {
        System.out.println("Steeping the tea");
    }
    
    @Override
    protected void addCondiments() {
        System.out.println("Adding lemon");
    }
}

// Usage
Beverage coffee = new Coffee();
coffee.prepareRecipe();
// Output:
// Boiling water
// Dripping coffee through filter
// Pouring into cup
// (no condiments because hook returned false)

Beverage tea = new Tea();
tea.prepareRecipe();
// Output:
// Boiling water
// Steeping the tea
// Pouring into cup
// Adding lemon
```

**State Pattern:** Allows an object to alter its behavior when its internal state changes.

```java
// State interface
interface State {
    void insertQuarter();
    void ejectQuarter();
    void turnCrank();
    void dispense();
}

// Context class
class GumballMachine {
    private State soldOutState;
    private State noQuarterState;
    private State hasQuarterState;
    private State soldState;
    
    private State currentState;
    private int count = 0;
    
    public GumballMachine(int numberOfGumballs) {
        soldOutState = new SoldOutState(this);
        noQuarterState = new NoQuarterState(this);
        hasQuarterState = new HasQuarterState(this);
        soldState = new SoldState(this);
        
        this.count = numberOfGumballs;
        if (numberOfGumballs > 0) {
            currentState = noQuarterState;
        } else {
            currentState = soldOutState;
        }
    }
    
    // Actions delegated to the current state
    public void insertQuarter() {
        currentState.insertQuarter();
    }
    
    public void ejectQuarter() {
        currentState.ejectQuarter();
    }
    
    public void turnCrank() {
        currentState.turnCrank();
        currentState.dispense();
    }
    
    // Other methods and getters/setters
    void setState(State state) {
        this.currentState = state;
    }
    
    void releaseBall() {
        System.out.println("A gumball comes rolling out!");
        if (count > 0) {
            count--;
        }
    }
    
    // Getters for states and count
    State getNoQuarterState() { return noQuarterState; }
    State getHasQuarterState() { return hasQuarterState; }
    State getSoldState() { return soldState; }
    State getSoldOutState() { return soldOutState; }
    int getCount() { return count; }
}

// Concrete States
class NoQuarterState implements State {
    private GumballMachine gumballMachine;
    
    public NoQuarterState(GumballMachine gumballMachine) {
        this.gumballMachine = gumballMachine;
    }
    
    @Override
    public void insertQuarter() {
        System.out.println("You inserted a quarter");
        gumballMachine.setState(gumballMachine.getHasQuarterState());
    }
    
    @Override
    public void ejectQuarter() {
        System.out.println("You haven't inserted a quarter");
    }
    
    @Override
    public void turnCrank() {
        System.out.println("You turned, but there's no quarter");
    }
    
    @Override
    public void dispense() {
        System.out.println("You need to pay first");
    }
}

// Other state implementations follow similar pattern
class HasQuarterState implements State {
    private GumballMachine gumballMachine;
    
    public HasQuarterState(GumballMachine gumballMachine) {
        this.gumballMachine = gumballMachine;
    }
    
    @Override
    public void insertQuarter() {
        System.out.println("You can't insert another quarter");
    }
    
    @Override
    public void ejectQuarter() {
        System.out.println("Quarter returned");
        gumballMachine.setState(gumballMachine.getNoQuarterState());
    }
    
    @Override
    public void turnCrank() {
        System.out.println("You turned...");
        gumballMachine.setState(gumballMachine.getSoldState());
    }
    
    @Override
    public void dispense() {
        System.out.println("No gumball dispensed");
    }
}

// Usage
GumballMachine gumballMachine = new GumballMachine(5);
gumballMachine.insertQuarter();
gumballMachine.turnCrank();
// Machine will change state from NoQuarterState -> HasQuarterState -> SoldState
// Then back to NoQuarterState after dispensing
```

**Iterator Pattern:** Provides a way to access elements of a collection without exposing its underlying representation.

```java
import java.util.Iterator;
import java.util.NoSuchElementException;

// Custom collection
class NameRepository {
    private String[] names = {"John", "Jane", "Jack", "Jill"};
    
    public Iterator<String> getIterator() {
        return new NameIterator();
    }
    
    // Inner Iterator implementation
    private class NameIterator implements Iterator<String> {
        private int index = 0;
        
        @Override
        public boolean hasNext() {
            return index < names.length;
        }
        
        @Override
        public String next() {
            if (!hasNext()) {
                throw new NoSuchElementException();
            }
            return names[index++];
        }
    }
}

// Usage
NameRepository namesRepository = new NameRepository();
Iterator<String> iterator = namesRepository.getIterator();

while (iterator.hasNext()) {
    String name = iterator.next();
    System.out.println("Name: " + name);
}
```