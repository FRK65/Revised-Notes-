# Exception in JAVA

**Exception Handling in Java** :
The Exception Handling in Java is one of the powerful mechanism to handle the runtime errors 
so that the normal flow of the application can be maintained. 
By handling exceptions appropriately, you can improve the resilience of your applications 
and provide better user experiences

# What is Exception in Java?
In Java, an exception is an event that occurs during the execution of a program that disrupts 
the normal flow of instructions.

These exceptions can occur for various reasons, such as invalid user input, file not found, or division by zero. 
When an exception occurs, it is typically represented by an object of a subclass of the **java.lang.Exception** class.

# What is Exception Handling?
Exception Handling is a mechanism to handle runtime errors such as **ClassNotFoundException, IOException, SQLException, 
RemoteException**, etc

Advantage of Exception Handling
The core advantage of exception handling is to maintain the normal flow of the application. 
An exception normally disrupts the normal flow of the application; that is why we need to handle exceptions.

Let's consider a scenario:
~~~
1.	statement 1;
2.	statement 2;  // Exception occures
3.	statement 3;
~~~
if exception occurs in statement 2 the rest of the code will not be executed, i.e., statements  3 will not be executed. 
However, when we perform exception handling, the rest of the statements will be executed. 
That is why we use exception handling in java.


# Hierarchy of Java Exception classes
The **java.lang.Throwable** class is the root class of Java Exception hierarchy inherited by two subclasses: 
Exception and Error. The hierarchy of Java Exception classes is given below:


# Types of Exceptions :

There are mainly two types of exceptions: checked and unchecked.

An error is considered as the unchecked exception. However, according to Oracle,
there are three types of exceptions namely:

1. Checked Exception
2. Unchecked Exception
3. Error

# 1. Checked Exceptions
Checked exceptions are the exceptions that are checked at compile-time. 
This means that the compiler verifies that the code handles these exceptions either by catching them or declaring them 
in the method signature using the throws keyword.

Examples of checked exceptions include:

- **IOException**: This exception is thrown when an input/output operation fails, such as when reading from or writing 
to a file.

- **SQLException**: It is thrown when an error occurs while accessing a database.
- **ParseException**: Indicates a problem while parsing a string into another data type, such as parsing a date.
- **ClassNotFoundException**: It is thrown when an application tries to load a class through its string name using 
methods like Class.forName(), but the class with the specified name cannot be found in the classpath 

# 2 Unchecked Exceptions (Runtime Exceptions)
Unchecked exceptions, also known as runtime exceptions, this are not checked at compile-time. 
These exceptions usually occur due to programming errors, such as logic errors or incorrect assumptions in the code. 
They do not need to be declared in the method signature using the throws keyword, making it optional to handle them.

Examples of unchecked exceptions include:
- **NullPointerException**: It is thrown when trying to access or call a method on an object reference that is null.
- **ArrayIndexOutOfBoundsException**: It occurs when we try to access an array element with an invalid index.
- **ArithmeticException**: It is thrown when an arithmetic operation fails, such as division by zero.
- **IllegalArgumentException**: It indicates that a method has been passed an illegal or inappropriate argument.

# 3 Errors
Errors represent exceptional conditions that are not expected to be caught under normal circumstances. 
They are typically caused by issues outside the control of the application, such as system failures or resource 
exhaustion. 

Errors are not meant to be caught or handled by application code. Examples of errors include:

- **OutOfMemoryError**: It occurs when the Java Virtual Machine (JVM) cannot allocate enough memory for the application.
- **StackOverflowError** It is thrown when the stack memory is exhausted due to excessive recursion.
- **NoClassDefFoundError**: It indicates that the JVM cannot find the definition of a class that was available at 
compile-time.

# Difference between Checked and Unchecked Exceptions

**Checked Exceptions:**
- **Definition**: Checked exceptions are exceptions that are explicitly checked by the Java compiler. 
  The compiler forces the programmer to either handle these exceptions using a try-catch block or declare them in the 
  method signature using the throws keyword.
- **Superclass**: These exceptions are subclasses of **Exception**, but not of RuntimeException.
- **Handling**: The programmer is required to handle or declare these exceptions. If not handled, 
  the code will not compile.
- **Typical Use Cases**: Checked exceptions are typically used for conditions that a program can recover from, 
  like I/O errors, network failures, or database errors.
