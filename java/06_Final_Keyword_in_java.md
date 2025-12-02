# Final keyword 

**Final keyword** Used to define constants (variables that cannot change), 
prevent method overriding, or prevent inheritance.

**Summary**

-	The final keyword in Java ensures immutability and prevents modification in various 
    contexts (variables, methods, classes).
-	**Final Variables**: Constants or values that can only be assigned once.
-	**Final Methods**: Methods that cannot be overridden by subclasses.
-	**Final Classes**: Classes that cannot be subclassed.
-	**Final with Other Keywords**: Can be used with static, volatile, and transient for additional behavior (e.g., thread safety, constant values).

**1. final with Variables :**

-	When a variable is declared as final, it means that its value cannot be changed once 
    it has been initialized.
-	A final variable can only be assigned once, either during initialization or in 
    the constructor if it is an instance variable.
-	If a reference type variable is declared final, the reference itself cannot be 
    changed to point to another object, but the object that the reference points to 
    can still be modified (if mutable).
-	Local variables inside methods can also be declared final, meaning their values 
    cannot be changed after initialization.

**2. final with Methods:**

-	A final method cannot be overridden by subclasses. 
-   It can be used to ensure that the method behaviour is not modified
-	A final method is guaranteed to retain its behaviour across subclasses.
-	It Prevent Method Overriding
-	Final Methods in Inheritance, The method will always execute the same way, 
    no matter what class calls it, and can not be changed by subclasses

**3. final with Classes:**

-	A final class cannot be subclassed. This is useful when you want to prevent inheritance 
    for security or design reasons.
-	**Preventing Inheritance**: A final class cannot have any subclass. It cannot be extended.
-	Common Usage: The String class in Java is final, meaning you cannot subclass it.

**4. final with Interfaces:**

-	You cannot declare an interface as final because interfaces are designed to be implemented 
    by other classes. 
-   The concept of "no inheritance" is not applicable to interfaces.
-	Java does not allow interfaces to be declared final.
-	If you want to restrict the implementation of a certain method in an interface, 
    you can use default methods and make them final (but this is rarely done).


**5. final with Abstract Classes:**

-	You cannot declare an abstract class as final because an abstract class is 
    designed to be subclassed, and final prevents inheritance.
-	Since abstract classes are meant to be extended, they cannot be declared final.
-	An abstract class can be used as a template for subclasses, and final would 
    contradict this purpose.

**6. Can We Override and Overload final Methods?**

**No, final methods cannot be overridden in subclasses.** 
The purpose of declaring a method final is to lock the behaviour and prevent any subclass 
from changing it.

**Yes, you can overload a final method.** 
Overloading is based on method signatures (parameters), and it doesn't change the behaviour 
of the existing method.


**7. How to Use and When to Use the final Keyword**

**When to Use final with Variables**:
-	**Constants**: To define constant values that should not change, e.g., PI, MAX_SIZE, etc.
-	**Thread Safety**: Final variables in multi-threaded environments are automatically 
     thread-safe after initialization because their values cannot change.
-	**Ensuring Initialization**: Final instance variables must be initialized in the constructor 
    or at the point of declaration. This is helpful for creating immutable objects.

**8. When to Use final with Methods:**
-	**Prevent Method Overriding**: Use final when you want to ensure that a method cannot be overridden by any subclass (for example, to maintain security or consistency of behavior).
-	**Performance Optimization**: Some JVMs can optimize final methods better, especially in cases like method dispatch.
     When to Use final with Classes:
-	**Prevent Inheritance**: Use final when you want to prevent a class from being subclassed. This can be important for security or if you want the class to function as a singleton (like String in Java).


**9. final Keyword with Other Keywords**

**final and static:**
-	**Final Static Variables**: A final static variable is a constant that is shared across 
    all instances of the class. It cannot be changed after initialization
-	**Final Static Methods**: A final static method cannot be overridden or changed by subclasses.
     final and volatile:
-	**Final Volatile Variables**: A final volatile variable guarantees that once the variable is 
    assigned a value, its value is visible to all threads. 
    The value of the variable cannot change once set.
 	final and transient:
-	**Final Transient Variables**: You can declare a final transient variable, 
    but it means the value of the final variable will not be serialized.

**10. Tricky Questions and Answers on final:**

**a. Can we initialize a final variable multiple times?**

No, a final variable can only be assigned once, either in the constructor 
(for instance variables) or at the point of declaration.

**b. What happens if a final variable is initialized in a constructor?**

If a final variable is initialized in a constructor, 
it can be different for each instance of the class, 
but it can still only be assigned once per instance.

**c. Can we create an array of final objects?**

Yes, but while the reference to the array is final (i.e., you cannot reassign the reference), 
the elements of the array can still be modified if they are mutable objects.
~~~
Example:

    final int[] arr = new int[5];
    arr[0] = 10;  // This is allowed
    arr = new int[10];
    // Compile-time error: cannot assign a new array to final variable arr
~~~

**d. Can a final class have a constructor?**
Yes, a final class can have a constructor. 
Declaring a class final just prevents subclassing but doesn't affect the ability to 
initialize instances of the class.

**e. Can we extend a final class and implement its final methods?**

**No**, you cannot extend a final class, and you cannot override its final methods. 
However, you can still call the final methods from the subclass.

**f. Can we make a method final and synchronized at the same time?**

Yes, you can declare a method final and synchronized together. 
A final method is just one that cannot be overridden, and synchronized ensures that only 
one thread can access it at a time.
~~~
Example:
class Example {
    final synchronized void display() {
        
        System.out.println("Thread-safe and non-overridable method");
    }
}
~~~


