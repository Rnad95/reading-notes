# Read: 01 - Java Basics

## Outlines

---

1. Variables  

2. Operators

3. Expression, statement and Blocks

4. Control Flow Statements

**1. Variables:**
-

 ***Definition:*** Variable is a place to store the data for using later.

***The Type of Variables in Java:***
-

| Instance Variables (Non-Static Fields)                                                                                                                                                                                                                                                                                                                                         | Class Variables (Static Fields)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          | Local Variables                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            | Parameters                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Technically speaking, objects store their individual states in "non-static fields", that is, fields declared without the static keyword. Non-static fields are also known as instance variables because their values are unique to each instance of a class (to each object, in other words); the currentSpeed of one bicycle is independent from the currentSpeed of another. | A class variable is any field declared with the static modifier; this tells the compiler that there is exactly one copy of this variable in existence, regardless of how many times the class has been instantiated. A field defining the number of gears for a particular kind of bicycle could be marked as static since conceptually the same number of gears will apply to all instances. The code static int numGears = 6; would create such a static field. Additionally, the keyword final could be added to indicate that the number of gears will never change. | Similar to how an object stores its state in fields, a method will often store its temporary state in local variables. The syntax for declaring a local variable is similar to declaring a field (for example, int count = 0;). There is no special keyword designating a variable as local; that determination comes entirely from the location in which the variable is declared — which is between the opening and closing braces of a method. As such, local variables are only visible to the methods in which they are declared; they are not accessible from the rest of the class. | You've already seen examples of parameters, both in the Bicycle class and in the main method of the "Hello World!" application. Recall that the signature for the main method is public static void main(String[] args). Here, the args variable is the parameter to this method. The important thing to remember is that parameters are always classified as "variables" not "fields". This applies to other parameter-accepting constructs as well (such as constructors and exception handlers) that you'll learn about later in the tutorial. |

| ***These Information from [Oracle Variable Documentation]( https://docs.oracle.com/javase/tutorial/java/nutsandbolts/variables.html )*** |
|----------------------------------------------------------------------------------------------------------------------------------------------|

### **Naming:** There are rules to name the variable

1. Variable is case Sensitive.  

2. we can started the name of variable using letters, digits, dollar signs, or underscore characters.  

3. The Name is selected out of the reserve words and the name should be meaningful.  

**2. Operators:**
-

### ***The operator is integral part of coding***  

![Operators](https://i.ibb.co/4ph5JFm/Screenshot-from-2022-02-26-12-48-47.png)

**3. Expression, statement and Blocks:**
-

- **Expression is the rules to write the code in any code language**

- **Statement is considered as anything end with semicolon `;`**

        int cadence = 0;
   
        anArray[0] = 100;
    
        System.out.println("Element 1 at index 0: " + anArray[0]);

        int result = 1 + 2; // result is now 3
    
        if (value1 == value2) 
    
        System.out.println("value1 == value2");

- **Block is considered as each statment inside two curley brackets As shown below**  

![example of Block](https://i.ibb.co/gMnW1xV/Screenshot-from-2022-02-26-13-06-41.png)

**4. Control Flow Statements**
-

The code in  java is executed from top to bottom in general except some rules for example: functions, loops, Jump statement (break and continue), and decision-making statements like if-statement.

![Control Flow](https://i.ibb.co/vDT7qQM/Screenshot-from-2022-02-26-13-16-03.png)

**To get more details about the image and the control flow we can go to [BTech. Smart Class](http://www.btechsmartclass.com/java/java-control-statements.html)**  

- > we have some principles in the programming language  
Like:  
**Compiling** which means that we write the java in high-level language ( English words within Java rules ) and the machine understand ONLY 1's and 0's. The compilor takes the program the human wrote, and converts it into the program the computer can understand.  

---

**`Resources:`**

---
Resource 1: [Oracle Documentation](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/index.html)  
Resource 2: [Reddit](https://www.reddit.com/r/explainlikeimfive/comments/233dq5/eli5_what_does_it_mean_to_compile_code/)  
Resource 3: [BTech. Smart Class](http://www.btechsmartclass.com/java/java-control-statements.html)  
Resource 4: [dummies Articles](https://www.dummies.com/category/articles/java-33602)  
