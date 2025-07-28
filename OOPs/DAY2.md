# 🎯 Object-Oriented Programming - Day 2

## 📚 Topic 4.3: Inheritance and Polymorphism

> **🌟 Core Concept**: Object-Oriented Programming (OOP) is built on several core principles, and inheritance and polymorphism are two of its most powerful features. They allow us to create flexible, reusable, and maintainable code.

---

## 🧬 Inheritance: Building on What's Already There

### 🌳 Real-Life Analogy
Think of inheritance in programming just like inheritance in real life, such as a **family tree**. A child inherits certain characteristics from their parents. In OOP, a **subclass** (or derived class) can inherit properties (attributes) and behaviors (methods) from a **superclass** (or base class).
### 💡 Why is Inheritance Useful?

| **Benefit** | **Description** | **Example** |
|-------------|-----------------|-------------|
| 🔄 **Code Reusability** | Instead of writing the same code over and over, you can define common functionalities in a superclass and reuse them in subclasses | All animals can `eat()` and `sleep()` |
| 🏗️ **Hierarchy and Organization** | It helps establish a logical "is-a" relationship, making your code structure clearer | A "Dog **is-a** Animal" |
| 🚀 **Extensibility** | You can easily extend existing functionality by creating new subclasses without modifying the original superclass code | Add new animal types without changing `Animal` class |

> **📝 Note**: The source mentions that inheritance can form a hierarchy of classes, where each subclass inherits from its superclass and can add its own attributes or methods.

---

### 🐕 Java Example: Pet Store System
Let's imagine we're building a system for a pet store. We'll start with a general `Animal` class, and then create more specific types of animals like `Dog` and `Cat`.

```java
// 🦴 Superclass (also called Base Class or Parent Class)
class Animal {
    String name;

    Animal(String name) { // Constructor for Animal
        this.name = name;
    }

    void eat() { // Common behavior for all animals
        System.out.println(name + " is eating.");
    }

    void sleep() { // Another common behavior
        System.out.println(name + " is sleeping.");
    }

    // This method will be overridden by subclasses
    void makeSound() {
        System.out.println("The animal makes a sound."); // [8]
    }
}

// 🐕 Subclass (also called Derived Class or Child Class)
// The 'extends' keyword is used to indicate inheritance in Java [9]
class Dog extends Animal {
    Dog(String name) {
        // 'super' keyword calls the constructor of the superclass [10, 11]
        super(name); 
    }

    // Method Overriding: Providing a specific implementation for a method
    // that is already defined in the superclass [5, 12-15]
    @Override // It's good practice to use @Override annotation
    void makeSound() {
        System.out.println(name + " barks: Woof! Woof!"); // [8]
    }

    // Dog's unique behavior
    void fetch() {
        System.out.println(name + " is fetching the ball.");
    }
}

// 🐱 Another Subclass
class Cat extends Animal {
    Cat(String name) {
        super(name);
    }

    @Override
    void makeSound() {
        System.out.println(name + " meows: Meow!");
    }

    // Cat's unique behavior
    void purr() {
        System.out.println(name + " is purring contentedly.");
    }
}

// 🎯 Main Class
public class InheritanceExample {
    public static void main(String[] args) {
        Dog myDog = new Dog("Buddy");
        Cat myCat = new Cat("Whiskers");

        myDog.eat();         // Inherited from Animal
        myDog.sleep();       // Inherited from Animal
        myDog.makeSound();   // Overridden in Dog
        myDog.fetch();       // Unique to Dog

        System.out.println("---");

        myCat.eat();         // Inherited from Animal
        myCat.sleep();       // Inherited from Animal
        myCat.makeSound();   // Overridden in Cat
        myCat.purr();        // Unique to Cat
    }
}
```
### 🔍 Key Points

- In this example, `Dog` and `Cat` **extend** `Animal`
- They inherit `eat()` and `sleep()` methods directly
- They **override** `makeSound()` to provide their specific sounds
- The `super(name)` call in the subclass constructors ensures that the `Animal` part of the `Dog` and `Cat` objects is properly initialized
- This is an important use of the `super` keyword to refer to the immediate parent class's constructor or methods

---

## 🎭 Polymorphism: Many Forms, One Interface

