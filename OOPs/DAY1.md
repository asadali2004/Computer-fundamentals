# Object-Oriented Programming (OOP) Fundamentals

## 4.1 Introduction to Object-Oriented Programming (OOP)

Let's start with the big picture. **Object-Oriented Programming (OOP) is a programming paradigm based on the concept of "objects"**. Think of it as a way of organizing your software that mimics how things work in the real world. Instead of just writing a sequence of instructions (like a recipe), you model real-world entities as independent "objects" that have characteristics (data) and can perform actions (code).

The primary goal of OOP is to make software more modular and reusable. Imagine building a complex machine like a car. You don't just throw wires and metal together. You design distinct parts like an engine, wheels, and a steering system, each with its own specific function. In OOP, these parts are analogous to objects.

Your guidebook highlights four main pillars, often referred to as the **"Four Pillars of OOP"**:

1. **Encapsulation**
2. **Inheritance**
3. **Polymorphism**
4. **Abstraction**

Let's break each of these down with simple analogies:

### 1. Encapsulation

**Definition:** Encapsulation is about **bundling data (attributes) and the methods (functions) that operate on that data into a single unit, called an object**. It also involves **hiding the internal state of an object and only exposing necessary operations** through well-defined interfaces.

**Analogy:** Imagine your smartphone. You use it every day to make calls, send messages, and take photos. You don't need to know *how* the phone processes cellular signals, *how* the camera sensor converts light into digital data, or *how* the operating system manages memory. All those complex internal workings are hidden from you. You just interact with the screen, buttons, and apps (which are the exposed "operations"). This is encapsulation! The phone bundles its data (like your contacts, photos, apps) and its functions (making calls, taking pictures) together, and it controls how you access that data, preventing you from accidentally corrupting its internal components.

**Purpose:**
- **Data Hiding:** It prevents direct modification of an object's internal attributes from outside, maintaining data integrity.
- **Access Control:** You can specify visibility levels (like public, private, protected) to manage how other parts of the program can interact with the object's members.
- **Information Hiding:** It simplifies the interface by showing only the essential details while hiding complexity.

### 2. Inheritance

**Definition:** Inheritance is a mechanism where **one class (called the subclass or derived class) inherits properties and behavior from another class (called the superclass or base class)**. It allows the subclass to reuse and extend the functionality of the superclass.

**Analogy:** Think about biological inheritance. You might inherit certain traits (like eye color or hair color) from your parents. In OOP, a `Dog` class might inherit characteristics and behaviors from an `Animal` class. An `Animal` might have a `speak()` method, but a `Dog` would override it to specifically `bark()`. This means `Dog` gets all the general `Animal` stuff but can also add its own unique `Dog` stuff.

**Purpose:**
- **Code Reuse:** Subclasses can reuse code from their superclass without duplicating it.
- **Hierarchy:** It promotes the creation of a hierarchical relationship between classes, representing "is-a" relationships (e.g., a Dog *is a* Animal).
- **Extensibility:** You can extend existing functionality without modifying the original code.

### 3. Polymorphism

**Definition:** Polymorphism literally means "many forms." In OOP, it allows **objects of different classes to be treated as objects of a common superclass**. This enables a single interface to represent multiple underlying forms.

**Analogy:** Imagine a remote control. You can use it to turn on a TV, a sound system, or a DVD player. The "turn on" button (the single interface) performs a different action depending on which device it's interacting with (the multiple underlying forms). In OOP, if you have an `Animal` superclass and `Dog` and `Cat` subclasses, you could have a `makeSound()` method. When you call `makeSound()` on a `Dog` object, it barks; when you call it on a `Cat` object, it meows. The *same method call* produces *different results* based on the *actual object type* at runtime.

**How it's achieved:**
- **Method Overloading (Compile-time Polymorphism):** Defining multiple methods in the same class with the same name but different parameters. The compiler decides which method to call based on the arguments.
- **Method Overriding (Runtime Polymorphism):** A subclass provides its own specific implementation for a method that is already defined in its superclass. The actual method invoked is determined at runtime based on the object's type (dynamic binding).

