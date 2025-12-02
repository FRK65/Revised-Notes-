# 1. What is OOPS

"OOPS", which stands for Object-Oriented Programming. 
It’s a programming paradigm that organizes software design around data, or objects, 
rather than functions and logic. 
In OOP, objects are instances of classes, and classes define the properties (attributes) 
and behaviors (methods) of these objects.

# 2. core principles of OOP
**1.Abstraction  
2.Encapsulation  
3.Inheritance  
4.Polymorphism**

# 3. Object, Class, State of Object, Behaviour of Object in Java

**Class**: A class is a blueprint or template that defines the structure and behavior of objects.
It defines the properties (data) and methods (functions) that the objects
created from the class will have.

**Object**: An object is an instance of a class. It has the properties and behaviours defined
in the class.

**State of Object**: The state of an object refers to the values of its attributes (data members).
In Java, the state is defined by the values of fields in the object.

Example: In the Car class, color and model are data members that define the state of an object.

**Behaviour of Object** : The behaviour of an object refers to the actions or methods
that can be performed on that object.
This is what the object can do or what can be done to it

# 4. Encapsulation in OOP

Encapsulation refers to the practice of keeping fields (attributes) private and providing access to them via 
public methods, often known as getters and setters. 

The main purpose of encapsulation is to protect the internal state of an object and ensure 
that the object's data is modified only through well-defined interfaces.

In simple terms, encapsulation helps to hide the internal details of an object from the outside world 
and provides a controlled access mechanism.

# 4.1 Real-life Example of Encapsulation
Let's consider the example of a Bank Account.

The balance of a bank account should not be directly accessible or modifiable by just anyone. 
The balance is a private field, and we only want to allow access to it through specific methods 
(like deposit, withdraw, or check balance).

These methods (called "getters" and "setters") provide controlled access to the account balance. 
For example, you can deposit money or withdraw money, but there could be checks in place 
(e.g., you can’t withdraw more money than you have).

# 4.2 Why is Encapsulation Useful?

- **Data Protection**: By making fields private, you prevent/stop external code from accessing or 
modifying the internal state directly. This ensures that the object’s data can only be modified 
via controlled methods.

- **Flexibility**: If you later want to change how the balance is calculated or add additional validation, 
you can do so without changing the interface that users of the BankAccount class rely on.

- **Maintainability**: Encapsulation allows for better maintainability. 
You can change the internal implementation (e.g., how the balance is calculated) 
without affecting external classes that use your object.

# 5.1 Abstraction in OOP

Abstraction refers to the process of hiding the complex implementation details of a system and 
exposing only the essential features or functionalities to the outside world. 
This helps to reduce complexity and allows a programmer to focus on interactions at a higher level.

In simple terms, abstraction lets you define what a system does without having 
to know how it does it.

It allows for a cleaner, easier-to-understand interface, making code more modular, flexible, 
and easier to maintain.

# 5.2 Key Points about Abstraction:

1. **Hiding Complexity**: Abstraction allows you to define an interface to interact with, without needing to understand the complex workings behind it.
2. **Simplifies Usage**: It simplifies the interface for the user of the object by exposing only necessary details and hiding the unnecessary ones.
3. **Encapsulation vs Abstraction**:
- **Encapsulation** is about bundling the data and methods that operate on the data together and restricting direct access to the data.
- **Abstraction** is about hiding the complexity of the implementation and providing a simpler interface for the user.

# 5.3 Abstraction in Java

In Java, abstraction is achieved through:

**Abstract Classes**: 
A class that cannot be instantiated on its own and may contain abstract methods 
(methods without implementations). 
Abstract classes allow partial abstraction, as they can define some methods with implementation 
and others without.

~~~
// Abstract class representing a general animal

abstract class Animal {
    // Abstract method (doesn't have a body)
    public abstract void sound();

    // Regular method with implementation
    public void eat() {
        System.out.println("This animal is eating.");
    }
}

// Concrete class that extends the abstract class Animal

class Dog extends Animal {
    // Provide implementation for the abstract method sound
    public void sound() {
        System.out.println("The dog barks.");
    }
}
~~~

**Interfaces**: A contract that defines a set of methods that a class must implement. 
Interfaces only define the "what" but not the "how".

~~~
// Interface that defines the contract for animals
interface Animal {
    // Abstract methods
    void sound();
    void eat();
}

// Concrete class implementing the Animal interface
class Dog implements Animal {
    public void sound() {
        System.out.println("The dog barks.");
    }

    public void eat() {
        System.out.println("The dog eats.");
    }
}
~~~

In Java 8, interfaces have received some significant updates. 
The introduction of default methods and static methods in interfaces, 
as well as the functional interfaces concept, brought new capabilities