Examples:
~~~
•	IOException (e.g., file reading/writing errors)
•	SQLException (e.g., database query failures)
•	ClassNotFoundException (e.g., trying to load a class that doesn't exist)
•	InterruptedException (e.g., thread interruption)
~~~

**Unchecked Exceptions:**
- **Definition**: Unchecked exceptions, also known as runtime exceptions, this are exceptions that do not need to be 
explicitly handled or declared by the programmer. 
These exceptions are a result of programming bugs or logical errors that can generally be avoided by careful coding.
- **Superclass**: These exceptions are subclasses of RuntimeException, which itself is a subclass of Exception.
- **Handling**: The programmer is not required to handle or declare these exceptions. However, 
they may choose to do so if they wish.
- **Typical Use Cases**: Unchecked exceptions usually represent programming errors, such as accessing an array out of 
bounds, dividing by zero, or invoking a method on a null object.
~~~
Examples:
•	NullPointerException (e.g., dereferencing a null reference)
•	ArrayIndexOutOfBoundsException (e.g., accessing an invalid index in an array)
•	ArithmeticException (e.g., dividing by zero)
•	IllegalArgumentException (e.g., passing an invalid argument to a method)
~~~

# 4. Java Exception Keywords
Java provides five keywords that are used to handle the exception. The following table describes each.
Keyword	Description

# 1. try Keywords  
- The "try" keyword is used to specify a block where we should place an exception code. 
- It means we can't use try block alone. 
- The try block must be followed (before) by either catch or finally.

# 2. catch	
- The "catch" block is used to handle the exception. 
- It must be preceded (after) by try block 
- which means we can't use catch block alone. It can be followed (after) by finally block later.

# 3. finally	
- The "finally" block is used to execute the necessary code of the program. 
- It is executed whether an exception is handled or not.

# 4. throw	
- The "throw" keyword is used to throw an exception.

# 5. throws + S	
- The "throws" keyword is used to declare exceptions. 
- It specifies that there may occur an exception in the method. 
- It doesn't throw an exception. It is always used with method signature.


# The try-catch Block

The try block contains the code that may throw an exception, 
and the catch block is used to handle the exception if it occurs. 
Here's a basic example:
~~~
try {  

    // Code that may throw an exception 
     
} catch (ExceptionType e) {  

    // Exception handling code  
    
}
~~~

# Handling Multiple Exceptions
You can handle multiple types of exceptions by providing multiple catch blocks, 
each catching a different type of exception. 
This allows you to tailor your exception handling logic based on the specific type of exception thrown. 
Here's an example:
~~~
try {  

    Code that may throw an exception  
    
} catch (IOException e) {  

   - Handle IOException 
     
} catch (NumberFormatException e) {  
    
   - Handle NumberFormatException  
    
} catch (Exception e) {  
    
    - Handle any other exceptions  
}
~~~

# The finally Block
In addition to try and catch, Java also provides a finally block, which allows you to execute cleanup code, 
such as closing resources, regardless of whether an exception occurs or not. 
The finally block is typically used to release resources that were acquired in the try block. 
Here's an example:
~~~
try {  

    Code that may throw an exception  
    
} catch (Exception e) {  

    - Exception handling code
      
} finally {  

    - Cleanup code
      
}
~~~


# 5. what is custom exception
A custom exception in Java is an exception that you create to represent specific error conditions or 
application-specific problems that aren't covered by Java’s built-in exceptions 
(**such as IOException, NullPointerException**, etc.). 
Custom exceptions allow you to handle application-specific errors in a more meaningful and readable way.

# Why Create a Custom Exception?
Custom exceptions allow you to categorize and clearly identify the type of error. 
This can help other developers (or even you) understand exactly what went wrong when reviewing the exception.

Creating custom exceptions is a great way to handle errors specific to your application’s logic. 
It makes your code more robust, readable, and maintainable by allowing you to clearly define the types of exceptions 
that can occur and how they should be handled.

Benefits of Using Custom Exceptions:

- **Application-Specific Clarity**: Custom exceptions can provide better context for what went wrong in your application 
(e.g., DatabaseConnectionException, UserNotFoundException).

- **Code Readability**: They make your code more readable and expressive because their names provide meaningful 
information about the error condition.
- **Handling Specific Errors**: You can catch specific types of exceptions and handle them differently 
(e.g., logging, re-throwing, or providing user feedback).

Key Points to Remember:
1.	**Checked vs. Unchecked**:

      - **Checked Exception**: If you want your custom exception to be a checked exception, extend Exception class 
        and ensure the calling method either catches or declares it.

      - **Unchecked Exception**: If you want your custom exception to be unchecked (runtime exception), 
        extend RuntimeException class.

2.	**Constructors**:

      - It's a good practice to provide constructors that allow you to pass custom messages and exceptions 
       (i.e., the cause) to the parent exception class.

3.	**Exception Hierarchy**:

      - You can create your custom exception at any level of the exception hierarchy. But typically, it's either under Exception for checked exceptions or RuntimeException for unchecked exceptions.


# How to Create a Custom Exception
To create a custom exception in Java, you generally extend one of Java's built-in exception classes. 
Most commonly, you’ll extend either:

•	**Exception class for checked exceptions** (exceptions that must be caught or declared in the method signature).

•	**RuntimeException class for unchecked exceptions** (exceptions that do not need to be explicitly handled or declared).

Steps to Create a Custom Exception:

1.	**Extend the Exception or RuntimeException class.**
2.	Define **constructors** to initialize the exception message, cause, or both. 
3.  A custom exception usually has **at least one constructor** that accepts a string message or 
 **another exception to pass to the superclass**.


# Example 1: Custom Checked Exception
~~~
public class InvalidAccountException extends Exception {

    // Constructor with no arguments
    public InvalidAccountException() {
        super("Invalid account");
    }

    // Constructor with a custom message
    public InvalidAccountException(String message) {
        super(message);
    }

    // Constructor with a custom message and cause
    public InvalidAccountException(String message, Throwable cause) {
        super(message, cause);
    }

    // Constructor with a cause
    public InvalidAccountException(Throwable cause) {
        super(cause);
    }
}
~~~
~~~
// Custom checked exception
public class BankAccount {

    public void withdraw(double amount) throws InvalidAccountException {
         
	 boolean accountIsInvalid = true;  // This could be a condition that triggers the exception

        if (accountIsInvalid) {
            throw new InvalidAccountException("Account is invalid for withdrawal.");
        }

        // Proceed with withdrawal logic
    }

    public static void main(String[] args) {
        BankAccount account = new BankAccount();

        try {
            account.withdraw(100.00);
        } catch (InvalidAccountException e) {
            System.out.println("Error: " + e.getMessage());
        }
    }
}
~~~



# Example 2: Custom Unchecked Exception
Unchecked exceptions do not require the caller to handle them (they are not checked by the compiler).
~~~
// Custom unchecked exception
public class InsufficientFundsException extends RuntimeException {

    // Constructor with no arguments
    public InsufficientFundsException() {
        super("Insufficient funds in the account.");
    }

    // Constructor with custom message
    public InsufficientFundsException(String message) {
        super(message);
    }

    // Constructor with custom message and cause
    public InsufficientFundsException(String message, Throwable cause) {
        super(message, cause);
    }

    // Constructor with cause
    public InsufficientFundsException(Throwable cause) {
        super(cause);
    }
}
~~~
~~~

public class BankAccount {
private double balance = 100.00;
public void withdraw(double amount) {
if (amount > balance) {
throw new InsufficientFundsException("Attempted withdrawal exceeds balance.");
}
balance -= amount;
}
public static void main(String[] args) {
BankAccount account = new BankAccount();

        try {
            account.withdraw(150.00);  // This will throw InsufficientFundsException
        } catch (InsufficientFundsException e) {
            System.out.println("Error: " + e.getMessage());
        }
    }
}
~~~

# 1. What is an exception in Java?
An exception in Java is an event that disrupts the normal flow of the program's execution. 
It Represents conditions that a program can catch and handle. Exceptions can be recoverable, and they are used to 
handle application-specific or unexpected events.

**Example: IOException, SQLException**

# 2. What is an Error in Java?
Error: Represents serious problems that a reasonable application should not try to handle, such as system-level 
issues like memory exhaustion or JVM crashes. These errors are typically not recoverable.

**Example: OutOfMemoryError, StackOverflowError**


# 3. What is the difference between checked and unchecked exceptions?

**Checked Exceptions** that the programmer must either handle or declare. 
These exceptions are checked at compile-time.

- **Examples: IOException, SQLException, ClassNotFoundException.**

- **Requirement**: The compiler forces you to handle these exceptions, either by catching them (try-catch) or by 
declaring them (throws).

**Unchecked Exceptions** that do not need to be explicitly handled or declared. 
They extend RuntimeException and occur due to programming errors.

- **Examples: NullPointerException, ArithmeticException, ArrayIndexOutOfBoundsException.**
- **Requirement**: The compiler does not force you to handle them.

# 4. What is the role of the throws+S keyword?
The throws keyword is used in the method signature to indicate that a method might throw one or more exceptions. 
It is a way of declaring exceptions that the method can throw but does not handle. 
It lets the caller of the method know that it should be prepared to handle the exception.
~~~
public void readFile(String fileName) throws IOException {
    // Code that might throw IOException
}
~~~


# 5. What is the role of the throw keyword?
The throw keyword is used to explicitly throw an exception from within a method or block of code. 
This is typically used to indicate an error condition or to raise a custom exception.
~~~
public void checkAge(int age) {
    if (age < 18) {
        throw new IllegalArgumentException("Age must be 18 or older.");
    }
}
~~~

# 6. What is the difference between try-catch and try-finally?

- **try-catch**: Used for handling exceptions.
  When an exception occurs in the try block, the control is transferred to the corresponding catch block. 
  If no exception occurs, the catch block is skipped.
- **try-finally**: The finally block is always executed, whether or not an exception occurs. 
  It's typically used for cleanup operations like closing files, network connections, or database connections.

~~~
try {
        // Code that may throw an exception
} catch (IOException e) {
        // Exception handling code
} finally {
        // Cleanup code, always executed
}
~~~

# 7. What is a custom exception?
A custom exception is a user-defined exception created by 
extending the **built-in Exception** (for checked exceptions) or **RuntimeException** (for unchecked exceptions). 

Custom exceptions are used when you need to represent specific error conditions in your application.
~~~
public class InsufficientFundsException extends Exception {
    
    public InsufficientFundsException(String message) {
            
            super(message);
    }
}
~~~

# 8. What is the difference between final, finally, and finalize?

# 8.1 final keyword: 
A keyword used to declare constants, prevent method overriding, or prevent inheritance.

# 8.2 finally: 
A block used in exception handling to ensure that a block of code is executed regardless of whether an 
exception occurs. It is typically used for cleanup operations.

- you can use a try block without a catch block, followed by a finally block, like below
- But you cannot have a finally or catch block without a try block in Java. 
- Both catch and finally blocks must be associated with a try block

~~~
    try {
            // code
    } finally {
            // cleanup code
    }
~~~

# 8.3 finalize: 
A method defined in the Object class that is called by the garbage collector before an object is destroyed. 
It's used for resource cleanup before the object is removed from memory.
~~~
protected void finalize() throws Throwable {
    
    // Cleanup code before object is garbage collected
}
~~~


# 9. What is the difference between throw and throws in Java?

# throw keyword: 
- It Used to explicitly throw an exception from a method or a block of code. 
- It can be used to throw both predefined and custom exceptions.
- Example: throw new IllegalArgumentException("Invalid argument");

# throws: 
- It Used in the method signature to declare that a method might throw certain exceptions. 
- It does not throw an exception but indicates to the caller that the method could throw exceptions, 
 which should be handled.
- Example: public void readFile() throws IOException { }

# 10. Can we catch a Throwable?
Yes, you can catch a Throwable, which is the superclass of both Error and Exception. 
However, it is not recommended to catch Throwable unless you are writing a very generic or low-level framework. 
Catching Throwable also includes catching Error types, which typically represent serious problems 
(like OutOfMemoryError), and these should not generally be caught.
~~~
    try {
        
        // Code
    } catch (Throwable t) {
    
        // Catch all exceptions and errors
    }
~~~

# 11. Can we throw multiple exceptions in a method?

Yes, you can throw multiple exceptions from a method, 
but they must be declared using the throws clause, and each exception must be separated by a comma.
~~~
    public void method() throws IOException, SQLException 
    {
        // code
    }
~~~

# 12. What is the purpose of the ExceptionInInitializerError in Java?

**ExceptionInInitializerError** is thrown when an exception occurs during the static initialization of a class. 
This could happen when static blocks or static variable initializers throw exceptions.
~~~
    class MyClass {  
       static {
          if (true) {
            throw new RuntimeException("Static initialization failed");
          }
       }
    }
~~~

# 13. What is the NoClassDefFoundError?

**NoClassDefFoundError** is thrown when the JVM attempts to load a class and cannot find it. 
This often occurs when a class was available at compile-time but is missing at runtime. 
This can happen due to issues with the classpath or incorrect dependencies.

# 14. What happens if you don’t catch an exception?

If you don't catch an exception, it will propagate up the call stack. 
If it is not handled at any level, the JVM will terminate the program and print the exception's stack trace 
to the console. 
For checked exceptions, if not caught or declared, the program will not compile.

# 15. What is stack unwinding in exception handling?
Stack unwinding refers to the process where the Java runtime system unwinds the call stack when an 
exception is thrown. 
The method where the exception occurred will exit, and the runtime will look for an appropriate catch block 
in the calling methods. 
This continues until the exception is caught or the program terminates.