### 📖 Definition
The term **Polymorphism** means "many forms". It allows objects of different classes to be treated as objects of a common superclass, enabling a single interface to represent multiple underlying forms.

### 🛠️ How is Polymorphism Achieved?

The source highlights two main ways polymorphism is achieved:

| **Type** | **When Decided** | **Description** | **Example** |
|----------|------------------|-----------------|-------------|
| 🔧 **Method Overloading** | Compile-time | Multiple methods within the same class with same name but different parameter lists | `add(int, int)` vs `add(double, double)` |
| ⚡ **Method Overriding** | Runtime | Subclass provides its own implementation of a method defined in superclass | `Dog.makeSound()` vs `Cat.makeSound()` |

### 📺 Real-life Analogy: Universal Remote Control

Imagine a **universal remote control** for different electronic devices like a TV, DVD player, and sound system. The **"Power" button** is the same interface on the remote (polymorphism). When you press it, the underlying action (turning on/off) is different for each device:

- 📺 **TV**: Turns on/off
- 💿 **DVD Player**: Turns on/off  
- 🔊 **Sound System**: Turns on/off

The remote doesn't need to know the specific internal mechanisms; it just sends the "Power" signal, and each device responds in its own way.

---

### 🎯 Java Example: Polymorphism in Action
Let's extend our Animal example to demonstrate polymorphism.

```java
// Re-using Animal, Dog, and Cat classes from the Inheritance example.

public class PolymorphismExample {
    public static void main(String[] args) {
        // 🎭 Polymorphic behavior:
        // We can declare a variable of type Animal, but assign it an object of a subclass (Dog or Cat).
        // This is possible because a Dog IS-A Animal, and a Cat IS-A Animal. [6]

        Animal animal1 = new Dog("Lucy");      // Animal reference, Dog object
        Animal animal2 = new Cat("Mittens");   // Animal reference, Cat object
        Animal animal3 = new Animal("Generic Animal"); // Animal reference, Animal object

        // When makeSound() is called, the actual method invoked depends on the
        // *runtime type* of the object, not the *reference type*. This is dynamic binding. [12, 15, 22]
        animal1.makeSound(); // Output: Lucy barks: Woof! Woof! (Dog's overridden method)
        animal2.makeSound(); // Output: Mittens meows: Meow! (Cat's overridden method)
        animal3.makeSound(); // Output: The animal makes a sound. (Animal's method)

        System.out.println("--- 🧮 Method Overloading Example (Compile-time Polymorphism) ---");
        Calculator calc = new Calculator();
        System.out.println("Sum of two ints: " + calc.add(5, 3));        // Calls add(int, int)
        System.out.println("Sum of three ints: " + calc.add(5, 3, 2));   // Calls add(int, int, int)
        System.out.println("Sum of two doubles: " + calc.add(5.5, 3.2)); // Calls add(double, double)
    }
}

// 🧮 Calculator Class demonstrating Method Overloading
class Calculator {
    // Method Overloading: Same method name 'add', but different parameter lists [5, 12]
    int add(int a, int b) {
        return a + b;
    }

    int add(int a, int b, int c) { // Different number of arguments
        return a + b + c;
    }

    double add(double a, double b) { // Different types of arguments
        return a + b;
    }
}
```

### 🔍 Key Insights

In the `PolymorphismExample`:
- `animal1` and `animal2` are declared as `Animal` types, but they actually hold `Dog` and `Cat` objects
- When `makeSound()` is called on them, the **JVM (Java Virtual Machine)** determines at runtime which specific `makeSound()` method to execute
- This showcases **runtime polymorphism** or **dynamic binding**

For **method overloading**, the `Calculator` class demonstrates how you can have multiple `add` methods with distinct parameter lists. The compiler knows which `add` method to call based on the arguments provided during the method call.

---
## 📚 Topic 4.4: Encapsulation and Abstraction

> **🤝 Working Together**: These two principles work hand-in-hand to make your software robust, secure, and easier to manage.

---

## 🛡️ Encapsulation: The Secure Capsule

### 📖 Definition
**Encapsulation** is about bundling data (attributes) and the methods (functions) that operate on that data into a single unit, known as an **object**. It's also about hiding the internal state of an object and only exposing necessary operations through well-defined interfaces.

### 💊 Real-life Analogy: Medicine Capsule

