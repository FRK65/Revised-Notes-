# Serialization and Deserialization in Java

# 1. Serialization in Java

Serialization in Java is the process of converting an object's state into a byte stream 
so that it can be easily stored (in a file, database) or transmitted over a network. 
Once the object has been serialized, it can later be deserialized, means converted back from 
the byte stream to an identical copy of the original object.

**why important**

Serialization is an essential concept in Java for object persistence and communication. 
It provides a way to save and transfer objects, but also requires careful handling 
(such as version control and managing security risks) to ensure reliability and safety.

**property** 

The serialization and deserialization process is platform-independent, it means you can serialize 
an object on one platform (windows) and deserialize it on a different platform (MacOs).

For serializing the object, we call the **writeObject()** method of **ObjectOutputStream class**, and 
for deserialization we call the **readObject()** method of **ObjectInputStream class**.

**If we want to serialize an Object**, We must have to implement the **Serializable interface** 
for serializing the object.

**Purpose:** Serialization is primarily used for saving an object's state or for sending an object over a 
network (such as in **RMI, REST APIs**, etc.).

# 2. Serialization (java.io.Serializable) Interface: 
In Java, a class must implement the Serializable interface to indicate that its instances can be serialized. 
**This is a marker interface**,marker interface means it doesn't have any data member and methods, 
but its presence signals to the JVM that the class is eligible for serialization.

The Cloneable and Remote are also marker interfaces.

The Serializable interface must be implemented by the class whose object needs to be transmitted.

# 3. Deserialization
Deserialization is the process of reconstructing the object from the serialized state. 
It is the reverse operation of serialization. The object is restored from a serialized state using 
the **ObjectInputStream class**.

# 4. Advantages & Disadvantagesof Serialization:
**Advantages**

-	**Persistence**: You can save the state of objects to disk and retrieve them later.
  -	**Communication**: Serialized objects can be transmitted over a network or used in distributed applications 
  (e.g., Java RMI).
-	**Simplified Object Handling**: Serialization automates the process of turning objects into a transferable format.

**Disadvantages:**
- **Performance**: Serialization and deserialization can be resource-intensive and may impact performance, 
    especially for large objects.
- **Security**: Deserializing data from untrusted sources can be risky, as it may lead to malicious code execution.

~~~
import java.io.Serializable;  
public class Student implements Serializable{  
int id;  
String name;  
public Student(int id, String name) {  
this.id = id;  
this.name = name;  
}  
}  
// In the above example, Student class implements Serializable interface. Now its objects can be converted into stream
~~~

# 5. How Serialization Works: (OI)

**The ObjectOutputStream class** is used to write the object to a stream (i.e., serialize it).

**The ObjectInputStream** class is used to read the object from the stream (i.e., deserialize it).

The writeObject() method of ObjectOutputStream class provides the functionality to serialize the object. 
We can save the state of the object in the file. and 

The readObject() method of the ObjectInputStream class is used to deserialize an object from an input stream. 
It reads the byte stream and reconstructs the object. 

# 6. Example 

**Example of serialization:**
~~~
import java.io.*;

    public class SerializeExample {
        public static void main(String[] args) {
            try {
                // Create an object
                Person person = new Person("John Doe", 30);

                // Create a FileOutputStream and ObjectOutputStream
                FileOutputStream fileOut = new FileOutputStream("person.ser");
                ObjectOutputStream out = new ObjectOutputStream(fileOut);

                // Serialize the object
                out.writeObject(person);

                // Close the output stream
                out.close();
                fileOut.close();

                System.out.println("Serialization complete.");
            } catch (IOException i) {
                i.printStackTrace();
            }
        }
    }
~~~

The object is restored from a serialized state using the ObjectInputStream class.
~~~
import java.io.*;

    public class DeserializeExample {
        public static void main(String[] args) {
            try {
                // Create a FileInputStream and ObjectInputStream
                FileInputStream fileIn = new FileInputStream("person.ser");
                ObjectInputStream in = new ObjectInputStream(fileIn);

                // Deserialize the object
                Person person = (Person) in.readObject();

                // Close the input stream
                in.close();
                fileIn.close();

                System.out.println("Deserialization complete.");
                System.out.println("Person name: " + person.getName());
                System.out.println("Person age: " + person.getAge());
            } catch (IOException | ClassNotFoundException i) {
                i.printStackTrace();
            }
        }
    }
~~~

# 7. Java Serialization with Inheritance (IS-A Relationship)

If a class implements Serializable interface then all its sub classes will also be serializable.

Parent class properties are inherited to subclasses so if parent class is Serializable, child class would also be 
Serializable.

# 8. Java Serialization with Aggregation (HAS-A Relationship)

