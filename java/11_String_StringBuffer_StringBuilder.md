# CharSequence Interface

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


Classes Implementing CharSequence:

**String**: Immutable sequence of characters.

**StringBuilder**: Mutable sequence of characters (for efficient string manipulation).

**StringBuffer**: Mutable sequence of characters 
(similar to StringBuilder, but synchronized for thread safety).

# 1. What is String, StringBuilder, and StringBuffer

In Java, String, StringBuilder, and StringBuffer are all classes used to 
represent sequences of characters, but they differ in terms of mutability, performance, 
and thread-safety.

# 5.1 String 
**(Not efficient for frequent modifications)**

- **Immutability**: A String is immutable, meaning once a String object is created, 
  its value cannot be changed.
- **Memory Usage**: Since String objects are immutable, any modification to a 
  String creates a new String object, which can lead to higher memory consumption 
  when performing many string operations.

- **Thread Safety**: Being immutable, String objects are inherently thread-safe.
- **Performance**: String is not suitable for frequent modifications (e.g., in loops) 
  because modifying a String involves creating new String objects every time. 
  This results in less efficient memory usage and performance.

- **When to Use** : Use when you have a constant string value or when you don't need to 
  modify the string after its creation. Since strings are immutable, 
  this is the preferred choice for data that doesn't change (like constants).
- **Using String** (Inefficient for frequent modifications):
~~~
   String s = "Hello";
   s = s + " World";  
   // A new String is created every time this operation is performed
~~~

# 5.2 StringBuilder 
**(Efficient for single-threaded frequent modifications))**

- **Mutability**: StringBuilder is mutable, meaning its value can be changed without 
  creating new objects.

- **Memory Usage**: It is more efficient than String when you need to modify the 
  contents of a string, as it doesn’t create new objects with each modification.  
  It modifies the string in place.

- **Thread Safety**: StringBuilder is not thread-safe, meaning it is not synchronized. 
  Multiple threads modifying a StringBuilder object concurrently can lead to 
  inconsistent results.

- **Performance**: StringBuilder is typically faster than String when performing many string 
  manipulations (like concatenation) in a single thread, because it avoids the overhead of 
  creating multiple string objects.

- **When to use** : StringBuilder Use when you need to modify strings frequently in 
  a single-threaded environment. 
  It's more efficient than String when performing repeated concatenations or modifications.
~~~
   StringBuilder sb = new StringBuilder("Hello");
   sb.append(" World");  // Modifies the existing StringBuilder object
   System.out.println(sb.toString());  // Output: "Hello World"
~~~

# 5.3 StringBuffer 
**(Thread-safe, but slower)**
   
- **Mutability**: Like StringBuilder, StringBuffer is mutable, meaning its value can be modified.
- **Memory Usage**: StringBuffer is also efficient in terms of memory usage because 
  it doesn't create new objects with each modification.
- **Thread Safety**: StringBuffer is thread-safe, meaning its methods are synchronized. 
  This ensures that multiple threads can safely modify a StringBuffer object concurrently, 
  but this comes with a performance cost due to the synchronization overhead.
- **Performance**: StringBuffer is slower than StringBuilder because of its synchronization, 
  making it less suitable for single-threaded applications where thread safety is not a concern.
- **When to use** : StringBuffer Use when you need to modify strings in a multi-threaded 
  environment and require thread safety. However, due to synchronization, 
  it tends to be slower than StringBuilder in a single-threaded scenario.

~~~   
   StringBuffer sbf = new StringBuffer("Hello");
   sbf.append(" World");
   System.out.println(sbf.toString());  // Output: "Hello World"
~~~


| Feature   | String   | StringBuilder   | StringBuffer   |
|------------|------------|------------|------------|
| Mutability | Immutable (cannot be changed) | Mutable (can be modified) | Mutable (can be modified) |
| Thread-Safety | Thread-safe (due to immutability)| Not thread-safe | Thread-safe (synchronized methods) |
| Performance | Not efficient for frequent modifications | Fast for frequent modifications (single-threaded) | Slower due to synchronization overhead |
| Usage | Ideal for constant, unchanging strings | Ideal for single-threaded scenarios with frequent string modifications | Ideal for multi-threaded scenarios where thread safety is needed |
| Memory Consumption | Higher, as new objects are created with each modification | More efficient, modifies the same object | More efficient, modifies the same object |


# 6. String Equality and Identity


**equals()** : Compares the content of two strings.

**==** : Compares the reference or memory address of two string

~~~
String s1 = "Java";
String s2 = "Java";
String s3 = new String("Java");

System.out.println(s1 == s2);  
// true, because both refer to the same object in the string pool

System.out.println(s1 == s3);  
// false, because s3 refers to a new object on the heap

System.out.println(s1.equals(s3));  
// true, because both have the same content
~~~

**String.join()** : Introduced in Java 8, String.join() joins multiple strings with a delimiter.
~~~
String joined = String.join("-", "2024", "12", "20");
// Output: 2024-12-20
~~~

**String Conversion with valueOf()**: 
String.valueOf() can be used to convert other data types (like int, char, boolean, etc.) 
into strings.

~~~
int num = 100;
String str = String.valueOf(num);  // Converts integer to String
~~~


# 7. Common String Methods

Java provides a wide range of methods in the String class to perform various operations 
on strings. 
Some of the most common methods include:

**a) Length of String**

~~~
String s = "Hello";
int len = s.length();  // Returns the number of characters in the string (5)
~~~

**b) Accessing Characters**
~~~
char c = s.charAt(1);  
// Returns the character at index 1, which is 'e'
~~~

**c) Substring**
~~~
String sub = s.substring(1, 4);  
// Returns "ell" (from index 1 to 3)
~~~

**d) String Concatenation**
~~~
String s1 = "Hello";
String s2 = "World";
String result = s1.concat(" " + s2);  
// Concatenates strings
~~~

**e) Replacing Characters**
~~~
String s = "Hello World";
String newStr = s.replace('o', 'a');  
// Replaces 'o' with 'a', result: "Hella Warld"
~~~

**f) Case Conversion**
~~~
String s = "Hello World";
String upper = s.toUpperCase();  // Converts to "HELLO WORLD"
String lower = s.toLowerCase();  // Converts to "hello world"
~~~

**g) Trimming Whitespace**

~~~
String s = "  Hello  ";
String trimmed = s.trim();  
// Removes leading and trailing spaces, result: "Hello"
~~~

**h) String Comparison**
~~~
String s1 = "Hello";
String s2 = "Hello";
String s3 = "World";

boolean equals = s1.equals(s2);  
// true, checks if the content is equal

boolean equalsIgnoreCase = s1.equalsIgnoreCase(s2);  
// true, case insensitive comparison

boolean compare = s1.compareTo(s3);  
// Negative value, as "Hello" is lexicographically less than "World"
~~~


**i) Checking if String Contains a Substring**
~~~
boolean contains = s1.contains("ell");  // true
~~~

**j) Splitting a String**
~~~
String s = "apple,banana,orange";
String[] fruits = s.split(",");  
// Splits the string into an array of strings based on comma
~~~

**k) String to Integer Conversion**
~~~
String s = "123";
int num = Integer.parseInt(s);  
// Converts string "123" to integer 123
~~~