Imagine a **medicine capsule**:
- The **capsule** (the object) contains different **ingredients** (data) inside
- You don't need to know the exact chemical composition or how the ingredients are mixed to take the medicine
- You just take the capsule, and it performs its intended function (the method)
- The **internal details are hidden** from you, and you interact with it only through its external form (taking it)

### 💡 Why is Encapsulation Useful?

| **Benefit** | **Description** | **Example** |
|-------------|-----------------|-------------|
| 🔒 **Data Hiding** | Prevents direct, uncontrolled access to an object's internal data, maintaining its integrity | Private bank account balance |
| 🎛️ **Access Control** | Specify visibility levels for attributes and methods, allowing controlled access | Public, private, protected modifiers |
| 🧩 **Modularity** | Changes to internal implementation don't affect other parts of the code | Update internal logic without breaking client code |

### 🔐 Access Control Levels

| **Modifier** | **Visibility** | **Access Level** |
|--------------|---------------|------------------|
| `private` | 🔴 **Restricted** | Only within the same class |
| `default` | 🟡 **Package** | Only within the same package |
| `protected` | 🟠 **Family** | Same package + subclasses (even in different package) |
| `public` | 🟢 **Open** | Accessible from anywhere |

---

### 🏦 Java Example: Bank Account System
Let's create a `BankAccount` class. We want to ensure that the account balance can't be directly changed from outside the class, only through specific methods like `deposit` and `withdraw`.

```java
class BankAccount {
    // 🔒 Attributes (data) are typically made private to hide them [23]
    private String accountNumber;
    private double balance;

    // 🏗️ Constructor to initialize the object
    public BankAccount(String accountNumber, double initialBalance) {
        this.accountNumber = accountNumber; // 'this' keyword refers to the current object [18, 21]
        if (initialBalance >= 0) {
            this.balance = initialBalance;
        } else {
            System.out.println("Initial balance cannot be negative. Setting to 0.");
            this.balance = 0;
        }
    }

    // 🔍 Public methods (behaviors) to allow controlled access to the data (getters/setters)
    public String getAccountNumber() { // Getter method to retrieve account number
        return accountNumber;
    }

    public double getBalance() { // Getter method to retrieve balance
        return balance;
    }

    // 💰 Method to modify balance (deposit)
    public void deposit(double amount) {
        if (amount > 0) {
            balance += amount;
            System.out.println("Deposited: $" + amount + ". New balance: $" + balance);
        } else {
            System.out.println("Deposit amount must be positive.");
        }
    }

    // 💸 Method to modify balance (withdraw)
    public void withdraw(double amount) {
        if (amount > 0 && balance >= amount) {
            balance -= amount;
            System.out.println("Withdrew: $" + amount + ". New balance: $" + balance);
        } else {
            System.out.println("Invalid withdrawal amount or insufficient balance.");
        }
    }
}

// 🎯 Main Class
public class EncapsulationExample {
    public static void main(String[] args) {
        BankAccount myAccount = new BankAccount("123456789", 1000.0);

        // ✅ Accessing data through public getter methods
        System.out.println("Account Number: " + myAccount.getAccountNumber());
        System.out.println("Current Balance: $" + myAccount.getBalance());

        // ✅ Modifying data through public methods (controlled access)
        myAccount.deposit(500.0);
        myAccount.withdraw(200.0);
        myAccount.withdraw(1500.0); // This will show an error message due to insufficient balance
        myAccount.deposit(-100.0);  // This will show an error message due to negative amount

        // ❌ Attempting to directly access or modify private data will result in a compilation error:
        // myAccount.balance = 5000.0; // ERROR: balance has private access in BankAccount
    }
}
```

### 🔍 Key Points

In this `BankAccount` example:
- `accountNumber` and `balance` are **private**, meaning they can only be accessed or modified from within the `BankAccount` class itself
- We provide **public methods** (`getAccountNumber`, `getBalance`, `deposit`, `withdraw`) as the only "gates" to interact with the account data
- This encapsulation ensures that the data **remains consistent** and is handled according to defined rules (e.g., no negative deposits)

---

## 🎭 Abstraction: Focusing on What Matters

### 📖 Definition
**Abstraction** is the process of hiding the implementation details of an object and exposing only its essential features or behaviors. It allows us to focus on **"what an object does"** rather than **"how it does it"**.

