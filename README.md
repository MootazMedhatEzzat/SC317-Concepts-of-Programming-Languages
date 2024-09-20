# SC317-Concepts-of-Programming-Languages

<div align="center">
  <table width="100%" border="1" cellpadding="10" cellspacing="0">
    <tr style="background-color:#f2f2f2;">
      <td align="center" colspan="2"><strong>Assignment 1: Exploring Java's Key Language Design Features</strong></td>
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

## 📝 Assignment #1 (Deadline 24/3/2023)

Cairo University  
Faculty of Computers and Artificial Intelligence  
Concepts of Programming Languages Course (Spring 2023)

### ⚙️ Overview

This assignment focuses on exploring Java programming language in the context of key programming concepts like expressivity, orthogonality, syntax, exceptions, type binding, and more. The examples and explanations provided discuss how different language features impact writability, readability, and overall language design.

### 📚 Key Concepts in Java:

#### 1. **Expressivity and Writability vs. Readability**
- Expressivity enhances how easily ideas can be written, but it can reduce readability when too much is left implicit.  
Example:
```java
boolean isMorning = true; 
String greeting;
if (isMorning) {
    System.out.println(greeting);
} else {
    System.out.println(greeting);
}
greeting = isMorning ? "Good Morning" : "Good Evening";
```
- The ternary operator (`? :`) enhances writability by being concise, but can reduce readability because the programmer needs to mentally track the conditional flow.

#### 2. **Lack of Orthogonality**
- Orthogonality refers to how a language allows similar constructs to be used in a consistent way. In Java, the lack of orthogonality can negatively affect readability.  
Example:
```java
int x; 
int arr1[] = new int[3];
x = 5;                // Allowed assignment
arr1 = {1, 2, 3};     // Not allowed (must initialize arrays in a specific way)
```
- Java does not allow assignment of arrays after initialization, which requires developers to remember different rules for similar constructs, reducing simplicity and readability.

#### 3. **Syntax Design Issues Affecting Readability**
- In Java, statement groups are terminated in the same way (with a closing curly brace `}`), making it harder to determine which block is ending. This enhances simplicity but can reduce readability.
- Additionally, reserved words cannot be used as variable names, enhancing readability:
```java
double int;  // Invalid in Java, as `int` is a reserved word.
```

#### 4. **Handling Exceptions in Java**
- Java handles exceptions both **implicitly** (handled by the JVM) and **explicitly** (handled by the programmer):
  - **Implicit Handling**: Predefined exceptions like `ArithmeticException` when dividing by zero.
  ```java
  int result = 5 / 0;  // This throws an ArithmeticException.
  ```
  - **Explicit Handling**: Using `try-catch` blocks to handle exceptions and continue normal execution.
  ```java
  try {
      // Code that might throw an exception
  } catch (Exception e) {
      // Handling code
  }
  ```

#### 5. **Named Constants in Java**
- Java allows the definition of named constants using the `final` keyword. These constants can have dynamic values assigned at runtime:
```java
final int x = 2 * Y + 10;
```

#### 6. **Static Type Binding in Java**
- Java is statically typed, meaning variables must have their type declared at compile time, which helps in preventing type errors.
```java
int var = 10;
```

#### 7. **Variable Categories According to Lifetime in Java**
Java supports three categories of variables:
1. **Static Variables**: Global or class-level variables that exist for the duration of the program.
2. **Stack-Dynamic Variables**: Allocated at runtime on the stack.
3. **Explicit Heap-Dynamic Variables**: Managed dynamically via the heap, with memory deallocation handled by Java's garbage collector.

#### 8. **Static Typing and Type Checking**
- Java checks variable types at compile time, ensuring that operations are valid for the given types, which helps prevent runtime errors:
```java
int result = 2 * x;  // 'x' must be an integer or a type compatible with multiplication.
```

#### 9. **Side Effects in Functions**
- In Java, side effects (changes to global variables or parameters) are avoided by guaranteeing the order of operand evaluation (left to right), ensuring predictable behavior.

---

### 💬 Let's Connect
Feel free to reach out to me if you'd like to collaborate on a project or discuss technology! As a Software Engineer, I'm always open to tackling new challenges, sharing knowledge, and growing through collaborative opportunities.

**Mootaz Medhat Ezzat Abdelwahab**  
🎓 Software Engineering Graduate | Faculty of Computers and Artificial Intelligence, Cairo University  

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/mootaz-medhat-ezzat-abdelwahab-377a60244)
