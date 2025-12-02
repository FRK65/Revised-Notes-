# Static keyword

The static keyword in Java used to define class-level members (variables, methods, blocks, etc.) 
that are shared by all instances of the class rather than tied to individual objects.

**Summary**:

- The static keyword can be applied to variables, methods, blocks, inner classes, etc.
- It is used for memory management and to ensure that certain properties are shared across 
 all instances of a class.
- You cannot override static methods, but you can overload them.
- You cannot declare an interface or an abstract class as static.
- Static keyword can be used with other keywords like final, volatile, transient, etc., 
 with specific constraints and behaviors.


**1. Static Variable (Class Variable):**
- A static variable is shared by all instances of the class.
- It is initialized only once when the class is loaded into memory and is common 
  for all objects of that class.
- All instances of the class share the same static variable, so any changes made to 
  the static variable affect all objects.
- Static variables can be accessed using the class name or the object name, 
  **but using the class name is recommended.**

**2. Static Method :**
- A static method belongs to the class rather than Object of the class. 
- It can be called without creating an object of the class.
- Static methods can access only static variables and static data members of the class.
- Static methods cannot access Object variables or Object methods directly.
- Static methods can be called using the class name (preferred) or through an object. (Thread.start())
- Object methods (non-static methods) belong to an object of the class, and 
you need an object to call them.
- **We can access a static method using an object of a class, but this is generally considered poor practice**

**3. Can We Override and Overload Static Methods ?**

**No**, **static methods cannot be overridden** because they are bound to the class rather 
than to an instance of the class. 
- When you declare a static method in a subclass with 
the same signature as a static method in the superclass, 
it is considered **method hiding (not overriding)**.

**Yes**, **static methods can be overloaded**. 
Overloading is when you have multiple methods with the same name but different parameter lists.

**4. Static Block:**
- A static block is used for static initialization of a class. 
- It is executed only once when the class is loaded into memory.
- Static blocks are used to initialize static variables or perform other one-time operations 
during class loading.
- It is executed before the main method or any static methods.
- It is executed only once, even if multiple objects are created.

**5. Static Class:**

- In Java, static classes are inner classes (nested classes) that are declared with 
the static keyword.
- A static nested class can access static members of the outer class.
- A static class can be instantiated without an instance of the outer class.
- It cannot access instance members of the outer class.

**6. Can We Make an Interface Static ?**

**No, interfaces cannot be declared as static in Java**. 
An interface is implicitly static because all its Methods (constants and abstract methods) 
are implicitly static. 

However, **you can have static methods in an interface since Java 8**.

**7 Can We Make an Abstract Class Static ?**

**No, an abstract class cannot be declared static**. 
The static keyword is used with nested classes (inner classes) and does not apply 
to top-level classes like abstract classes.

**8. How to Use Static Keywords with Variable, Method, and Class**

1. **When to Use Static with Variable** :
-	Use static variables when you want them to be shared among all instances of the class.
-	Example: Counter for tracking the number of instances of a class

2. **When to Use Static with Method:**
-	Use static methods for operations that do not depend on the object of the class.
-	Example: Utility functions like Math.sqrt()
     When to Use Static with Class:
-	Use static classes when the nested/inner class does not require an instance of the outer class.

**9. Static Keyword with Other Keywords :**

1. **Static and Final**:
-	A **static final variable** is a constant, meaning it cannot be changed once initialized.
-	A **static final method** cannot be overridden but can be called using the class name.

2. **Static and Volatile:**
Volatile and static are typically used together when you need a variable to be shared 
across threads and modified in a thread-safe manner. 

    - A **volatile static variable** is a shared variable that can be accessed and modified by multiple 
threads.

3. **Static and Transient:**
The transient keyword prevents a field from being serialized, but it can still be static. 
Static fields are not serialized because they are part of the class, not the object instance.

4. **Can we instantiate a static class?**

- **Yes**, you can instantiate a static nested class without creating an instance of the outer class.

5. **What happens if you declare a static method inside an instance method?**
- This is not allowed. Static methods can only be declared inside a class or interface, 
  not within instance methods or constructors.

6. **Can we access non-static members of a class from a static context?**

No, you cannot directly access non-static members (variables or methods) from a static context. 
You would need to create an instance of the class to access non-static members.

7. **What is the behavior of static variables in multithreading?**

Static variables are shared among all threads, which can lead to issues in 
multi-threaded applications if they are not handled properly (e.g., using synchronization).

8. **Can you initialize static variables inside the constructor?** 
No, static variables should be initialized in the static block or at the point of 
declaration, not inside constructors.