### 🚗 Real-life Analogy: Driving a Car

When you **drive a car**, you use:
- 🎛️ **Steering wheel**
- ⚡ **Accelerator**  
- 🛑 **Brake**

You **don't need to know**:
- How the engine works
- How fuel is ignited
- How the braking system engages

The car provides an **abstracted interface** (the controls) that allows you to operate it without understanding its complex internal machinery. This is **abstraction**!

### 💡 Why is Abstraction Useful?

| **Benefit** | **Description** | **Example** |
|-------------|-----------------|-------------|
| 🎯 **Reduces Complexity** | By hiding unnecessary details, simplifies user interaction with code | Use `calculateArea()` without knowing geometry formulas |
| 🔧 **Improves Maintainability** | Changes to internal logic won't break external code | Update calculation method without affecting client code |
| 🧩 **Promotes Modularity** | Build systems from high-level components with common interfaces | Different shapes, same `calculateArea()` interface |

> **🛠️ Implementation**: Abstraction can be achieved in Java using **abstract classes** and **interfaces**.

---

### 🔺 Java Example: Shape System
Let's revisit our Shape concept. We know all shapes have an area, but the way to calculate it differs for each shape. We can use an **abstract class** to represent the generic concept of a Shape.

```java
// 🔺 Abstract Class
// An abstract class cannot be instantiated directly [32, 33].
// It may contain abstract methods (methods without implementation) and concrete methods. [34]
// A class extending an abstract class *must* provide implementations for all abstract methods,
// unless it is also declared abstract. [34, 35]
abstract class Shape { // The 'abstract' keyword makes this class abstract
    String color;

    Shape(String color) {
        this.color = color;
    }

    // 🚫 An abstract method - no implementation here, only signature [22, 32, 34]
    // Subclasses are forced to implement this method.
    abstract double calculateArea(); // [35]

    // ✅ A concrete method - has implementation, can be inherited directly
    void displayColor() {
        System.out.println("This shape is " + color);
    }
}

// 🔴 Concrete subclass of Shape
class Circle extends Shape {
    double radius;

    Circle(String color, double radius) {
        super(color);
        this.radius = radius;
    }

    @Override
    double calculateArea() { // Implementation for Circle's area
        return Math.PI * radius * radius;
    }
}

// ⬜ Concrete subclass of Shape
class Rectangle extends Shape {
    double length;
    double width;

    Rectangle(String color, double length, double width) {
        super(color);
        this.length = length;
        this.width = width;
    }

    @Override
    double calculateArea() { // Implementation for Rectangle's area
        return length * width;
    }
}

// 🎯 Main Class
public class AbstractionExample {
    public static void main(String[] args) {
        // ❌ We cannot create an object of the abstract class Shape directly:
        // Shape myShape = new Shape("Blue"); // ERROR: Shape is abstract; cannot be instantiated

        // ✅ We can create objects of concrete subclasses
        Circle circle = new Circle("Red", 7.0);
        Rectangle rectangle = new Rectangle("Blue", 4.0, 5.0);

        // 🎭 We can treat them polymorphically as Shape objects (abstraction in action!)
        Shape shape1 = circle;
        Shape shape2 = rectangle;

        System.out.println("Circle Area: " + shape1.calculateArea());    // Calls Circle's implementation
        shape1.displayColor(); // Inherited concrete method

        System.out.println("Rectangle Area: " + shape2.calculateArea()); // Calls Rectangle's implementation
        shape2.displayColor(); // Inherited concrete method
    }
}
```

### 🔍 Key Points

In this example:
- `Shape` is an **abstract class** with an abstract method `calculateArea()`
- This **forces** any concrete subclass (like `Circle` and `Rectangle`) to provide its own specific `calculateArea()` implementation
- The **client code** (in main) interacts with `Shape` objects at a high level, calling `calculateArea()` without needing to know the precise geometric formula for each shape
- This is the **essence of abstraction** - hiding complexity while providing a clean interface

---
## 🚀 Practice Tasks for Reinforcing Learning

> **💪 Challenge Yourself**: Here are some coding challenges to help you solidify your understanding of **Inheritance**, **Polymorphism**, **Encapsulation**, and **Abstraction**.

---

### 🚗 Task 1: Building a Vehicle Hierarchy (Inheritance & Polymorphism)

