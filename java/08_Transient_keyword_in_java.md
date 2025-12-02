# Transient keyword :

**Transient keyword** Used to indicate that a field should not be serialized

The transient keyword in Java is used in serialization to indicate that a specific 
field should not be serialized. It is primarily used when you want to exclude/remove certain 
fields of an object from being written to a stream during the serialization process.

**Summary**
-	The transient keyword is used to prevent fields from being serialized.
-	transient is only applicable to instance variables (fields), not methods, classes, or blocks.
-	It is commonly used to exclude sensitive or non-essential data from serialization, such as passwords, session data, or cached information.
-	transient does not affect static fields, as static fields are not part of the serialization process.
-	You can combine transient with other keywords like final, volatile, and static based on the requirements of the field.

**1. What is the transient Keyword?**

The transient keyword is used in Java to mark fields of a class as non-serializable. 
When an object is serialized (i.e., converted into a byte stream for storage or transmission), 
the fields marked with transient will not be included in the serialization process. 
This is useful when you want to avoid serializing sensitive information (e.g., passwords) or 
derived values that can be recalculated.

**Key Features:**
-	**Prevents Serialization**: When you mark a variable as transient, it is not serialized when the 
    object is serialized.
-	**Serialization**: Serialization is the process of converting an object into a byte stream so 
    that it can be saved to a file, sent over a network, or persisted. transient helps exclude 
    unnecessary or sensitive data.
-	**Default Values for Transient Fields**: When deserialized, transient fields are assigned their 
    default values (null for reference types, 0 for numeric types, false for boolean, etc.), 
    unless explicitly restored during deserialization.

**2. Can We Apply transient to Methods, Blocks, or Classes?**

No, we can not apply transient to Methods, Blocks and Class.
It is only applicable to instance variables.

**transient with Methods:**
-	No, the transient keyword cannot be applied to methods. 

**transient with Blocks:**
-	There is no concept of a transient block in Java. You can only use transient with fields (variables), 
 not blocks.

**transient with Classes:**
-	You cannot declare a class as transient.
-	You can have transient fields in a class, but you cannot mark the entire class as transient.

**3. Can We Overload or Override Methods with transient?**

No, the transient keyword cannot be applied to methods. It is only applicable to instance variables.
**Overloading a transient method is possible**, but the transient modifier does not apply to methods—only fields
**You cannot override a method based on transien**t because it's not part of the method signature.

**4. Can We Make a Class transient?**

No, you cannot apply transient to a class. 
A class, by definition, is a template or blueprint for objects, and serialization concerns 
individual object fields, not the class itself.

**5. Can We Inherit a transient Class?**

The transient modifier applies to the fields of the parent class but it is not 
inherited by the subclass fields.
You can inherit from a class with transient fields, 
but the transient keyword on the fields of the parent class will not affect 
the fields in the subclass.
If the subclass has fields marked transient, 
those fields will also not be serialized when the object is serialized.

**6. Can We Make an Interface transient?**

No, you cannot declare an interface as transient. 

**7. Can We Make an Abstract Class transient?**

No, you cannot declare an abstract class as transient. 
As mentioned, transient is only used to mark instance variables as non-serializable. 
You cannot use transient for the class itself, whether it's abstract or concrete.
However, an abstract class can have transient fields, which will not be serialized when 
objects of a subclass are serialized.

**8. When to Use the transient Keyword**

**When to Use transient with Variables:**
- **Sensitive Data**: Use transient to prevent sensitive information like passwords, 
  personal identification numbers (PINs), or credit card details from being serialized.
- **Derived/Calculated Fields**: If a field's value can be derived or recalculated when needed, 
  and doesn't need to be stored during serialization, mark it as transient.
- **Large Fields**: If a field contains a large object (e.g., a huge array, cache, or connection pool) 
  that you don't need to serialize, you can mark it as transient to reduce the size of the 
  serialized object.

**When Not to Use transient:**

When You Need the Field Serialized: If a field must be serialized for object restoration 
during deserialization, you should not mark it as transient.

**9. transient Keyword with Other Keywords :**

**transient and static**: A static transient variable does not make much sense because static 
variables are shared across all instances of the class and are not part of the instance 
serialization process. Serialization is for object state, and static variables do not belong to instances of a class but rather to the class itself.

**transient and volatile:**
The transient and volatile keywords can be used together, but they have distinct roles:

-	volatile ensures that changes to a variable are visible across all threads immediately.
-	transient ensures that a variable is not serialized.

**transient and final:**
-	final and transient can be used together.
-	A final transient variable can be useful when you want to ensure the field's value is not changed after initialization but should not be serialized.

**transient and synchronized:**
-	transient is unrelated to synchronization.
-	While transient affects the serialization of a field, synchronized affects thread safety by controlling access to shared resources.
-	These two keywords typically do not interact directly.

**Tricky Questions on transient**
1.	**What happens when a transient field is deserialized?**
- When an object is deserialized, transient fields are not restored to their original value. 
 Instead, they are initialized to their default values (e.g., null for reference types, 
0 for numeric types).

2.	**Can we serialize a transient field manually during deserialization?**
- Yes, you can manually restore the value of a transient field during the readObject method by 
implementing custom deserialization.
3.	**Does transient affect the deserialization of object graphs (fields of objects)?**
- No, transient only affects the field it is applied to. If an object is a field of another object, 
it will still be serialized unless its own fields are marked as transient.

4.	**What happens if you serialize an object with transient fields and the class structure changes?**
- If the class structure changes (e.g., fields are added or removed), and you try to deserialize 
an object that has transient fields, the default values for transient fields will be used. 
- If the class is incompatible (e.g., fields have been renamed or removed), it may lead to an 
**InvalidClassException.**

# Constants 
**Constants** are typically defined using the final keyword to ensure the value cannot change