If a class has a reference to another class, all the references must be Serializable otherwise 
serialization process will not be performed. In such case, **NotSerializableException** is thrown at runtime.
~~~
Eg. Class Address is a simple class.
Class Student has a reference of Address class and Student class is implementing Serializable interface.
Since Address is not Serializable, you cannot serialize the instance of the Student class.
~~~
**Note: All the objects within an object must be Serializable.**

# 9. Java Serialization with the static data member

If there is any static data member in a class, it will not be serialized because static is the part of 
class not object.

# 10. Java Serialization with array or collection

**Rule:** In case of array or collection, all the objects of array or collection must be serializable. 
If any object is not serialiizable, serialization will be failed.

# 11. Java Transient Keyword

If you don't want to serialize any data member of a class, you can mark it as transient.
~~~
private transient String password; // This will not be serialized
~~~
In below example id will not be serialized, so when you deserialize the object after serialization,
you will not get the value of id. It will return default value always.
In such case, it will return 0 because the data type of id is an integer.
~~~
class Student implements Serializable{  
    transient int id;  
    String name;  
    
    public Student(int id, String name) {  
        this.id = id;  
        this.name = name;  
    }
}
~~~

# 12. SerialVersionUID

In serialization process, at runtime it associates an id with each Serializable class which is known as 
SerialVersionUID. 

It is used to verify the sender and receiver of the serialized object.

The sender and receiver must be the same. To verify it, SerialVersionUID is used. 

The sender and receiver must have the same SerialVersionUID, otherwise, InvalidClassException 
will be thrown when you deserialize the object.

We can also declare our own SerialVersionUID in the Serializable class. 
To do so, you need to create a field SerialVersionUID and assign a value to it. 
It must be of the long type with static and final. 

It is suggested to explicitly declare the serialVersionUID field in the class and have it private also. 
For example:
~~~
private static final long serialVersionUID=1L;
~~~


# 13. Externalizable inerface in java

In addition to Serializable, Java also provides the **Externalizable interface**, which gives more control 
over the serialization process. 
A class that implements **Externalizable** must override the **writeExternal() and readExternal() methods** 
to explicitly define how the object is serialized and deserialized. 

**It is not a marker interface.**


The Externalizable interface provides two methods:
~~~
public void writeExternal(ObjectOutput out) throws IOException
public void readExternal(ObjectInput in) throws IOException
~~~

Example :
~~~
public class CustomPerson implements Externalizable {
    private String name;
    private int age;

    @Override
    public void writeExternal(ObjectOutput out) throws IOException {
        
        out.writeObject(name);
        out.writeInt(age);
    }

    @Override
    public void readExternal(ObjectInput in) throws IOException, ClassNotFoundException {
        
        name = (String) in.readObject();
        age = in.readInt();
    }
}
~~~


# 14. what is difference between Externalizable and serializable interface

**Serializable** is easier to use and is ideal when you don't need to modify the default serialization behavior.

**Externalizable** gives you full control over the serialization process and is suitable when you need 
customized or optimized serialization logic

**Key Differences:**

|Feature |                   	Serializable                   |	Externalizable |
| :---         |:---------------------------------------------:|          ---: |
|Control over Serialization	|Minimal (automatic serialization of all fields)	|Full control (custom serialization and deserialization)|
|Methods to Implement	|None (marker interface)	|writeExternal() and readExternal() must be implemented|
|Use Case	|When default serialization is sufficient	|When custom logic or performance optimization is needed|
|Flexibility	|Low (automatic handling of object state)	|High (you control the serialization and deserialization process)|

# 1. What is Serialization in Java?

Serialization in Java is the process of converting an object into a byte stream so that it can be easily 
saved to a file or sent over a network. 

The Serializable interface is used to mark a class as eligible for serialization.

# 2. What is the difference between Serialization and Deserialization in Java?

**Serialization:** The process of converting an object's state (data) into a byte stream.

**Deserialization:** The process of converting the byte stream back into an object with the original state.

# 3. What is the Serializable interface?
The Serializable interface is a marker interface (it has no data member and methods) used to 
indicate that a class can be serialized. When a class implements Serializable, the Java runtime can 
automatically serialize and deserialize its objects.

# 4. What is the purpose of the serialVersionUID in Java?

The serialVersionUID is a unique identifier for each class that is serialized. It helps in version 
control when deserializing objects.

If the class definition changes (like adding/removing fields), the serialVersionUID ensures compatibility, 
and the JVM checks it during deserialization to avoid **InvalidClassException** if the version is incompatible.
~~~
private static final long serialVersionUID = 1L;
~~~

# 5. What will happen if a class does not implement the Serializable interface but you try to serialize it ?
If a class does not implement the Serializable interface, attempting to serialize its objects 
will throw a **java.io.NotSerializableException.**

# 6. Can we serialize static and transient fields?

