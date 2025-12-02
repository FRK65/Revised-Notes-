# 1. Data Members, Methods, and Types of Data Types in Java

1. **Data Members:** Data members are variables defined inside a class but outside any 
method or constructor. They hold the state of the object.

2. **Methods** : A method is a function that defines the behaviour of an object. 
It performs operations on data members or performs any specific task.

3. **Types of Data Types** 

**Primitive Data Types**: These are basic types like int, char, boolean, float, double, long, 
byte, and short

Example: int age = 25;

**Reference Data Types**: These refer to objects or arrays. They hold references (or addresses) 
to objects in memory.

Example: String name = "John";


# 2. What are Wrapper classes?

1. **Wrapper classes** in Java are object-oriented representations of the primitive data types. 
Each primitive type (like int, char, double, etc.) has a corresponding wrapper class:
~~~
int → Integer
char → Character
~~~

These wrapper classes provide methods to conversion between primitive values and objects, 
and they allow primitive types to be used in contexts where objects are required 
(e.g., in collections like ArrayList).

2. **Why do we need Wrapper classes in Java?**

- Working with Collections:
- Autoboxing and Unboxing
- Utility Methods : **Integer.parseInt(), Double.valueOf(), Character.isDigit()**
- Nullability: **Primitive types can't be null, but wrapper classes can**
Interoperability with Reflection and APIs:

3. **What are the different ways of creating Wrapper class instances?**

**Using Constructor** :
~~~
Integer intObj = new Integer(10); 
 
char Obj = new Character('A'); 
~~~
**Using ValueOf() Method**:
~~~
Integer intObj = Integer.valueOf(10); 
// Preferred 
Double doubleObj = Double.valueOf(3.14);
~~~
**Autoboxing (Automatic Conversion)**:
~~~
int primitive = 10;
Integer intObj = primitive; // Autoboxing: automatically converts int to Integer
~~~
**Using Constructor for String Conversion**:
~~~
Integer intObj = new Integer("10");
Using parse Methods (For Parsing Strings)
int primitiveInt = Integer.parseInt("100");
~~~



3. **What is Type casting**

In Java, type casting refers to the conversion of one data type to another. 
Java supports two types of type casting:

-	**Implicit Type Casting** (Automatic Type Conversion)
-	**Explicit Type Casting** (Manual Type Conversion)

**Implicit Type Casting (Widening Casting)** : 
Implicit type casting occurs automatically when you are converting a smaller data type to a 
larger data type. 
The Java compiler performs this conversion automatically without any loss of data.

Implicit Casting Rules: **byte → short → int → long → float → double**

The conversion is done automatically when converting from a smaller type to a larger type.
~~~
int num = 100;       // int type
double d = num;      // Implicit casting: int to double
~~~

**Explicit Type Casting (Narrowing Casting)**: Explicit type casting occurs when you want to 
convert a larger data type to a smaller data type. 
Java does not perform this conversion automatically because it may lead to loss of 
data or precision. You must explicitly tell the compiler to cast the value.

Explicit Casting Rules: **double → float → long → int → short → byte**

You must explicitly cast when converting from a larger type to a smaller type, 
as it can result in a loss of data or precision.
~~~
double num = 100.99;   // double type
int i = (int) num;     // Explicit casting: double to int
System.out.println(i);  // Output: 100 (fractional part is lost)
~~~