**Key Points to Remember:**
1. **Default methods** help you add new methods to an interface without breaking existing implementations.
2. **Static methods** can be declared in interfaces but must be invoked using the interface name.
3. **Functional interfaces** can be used with lambda expressions, enabling a functional style of programming.
4. **Java 8 interfaces** can still be inherited by other interfaces, but a class can only implement them.

A functional interface is an interface that contains exactly one abstract method. 
Functional interfaces can be used as the target type for lambda expressions and 
method references.

In Java 8, interfaces can inherit from multiple interfaces. 
This provides a form of multiple inheritance for interfaces (but not for classes).

~~~
interface MyInterface {
    // Default method with an implementation
    default void defaultMethod() {
        System.out.println("This is a default method.");
    }

    // Abstract method (still needs to be implemented by concrete classes)
    void abstractMethod();
}

~~~
**Advantages of Abstraction:**

- **Reduces Complexity**: Users don't need to understand the internal workings; 
they only interact with the high-level interface.
- **Increases Reusability**: The abstract class or interface can be reused by different 
concrete classes.
- **Enforces Consistency**: In the case of interfaces, it ensures that all classes implementing 
the interface follow the same method signatures, which improves code consistency.
- **Flexibility**: You can easily extend and modify the system by adding new classes or 
changing the implementation without affecting other parts of the code.


# 6. What is polymorphism in OOP

In the context of OOP, polymorphism refers to the ability of a single function, method, or operator 
to operate in different ways depending on the context.

In simpler terms, Polymorphism is a powerful feature in OOP that allows objects of different types to
be treated as instances of a common superclass.
The primary benefit is that you can write more flexible and reusable code, as the same interface 
can be used to represent different underlying forms (types).

It enables you to write more flexible, reusable, and maintainable code by allowing methods
to operate on objects of multiple types.
Polymorphism in Java is typically implemented through method overloading (compile-time)
and method overriding (run-time).

**Types of Polymorphism in OOP**

**1. Compile-time Polymorphism (also called Static Polymorphism):** **Method Overloading**

- This type of polymorphism is resolved during compile time.
- The most common examples are method overloading and operator overloading.

**2. Run-time Polymorphism (also called Dynamic Polymorphism):** **Method Overriding**

- This type of polymorphism is resolved during runtime.
- The most common example is method overriding, where a subclass provides a 
specific implementation for a method that is already defined in its superclass.

**Key Concepts in Polymorphism:**
- **Upcasting**: In run-time polymorphism, the reference type is the parent class (e.g., Animal), 
but the actual object is of the subclass (e.g., Dog or Cat). 
This is called upcasting.

- **Method Resolution**: The method that gets called is resolved dynamically at runtime based 
on the actual object type (the object that the reference is pointing to), 
rather than the reference type itself.


**Advantages of Polymorphism:**

1. **Flexibility and Extensibility**: Polymorphism allows new functionality to be added to a 
system with minimal changes to existing code. 
You can introduce new classes (e.g., new animals) without modifying existing code that 
uses the parent class Animal.

2. **Code Reusability**: You can write code that works with objects of various subclasses using a 
common interface or base class. This avoids the need for repetitive code.

3. **Maintainability**: Polymorphism allows for easier maintenance and modification. 
Since you don't need to change the interface, you can simply add new subclasses and 
override methods to introduce new behavior.

4. **Improved Readability**: It simplifies the code because you can use the same method name 
across different types of objects, reducing the need to create distinct method names for 
each specific case.


Below is a **complete explanation of *Inheritance*** written in the **same structured, clear, and detailed style** as all the topics you provided above.
This will help you maintain consistency in your notes and understanding.

---

# **6. Inheritance in OOP (Explained Like Previous Sections)**

# **6.1 What is Inheritance?**

**Inheritance** is an important pillar of Object-Oriented Programming that allows one class (called the *child class* or *subclass*) to inherit the properties and behaviors (fields and methods) of another class (called the *parent class* or *superclass*).

In simple terms:

> **Inheritance allows you to create a new class based on an existing class.**
> The new class automatically gets the fields and methods of the old class, and can also add its own.

This promotes **code reuse**, improves **maintainability**, and supports **hierarchical relationships** between classes.



# **6.2 Why is Inheritance Used? (Key Objectives)**

### **1. Code Reusability**

Instead of writing the same code in multiple classes, it can be written once in the parent class and inherited wherever needed.

### **2. Method Overriding (Runtime Polymorphism)**

Inheritance supports polymorphism by allowing subclasses to change (override) the behavior of inherited methods.

### **3. Hierarchical Classification**

It helps model real-world relationships. Example:
`Animal` → `Dog` → `Puppy`

### **4. Easy Maintenance**

Fixing/improving the parent class automatically affects all subclasses.


# **6.3 Key Terminology in Inheritance**

