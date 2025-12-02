# 1. Constructor and Destructor in Java

**Constructor** : A constructor is a special method used to initialize objects. 
It is called when an object is created.

**When are Constructors Called?**
- A constructor is automatically called when an object is created using the new keyword.
- The constructor initializes the instance variables based on the values passed 
to it (for parameterized constructors) or assigns default values (for the default constructor).

Key Characteristics of Constructors:
-	A constructor has the same name as the class.
-	A constructor does not have a return type (not even void).
-	A constructor is automatically invoked when an object is created using the new keyword.
-	A constructor is used to initialize objects.
-	Constructors do not return values.
-	If no constructor is explicitly defined, Java provides a default constructor that initializes fields to their default values.
-	A parameterized constructor is a constructor that takes one or more arguments. 

**In Java, there are two types of constructors:**
1.	**Default Constructor** (No-Argument Constructor)
2.	**Parameterized Constructor**

**Constructor Overloading**

Java allows constructor overloading, which means you can define multiple constructors with 
different parameter lists within the same class. This enables you to create objects in 
different ways, depending on what parameters you pass.

**Destructor** : Java does not have explicit destructors. 
Instead, it has garbage collection, which automatically manages memory and removes 
objects that are no longer in use. 
The finalize() method is called by the garbage collector before an object is destroyed 
(though its use is discouraged).


# 2. Access Specifiers and Access Modifiers in Java

**Access Specifiers:**

- **Public**: The member is accessible from any class.
- **Private**: The member is accessible only within the class it is defined.
- **Protected**: The member is accessible within the same package and subclasses.
- **Default (no specifier)**: The member is accessible only within the same package.

**Access Modifiers:**

public, private, protected, and default are also considered access modifiers. 
In addition, we have:

- **static**: Makes the member belong to the class rather than any instance.
- **final**: Used to declare constants, prevent method overriding, or prevent inheritance.
- **synchronized**: Ensures that only one thread can access the method or block at a time.
- **volatile**: Ensures that a variable is directly read from or written to the main memory.
- **transient**: Prevents a field from being serialized.

# 3. this() and super() in Java

**this() Keyword**:

The this() keyword is used to call a constructor of the current class. 
It helps in constructor chaining — invoking one constructor from another within the same class.

**Key Features and Concepts of this()**
1.	**Constructor Chaining:** :this() is used to call another constructor of the same class. This must be the first statement in the constructor body.
2.	**Purpose**:	this() helps to initialize the object using a different constructor
      AND It is used to delegate the initialization of an object to another constructor in 
       the same class.
3.	**Constructor Overloading:**
      - In a class, you can have multiple constructors with different parameter lists. 
        You can use this() to call a constructor with different arguments.
4.	**Usage**: Call another constructor within the same class:
5.	**Limitation**: The this() constructor call must be the first statement in a constructor.

6. **When to Use this():**
   - To avoid repetition of constructor code.
   - When you have multiple constructors with different parameters but want to 
     initialize the same state in the object.

#4.  **super() Keyword**:
The super() keyword refers to the parent class (superclass) and is used in two major contexts: 
**calling the parent class constructor and invoking parent class methods.**

Key Features and Concepts of **super()**
1.	**Calling Parent Class Constructor**:
      - super() is used to call the constructor of the parent class. 
      - It must be the first statement in the child class constructor.
      - If no explicit call to super() is made, the default constructor of the 
      superclass is called automatically (if it exists).
2.	**Accessing Parent Class Methods and Variables**:
      - You can use super to call parent class methods or access parent class fields 
       if they are hidden or overridden in the child class.
      - It is especially useful when a method is overridden, and you want to call 
      the parent class method.
3.	**Constructor Chaining Across Classes**:
      - In a class hierarchy, super() can be used to chain constructor calls from the 
      subclass to the superclass. 
      - This allows proper initialization of the inherited part of the object.
4.	**Usage**:
      - Calling the superclass constructor:
5.	**Accessing Parent Class Fields and Methods:**
      - If a field or method in the child class hides or overrides a field or method in 
       the parent class, you can use super to access the parent class's version.

**Important Concepts and Behavior:**
1.	**super() vs this():**
      - this() calls a constructor in the same class, while super() calls the constructor of the superclass.
      - You cannot use both this() and super() in the same constructor, 
       because both are constructor calls, and Java allows only one constructor call 
      in the beginning of a constructor.
      
2.	**Calling Parent Constructor Implicitly**:
      - If you don’t explicitly call super(), the default constructor of the parent class is 
       called automatically.
      - If the parent class doesn’t have a default constructor, you must explicitly call a 
      constructor of the parent class using super(<arguments>).
3.	**Accessing Parent Members**:
      - super is particularly useful to access members (fields, methods) that are hidden or 
      overridden in the subclass.
4.	**Constructor Chaining Across Classes:**
      - Constructor chaining occurs when a constructor calls another constructor 
      (either within the same class using this() or from the parent class using super()).

**Tricky and Complex Concepts:**
1. It’s important to note that constructors in Java do not inherit from the parent class. 
2. Each class must explicitly define its own constructor. 
 You use super() to invoke a constructor from the parent class.
3. Constructor of Abstract Classes:
      - In case the parent class is abstract, you still need to call its constructor 
        explicitly using super(). 
      - The abstract class constructor will still run, but you cannot instantiate 
        the abstract class directly.
3.	Constructor Overloading and Inheritance:
      - In case of constructor overloading, the choice of which constructor to call (using this() or super()) 
        depends on the arguments passed during object creation.
4.	Multiple Inheritance in Java:
      - Java doesn’t support multiple inheritance via classes (you can use interfaces for that), 
       but the super() keyword still ensures that only one parent class constructor 
       is invoked in a single inheritance hierarchy.

**Interview Questions on this() and super():**
1.	What is the difference between this() and super()?
- this() calls a constructor of the same class, while super() calls a constructor of the superclass.

2. Can you call this() and super() in the same constructor?
- No, you cannot call both this() and super() in the same constructor. 
Only one constructor call is allowed, and it must be the first statement in the constructor.

3.	What happens if you don’t explicitly call super() in a constructor?
- If you don't explicitly call super(), the default constructor of the superclass is called implicitly, 
if the superclass has a no-argument constructor.

4.	Can super() be used to call a constructor from the parent class with arguments?
- Yes, super() can be used to call a constructor of the parent class with arguments, 
like super(arg1, arg2).

5.	Can you access the private members of a parent class using super?
- No, super cannot access private members of the parent class. It can only access public or 
protected members of the parent class.

6.	Is it possible to call the constructor of the superclass without using super()?
- Yes, but only if the superclass has a no-argument constructor. 
In this case, it is called automatically.
      
7.	What will happen if you try to call super() after this() in a constructor?
      - It will result in a compile-time error, as Java only allows one constructor call 
       (super() or this()) in a constructor, and it must be the first statement.
      
8.	Can we use this to refer to another object of the same class?
- Yes, this refers to the current instance of the class, but it can also be passed to methods or 
 constructors of the same class as an argument.

