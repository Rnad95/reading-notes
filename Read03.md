# Read: 03 -

## Java Data types

---  
Java has two types of datatype:

1. primitive like int, boolean, float, and so on which live on stack.
2. references like Array, String, Object, function, Integer, Boolean and so on.

The process of converting a primitive type to a reference one is called auto-boxing, the opposite process is called unboxing.  *Resource
[baeldung](https://www.baeldung.com/java-primitives-vs-objects#:~:text=The%20process%20of%20converting%20a%20primitive%20type%20to%20a%20reference%20one%20is%20called%20autoboxing%2C%20the%20opposite%20process%20is%20called%20unboxing.)

![autoboxing and unboxing](https://i.ibb.co/ngRrckN/Screenshot-from-2022-02-27-20-11-54.png)

**The Object** is selected based on what the performance of App , memory we need and what the default values we should to handle .

**Single Item Memory Footprint**  
Just for the reference, the primitive type variables have the following impact on the memory:
The primitive datatype impact on the memory 1 bit for boolean, 1 byte size for byte, 2 byte for short and char, 4 byte for int and float, and 8 byte for long and double though in practical may we got some different.

Reference data types are an Object and they store on the heap which is a dynamic allocation for java objects and are relatively slow in access operation.

The size of reference datatype are different related on primitive where the size of Boolean, Byte, Short, Character, Integer, and Float are 16 bytes Meanwhile the Long and Double are 24 bytes.  

## Exceptions

---
An Exception is the object which is generated as the result of the error or unexpected result.
The main goal of exception is to make the code running with run time error and prevent the code crash.
Java has an exception classes to handle a various of run time error

## Scanning

---
One of the modern method to get data or resource from user is a Scanner regarding to its benefit for breaking down formatted input into tokens and translating individual tokens according to their datatype.  
Resource[oracle](https://docs.oracle.com/javase/tutorial/essential/io/scanning.html#:~:text=Objects%20of%20type%20Scanner%20are%20useful%20for%20breaking%20down%20formatted%20input%20into%20tokens%20and%20translating%20individual%20tokens%20according%20to%20their%20data%20type.)

Breaking Input into Tokens which use the white space(blanks, tabs, and the lines) to separate its token. It can takes individual word or whole line depending what the programmer used.