| Term                                     | Meaning                                                           |
| ---------------------------------------- | ----------------------------------------------------------------- |
| **Parent Class (Superclass)**            | The class whose properties are inherited                          |
| **Child Class (Subclass/Derived Class)** | The class that inherits from the parent class                     |
| **extends keyword (Java)**               | Used by the subclass to inherit from the superclass               |
| **super keyword (Java)**                 | Used to access parent class members (methods/fields/constructors) |


# **6.4 Types of Inheritance (In Java)**

Java supports:

1. **Single Inheritance**
   → One class inherits from one parent
   `class Dog extends Animal`

2. **Multilevel Inheritance**
   → A chain of inheritance
   `Animal → Dog → Puppy`

3. **Hierarchical Inheritance**
   → Multiple classes inherit from a single parent
   `Animal → Dog, Cat, Cow`

Java **does NOT support multiple inheritance through classes** (to avoid ambiguity like the diamond problem).
But **multiple inheritance is supported using interfaces**.


# **6.5 Example of Inheritance in Java**

### **Parent Class (SuperClass)**

```java
class Animal {
    String name;

    void eat() {
        System.out.println("Animal is eating...");
    }
}
```

### **Child Class (Subclass)**

```java
class Dog extends Animal {

    void bark() {
        System.out.println("Dog is barking...");
    }
}
```

### **Usage**

```java
public class Main {
    public static void main(String[] args) {
        Dog d = new Dog();
        d.name = "Tommy";        // inherited field
        d.eat();                 // inherited method
        d.bark();                // own method
    }
}
```

Output:

```
Animal is eating...
Dog is barking...
```

# **6.6 Important Points About Inheritance**

1. **Child class automatically gets all non-private fields and methods of parent class.**
2. **Constructors are NOT inherited**, but the child class calls parent constructor using `super()`.
3. Private members are not directly inherited but can be accessed using **public/protected getters**.
4. Inheritance supports **method overriding**, enabling **runtime polymorphism**.
5. Helps implement **IS-A relationship** (Dog *is a* Animal).


# **6.7 When Should You Use Inheritance?**

Use inheritance only when the child class **is a specialized version of the parent class**.

✔ Good example:
`Car extends Vehicle`
`Teacher extends Person`

✘ Bad example:
`Car extends MusicPlayer`
(No IS-A relationship → use composition instead)



# **6.8 Real-life Example of Inheritance**

### **Example: Vehicles**

* Parent: `Vehicle`
  → Common properties: speed, brand
  → Common behaviors: start(), stop()

* Child: `Car`, `Bike`, `Truck`
  → Inherits Vehicle properties
  → Adds unique behaviors like playMusic(), loadCargo(), etc.

This models real-world hierarchy accurately.



# **6.9 super Keyword in Inheritance**

### **Uses of super**

1. **Call parent class constructor**

```java
super(); // first line in child constructor
```

2. **Access parent class method**

```java
super.eat();
```

3. **Access parent class field**

```java
super.name = "Tommy";
```

---

# **6.10 Method Overriding in Inheritance**

Child class provides its own implementation to a method defined in parent class.

Example:

```java
class Animal {
    void sound() {
        System.out.println("Animal makes a sound");
    }
}

class Dog extends Animal {
    @Override
    void sound() {
        System.out.println("Dog barks");
    }
}
```

---

# **6.11 Advantages of Inheritance**

1. **Reusability**
   Common code is written once and reused by multiple classes.

2. **Improves Maintainability**
   Change in parent reflects in all children.

3. **Polymorphism Support**
   Achieves runtime polymorphism via method overriding.

4. **Logical Hierarchy Representation**
   Helps model natural relationships.

5. **Extensibility**
   Easy to add new child classes without modifying existing code.

---

# **6.12 Disadvantages of Inheritance (Important to Know)**

1. **Tight Coupling**
   Child depends heavily on parent class structure.

2. **Not always flexible**
   Wrong use of inheritance creates bad design (use composition instead).

3. **Complex Hierarchies**
   Too many inheritance levels → confusing and hard to manage.

---

# **6.13 Composition vs Inheritance (Very Important Interview Point)**

| Inheritance                  | Composition                      |
| ---------------------------- | -------------------------------- |
| “IS-A” relationship          | “HAS-A” relationship             |
| Reuse through inheritance    | Reuse through creating objects   |
| Strong coupling              | Loose coupling                   |
| Can override parent behavior | More flexible for design changes |

**Rule of thumb:**

> Use inheritance only if a strong *IS-A* relationship exists.
> Otherwise use composition.


**Complete Summary of Inheritance**

* Inheritance allows a class to acquire attributes and methods of another class.
* Achieved using `extends` in Java.
* Enables code reuse, polymorphism, and hierarchical design.
* Supports single, multilevel, and hierarchical inheritance.
* Does NOT support multiple class inheritance (only with interfaces).
* Key tools: `super`, overriding, access modifiers.
* Must be used carefully to avoid tight coupling.



