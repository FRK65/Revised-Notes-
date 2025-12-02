# 1. Object, Class, State of Object, Behaviour of Object in Java

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
This is what the object can do or what can be done to it.

Example: In the Car class, the start() method represents the behavior of a car.

# 2. First Program Explanation :
**Key Takeaways:**
-	**Static**: The main method must be static.
-	**Correct Signature**: The method signature must always be **public static void main(String[] args)** 
    for the JVM to recognize it as the entry point.
-	**Access Modifier**: The method must be public, otherwise, the JVM will not be able to 
    access it.
-	**Method Name**: The method name must be main.
-	**Args Parameter**: While you can choose not to use args, 
it must still be present in the method signature.

~~~
public class HelloWorld 
{
    public static void main(String[] args) {
        
        System.out.println("Hello, World!");
    }
}
~~~

**Explanation of Each Word** in **public static void main(String[] args)**

1. **public**:

-   This is an access modifier that specifies the visibility of the class, method, or field. 
    When used with the main method, it means the method is accessible from anywhere.
-   It makes the class or method accessible to all other classes and packages.
-   If you make the main method private, Java will still compile the code. 
    However, when running the program, the Java runtime will not be able to access 
    the main method, as it's private. 
You will get a runtime error: **No main method found in class HelloWorld.**

2. **static:**

-	This keyword indicates that the method or field belongs to the class, 
rather than object of the class. 
-   The main method is static because it is invoked by the JVM when the program starts, 
 without creating an object of the class.
-	static methods can be called without creating an instance of the class.
-	If you remove the static keyword from the main method, the method will no longer be 
recognized as the entry point by the Java runtime. 
- This will result in the following error at runtime:
No main method found in class HelloWorld

3. **void:**

- This is the return type of the main method. void means that the method does not 
return any value.

4. **main**

- This is the entry point of any Java application. The Java Virtual Machine (JVM) 
  calls this method when you run the program.
- If you change the method name to something other than main, such as main1, 
the Java runtime will not recognize it as the entry point. 
- The main method must always be named main for the JVM to start execution. 
In this case, you'll get a runtime error:
No main method found in class HelloWorld
- If there is no main method, the class cannot be executed from the command line or any Java runtime environment. 
You will get an error message from the Java runtime like this:
Error: Main method not found in class HelloWorld, please define the main method as: 
public static void main(String[] args).

5. **String[] args**

- This is a parameter that represents command-line arguments. args is an array of String 
objects that can hold values passed to the program when it's run. 
The program can access and use these values.
- Example: If you run java HelloWorld arg1 arg2, then args[0] will contain "arg1" and args[1] will 
contain "arg2".
- The main method must take a String[] args parameter because it's the signature expected 
by the JVM. If you remove or change this parameter, it will not match the expected entry point. 
The program will still compile, but when you attempt to run it, you'll get the following error:
No main method found in class HelloWorld.
- If you provide the args parameter but do not use it in the method body, 
the program will still compile and run correctly. 
- The args parameter is optional for the functionality of the program. 
You can ignore it or leave it unused without any issue. 
The program will still output "Hello, World!" as expected.
- Java allows the use of "varargs" (String... args) in place of a regular array (String[] args). 
This will still work perfectly fine, and the program will compile and run successfully, 
printing "Hello, World!". This is simply a syntactic alternative to using an array.

6. **What if, if we Making the class abstract or final**

**Abstract Class**: If you make the main class as abstract class, the main method is still allowed because 
it's a static method and doesn't require instantiation of the class. 
The program will compile and run without any issue.
~~~
public abstract class HelloWorld {
    
    public static void main(String[] args) {
    
        System.out.println("Hello, World!");
    }
}
~~~

7. **What if, if we make it Final Class**:
   If you make the class final, no subclassing is allowed, 
but that doesn't affect the execution of the program. 
The program will compile and run normally.
~~~
public final class HelloWorld {

    public static void main(String[] args) {
    
        System.out.println("Hello, World!");
    
    }
}
~~~

