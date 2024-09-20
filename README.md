# SC317-Concepts-of-Programming-Languages

<div align="center">
  <table width="100%" border="1" cellpadding="10" cellspacing="0">
    <tr style="background-color:#f2f2f2;">
      <td align="center" colspan="2"><strong>Assignment 2: Advanced Java Concepts</strong></td>
    </tr>
    <tr>
      <td align="center"><strong>Names:</strong><br>Mootaz Medhat Ezzat Abdelwahab</td>
      <td align="center"><strong>IDs:</strong><br>20206074</td>
    </tr>
    <tr style="background-color:#f9f9f9;">
      <td align="center"><strong>Program:</strong><br>Software Engineering</td>
      <td align="center"><strong>Group:</strong><br>S (5)</td>
    </tr>
    <tr>
      <td align="center" colspan="2"><strong>Delivered To:</strong><br>DR. Amin Allam</td>
    </tr>
  </table>
</div>

---

## 📝 Assignment #2 (Deadline 12/5/2023)

Cairo University  
Faculty of Computers and Artificial Intelligence  
Concepts of Programming Languages Course (Spring 2023)

### ⚙️ Overview

This assignment covers key advanced Java concepts that are essential for building robust, flexible, and maintainable software. The assignment includes:

1. **Variable Arguments (Varargs)**
2. **Subprograms as Parameters (Function Pointer Simulation)**
3. **Static and Dynamic Polymorphism**
4. **Generics (Generic Classes and Methods)**

### ✍️ Detailed Examples and Explanations

#### 1. **Variable Arguments (Varargs)**

In Java, varargs (short for variable-length arguments) allow you to pass a variable number of arguments to a method. This feature simplifies method overloading, making your code more concise and readable.

```java
public class VarargsExample {
    // Takes double as an argument followed by a variable number of strings
    static void display(double gpa, String... name) {
        String sName = " ";
        for (String i : name) {
            sName = sName + i + " ";  // Concatenate names
        }
        System.out.print("GPA : " + gpa + "\n" + "Name: " + sName + "\n");
    }

    public static void main(String args[]) {
        display(3.3);                      // GPA : 3.3 Name: 
        display(3.3, "Mootaz");            // GPA : 3.3 Name: Mootaz
        display(3.3, "Mootaz", "Medhat");  // GPA : 3.3 Name: Mootaz Medhat
        // Compile time error: varargs mismatch; double cannot be converted to String
        // display(3.3, 2.5); 
    }
}
```

- Varargs allow you to pass zero or more arguments to a method. However, **only one variable argument is allowed per method** and it **must be the last parameter**:
  - `static void display(double... gpa, String... name)` // Compile time error.
  - `static void display(double... gpa, String name)`    // Compile time error.
  
- **Before JDK 5**, programmers had to overload methods or pass arguments as an array, which made the code more verbose and less readable.
  
- **Varargs enhance generality** by allowing methods to handle varying numbers of arguments while ensuring **type safety** at compile time.

#### 2. **Subprograms As Parameters (Function Pointer Simulation)**

Java does not support function pointers like C/C++, but we can simulate their behavior using **method references** or **lambda expressions**. This technique enables us to pass methods as arguments to other methods, promoting code generality and modularity.

```java
public class FunctionPointerEx {
    // Method that takes another method as a parameter
    public static void hello(Runnable obj) {
        obj.run();  // Executes the passed method
    }

    // Methods to pass as arguments
    public static void english() {
        System.out.print("Hello\n");
    }

    public static void french() {
        System.out.print("Bienvenue\n");
    }

    public static void main(String args[]) {
        hello(FunctionPointerEx::english);  // Prints "Hello"
        hello(FunctionPointerEx::french);   // Prints "Bienvenue"
    }
}
```

- **Function pointers** in C/C++ are variables that store the memory address of a function, allowing for efficient memory use and generality.
  
- Although Java does not support pointers directly, **method references** (e.g., `FunctionPointerEx::english`) or **lambda expressions** (`hello(() -> System.out.println("Hello"))`) allow similar functionality by referencing methods as arguments.
  