**🎯 Scenario**: You need to model different types of vehicles. All vehicles have a speed and can `start()` and `stop()`. Cars also have a `numberOfDoors` and can `honk()`. Motorcycles have a `handlebarType` and can `wheelie()`.

#### 📋 Instructions:

| **Step** | **Task** | **Details** |
|----------|----------|-------------|
| 1️⃣ | Create `Vehicle` class | Add `speed` attribute, `start()` and `stop()` methods |
| 2️⃣ | Create `Car` subclass | Extends `Vehicle`, add `numberOfDoors`, override `start()`, add `honk()` |
| 3️⃣ | Create `Motorcycle` subclass | Extends `Vehicle`, add `handlebarType`, override `stop()`, add `wheelie()` |
| 4️⃣ | Demonstrate inheritance | Create instances and call inherited methods |
| 5️⃣ | Show polymorphism | Use `Vehicle` array/list, call overridden methods |

#### 🎨 Expected Output Structure:
```java
// Vehicle started.
// Car started.
// Beep beep!
// Vehicle stopped.
// Motorcycle stopped.
// Doing a wheelie!
```

---

### 👤 Task 2: User Profile Management (Encapsulation)

**🎯 Scenario**: Design a `User` class for a simple application that stores user details. You need to ensure data integrity for user passwords.

#### 📋 Instructions:

| **Step** | **Task** | **Security Rule** |
|----------|----------|-------------------|
| 1️⃣ | Create `User` class | Private: `username`, `email`, `password` |
| 2️⃣ | Add constructor | Initialize all three attributes |
| 3️⃣ | Create getters | Public methods for `username` and `email` only |
| 4️⃣ | Password validation | `setPassword()` - minimum 8 characters |
| 5️⃣ | Display method | `displayUserInfo()` shows username and email |
| 6️⃣ | Test security | Try valid/invalid passwords, attempt direct access |

#### 🔐 Security Features:
- ❌ **No** `getPassword()` method (security reasons)
- ✅ **Only** `setPassword()` with validation
- 🛡️ **Private** attributes cannot be accessed directly

---

### 💳 Task 3: Payment Gateway (Abstraction with Interface)

**🎯 Scenario**: You are building an e-commerce platform that needs to integrate with different payment gateways (e.g., PayPal, Stripe). You want a common way to process payments regardless of the specific gateway.

#### 📋 Instructions:

| **Step** | **Component** | **Implementation** |
|----------|---------------|-------------------|
| 1️⃣ | `PaymentGateway` interface | `processPayment(double amount)` → boolean |
| 2️⃣ | Interface method | `refundPayment(String transactionId)` → boolean |
| 3️⃣ | `PayPalGateway` class | Implements interface, always successful |
| 4️⃣ | `StripeGateway` class | Implements interface, 80% success rate |
| 5️⃣ | Polymorphic usage | Declare as `PaymentGateway`, assign concrete objects |
| 6️⃣ | Test abstraction | Call methods through interface references |

#### 💰 Payment Gateway Specifications:

| **Gateway** | **processPayment()** | **refundPayment()** |
|-------------|---------------------|-------------------|
| 💙 **PayPal** | "Processing PayPal payment of $X. Always successful." → `true` | "Refunding PayPal transaction X. Always successful." → `true` |
| 💜 **Stripe** | "Processing Stripe payment of $X. Simulating 80% success rate." → 80% `true` | "Refunding Stripe transaction X. Always successful." → `true` |

#### 🎲 Random Success Implementation:
```java
// For Stripe 80% success rate
return Math.random() < 0.8; // Returns true 80% of the time
```

---

## 🎯 Learning Objectives Achieved

After completing these tasks, you will have hands-on experience with:

| **Concept** | **What You'll Learn** | **Real-World Application** |
|-------------|----------------------|---------------------------|
| 🧬 **Inheritance** | Code reuse, "is-a" relationships | Vehicle hierarchy, UI components |
| 🎭 **Polymorphism** | One interface, many implementations | Plugin systems, strategy patterns |
| 🛡️ **Encapsulation** | Data protection, controlled access | User authentication, banking systems |
| 🎭 **Abstraction** | Hide complexity, focus on essentials | Payment processing, database access |

> **🎉 Good Luck!** These tasks should provide a comprehensive hands-on experience with the core OOP concepts we discussed!