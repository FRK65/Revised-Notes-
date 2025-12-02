# JVM JRE and JDK

# 1. What is JDK 

JDK stands for Java Development Kit. It is a software development kit (SDK) used 
to develop Java applications. 
The JDK provides everything you need to create Java Application or program, including:

- **Java Compiler (javac)**
- **Java Runtime Environment (JRE)**
- **Java Standard Library**
- **Development Tools**
- **Java APIs**

**JDK, It physically exists and It contains JRE + development tools.**

**JDK (Java Development Kit)**: Used for developing Java programs.

**JRE (Java Runtime Environment):** Used for running Java programs (it doesn't include the development tools).

JDK is an implementation of any one of the below given Java Platforms released by Oracle Corporation:
- Standard Edition Java Platform
- Enterprise Edition Java Platform
- Micro Edition Java Platform


Java is continuously updated, and each version of the JDK typically corresponds to a new release 
of the Java programming language.

For example, JDK 8, JDK 11, and JDK 17 are some of the major versions released in recent years.

In summary, **the JDK is essential for developers who are creating Java applications, 
as it includes the tools needed to compile, debug, and run Java code.**


# Relationship and Usage

•	**Development**: Use the **JDK** to write, compile, and debug Java code.

•	**Deployment**: Use the **JRE** to run Java applications on end-user machines.

•	**Execution**: The **JVM**, part of both JRE and JDK, actually runs the Java program.



# In simple terms:

•	**JDK = JRE + development tools (compiler, debugger, etc.)**

•	**JRE = JVM + libraries for running Java applications**

•	**JVM = The engine that runs Java bytecode.**


# 2. What is JRE

JRE stands for Java Runtime Environment. It is a software package that provides the necessary 
libraries, Java Virtual Machine (JVM), and other components to run Java applications. 
The JRE allows you to execute Java programs, but it does not provide development tools like 
compilers (those are provided by the JDK or Java Development Kit).

It is the implementation of JVM. It physically exists. 

It contains a set of libraries + other files that JVM uses at runtime.

The implementation of JVM is also actively released by other companies besides Sun Micro Systems.

**JRE components = JVM + Set of Libraries + Other Files**

**JRE components :**
1.	**Java Virtual Machine (JVM)**
2.	**Set of Libraries**
3.	**Other Files**

If you want to run Java applications, you only need the JRE. 

If you want to develop Java applications, you need the JDK, which includes the JRE along 
with the tools to create Java programs.

# 3. What is JVM

The Java Virtual Machine (JVM) is a core component of the Java Runtime Environment (JRE) that 
makes Java applications to be platform-independent.

It provides an abstract layer between the compiled Java bytecode and the underlying hardware 
and operating system, which allows Java programs to run on any device or operating system that 
has a JVM implementation. This is one of the key reasons why Java follows the "Write Once, 
Run Anywhere" principle.

JVM (Java Virtual Machine) is an abstract machine. 
It is called a virtual machine because it doesn't physically exist.

JVM provides a runtime environment in which Java bytecode can be executed. 
It can also run those programs which are written in other languages and compiled to Java bytecode.
JVMs are available for many hardware and software platforms. 
JVM, JRE, and JDK all are platform dependent because the configuration of each OS is 
different from each other. However, Java is platform independent.

**JVM is platform dependent**

# 4. Notions of JVM 

There are three notions of the JVM:

**specification, implementation, and instance.**

1.	A **specification**, where working of Java Virtual Machine is specified. 
    But implementation provider is independent to choose the algorithm. 
    Its implementation has been provided by Oracle and other companies.

2.	An **implementation** Its implementation is known as JRE (Java Runtime Environment).

3.	Runtime **Instance** Whenever you write java command on the command prompt to run the java class, 
    an instance of JVM is created.

# 5. What JVM does or Key Responsibilities of the JVM:

The JVM performs following operation:
- **Loads code**
- **Verifies code**
- **Executes code**
- **Provides runtime environment**
- **Memory management.**

# 6. Components of JVM :
-	**Class Loader** (Bootstrap, Extension and Application class loader)
-	**Runtime Data Areas** (Method Area, Heap, Stack, Program Counter (PC) Register, Native Method Stack)
-	**Execution Engin** (Interpreter, JIT Compiler (Just-In-Time))
-	**Garbage Collector** (GC)

# 7. How JVM Works (High-Level Overview)

1.	**Java Source Code**:
      - You write Java code in a .java file.
2.	**Compilation:**
      - The Java compiler (javac) compiles the .java source code into bytecode (.class files).
      - Bytecode is platform-independent and can run on any JVM.
3.	**Class Loading:**
      - When you run a Java program, the JVM uses a class loader to load the compiled bytecode into memory.
4.	**Execution**:
      - The execution engine of the JVM reads the bytecode and either interprets or compiles 
        it into machine code for execution.
      - The JVM handles memory management, garbage collection, and other runtime tasks.
5.	**Output**:
      - The JVM executes the program and produces the output on the console or any other 
        specified output destination.

**Here are some interview questions on JDK, JRE, and JVM in Java, 
which cover the core differences and functionalities of these components:**

# 8. What is the difference between JDK, JRE, and JVM?

**JDK (Java Development Kit):** 
It is a software development kit used for developing Java applications. 
It includes the JRE (Java Runtime Environment) and additional tools like compilers (javac), 
debuggers, and libraries for Java development.

**JRE (Java Runtime Environment):** 
It provides the necessary runtime environment to run Java applications. 
It includes the JVM (Java Virtual Machine) and standard Java libraries, but it does not 
contain development tools like compilers.

**JVM (Java Virtual Machine):** It is a part of the JRE that executes Java bytecode. 
It abstracts the underlying hardware and operating system, enabling Java applications to be 
platform-independent.

# 9. What is JDK used for?

The JDK (Java Development Kit) is used for developing Java applications. 
It contains everything needed to write, compile, debug, and run Java programs, 
including:
-	**Java compiler (javac)** for compiling .java files into bytecode (.class files).
-	**Java Runtime Environment (JRE)** for running Java programs.
-	Additional tools like **debuggers, documentation generators, JVMs, and package managers**.

# 10. What is JRE used for?

The JRE (Java Runtime Environment) provides the runtime environment to run Java programs. 
It includes:
-	**The Java Virtual Machine (JVM)** to execute Java bytecode.
-	**Core libraries** (standard class libraries, such as java.util, java.io, etc.).
-	Support files to allow Java applications to run, but it does not include 
    development tools like compilers.


# 11. Can we run Java programs without JDK?

Yes, you can run Java programs without JDK, but you will need at least JRE 
installed on the machine. 
The JRE provides the necessary JVM and libraries to execute Java bytecode, 
but it does not provide development tools (like the Java compiler javac).

Therefore, you need JDK if you want to develop or compile Java programs, 
but only JRE is required to run them.

# 12. What is the role of the JVM in the Java ecosystem?

The JVM (Java Virtual Machine) is responsible for executing Java bytecode. 
It is the key component that provides Java's platform independence. 
The JVM performs the following tasks:

-	**Loads compiled Java classes.**
-	**Verifies the bytecode to ensure its valid**.
-	**Executes the bytecode on the host machine**.
-	**Manages memory via garbage collection.**
-	**Provides an execution environment** that abstracts away the underlying hardware 
    and operating system.

# 13. What happens when you run a Java program (java MyClass)?

1.	**Loading**: The Java command (java MyClass) starts by calling the JVM, 
    which loads the class MyClass from the classpath.
2.	**Class Verification**: The JVM verifies the class file (bytecode) to ensure 
    there are no security issues or invalid code.
3.	**Execution**: The JVM executes the bytecode of MyClass using its execution engine.
4.	**Memory Management**: The JVM manages memory allocation and garbage collection during 
    the execution of the program.


# 14. What is the main difference between JDK and JRE?

JDK is a development kit for building Java applications. 
It contains everything in JRE plus development tools like the Java compiler (javac), 
debuggers, and other tools.

JRE is a runtime environment that provides everything required to run Java programs, 
including the JVM and standard libraries, 
but does not contain development tools like compilers.

# 15. What are the components of the JDK?

The JDK consists of several components:
-	**JRE (Java Runtime Environment)** - For running Java applications.
-	**Java Compiler (javac)** - Compiles Java source code into bytecode.
-	**Java Debugger (jdb)** - For debugging Java programs.
-	**Javadoc** - A tool for generating API documentation from Java source code.
-	**JVM** - The Java Virtual Machine that executes the bytecode.
-	**Tools** like jar, javap, jconsole, javap, and others for various development tasks.

# 16. What is the difference between JVM and JRE?

**JVM (Java Virtual Machine)** is the engine that runs Java bytecode. 
It is part of the JRE and provides the mechanism to execute Java applications.

**JRE (Java Runtime Environment)** includes the JVM and the set of libraries required to 
run Java applications, but it does not include development tools like the Java compiler.

# 17. Why do we need a JVM if the program is already compiled into bytecode?

Java bytecode is platform-independent, meaning it can run on any platform that has a JVM. 
The JVM is needed to:

- Interpret or compile the bytecode into machine-specific code (native instructions).
- Provide memory management through the heap and garbage collection.
- Offer security features such as bytecode verification.
- Abstract the underlying system, allowing Java to run on any platform (Windows, Linux, macOS) 
without modification.

# 18. What is the difference between bytecode and machine code?
 
**Bytecode** is an intermediate representation of a Java program. 
It is generated after compiling Java source code (.java) using the Java compiler (javac). 
It is platform-independent and executed by the JVM.

**Machine code** is the low-level code that is executed by a computer's CPU. 
It is platform-specific and is generated by compiling the bytecode 
(via JIT or native compilers).

# 19. What are the advantages of using JVM?
 
- **Platform independence**: JVM allows Java programs to be written once and run anywhere, 
making Java applications cross-platform.
- **Memory management:** JVM automatically handles memory allocation and garbage collection.
- **Security:** The JVM verifies bytecode before execution to prevent security threats like 
 buffer overflows or code injection.
- **Performance:** With the use of JIT compilation, the JVM can optimize the execution of Java 
 programs at runtime.
- **Multithreading support:** JVM natively supports multi-threading for concurrent execution.

# 20. What is the role of the Java Class Loader in JVM?

The Java Class Loader is responsible for loading Java classes into the JVM during runtime. 
It loads .class files (bytecode) and dynamically loads classes as needed. 
There are three main types of class loaders in Java:

1. **Bootstrap Class Loader**: Loads core Java classes from the JDK.
2. **Extension Class Loader**: Loads classes from the JDK's extension directory.
3. **System/Application Class Loader**: Loads classes from the classpath (e.g., your project classes).

# 21.  Can we run a Java program without JVM?
No, we cannot run a Java program without the JVM. 
The JVM is essential for executing Java bytecode. 
When you compile Java source code, it generates bytecode, but the bytecode needs 
the JVM to be executed on any platform.

# 22. What happens when you execute the command java MyClass?

1.	The Java launcher starts the JVM and loads the class MyClass.
2.	The class loader loads the compiled bytecode of MyClass.
3.	The JVM verifies the bytecode to ensure it is valid and complies with Java security.
4.	The JVM executes the bytecode of the main() method in MyClass using the execution engine.
5.	During the program execution, the JVM manages memory and performs garbage collection.
6.	The program output is generated (printed to the console or logged).

# 23. Explain the term "Java Write Once, Run Anywhere".

The phrase "Write Once, Run Anywhere" refers to Java’s cross-platform capability. 
Java programs are compiled into bytecode, which can be executed on any platform that has a JVM. 
This allows Java applications to run on multiple operating systems without modification, 
as long as the correct JVM implementation is available for the platform.

# 24. What happens if the JDK is not installed on a machine?

If the JDK is not installed, you cannot compile Java programs because the JDK includes 
the Java compiler (javac). 
However, if you only need to run Java programs, the JRE is sufficient as it contains 
the JVM and required libraries.
 