**Static Fields:** Static fields are not serialized because they belong to the class, 
not the instance of the class. They are shared across all instances.

**Transient Fields:** Fields marked as transient are not serialized. 
The transient keyword is used to indicate that a field should not be part of the serialization process.

# 7. Explain How Externalizable is different from Serializable?

**Serializable** is a marker interface that automatically handles the serialization process for you.

**Externalizable** extends Serializable interface but requires you to define custom logic for the 
serialization and deserialization process by implementing writeExternal() and readExternal() methods.

**Use Case:** Use Externalizable when you need fine control over the serialization process, such as excluding fields 
or altering the format of serialized data.

# 8. What happens if a class is serialized and then deserialized with an incompatible version?

If the serialVersionUID in the class is not compatible between the serialized version and the current 
class version, a **java.io.InvalidClassException** will be thrown during deserialization. 
If the serialVersionUID is the same, the deserialization process will work fine, even if other fields have changed.

# 9. What is the role of ObjectOutputStream and ObjectInputStream in Serialization and Deserialization?

**ObjectOutputStream:** This class is used to serialize an object by writing it to an output stream.
**ObjectInputStream:** This class is used to deserialize an object by reading from an input stream.

~~~
ObjectOutputStream out = new ObjectOutputStream(new FileOutputStream("object.ser"));
out.writeObject(object);
out.close();

ObjectInputStream in = new ObjectInputStream(new FileInputStream("object.ser"));
Object object = in.readObject();
in.close();
~~~

# 10. Can we serialize a Singleton class in Java?

Yes, a singleton class can be serialized, but to maintain the singleton property 
(one instance throughout the application), you need to handle deserialization carefully. 
If a singleton class is serialized and deserialized, it could create multiple instances.
To prevent this, you should implement the **readResolve()** method.
~~~
private Object readResolve() {
return instance;  // Return the single instance
}
~~~

# 11. What is the writeObject() method in Java Serialization?

The **writeObject()** method is used to serialize an object and write it to an output stream. 
It is part of the **ObjectOutputStream class**. If you want to serialize an object, you call this method.
~~~
Student s1 =new Student();
ObjectOutputStream out=new ObjectOutputStream(fout);    
out.writeObject(myObject);  // Serialize myObject
~~~

# 12. What is the purpose of the readObject() method in Java Deserialization?
The **readObject()** method is used to deserialize an object from an input stream. 
It reads the byte stream and reconstructs the object. This method is part of the **ObjectInputStream class.**
~~~
MyObject obj = (MyObject) in.readObject();  // Deserialize an object
~~~

# 13. Can you serialize an object that contains non-serializable members (fields)?

If an object contains a field that is not serializable, the serialization process will fail, 
throwing a **java.io.NotSerializableException**. 
To solve this, you can mark non-serializable fields as transient, so they are not serialized.

# 14. What is the significance of the transient keyword in Serialization?

The transient keyword is used to indicate that a particular field should not be serialized. 
When a field is marked as transient, it will be skipped during the serialization process, 
and its value will not be saved
~~~
private transient String password;  // This field won't be serialized
~~~

# 15. What happens during the deserialization of an object in Java?

During deserialization, the byte stream representing the object is converted back into a copy of the original object. 
The object's fields are restored from the stream, and the object is re-created in memory. 
The **readObject()** method is used to perform this process.

# 16. How does Java handle versioning of serialized objects?

Java handles versioning through the serialVersionUID field. 
This field is used to check the compatibility between the version of the class that was serialized and 
the version that is being deserialized. 
If the serialVersionUID values do not match, an InvalidClassException is thrown.


# 17. Can you serialize a Thread or a Socket in Java?
No, you cannot serialize a Thread or a Socket because these are system resources and 
are inherently non-serializable. 

Attempting to serialize such objects will result in a java.io.NotSerializableException.

# 18. How can you customize the serialization process in Java?

you can customize the serialization process by overriding the **writeObject() and readObject()** 
methods in the class. 
This allows you to control what gets serialized and how the fields are serialized/deserialized.

~~~
private void writeObject(ObjectOutputStream out) throws IOException {
    
    out.defaultWriteObject();  // Serialize non-transient fields
    
    // Custom logic for additional fields
}
~~~

# 19. What is the difference between ObjectOutputStream and DataOutputStream in Java?

**ObjectOutputStream** is used specifically for serializing objects (including their state and class information).

**DataOutputStream** is used for writing primitive data types (e.g., int, float, boolean) in a machine-independent way.

# 20. How does the readResolve() method help in maintaining object consistency during deserialization?

The **readResolve()** method is used to maintain consistency for special cases like singleton objects. 
When the object is deserialized, this method is called, and it returns the single instance of the class, 
ensuring that only one instance is used.
~~~
private Object readResolve() {
    return Singleton.getInstance();
}
~~~