### 4. Abstraction

**Definition:** Abstraction is the process of **hiding unnecessary details while exposing only the essential features of an object**. It allows programmers to focus on what an object *does* rather than *how* it does it.

**Analogy:** When you drive a car, you use the steering wheel, pedals, and gear shifter. You don't need to understand the intricate mechanics of the engine, transmission, or braking system. The car abstracts away those complexities, providing you with a simplified interface to control it. Similarly, when you use a map application, you see streets and landmarks, not the satellite imagery processing or GPS signal triangulation that happens behind the scenes.

**Purpose:**
- **Simplification:** Reduces complexity by providing a high-level view of functionality.
- **Focus on Essentials:** Helps you concentrate on the relevant aspects without getting bogged down in details.
- **Generalization:** Defines common interfaces or base classes that can be reused across different implementations.

These four pillars are what make OOP powerful, promoting **modularity, reusability, flexibility, and scalability** in software development.

---

## 4.2 Classes and Objects

Now, let's zoom in on the fundamental building blocks of OOP: Classes and Objects.

### What is a Class?

**A class is essentially a blueprint or a template for creating objects**. It defines the structure and behavior that all objects created from this blueprint will have.

Think of a **"cookie cutter"** as a class. It defines the shape (structure) of the cookies you'll make. It doesn't actually *make* a cookie itself, but it dictates what characteristics the cookies will have.

In programming terms, a class defines:
- **Attributes (or Properties/Fields):** These are variables that represent the **state** or **characteristics** of an object. For our cookie cutter, these could be `shape`, `size`, `pattern`.
- **Methods (or Functions):** These are functions defined within a class that perform specific tasks or operations on the object's data. These encapsulate the **behavior** of the object. For our cookie cutter, maybe it has methods like `cutDough()` or `imprintPattern()`.

### What is an Object?

**An object is an instance (or concrete realization) of a class**. While a class is the blueprint, an object is the actual thing built from that blueprint. Each object created from the same class will have its own unique set of attribute values.

Following our analogy, if the cookie cutter is the **class**, then the **actual cookies** you bake using that cutter are the **objects**. Each cookie might have the same shape and pattern (defined by the class), but they are individual cookies. One might be chocolate, another oatmeal. They have their own unique "state" (e.g., `flavor`, `icing`).

**Objects can interact with each other and with the outside world through their methods**.

---

### Java-based Coding Example: Car Class and Objects

Let's use the `Car` example from your source to illustrate classes and objects in Java.

First, we define the `Car` **class** (our blueprint):

```java
// Car.java - This is our blueprint (the Class)
public class Car {
    // Attributes (or Properties/Fields) - these define the state of a Car object
    String brand;
    String model;
    int year;
    String color;

    // Constructor - a special method to initialize a new Car object
    // It's called automatically when an object is created
    public Car(String brandName, String modelName, int manufacturedYear, String carColor) {
        this.brand = brandName;
        this.model = modelName;
        this.year = manufacturedYear;
        this.color = carColor;
        // 'this' keyword refers to the current object
    }

    // Methods - these define the behavior of a Car object
    public void startEngine() {
        System.out.println(brand + " " + model + " engine started. Vroom!");
    }

    public void drive() {
        System.out.println(brand + " " + model + " is now driving.");
    }

    public void displayInfo() {
        System.out.println("Brand: " + brand + ", Model: " + model + ", Year: " + year + ", Color: " + color);
    }
}
```
#### Explanation of the Car Class:

- `public class Car`: This line declares our `Car` class. `public` means it can be accessed from anywhere.
- `String brand;`, `String model;`, `int year;`, `String color;`: These are the **attributes** (or instance variables) that every `Car` object will have. They define the data that describes a car.
- `public Car(String brandName, ...)`: This is the **constructor**. Its purpose is to initialize a new object. Notice it has the same name as the class and no return type. When you create a `Car` object, you'll pass these values to set its initial state. The `this` keyword is important here; it refers to the current instance of the object, distinguishing between the parameter `brandName` and the instance variable `this.brand`.
- `public void startEngine()`, `public void drive()`, `public void displayInfo()`: These are the **methods**. They define what a `Car` object *can do*. `void` means they don't return any value.

