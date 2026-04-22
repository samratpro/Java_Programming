# ☕ Java Complete Learning Guide
> A comprehensive reference for teaching Java — from basics to advanced OOP concepts.

---

## 📚 Table of Contents

1. [Introduction to Java](#1-introduction-to-java)
2. [Identifiers & Keywords](#2-identifiers--keywords)
3. [Variables & Data Types](#3-variables--data-types)
4. [Operators](#4-operators)
5. [Input & Output](#5-input--output)
6. [Conditions (if/else, switch)](#6-conditions)
7. [Loops](#7-loops)
8. [Arrays](#8-arrays)
9. [Methods](#9-methods)
10. [String Handling](#10-string-handling)
11. [OOP — Classes & Objects](#11-oop--classes--objects)
12. [Constructors](#12-constructors)
13. [Access Modifiers](#13-access-modifiers)
14. [Packages & Import](#14-packages--import)
15. [External Packages (Libraries)](#15-external-packages-libraries)
16. [Encapsulation (Getter/Setter)](#16-encapsulation-gettersetter)
17. [Inheritance](#17-inheritance)
18. [Method Overloading](#18-method-overloading)
19. [Method Overriding](#19-method-overriding)
20. [Polymorphism](#20-polymorphism)
21. [Abstraction (Abstract Class)](#21-abstraction-abstract-class)
22. [Interface](#22-interface)
23. [Static Keyword](#23-static-keyword)
24. [Final Keyword](#24-final-keyword)
25. [Exception Handling](#25-exception-handling)
26. [Collections Framework](#26-collections-framework)

---

## 1. Introduction to Java

Java is a **platform-independent**, **object-oriented** programming language.
- Write Once, Run Anywhere (WORA) — thanks to the **JVM (Java Virtual Machine)**
- File extension: `.java`
- Compiled to **bytecode** (`.class`), then executed by JVM

### Basic Program Structure
```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello, World!");
    }
}
```

| Part | Meaning |
|------|---------|
| `public class HelloWorld` | Class declaration (filename must match) |
| `public static void main` | Entry point of the program |
| `String[] args` | Command-line arguments |
| `System.out.println()` | Print to console with newline |

---

## 2. Identifiers & Keywords

### Identifiers
An **identifier** is the name given to variables, methods, classes, etc.

**Rules:**
- Can contain letters, digits, `_`, `$`
- Cannot start with a digit
- Cannot be a Java keyword
- Case-sensitive (`name` ≠ `Name`)

```java
int age = 25;           // valid
int _count = 0;         // valid
int $value = 10;        // valid
// int 2fast = 5;       // INVALID — starts with digit
// int class = 1;       // INVALID — 'class' is a keyword
```

### Java Keywords (Reserved Words)
```
abstract  assert    boolean   break     byte
case      catch     char      class     const
continue  default   do        double    else
enum      extends   final     finally   float
for       goto      if        implements import
instanceof int      interface long      native
new       package   private   protected public
return    short     static    strictfp  super
switch    synchronized this    throw     throws
transient try       void      volatile  while
```
> ⚠️ Keywords cannot be used as identifiers.

---

## 3. Variables & Data Types

### Primitive Data Types
| Type | Size | Range | Example |
|------|------|-------|---------|
| `byte` | 1 byte | -128 to 127 | `byte b = 100;` |
| `short` | 2 bytes | -32,768 to 32,767 | `short s = 500;` |
| `int` | 4 bytes | -2B to 2B | `int i = 1000;` |
| `long` | 8 bytes | very large | `long l = 99999L;` |
| `float` | 4 bytes | decimal (6-7 digits) | `float f = 3.14f;` |
| `double` | 8 bytes | decimal (15 digits) | `double d = 3.14159;` |
| `char` | 2 bytes | single character | `char c = 'A';` |
| `boolean` | 1 bit | true / false | `boolean flag = true;` |

### Variable Types
```java
public class Variables {

    static int globalVar = 100;       // Class/Static variable

    public static void main(String[] args) {

        int localVar = 50;            // Local variable
        final double PI = 3.14159;    // Constant (final)

        System.out.println(localVar);
        System.out.println(globalVar);
        System.out.println(PI);
    }
}
```

### Type Casting
```java
// Widening (automatic) — smaller to larger
int x = 10;
double d = x;        // int → double (safe)

// Narrowing (manual) — larger to smaller
double pi = 3.99;
int n = (int) pi;    // double → int → result: 3 (decimal cut)

System.out.println(n); // 3
```

---

## 4. Operators

```java
public class Operators {
    public static void main(String[] args) {

        // Arithmetic
        int a = 10, b = 3;
        System.out.println(a + b);   // 13
        System.out.println(a - b);   // 7
        System.out.println(a * b);   // 30
        System.out.println(a / b);   // 3  (integer division)
        System.out.println(a % b);   // 1  (remainder)

        // Relational
        System.out.println(a > b);   // true
        System.out.println(a == b);  // false
        System.out.println(a != b);  // true

        // Logical
        boolean x = true, y = false;
        System.out.println(x && y);  // false (AND)
        System.out.println(x || y);  // true  (OR)
        System.out.println(!x);      // false (NOT)

        // Increment / Decrement
        int c = 5;
        System.out.println(c++);     // 5 (post-increment: use then add)
        System.out.println(c);       // 6
        System.out.println(++c);     // 7 (pre-increment: add then use)

        // Assignment
        int d = 10;
        d += 5;   // d = d + 5 = 15
        d -= 3;   // d = d - 3 = 12
        d *= 2;   // d = d * 2 = 24

        // Ternary
        int age = 18;
        String status = (age >= 18) ? "Adult" : "Minor";
        System.out.println(status);  // Adult
    }
}
```

---

## 5. Input & Output

```java
import java.util.Scanner;

public class InputOutput {
    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        System.out.print("Enter your name: ");
        String name = sc.nextLine();          // Read a full line (String)

        System.out.print("Enter your age: ");
        int age = sc.nextInt();               // Read integer

        System.out.print("Enter your GPA: ");
        double gpa = sc.nextDouble();         // Read decimal

        System.out.println("Name : " + name);
        System.out.println("Age  : " + age);
        System.out.printf("GPA  : %.2f%n", gpa);  // Formatted output

        sc.close();
    }
}
```

| Method | Reads |
|--------|-------|
| `nextLine()` | Full line (String) |
| `next()` | Single word (String) |
| `nextInt()` | Integer |
| `nextDouble()` | Double |
| `nextBoolean()` | Boolean |

---

## 6. Conditions

### if / else if / else
```java
int marks = 75;

if (marks >= 90) {
    System.out.println("Grade: A+");
} else if (marks >= 80) {
    System.out.println("Grade: A");
} else if (marks >= 70) {
    System.out.println("Grade: B");
} else if (marks >= 60) {
    System.out.println("Grade: C");
} else {
    System.out.println("Grade: F");
}
```

### switch Statement
```java
int day = 3;

switch (day) {
    case 1:
        System.out.println("Monday");
        break;
    case 2:
        System.out.println("Tuesday");
        break;
    case 3:
        System.out.println("Wednesday");
        break;
    case 4:
        System.out.println("Thursday");
        break;
    case 5:
        System.out.println("Friday");
        break;
    default:
        System.out.println("Weekend");
}
```

> ⚠️ Without `break`, execution **falls through** to the next case.

---

## 7. Loops

### for Loop
```java
// Print 1 to 5
for (int i = 1; i <= 5; i++) {
    System.out.println("i = " + i);
}
```

### while Loop
```java
int i = 1;
while (i <= 5) {
    System.out.println("i = " + i);
    i++;
}
```

### do-while Loop (runs at least once)
```java
int i = 1;
do {
    System.out.println("i = " + i);
    i++;
} while (i <= 5);
```

### Enhanced for Loop (for-each)
```java
int[] numbers = {10, 20, 30, 40, 50};

for (int num : numbers) {
    System.out.println(num);
}
```

### break & continue
```java
for (int i = 1; i <= 10; i++) {
    if (i == 6) break;       // stop loop at 6
    if (i % 2 == 0) continue; // skip even numbers
    System.out.println(i);   // prints: 1, 3, 5
}
```

### Nested Loop — Multiplication Table
```java
for (int i = 1; i <= 3; i++) {
    for (int j = 1; j <= 3; j++) {
        System.out.print(i * j + "\t");
    }
    System.out.println();
}
// Output:
// 1   2   3
// 2   4   6
// 3   6   9
```

---

## 8. Arrays

### 1D Array
```java
// Declaration and initialization
int[] marks = {85, 90, 78, 92, 88};

// Access element
System.out.println(marks[0]);   // 85
System.out.println(marks.length); // 5

// Traverse array
for (int i = 0; i < marks.length; i++) {
    System.out.println("marks[" + i + "] = " + marks[i]);
}
```

### 2D Array (Matrix)
```java
int[][] matrix = {
    {1, 2, 3},
    {4, 5, 6},
    {7, 8, 9}
};

// Print matrix
for (int row = 0; row < matrix.length; row++) {
    for (int col = 0; col < matrix[row].length; col++) {
        System.out.print(matrix[row][col] + " ");
    }
    System.out.println();
}
// Output:
// 1 2 3
// 4 5 6
// 7 8 9
```

### Useful Array Operations
```java
import java.util.Arrays;

int[] arr = {5, 2, 8, 1, 9};

Arrays.sort(arr);                      // Sort array
System.out.println(Arrays.toString(arr)); // [1, 2, 5, 8, 9]

int idx = Arrays.binarySearch(arr, 8); // Search after sort
System.out.println("Found at index: " + idx); // 3
```

---

## 9. Methods

### Method Syntax
```java
accessModifier returnType methodName(parameters) {
    // body
    return value; // if returnType is not void
}
```

### Examples
```java
public class MethodDemo {

    // Method with no parameter, no return
    static void greet() {
        System.out.println("Hello, Student!");
    }

    // Method with parameters
    static void add(int a, int b) {
        System.out.println("Sum = " + (a + b));
    }

    // Method with return value
    static int multiply(int a, int b) {
        return a * b;
    }

    // Method with multiple returns (using condition)
    static String checkEvenOdd(int n) {
        if (n % 2 == 0) return "Even";
        else return "Odd";
    }

    public static void main(String[] args) {
        greet();                             // Hello, Student!
        add(5, 3);                           // Sum = 8
        int result = multiply(4, 6);
        System.out.println(result);          // 24
        System.out.println(checkEvenOdd(7)); // Odd
    }
}
```

### Recursion (Method calling itself)
```java
static int factorial(int n) {
    if (n == 0) return 1;         // base case
    return n * factorial(n - 1);  // recursive call
}

// factorial(5) = 5 * 4 * 3 * 2 * 1 = 120
System.out.println(factorial(5)); // 120
```

---

## 10. String Handling

```java
String s = "Hello, Java!";

System.out.println(s.length());           // 12
System.out.println(s.toUpperCase());      // HELLO, JAVA!
System.out.println(s.toLowerCase());      // hello, java!
System.out.println(s.charAt(0));          // H
System.out.println(s.indexOf("Java"));   // 7
System.out.println(s.substring(7));       // Java!
System.out.println(s.substring(7, 11));   // Java
System.out.println(s.replace("Java", "World")); // Hello, World!
System.out.println(s.contains("Java"));   // true
System.out.println(s.startsWith("Hello")); // true
System.out.println(s.trim());             // removes spaces at edges

// String comparison
String a = "apple";
String b = "apple";
System.out.println(a.equals(b));          // true (compare content)
System.out.println(a.equalsIgnoreCase("APPLE")); // true

// String to number
int num = Integer.parseInt("42");
double d = Double.parseDouble("3.14");

// Number to String
String str = String.valueOf(100);
```

---

## 11. OOP — Classes & Objects

A **class** is a blueprint. An **object** is an instance of a class.

```java
// Class definition
class Student {
    // Fields (attributes)
    String name;
    int age;
    double gpa;

    // Method (behavior)
    void displayInfo() {
        System.out.println("Name : " + name);
        System.out.println("Age  : " + age);
        System.out.println("GPA  : " + gpa);
    }
}

// Using the class
public class Main {
    public static void main(String[] args) {

        // Create object (instance)
        Student s1 = new Student();
        s1.name = "Rahim";
        s1.age = 20;
        s1.gpa = 3.8;
        s1.displayInfo();

        // Another object
        Student s2 = new Student();
        s2.name = "Karim";
        s2.age = 22;
        s2.gpa = 3.5;
        s2.displayInfo();
    }
}
```

---

## 12. Constructors

A **constructor** is a special method called when an object is created.
- Same name as the class
- No return type

```java
class Student {
    String name;
    int age;

    // Default constructor
    Student() {
        name = "Unknown";
        age = 0;
    }

    // Parameterized constructor
    Student(String name, int age) {
        this.name = name;   // 'this' refers to current object
        this.age = age;
    }

    void show() {
        System.out.println(name + " | Age: " + age);
    }
}

public class Main {
    public static void main(String[] args) {
        Student s1 = new Student();               // default
        Student s2 = new Student("Rahim", 20);   // parameterized

        s1.show(); // Unknown | Age: 0
        s2.show(); // Rahim   | Age: 20
    }
}
```

---

## 13. Access Modifiers

| Modifier | Same Class | Same Package | Subclass | Everywhere |
|----------|------------|--------------|----------|------------|
| `private` | ✅ | ❌ | ❌ | ❌ |
| `default` (no keyword) | ✅ | ✅ | ❌ | ❌ |
| `protected` | ✅ | ✅ | ✅ | ❌ |
| `public` | ✅ | ✅ | ✅ | ✅ |

```java
class BankAccount {
    private double balance = 5000;   // only accessible inside this class
    protected String owner = "Rahim"; // accessible in subclass
    public String bankName = "BD Bank"; // accessible everywhere

    private void showBalance() {
        System.out.println("Balance: " + balance); // valid — same class
    }

    public void accessBalance() {
        showBalance(); // valid — calling private method from same class
    }
}

public class Main {
    public static void main(String[] args) {
        BankAccount acc = new BankAccount();
        // System.out.println(acc.balance); // ERROR — private
        System.out.println(acc.bankName);   // OK — public
        acc.accessBalance();                // OK — public method
    }
}
```

---

## 14. Packages & Import

A **package** is a folder/namespace that groups related classes.

### Creating a Package
```java
// File: mypackage/Calculator.java
package mypackage;

public class Calculator {
    public int add(int a, int b) {
        return a + b;
    }
}
```

### Using a Package
```java
// File: Main.java
import mypackage.Calculator;   // import specific class

public class Main {
    public static void main(String[] args) {
        Calculator calc = new Calculator();
        System.out.println(calc.add(5, 3)); // 8
    }
}
```

### Import Wildcard
```java
import mypackage.*;  // import ALL classes from mypackage
```

### Common Built-in Packages
| Package | Contents |
|---------|----------|
| `java.lang` | Auto-imported: String, Math, System |
| `java.util` | Scanner, ArrayList, Arrays, etc. |
| `java.io` | File, InputStream, etc. |
| `java.math` | BigInteger, BigDecimal |

---

## 15. External Packages (Libraries)

Using external libraries via **Maven** (most common build tool).

### Maven `pom.xml` example
```xml
<dependencies>
    <!-- Gson: JSON library by Google -->
    <dependency>
        <groupId>com.google.code.gson</groupId>
        <artifactId>gson</artifactId>
        <version>2.10.1</version>
    </dependency>
</dependencies>
```

### Using Gson Library
```java
import com.google.gson.Gson;

public class Main {
    public static void main(String[] args) {
        Gson gson = new Gson();

        // Object to JSON
        String[] fruits = {"Apple", "Mango", "Banana"};
        String json = gson.toJson(fruits);
        System.out.println(json); // ["Apple","Mango","Banana"]

        // JSON to Object
        String jsonStr = "[\"Cat\",\"Dog\"]";
        String[] animals = gson.fromJson(jsonStr, String[].class);
        System.out.println(animals[0]); // Cat
    }
}
```

---

## 16. Encapsulation (Getter/Setter)

**Encapsulation** = hiding data using `private` fields + providing `public` getters/setters.

```java
class Employee {
    private String name;
    private double salary;

    // Getter
    public String getName() { return name; }
    public double getSalary() { return salary; }

    // Setter with validation
    public void setName(String name) {
        if (name != null && !name.isEmpty())
            this.name = name;
        else
            System.out.println("Invalid name!");
    }

    public void setSalary(double salary) {
        if (salary > 0)
            this.salary = salary;
        else
            System.out.println("Salary must be positive!");
    }
}

public class Main {
    public static void main(String[] args) {
        Employee emp = new Employee();
        emp.setName("Rahim");
        emp.setSalary(50000);

        System.out.println(emp.getName());   // Rahim
        System.out.println(emp.getSalary()); // 50000.0

        emp.setSalary(-100); // Salary must be positive!
    }
}
```

---

## 17. Inheritance

**Inheritance** allows a child class to **inherit** fields and methods from a parent class.

```java
// Parent class (superclass)
class Animal {
    String name;

    Animal(String name) {
        this.name = name;
    }

    void eat() {
        System.out.println(name + " is eating.");
    }

    void sleep() {
        System.out.println(name + " is sleeping.");
    }
}

// Child class (subclass)
class Dog extends Animal {

    Dog(String name) {
        super(name); // call parent constructor
    }

    void bark() {
        System.out.println(name + " says: Woof!");
    }
}

class Cat extends Animal {

    Cat(String name) {
        super(name);
    }

    void meow() {
        System.out.println(name + " says: Meow!");
    }
}

public class Main {
    public static void main(String[] args) {
        Dog d = new Dog("Buddy");
        d.eat();    // inherited from Animal
        d.sleep();  // inherited from Animal
        d.bark();   // Dog's own method

        Cat c = new Cat("Kitty");
        c.eat();    // inherited
        c.meow();   // Cat's own method
    }
}
```

### Types of Inheritance in Java
| Type | Supported |
|------|-----------|
| Single | ✅ |
| Multilevel | ✅ |
| Hierarchical | ✅ |
| Multiple (via class) | ❌ (use Interface) |

### Multilevel Inheritance
```java
class A { void methodA() { System.out.println("A"); } }
class B extends A { void methodB() { System.out.println("B"); } }
class C extends B { void methodC() { System.out.println("C"); } }

// C inherits from B which inherits from A
C obj = new C();
obj.methodA(); // A
obj.methodB(); // B
obj.methodC(); // C
```

---

## 18. Method Overloading

**Overloading** = same method name, different parameters (compile-time polymorphism).

```java
class MathUtils {

    // Same name 'add' — different parameter types/count
    int add(int a, int b) {
        return a + b;
    }

    double add(double a, double b) {
        return a + b;
    }

    int add(int a, int b, int c) {
        return a + b + c;
    }

    String add(String a, String b) {
        return a + b;   // String concatenation
    }
}

public class Main {
    public static void main(String[] args) {
        MathUtils m = new MathUtils();
        System.out.println(m.add(2, 3));           // 5
        System.out.println(m.add(2.5, 3.5));       // 6.0
        System.out.println(m.add(1, 2, 3));        // 6
        System.out.println(m.add("Hello", " World")); // Hello World
    }
}
```

---

## 19. Method Overriding

**Overriding** = child class provides its own implementation of a parent method (runtime polymorphism).

```java
class Shape {
    void draw() {
        System.out.println("Drawing a shape...");
    }
}

class Circle extends Shape {
    @Override       // annotation — good practice
    void draw() {
        System.out.println("Drawing a Circle ⭕");
    }
}

class Rectangle extends Shape {
    @Override
    void draw() {
        System.out.println("Drawing a Rectangle ▬");
    }
}

public class Main {
    public static void main(String[] args) {
        Shape s1 = new Circle();     // parent reference, child object
        Shape s2 = new Rectangle();

        s1.draw();  // Drawing a Circle ⭕
        s2.draw();  // Drawing a Rectangle ▬
    }
}
```

### Calling Parent Method using `super`
```java
class Vehicle {
    void start() {
        System.out.println("Vehicle starting...");
    }
}

class Car extends Vehicle {
    @Override
    void start() {
        super.start();                   // call parent version
        System.out.println("Car engine ready!");
    }
}
```

---

## 20. Polymorphism

**Polymorphism** = one interface, many implementations.

### Compile-time (Overloading) — already covered in §18

### Runtime (Overriding with parent reference)
```java
class Payment {
    void pay(double amount) {
        System.out.println("Paying: " + amount);
    }
}

class CashPayment extends Payment {
    @Override
    void pay(double amount) {
        System.out.println("Paying " + amount + " in Cash 💵");
    }
}

class CardPayment extends Payment {
    @Override
    void pay(double amount) {
        System.out.println("Paying " + amount + " by Card 💳");
    }
}

class MobilePayment extends Payment {
    @Override
    void pay(double amount) {
        System.out.println("Paying " + amount + " via bKash 📱");
    }
}

public class Main {
    public static void main(String[] args) {

        // Array of parent type holding child objects
        Payment[] payments = {
            new CashPayment(),
            new CardPayment(),
            new MobilePayment()
        };

        for (Payment p : payments) {
            p.pay(500.0);  // polymorphic call
        }
    }
}
// Output:
// Paying 500.0 in Cash 💵
// Paying 500.0 by Card 💳
// Paying 500.0 via bKash 📱
```

---

## 21. Abstraction (Abstract Class)

An **abstract class** cannot be instantiated. It can have both abstract (no body) and concrete (with body) methods.

```java
abstract class Vehicle {

    String brand;

    Vehicle(String brand) {
        this.brand = brand;
    }

    // Abstract method — no body, MUST be overridden
    abstract void fuelType();

    // Concrete method — has body, can be inherited
    void start() {
        System.out.println(brand + " is starting...");
    }
}

class ElectricCar extends Vehicle {

    ElectricCar(String brand) {
        super(brand);
    }

    @Override
    void fuelType() {
        System.out.println(brand + " runs on Electricity ⚡");
    }
}

class PetrolBike extends Vehicle {

    PetrolBike(String brand) {
        super(brand);
    }

    @Override
    void fuelType() {
        System.out.println(brand + " runs on Petrol ⛽");
    }
}

public class Main {
    public static void main(String[] args) {
        Vehicle v1 = new ElectricCar("Tesla");
        Vehicle v2 = new PetrolBike("Yamaha");

        v1.start();     // Tesla is starting...
        v1.fuelType();  // Tesla runs on Electricity ⚡

        v2.start();     // Yamaha is starting...
        v2.fuelType();  // Yamaha runs on Petrol ⛽
    }
}
```

---

## 22. Interface

An **interface** is a 100% abstract contract. It defines what a class must do, not how.
- All methods are `public abstract` by default
- All fields are `public static final` by default
- A class can implement **multiple** interfaces

```java
interface Flyable {
    void fly();   // abstract by default
}

interface Swimmable {
    void swim();
}

interface Runnable {
    void run();
}

// Implementing multiple interfaces
class Duck implements Flyable, Swimmable, Runnable {

    @Override
    public void fly() { System.out.println("Duck is flying 🦆"); }

    @Override
    public void swim() { System.out.println("Duck is swimming 🌊"); }

    @Override
    public void run() { System.out.println("Duck is running 🏃"); }
}

// Implementing one interface
class Eagle implements Flyable {

    @Override
    public void fly() { System.out.println("Eagle is soaring high 🦅"); }
}

public class Main {
    public static void main(String[] args) {
        Duck duck = new Duck();
        duck.fly();
        duck.swim();
        duck.run();

        Eagle eagle = new Eagle();
        eagle.fly();
    }
}
```

### Interface vs Abstract Class
| Feature | Interface | Abstract Class |
|---------|-----------|----------------|
| Multiple inheritance | ✅ | ❌ |
| Constructor | ❌ | ✅ |
| Concrete methods | ✅ (default) | ✅ |
| Fields | Only constants | Any |
| Keyword | `implements` | `extends` |

---

## 23. Static Keyword

`static` members belong to the **class**, not to any object.

```java
class Counter {
    static int count = 0;   // shared across all objects
    String name;

    Counter(String name) {
        this.name = name;
        count++;            // increment shared counter
    }

    static void showCount() {
        System.out.println("Total objects: " + count);
    }
}

public class Main {
    public static void main(String[] args) {
        Counter c1 = new Counter("First");
        Counter c2 = new Counter("Second");
        Counter c3 = new Counter("Third");

        Counter.showCount(); // Total objects: 3
    }
}
```

### Static Import
```java
import static java.lang.Math.*;

public class Main {
    public static void main(String[] args) {
        System.out.println(sqrt(16));   // 4.0  (no need for Math.sqrt)
        System.out.println(pow(2, 8));  // 256.0
        System.out.println(PI);         // 3.141592653589793
    }
}
```

---

## 24. Final Keyword

| Usage | Effect |
|-------|--------|
| `final` variable | Constant — cannot be changed |
| `final` method | Cannot be overridden |
| `final` class | Cannot be extended (subclassed) |

```java
final class Constants {
    final double TAX_RATE = 0.15;  // cannot change
    // Cannot be extended
}

class BillCalculator {
    final void calculate(double amount) {
        // Cannot be overridden
        System.out.println("Tax: " + amount * 0.15);
    }
}
```

---

## 25. Exception Handling

**Exceptions** are runtime errors. Java handles them using try-catch.

```java
public class ExceptionDemo {
    public static void main(String[] args) {

        // Basic try-catch
        try {
            int result = 10 / 0;   // ArithmeticException
            System.out.println(result);
        } catch (ArithmeticException e) {
            System.out.println("Error: " + e.getMessage()); // / by zero
        } finally {
            System.out.println("This always runs.");
        }

        // Multiple catch blocks
        try {
            int[] arr = new int[3];
            arr[10] = 5;           // ArrayIndexOutOfBoundsException
        } catch (ArrayIndexOutOfBoundsException e) {
            System.out.println("Array index error: " + e.getMessage());
        } catch (Exception e) {
            System.out.println("General error: " + e.getMessage());
        }

        // NumberFormatException
        try {
            int n = Integer.parseInt("abc"); // invalid
        } catch (NumberFormatException e) {
            System.out.println("Invalid number format!");
        }
    }
}
```

### Custom Exception
```java
class AgeException extends Exception {
    AgeException(String message) {
        super(message);
    }
}

class Person {
    int age;

    void setAge(int age) throws AgeException {
        if (age < 0 || age > 150)
            throw new AgeException("Invalid age: " + age);
        this.age = age;
    }
}

public class Main {
    public static void main(String[] args) {
        Person p = new Person();
        try {
            p.setAge(-5);
        } catch (AgeException e) {
            System.out.println("Caught: " + e.getMessage());
        }
    }
}
```

---

## 26. Collections Framework

### ArrayList (dynamic array)
```java
import java.util.ArrayList;

ArrayList<String> names = new ArrayList<>();

names.add("Rahim");
names.add("Karim");
names.add("Jamal");

System.out.println(names);           // [Rahim, Karim, Jamal]
System.out.println(names.get(1));    // Karim
System.out.println(names.size());    // 3

names.remove("Karim");
System.out.println(names);           // [Rahim, Jamal]

for (String name : names) {
    System.out.println(name);
}
```

### HashMap (key-value pairs)
```java
import java.util.HashMap;

HashMap<String, Integer> scores = new HashMap<>();

scores.put("Rahim", 95);
scores.put("Karim", 88);
scores.put("Jamal", 72);

System.out.println(scores.get("Rahim")); // 95
System.out.println(scores.containsKey("Jamal")); // true

// Iterate
for (String key : scores.keySet()) {
    System.out.println(key + " → " + scores.get(key));
}
```

### HashSet (unique values, no duplicates)
```java
import java.util.HashSet;

HashSet<String> fruits = new HashSet<>();

fruits.add("Apple");
fruits.add("Mango");
fruits.add("Apple");  // duplicate — ignored

System.out.println(fruits.size()); // 2
System.out.println(fruits);        // [Apple, Mango]
```

---

## 🔁 Quick Reference Summary

| Concept | Keyword | Purpose |
|---------|---------|---------|
| Class | `class` | Blueprint for objects |
| Object | `new` | Instance of a class |
| Inheritance | `extends` | Reuse parent class |
| Interface | `implements` | Define a contract |
| Override | `@Override` | Redefine inherited method |
| Overload | (same name) | Multiple method signatures |
| Abstraction | `abstract` | Hide implementation |
| Encapsulation | `private` + getters/setters | Data hiding |
| Polymorphism | parent ref = child obj | Many forms |
| Constant | `final` | Unchangeable value |
| Shared | `static` | Belongs to class, not object |
| Package | `package` / `import` | Organize and reuse code |
| Error handling | `try-catch-finally` | Handle runtime errors |

---

## 📝 Teaching Tips

> 1. **Always run examples live** — students learn better by seeing output.
> 2. **Introduce OOP with real-world analogies** — `Student`, `Bank`, `Vehicle`.
> 3. **Build on each topic** — every section connects to the next.
> 4. **Mini-projects** after each section reinforces the concept.
> 5. **Encourage mistakes** — debugging is a core skill.

---

*Made for Java Teachers | Java SE 17+ Compatible*
