# 1. String in JAVA

String represents a sequence of characters and is widely used for working with text. 
Strings in Java are immutable, meaning once a String object is created, 
its value cannot be changed.

String is basically an object that represents sequence of char values. 
An array  of characters works same as Java string.
~~~
char[] ch={'F','r','a','n','k'};  
String s=new String(ch);
String s="Frank";
~~~

Java String class provides a lot of methods to perform operations on strings such 
as 
**compare(), concat(), equals(), split(), length(), replace(), compareTo(), intern(), substring() etc.**

The **java.lang.String class** implements Serializable, Comparable and CharSequence interfaces.
~~~
public final class String
implements java.io.Serializable, Comparable<String>, CharSequence {}
~~~

**1.1 Serializable:**
A marker interface that allows an object to be serialized (converted into a byte stream) and deserialized (reconstructed). It doesn’t have any methods; its presence signals that objects of a class can be saved and restored.

**1.2 Comparable:**
An interface that defines a natural order for objects of a class. It has the method
compareTo(To) which is used for comparing objects, typically for sorting them 
(e.g., sorting a list of objects).

**1.3 CharSequence:**
An interface for representing a sequence of characters (e.g., String, StringBuilder). 
It provides methods like **charAt(), length(), and subSequence()** to interact with characters 
in a sequence.

The CharSequence interface is used to represent the sequence of characters. 
String, StringBuffer and StringBuilder classes implement it. It means, we can create strings 
in Java by using these three classes.

# 2. Creation of String

The Java String is immutable which means it cannot be changed. 
Whenever we change any string, a new instance is created.

**For mutable strings, you can use StringBuffer and StringBuilder classes.**

**3. What is String in Java?**

Generally, String is a sequence of characters. But in Java, string is an object that represents 
a sequence of characters. The java.lang.String class is used to create a string object.

**4. How to create a string object?**

There are two ways to create String object:
1.	**By string literal**
2.	**By new keyword**
~~~
      String s1 = "Hello";  // String literal
      String s2 = new String("Hello");  // Using the new keyword
~~~

**String Literal** : Java String literal is created by using double quotes. 
Each time you create a string literal, the JVM checks in the "string constant pool" first.
If the string already exists in the pool, a reference to the pooled instance is returned. 
If the string doesn't exist in the pool, a new string instance is created and placed in the pool.

For example:
~~~
String s1="Welcome";  
String s2="Welcome";//It doesn't create a new instance
~~~

In the above example, only one object will be created. Firstly, JVM will not find any 
string object with the value "Welcome" in string constant pool that is why it will 
create a new object s1. 

After that it will find the string with the value "Welcome" in the pool, 
it will not create a new object but will return the reference to the same instance.

**Note: String objects are stored in a special memory area known as the "string constant pool" 
which in inside the Heap".**



**5. Why Java uses the concept of String literal?**

To make Java more memory efficient (because no new objects are created if it exists already 
in the string constant pool).

The String Constant Pool is a memory optimization technique where Java stores unique string 
literals. This reduces memory usage by ensuring that identical string literals 
are stored only once. 
It automatically applies to string literals, and you can explicitly use intern() to 
add strings to the pool.
~~~
String which are created via double quotes are String literal.
String s1 = "Hello";  // String literal
~~~

**By new keyword**
~~~
String s=new String("Welcome");
//creates two objects and one reference variable
~~~

**Differences:**

 1. String literals are automatically stored in the String Pool and are reused.

 2. new String() creates a new object on the heap, even if the string already exists in 
    the pool, which can lead to unnecessary memory overhead.

|Aspect |                   	String Literal (String s1 = "Hello";)                   |	Using new String() (String s2 = new String("Hello");) |
| :---         |:---------------------------------------------:|          ---: |
|Memory Location |   Stored in the String Constant Pool    | A new object is created on the heap |
|Memory Efficiency	|       Efficient, reuses the same reference for identical string literals.        | 	Less efficient, creates a new object even if the string is in the pool. |
| Equality Check (== operator) | 	Points to the same object if the string literal is the same. | Points to a new object in the heap, even if the content is the same. |
| Usage | Preferred when you are using string literals frequently | Less common, only needed when explicitly creating a new object |


# 6. Immutability & String Pool terms

**Immutability**: 
Once instantiated, a String object cannot be modified. 
This immutable design is a deliberate choice to ensure thread safety, consistency, 
and efficiency, especially regarding the String pool mechanism.

**String Pool**: Java maintains a pool of string literals to help save memory. 
When a new string literal is created, Java checks the Pool for a matching string. 
If found, the new variable references the pooled string. 
If not, the new string is added to the Pool.


# 7. CharSequence Interface

The CharSequence interface in Java is part of the java.lang package and is implemented by 
classes that represent sequences of characters.

CharSequence is a read-only interface for working with sequences of characters.

It provides a common set of methods for working with character sequences in Java. 
This includes both mutable and immutable types of character sequences 
like String, StringBuilder, and StringBuffer.

It provides essential methods for character access (charAt()), length (length()), 
and sub-sequencing (subSequence()).

Common **classes implementing CharSequence are String, StringBuilder, and StringBuffer.**

It allows flexibility and performance optimization in handling character data in 
both mutable and immutable forms

1.	String
2.	StringBuffer
3.	StringBuilder