- This approach enhances **generality** and provides **type safety** by ensuring that the method signature matches the expected parameter type (`Runnable` in this example).

#### 3. **Polymorphism**

Polymorphism in Java allows one interface to be used for different underlying forms (data types). It comes in two types:

##### Static Polymorphism (Compile-Time)

- Achieved through **method overloading**, where multiple methods with the same name differ by parameter types or number of parameters. The method to be executed is determined at **compile time**.

##### Dynamic Polymorphism (Run-Time)

- Achieved through **method overriding**, where a method in a subclass has the same name and parameter list as a method in its superclass. The method to be executed is determined at **runtime**, depending on the actual object type.

```java
class Animal {
    // Dynamic polymorphism: Method overridden in subclass
    void sound() {
        System.out.println("Animal makes a sound");
    }
}

class Dog extends Animal {
    // Overriding the sound method
    @Override
    void sound() {
        System.out.println("Dog barks");
    }
}

public class PolymorphismExample {
    public static void main(String[] args) {
        Animal myAnimal = new Animal();  // Parent class reference
        Animal myDog = new Dog();        // Reference to subclass

        myAnimal.sound();  // Output: Animal makes a sound
        myDog.sound();     // Output: Dog barks (dynamic binding)
    }
}
```

- **Static Polymorphism:** The method to be executed is determined at compile time, which does not involve any runtime overhead.
  
- **Dynamic Polymorphism:** Although **types are checked at compile time**, method binding occurs at runtime, based on the object's actual type (e.g., calling `Dog`'s `sound()` method). This may introduce **slight performance overhead** due to method forwarding.

#### 4. **Generics (Generic Classes and Methods)**

Generics provide a way to define methods and classes that can operate on any type while ensuring type safety at compile time. Generics make code more flexible without the need for casting and help prevent runtime errors.

```java
public class GenericBubbleSort {
    // Generic method that takes an array of any type and sorts its elements
    public static <T extends Comparable<T>> void sort(T[] arr) {
        for (int i = 0; i < (arr.length - 1); i++) {
            for (int j = 1; j < (arr.length - i); j++) {
                if (arr[j].compareTo(arr[j - 1]) < 0) {  // Compare and swap
                    T temp = arr[j];
                    arr[j] = arr[j - 1];
                    arr[j - 1] = temp;
                }
            }
        }
        // Printing sorted array
        for (T i : arr) {
            System.out.print(i + ", ");
        }
    }

    public static void main(String args[]) {
        Integer[] arrofInt = {10, 5, 0, 3, 6, 1};
        sort(arrofInt);  // Output: 0, 1, 3, 5, 6, 10

        Character[] arrofCha = {'v', 'g', 'a', 'c'};
        sort(arrofCha);  // Output: a, c, g, v
    }
}
```

- Generics ensure that classes and methods can handle different types (e.g., `Integer`, `Character`, user-defined types), enhancing **flexibility** and **reusability**.
  
- Generics handle **type checking at compile time**, catching errors early and ensuring that operations (like comparisons or arithmetic) are valid for the given type.
  
- **No runtime overhead** is introduced by generics. Code is compiled and optimized without the need for type casting or re-checking, making it ideal for algorithms and data structures.

### 📘 Conclusion

This assignment explores key advanced Java concepts, each contributing to the **generality**, **reusability**, and **reliability** of the code. By understanding and applying these concepts, developers can write more flexible and maintainable Java programs that handle a variety of data types and structures.

---

### 💬 Let's Connect
Feel free to reach out to me if you'd like to collaborate on a project or discuss technology! As a Software Engineer, I'm always open to tackling new challenges, sharing knowledge, and growing through collaborative opportunities.

**Mootaz Medhat Ezzat Abdelwahab**  
🎓 Software Engineering Graduate | Faculty of Computers and Artificial Intelligence, Cairo University  

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/mootaz-medhat-ezzat-abdelwahab-377a60244)
