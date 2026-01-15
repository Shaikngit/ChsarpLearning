## ➤ What are Header Files, Libraries, and Packages in terms of C, Java, C#, and Python?

### ➤ Header Files
- **C**: Header files in C contain declarations of functions, macros, and variables. They are included in the source code using the `#include` directive. Example:
  ```c
  #include <stdio.h>
  int main() {
      printf("Hello, World!\n");
      return 0;
  }
  ```
- **Java**: Java does not use header files. Instead, it uses class files and packages to organize code. Example:
  ```java
  package mypackage;
  public class HelloWorld {
      public static void main(String[] args) {
          System.out.println("Hello, World!");
      }
  }
  ```
- **C#**: Similar to Java, C# does not use header files. It uses namespaces and assemblies. Example:
  ```csharp
  using System;
  namespace MyNamespace {
      class Program {
          static void Main(string[] args) {
              Console.WriteLine("Hello, World!");
          }
      }
  }
  ```
- **Python**: Python does not use header files. It uses modules and packages. Example:
  ```python
  import math
  print("Square root of 16 is", math.sqrt(16))
  ```

### ➤ Libraries
- **C**: Libraries in C are collections of precompiled functions. Example:
  ```c
  #include <math.h>
  int main() {
      double result = sqrt(16.0);
      printf("Square root of 16 is %.2f\n", result);
      return 0;
  }
  ```
- **Java**: Libraries in Java are collections of classes and methods. Example:
  ```java
  import java.util.ArrayList;
  public class Example {
      public static void main(String[] args) {
          ArrayList<String> list = new ArrayList<>();
          list.add("Hello");
          list.add("World");
          System.out.println(list);
      }
  }
  ```
- **C#**: Libraries in C# are assemblies. Example:
  ```csharp
  using System.Collections.Generic;
  class Example {
      static void Main(string[] args) {
          List<string> list = new List<string> { "Hello", "World" };
          foreach (var item in list) {
              Console.WriteLine(item);
          }
      }
  }
  ```
- **Python**: Libraries in Python are collections of modules. Example:
  ```python
  import numpy as np
  array = np.array([1, 2, 3])
  print("Numpy array:", array)
  ```

### ➤ Packages
- **C**: C does not have a concept of packages.
- **Java**: Packages in Java group related classes. Example:
  ```java
  package mypackage;
  public class MyClass {
      public void display() {
          System.out.println("This is a package example.");
      }
  }
  ```
- **C#**: C# uses namespaces. Example:
  ```csharp
  namespace MyNamespace {
      class MyClass {
          public void Display() {
              Console.WriteLine("This is a namespace example.");
          }
      }
  }
  ```
- **Python**: Packages in Python are directories with an `__init__.py` file. Example:
  ```python
  # Directory structure:
  # mypackage/
  # ├── __init__.py
  # └── mymodule.py

  # mymodule.py
  def greet():
      print("Hello from mymodule!")

  # main.py
  from mypackage.mymodule import greet
  greet()
  ```

### ➤ Summary
| Language | Header Files | Libraries                  | Packages/Namespaces       |
|----------|--------------|----------------------------|---------------------------|
| C        | Yes          | Static/Dynamic Libraries   | No                        |
| Java     | No           | `.jar` Files              | Yes (Packages)            |
| C#       | No           | `.dll` Files              | Yes (Namespaces)          |
| Python   | No           | Modules/Packages          | Yes (Packages)            |
