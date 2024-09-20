# SC317-Concepts-of-Programming-Languages

<div align="center">
  <table width="100%" border="1" cellpadding="10" cellspacing="0">
    <tr style="background-color:#f2f2f2;">
      <td align="center" colspan="2"><strong>Assignment 2: Advanced Java Concepts: Varargs, Function Simulation, Polymorphism, and Generics</strong></td>
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

### ✍️ Examples and Explanations

#### 1. **Variable Arguments (Varargs)**

In Java, a method can accept a variable number of arguments using varargs. This is a powerful feature that allows flexibility when the exact number of arguments is not known at the time of method definition. It helps in making the code more concise by avoiding method overloading for different numbers of parameters.

- **Syntax:** To use varargs, the ellipsis `...` is placed after the type of the last parameter. The method can accept zero or more arguments of that type. Importantly, varargs must always be the last parameter in a method's parameter list.

```java
public class VarargsExample {
    // Takes a double as a fixed argument followed by a variable number of strings
    static void display(double gpa, String... name) {
        String sName = " ";
        for (String i : name) {
            sName += i + " ";  // Concatenate each name with a space
        }
        System.out.print("GPA: " + gpa + "\nName: " + sName + "\n");
    }

    public static void main(String args[]) {
        // Calling display with different numbers of String arguments
        display(3.3);                      // GPA: 3.3, Name: 
        display(3.3, "Mootaz");            // GPA: 3.3, Name: Mootaz 
        display(3.3, "Mootaz", "Medhat");  // GPA: 3.3, Name: Mootaz Medhat
    }
}
```

**Explanation:**
- The method `display(double gpa, String... name)` takes one `double` and a variable number of `String` arguments. 
- If no `String` argument is passed, the `name` array is empty. When one or more `String` arguments are passed, they are concatenated to form a single string (`sName`), which is then printed along with the `gpa`.
  
**Key Benefit:** Varargs eliminate the need for method overloading when the number of arguments is unknown or variable, thus improving **code simplicity** and **readability**.

#### 2. **Subprograms as Parameters (Function Pointer Simulation)**

In languages like C/C++, function pointers allow passing functions as parameters to other functions. While Java doesn’t support function pointers directly, similar behavior can be simulated using **method references** or **lambdas**.

```java
public class FunctionPointerEx {
    // Method that takes another method as a parameter (simulating function pointers)
    public static void hello(Runnable obj) {
        obj.run();  // Executes the passed method
    }

    // Methods to be passed as arguments
    public static void english() {
        System.out.print("Hello\n");
    }

    public static void french() {
        System.out.print("Bienvenue\n");
    }

    public static void main(String args[]) {
        // Passing methods by reference
        hello(FunctionPointerEx::english);  // Output: Hello
        hello(FunctionPointerEx::french);   // Output: Bienvenue
    }
}
```

**Explanation:**
- The `hello(Runnable obj)` method takes a `Runnable` object as an argument, which refers to a method.
- Using **method references** (`FunctionPointerEx::english`), the program can pass methods like `english` and `french` as arguments to `hello`.
- When `hello` is called, it invokes the passed method.

**Key Benefit:** This approach improves **generality** and **modularity** by decoupling the method that executes from the method it calls, making the code more flexible.

#### 3. **Polymorphism**

Polymorphism is a key concept in object-oriented programming. Java supports two types of polymorphism: **static polymorphism** and **dynamic polymorphism**.

- **Static Polymorphism:** Achieved through method overloading. The method to be executed is determined at compile-time.
  
- **Dynamic Polymorphism:** Achieved through method overriding, where the method to be executed is determined at runtime based on the object’s actual type.

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
        Animal myAnimal = new Animal();  // Reference to parent class
        Animal myDog = new Dog();        // Reference to subclass
        
        myAnimal.sound();  // Output: Animal makes a sound (Static binding)
        myDog.sound();     // Output: Dog barks (Dynamic binding)
    }
}
```

**Explanation:**
- **Static Polymorphism:** Involves method overloading, where multiple methods with the same name but different parameters are resolved at compile-time.
  
- **Dynamic Polymorphism:** Here, the base class reference `Animal` points to an object of the derived class `Dog`. The method `sound()` is overridden in the `Dog` class, and at runtime, the JVM dynamically determines the actual object type and calls the overridden method.

**Key Benefit:** Dynamic polymorphism provides flexibility, allowing a superclass to define common behavior while subclasses provide specific implementations.

#### 4. **Generics (Generic Classes and Methods)**

Generics allow classes and methods to operate on any type while maintaining type safety. They enable **code reusability** by eliminating the need for code duplication.

```java
public class GenericBubbleSort {
    // Generic method that sorts an array of any type (that implements Comparable)
    public static <T extends Comparable<T>> void sort(T[] arr) {
        for (int i = 0; i < (arr.length - 1); i++) {
            for (int j = 1; j < (arr.length - i); j++) {
                if (arr[j].compareTo(arr[j - 1]) < 0) {
                    // Swap the elements if they are in the wrong order
                    T temp = arr[j];
                    arr[j] = arr[j - 1];
                    arr[j - 1] = temp;
                }
            }
        }
        // Print the sorted array
        for (T i : arr) {
            System.out.print(i + ", ");
        }
    }

    public static void main(String args[]) {
        Integer[] intArray = {10, 5, 0, 3, 6, 1};
        sort(intArray);  // Output: 0, 1, 3, 5, 6, 10

        Character[] charArray = {'v', 'g', 'a', 'c'};
        sort(charArray);  // Output: a, c, g, v
    }
}
```

**Explanation:**
- The `sort` method is generic, meaning it can sort an array of any type (`T`) as long as that type implements the `Comparable` interface.
- The method uses the `compareTo` method to compare elements and swap them if necessary.
- This approach works for any data type that implements `Comparable`, such as `Integer`, `Character`, `String`, and even user-defined types.

**Key Benefit:** Generics provide **type safety** at compile-time and eliminate the need for casting, making the code more reliable and reducing runtime errors.

### 📘 Conclusion

This assignment explores important concepts in Java, demonstrating how they help enhance code flexibility, generality, and reusability. Through the use of varargs, method references, polymorphism, and generics, Java provides robust features that simplify complex tasks, making programs more efficient and adaptable.

---

### 💬 Let's Connect
Feel free to reach out to me if you'd like to collaborate on a project or discuss technology! As a Software Engineer, I'm always open to tackling new challenges, sharing knowledge, and growing through collaborative opportunities.

**Mootaz Medhat Ezzat Abdelwahab**  
🎓 Software Engineering Graduate | Faculty of Computers and Artificial Intelligence, Cairo University  

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/mootaz-medhat-ezzat-abdelwahab-377a60244)