Now, let's create and use `Car` **objects** from this blueprint:

```java
// Main.java - Where we create and use our Car objects
public class Main {
    public static void main(String[] args) {
        // Creating objects (instances) of the Car class
        Car myCar = new Car("Toyota", "Camry", 2022, "Blue");
        Car yourCar = new Car("Honda", "Civic", 2023, "Red");
        Car anotherCar = new Car("Tesla", "Model 3", 2024, "White");

        // Now, let's make our objects do things (call their methods)
        System.out.println("--- My Car Actions ---");
        myCar.displayInfo();  // Output: Brand: Toyota, Model: Camry, Year: 2022, Color: Blue
        myCar.startEngine();  // Output: Toyota Camry engine started. Vroom!
        myCar.drive();        // Output: Toyota Camry is now driving.

        System.out.println("\n--- Your Car Actions ---");
        yourCar.displayInfo(); // Output: Brand: Honda, Model: Civic, Year: 2023, Color: Red
        yourCar.drive();       // Output: Honda Civic is now driving.

        System.out.println("\n--- Another Car Actions ---");
        anotherCar.displayInfo(); // Output: Brand: Tesla, Model: Model 3, Year: 2024, Color: White
        anotherCar.startEngine(); // Output: Tesla Model 3 engine started. Vroom!
    }
}
```
#### Explanation of Object Creation and Usage:

- `Car myCar = new Car("Toyota", "Camry", 2022, "Blue");`: This line creates a new `Car` **object** named `myCar`. `new Car(...)` calls the constructor of the `Car` class to initialize this specific object with its unique brand, model, year, and color.
- `myCar.displayInfo();`: This calls the `displayInfo()` method *on the `myCar` object*. Each object maintains its own `brand`, `model`, `year`, and `color` values.

You can see how `myCar`, `yourCar`, and `anotherCar` are distinct objects, each with its own set of attributes (e.g., `myCar` is "Blue", `yourCar` is "Red") but they all share the same behaviors (methods like `startEngine()`, `drive()`, `displayInfo()`) defined by the `Car` class.

---

## Practice Tasks to Reinforce Learning

To truly solidify your understanding, try these coding exercises in Java:

### 1. Create a Book Class

**Task:** Define a class called `Book`.

**Attributes:** It should have attributes like `title` (String), `author` (String), `publicationYear` (int), and `isAvailable` (boolean).

**Constructor:** Create a constructor that takes `title`, `author`, `publicationYear` as arguments and initializes `isAvailable` to `true` by default.

**Methods:**
- `displayBookInfo()`: Prints all the book's details.
- `borrowBook()`: Changes `isAvailable` to `false` and prints a message indicating the book has been borrowed. If the book is already unavailable, it should print a message stating that.
- `returnBook()`: Changes `isAvailable` to `true` and prints a message indicating the book has been returned. If the book is already available, it should print a message stating that.

**Test:** In a `Main` class, create several `Book` objects and call their methods to simulate borrowing and returning, observing the output.

### 2. Create a Student Class

**Task:** Define a class called `Student`.

**Attributes:** Include `studentId` (int), `name` (String), `major` (String), and `gpa` (double).

**Constructor:** A constructor to initialize all these attributes.

**Methods:**
- `enrollCourse(String courseName)`: Prints a message that the student has enrolled in the given course.
- `updateMajor(String newMajor)`: Changes the student's `major` to `newMajor` and prints a confirmation.
- `getStudentInfo()`: Returns a String containing all student details.

**Test:** Create a few `Student` objects, update their majors, enroll them in courses, and print their information using the `getStudentInfo()` method.

