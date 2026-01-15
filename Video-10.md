Writing a program by using different Programming Approaches:

1. Procedural Programming Approach eG: C, FORTRAN, Pascal etc.,
2. Object-Oriented Programming Approach eG: C++, Java, C# etc., 

## The Main Program

Regardless of the programming language or approach used, every executable application must have a **main program** or entry point. This is where the program execution begins when it is launched by the operating system. The main program serves as the starting point that initializes the application, orchestrates the flow of execution, and eventually terminates when the work is complete.

In procedural languages like C, the main program is typically a function named `main()` that contains sequential instructions to be executed from top to bottom. In object-oriented languages like C++, Java, or C#, the main program is still a special method (often called `Main` or `main`), but it frequently instantiates objects, invokes methods on those objects, and delegates work to various classes. Despite differences in syntax and structure across languages, the fundamental concept remains the same: one designated entry point where execution begins.

The main program is responsible for setting up the runtime environment, handling command-line arguments if provided, and managing the overall lifecycle of the application. It acts as the conductor that brings together all components—whether they are functions, classes, or modules—to accomplish the intended task before gracefully exiting and returning control to the operating system.

## Procedural Programming Approach

## C Program Structure

A C program is a **collection of members** (Variables & Functions):

```c
void main()    // <= Entry Point
{
    // Call the members from here for execution
}
```

- **`void main()`** - The entry point where program execution begins
- **Members** - Variables (data) and Functions (operations) that make up the program
- Inside `main()`, you call other functions to perform tasks

Note:- the drawbacks of Procedural Programming Approach are:
- Lack of Security: Data is exposed and can be modified directly    
- Poor Reusability: Code cannot be easily reused in other programs without duplication

## Procedural vs OOP - Visual Comparison

```
┌─────────────────────────┐       ┌─────────────────────────────┐
│                         │       │                             │
│   ┌───────────────┐     │       │     ╭─────────────────╮     │
│   │               │     │       │    ╱                   ╲    │
│   │   -Members    │     │       │   │     -Members        │   │
│   │               │     │       │    ╲                   ╱    │
│   └───────────────┘     │       │     ╰─────────────────╯     │
│                         │       │       Wrapper (Class)       │
│   Procedural Program    │       │                             │
│                         │       │   Object Oriented Program   │
└─────────────────────────┘       └─────────────────────────────┘
```

- **Procedural**: Members (variables & functions) exist directly in the program
- **OOP**: Members are **wrapped inside a Class** (encapsulation)



## Object-Oriented Programming (OOP) Approach
The first OOP language was C++ which is an extension of C language. OOP languages organize code into **classes** that encapsulate both data (attributes) and behavior (methods).

In OOP also every program has collection of members, but here the members are wrapped into classes

## C++ Program Structure

A C++ program is a **collection of classes**:

```cpp

class MyClass {          // Class Definition
    public:
        void myMethod() { // Method Definition
            // Method code here
        }
};

int main() {             // <= Entry Point
    MyClass obj;         // Create an object of MyClass
    obj.myMethod();      // Call method on the object
    return 0;
}
```

- **`class MyClass`** - Defines a class with methods and attributes
- **`int main()`** - The entry point where program execution begins
- Inside `main()`, you create objects of classes and call their methods to perform tasks
Note:- the advantages of Object-Oriented Programming Approach are:
- Enhanced Security: Data is encapsulated within classes and accessed via methods   
- Improved Reusability: Classes can be reused across different programs without code duplication

## What is a Class?

A **class** is a **user-defined type** that serves as a blueprint for creating objects. It is essentially a **collection of members** (variables and functions) grouped together under a single name.

A class is similar to a struct in C language but with additional features that support Object-Oriented Programming (OOP) principles such as encapsulation, inheritance, and polymorphism.  

## What is a Struct?

A **struct** (short for "structure") is a user-defined data type that groups together variables of different types under a single name. It is a way to create a composite data type that can hold multiple related values.

structures were available in C language there were no classes. C++ introduced classes to bring security and reusability features to programming.

int,float,char etc., are predefined data types. These are available in libraries. 

C language does not have classes, it has only Functions (for behaviour and operations), Structs( for grouping related data together)  and Variables(for storing data).

## Struct vs Class - Syntax Comparison

```
┌─────────────────────────┐       ┌─────────────────────────────┐
│ struct <Name>           │       │ class <Name>                │
│ {                       │       │ {                           │
│   -Variables            │       │   -Variables & Functions    │
│ };                      │       │ };                          │
└─────────────────────────┘       └─────────────────────────────┘
```

- **Struct**: Contains only **variables** (data members)
- **Class**: Contains both **variables and functions** (data + behavior)


Eg:- 

struct in C:

```c
struct Point {
    int x;      // Variable to store x-coordinate
    int y;      // Variable to store y-coordinate
};

class in C++:

```cpp
class Point {
    public:
        int x;      // Variable to store x-coordinate
        int y;      // Variable to store y-coordinate

        void setCoordinates(int xCoord, int yCoord) { // Method to set coordinates
            x = xCoord;
            y = yCoord;
        }
};
```

- In the C struct example, `Point` only contains variables `x` and `y`.
- In the C++ class example, `Point` contains both variables `x` and `y`, as well as a method `setCoordinates()` to set their values.

int,float,char are predefined data types, point is a user-defined data type created using struct or class. In Cpp sometimes we use struct to create user-defined data types but most of the time we use class to create user-defined data types. 

int,float,char,string are scalar types where as point is a complex type.

## Scalar vs Complex Types

### Scalar Types
**Scalar types** hold a **single value**. They are the most basic, indivisible data types:

| Type | Example | Description |
|------|---------|-------------|
| `int` | `int age = 25;` | Integer numbers |
| `float` | `float price = 9.99f;` | Single-precision decimals |
| `double` | `double pi = 3.14159;` | Double-precision decimals |
| `char` | `char grade = 'A';` | Single character |
| `bool` | `bool isValid = true;` | True/false values |

### Complex Types (Compound Types)
**Complex types** are **composed of multiple values** or other types grouped together:

| Type | Example | Description |
|------|---------|-------------|
| `struct` | `struct Point { int x, y; };` | Groups related variables |
| `class` | `class Rectangle { int w, h; };` | Groups variables + functions |
| `array` | `int nums[5];` | Collection of same type |
| `string` | `string name = "John";` | Sequence of characters |

### Quick Comparison

```cpp
// Scalar types - single values
int x = 10;
float y = 3.14f;
char c = 'A';

// Complex types - multiple values grouped together
struct Point {
    int x;      // contains 2 scalar values
    int y;
};

class Circle {
    int radius;         // data
    float getArea();    // behavior
};
```

### Key Difference
- **Scalar**: Stores **one** atomic value (e.g., `int x = 5;`)
- **Complex**: Stores **multiple** values or combines data with behavior (e.g., `Point p = {10, 20};`) 

## How to Consume a Type

These concepts apply to **both scalar and complex types**.

Types **cannot be consumed directly** because a type doesn't have any memory allocated for storing a value.

```cpp
// Scalar type
int = 100;      // ❌ INVALID - Type alone cannot hold a value

// Complex type
Point = {10, 20};  // ❌ INVALID - Type alone cannot hold a value
```

To consume a type, you must first **create a copy (instance) of that type**. When you do this, the operating system allocates the required memory for storing a value.

```cpp
// Scalar type
int i = 100;           // ✅ VALID - 'i' is a copy/instance of type 'int' with memory allocated

// Complex type
Point p = {10, 20};    // ✅ VALID - 'p' is a copy/instance of type 'Point' with memory allocated
```

### Why This Matters

| Statement | Valid? | Explanation |
|-----------|--------|-------------|
| `int = 100;` | ❌ No | `int` is just a type definition, no memory |
| `int i = 100;` | ✅ Yes | `i` is a variable (instance) with allocated memory |
| `i = 100;` | ❌ No* | Only valid if `i` was previously declared |
| `Point = {10, 20};` | ❌ No | `Point` is just a type definition, no memory |
| `Point p = {10, 20};` | ✅ Yes | `p` is an object (instance) with allocated memory |

> **Note**: `i = 100;` is invalid if `i` has not been declared before. You must declare a variable before using it.

### Visual Representation

```
┌─────────────────────────────────────────────────────────────┐
│                         TYPE (int)                          │
│                    (No memory allocated)                    │
│                     Just a blueprint                        │
└─────────────────────────────────────────────────────────────┘
                              │
                              │ Create instance
                              ▼
┌─────────────────────────────────────────────────────────────┐
│                    VARIABLE (int i)                         │
│              ┌─────────────────────────┐                    │
│              │   Memory: 4 bytes       │                    │
│              │   Value: 100            │                    │
│              └─────────────────────────┘                    │
│                   OS allocates memory                       │
└─────────────────────────────────────────────────────────────┘
```

### Summary
- A **type** is a blueprint/template (e.g., `int`, `float`, `class Point`)
- A **variable** is an instance of a type with actual memory allocated
- You must create a variable (copy) of a type to store and use values

## Declaration vs Initialization

These concepts apply to **both scalar and complex types**.

You can also **separate declaration and initialization** into two statements:

```cpp
// Scalar type example
int i;      // Declaration - variable is declared but not initialized
i = 100;    // Assignment - value is assigned to the variable

// Complex type example
Point p;    // Declaration - object is declared but not initialized
p.x = 10;   // Assignment - values are assigned to the object members
p.y = 20;
```

This is valid because:
1. **Declaration** (`int i;`) - reserves memory for an integer variable named `i`
2. **Assignment** (`i = 100;`) - assigns the value 100 to the already declared variable

You can also combine them in a single statement:
```cpp
int i = 100;  // Declaration + Initialization
```

Both approaches are valid. The separate declaration style is useful when:
- You want to declare a variable at a broader scope but assign it later based on some condition
- You're declaring multiple variables of the same type and assigning them in different places

### Comparison

| Approach | Syntax | Description |
|----------|--------|-------------|
| Combined | `int i = 100;` | Declaration + Initialization in one line |
| Separate | `int i;` then `i = 100;` | Declaration first, assignment later |


- Copies of scalar types are called **variables**
- Copies of complex types are called **objects** or **instances**


## C Program Example - Functions for Add and Subtract

Here's a simple C program demonstrating the procedural programming approach with `add` and `subtract` functions:

```c
// Function to add two numbers
int add(int a, int b) {
    return a + b;
}

// Function to subtract two numbers
int subtract(int a, int b) {
    return a - b;
}

void main() {
    int result;
    
    // Call add function with arguments 100 and 50
    result = add(100, 50);
    printf("Addition: 100 + 50 = %d\n", result);
    
    // Call subtract function with arguments 100 and 50
    result = subtract(100, 50);
    printf("Subtraction: 100 - 50 = %d\n", result);
}
```

**Output:**
```
Addition: 100 + 50 = 150
Subtraction: 100 - 50 = 50
```

### Explanation:
- `add()` and `subtract()` are **functions** (members of the program)
- `main()` is the **entry point** where execution begins
- Functions are called from `main()` to perform operations
- This demonstrates the **procedural programming approach** where functions operate on data passed as arguments



## C++ Program Example - Class with Add and Subtract Methods

Here's the same program rewritten using C++ and the Object-Oriented Programming approach:

```cpp

// Class definition with add and subtract methods
class Math {
// Method to add two numbers
    int add(int a, int b) {
        return a + b;
    }
    
    // Method to subtract two numbers
    int subtract(int a, int b) {
        return a - b;
    }
};

int main() {
    // Create an object of Math class
    Math mathObj;
    int result;
    
    // Call add method using the object
    result = mathObj.add(100, 50);
    cout << "Addition: 100 + 50 = " << result << endl;
    
    // Call subtract method using the object
    result = mathObj.subtract(100, 50);
    cout << "Subtraction: 100 - 50 = " << result << endl;
    
    return 0;
}
```

**Output:**
```
Addition: 100 + 50 = 150
Subtraction: 100 - 50 = 50
```

### Explanation:
- `Math` is a **class** that encapsulates the `add()` and `subtract()` methods
- `mathObj` is an **object** (instance) of the `Math` class
- `main()` is the **entry point** where execution begins
- Methods are called on the object using dot notation: `mathObj.add()`, `mathObj.subtract()`
- This demonstrates the **Object-Oriented Programming approach** where data and behavior are encapsulated within a class

### Key Differences from C:
- **Encapsulation**: Functions are now methods inside a class
- **Object Creation**: Must create an object to call methods
- **Reusability**: The `Math` class can be reused in other programs
- **Security**: Class members can be made private to protect data

## C vs C++ Program Structure - Side by Side

| C Program (Procedural) | C++ Program (OOP) |
|------------------------|-------------------|
| **-Collection of Members (Variables & Functions)** | **class Example** |
| | **{** |
| | **-Collection of Members (Variables & Functions)** |
| | **};** |
| **void main() <= Entry Point** | **void main() <= Entry Point** |
| **{** | **{** |
| **-Call the members from here for execution** | **-Create the object of class** |
| | **-Call members of class by using the object created** |
| **}** | **}** |

### Key Differences

| Aspect | C (Procedural) | C++ (OOP) |
|--------|----------------|-----------|
| **Organization** | Members exist directly in the program | Members are wrapped inside classes |
| **Entry Point** | `void main()` | `void main()` (same) |
| **Execution** | Call members (functions) directly | 1. Create object of class<br>2. Call members using the object |
| **Data Access** | Direct access to variables | Access through objects |
| **Security** | No encapsulation | Encapsulation via classes |

```
┌────────────────────────────────┐    ┌────────────────────────────────┐
│         C PROGRAM              │    │        C++ PROGRAM             │
├────────────────────────────────┤    ├────────────────────────────────┤
│                                │    │  class Example                 │
│  -Members (Variables &         │    │  {                             │
│   Functions)                   │    │    -Members (Variables &       │
│                                │    │     Functions)                 │
│                                │    │  };                            │
├────────────────────────────────┤    ├────────────────────────────────┤
│  void main() <= Entry Point    │    │  void main() <= Entry Point    │
│  {                             │    │  {                             │
│    -Call members directly      │    │    -Create object of class     │
│                                │    │    -Call members via object    │
│  }                             │    │  }                             │
└────────────────────────────────┘    └────────────────────────────────┘
```

## C++ and the Pure OOP Debate

Although **C++ was the first Object-Oriented Programming language**, it has faced criticism for **not being fully object-oriented** according to strict OOP standards.

### The Criticism

According to pure Object-Oriented language standards, **every member should be defined inside a class**. However, in C++:

- The **`main()` function exists outside any class**
- This violates the principle that everything should be encapsulated within objects
- C++ allows mixing procedural and object-oriented paradigms

### Example of C++ Structure

```cpp
class Math {
    int add(int a, int b) {
        return a + b;
    }
};

int main() {           // ❌ main() is OUTSIDE the class
    Math obj;
    int c = obj.add(10, 20);
    return c;
}
```

**Issue**: `main()` is not part of any class, making C++ a **hybrid language** that supports both procedural and object-oriented programming.


```cpp
class Math {
    int add(int a, int b) {
        return a + b;
    }
    int main() {           // ❌ main() is INSIDE the class
    Math obj;
    int c = obj.add(10, 20);
    return c;
}
};
```

### Why This Won't Work - The Circular Dependency Problem

The above code fails because it creates a **chicken-and-egg paradox**:

1. **How to call members of a class?**  
   → By creating an object of the class.

2. **Where is the object of class created?**  
   → Inside of the main function.

3. **Is main function a member of the class now?**  
   → Yes, main is a member of the class now (since it's inside the class).

4. **If main function is a member of the class, how to call it for execution?**  
   → By creating an object of the class.

**But wait!** 🔄 This creates an impossible loop:

| Step | Requirement | Problem |
|------|-------------|---------|
| 1 | To call `main()`, you need an object | `main()` is inside the class |
| 2 | To create an object, you need `main()` to run first | But `main()` hasn't started yet! |

**You cannot create an object to call `main()` because `main()` itself is where you would create the object!**

The operating system looks for a **global `main()` function** as the entry point. When `main()` is inside a class:
- The OS cannot find it as a valid entry point
- Even if it could, there's no way to instantiate the class to access `main()` without already being inside `main()`

This is why C++ keeps `main()` outside classes—**it must be accessible without needing an object first**.


## Java's Solution to Pure OOP

In the early 1990s, Sun Microsystems was designing Java and took up the challenge of making it a **fully object-oriented language**. They addressed the criticism that C++ faced by ensuring that **every member must be defined inside a class**.

In Java , Members(Variables & Methods) are divided into two types:
1. **Non-Static Members** - Require an object to access
2. **Static Members** - Can be accessed without an object

- By default every member is a non-static member and till now what ever we have used in C and C++ are non-static members only.

- Static member means these member are prefixed with the keyword static at the time of declaration.

```java
class Test 
{
    int x = 100;                 // Non-static variable
    static int y = 200;          // Static variable

    int add(int a, int b) {      // Non-static method
        return a + b;
    }

    static int sub(int a, int b) { // Static method
        return a - b;
    }

    public static void main(String[] args) { // Static method - Entry Point
        Test obj = new Test();           // Create object to access non-static members
        int result1 = obj.add(100, 50);  // Call non-static method using object
        int result2 = Test.sub(75, 25);  // Call static method using class name // no object needed like add where add needs object 
        System.out.println("Addition: " + result1);
        System.out.println("Subtraction: " + result2);
    }
}
```

### Explanation:
- **Non-static members** (`x`, `add()`) - Require an object to access
- **Static members** (`y`, `sub()`, `main()`) - Can be accessed using the class name
- **`main()` is static** - JVM can call it without creating an object first
- Inside `main()`, we create a `Test` object to call non-static `add()` method
- Static `sub()` method is called directly using `Test.sub()` (no object needed)


### Java's Approach

Java enforced the following rules:

1. **Everything must be inside a class** - No standalone functions or variables allowed outside classes
2. **The `main()` method must be inside a class** - Unlike C++, Java's entry point is a method within a class
3. **The entry point is a special static method** - `main()` is declared as `public static void main(String[] args)`

### Why `static`?

Java solved the circular dependency problem by making `main()` a **static method**:

```java
class Example {
    int add(int a, int b) {        // Non-static method
        return a + b;
    }
    
    public static void main(String[] args) {   // Static method - Entry Point
        Example obj = new Example();   // Create object
        int result = obj.add(10, 20);  // Call non-static method via object
        System.out.println(result);
    }
}
```

### How Static Solves the Problem

| Aspect | Non-Static Members | Static Members |
|--------|-------------------|----------------|
| **Requires Object?** | ✅ Yes - need to create an object first | ❌ No - can be called directly using class name |
| **Memory Allocation** | Created when object is instantiated | Loaded when class is loaded by JVM |
| **Access Method** | `obj.method()` | `ClassName.method()` or directly if inside same class |

### The Circular Dependency - Broken!

```
❌ C++ Problem:
main() outside class → Need object to call class members
                    → But where to create object? (no entry point!)

✅ Java Solution:
main() is static inside class → No object needed to call main()
                              → JVM calls main() directly
                              → main() can create objects
                              → Objects call non-static members
```

### How Java Execution Works

1. **JVM loads the class** containing `main()` into memory
2. **JVM calls the static `main()` method** directly (no object needed!)
3. **Inside `main()`, objects are created** to access non-static members
4. **Program executes** by calling methods on these objects

### Visual Comparison

```
┌───────────────────────────────┐    ┌───────────────────────────────┐
│      C++ (Hybrid OOP)         │    │   Java (Pure OOP)             │
├───────────────────────────────┤    ├───────────────────────────────┤
│  class Math {                 │    │  class Math {                 │
│    int add() { ... }          │    │    int add() { ... }          │
│  };                           │    │                               │
│                               │    │    public static void main()  │
│  int main() {  ❌ Outside!    │    │    {  ✅ Inside & Static!     │
│    Math obj;                  │    │      Math obj = new Math();   │
│    obj.add();                 │    │      obj.add();               │
│  }                            │    │    }                          │
│                               │    │  }                            │
└───────────────────────────────┘    └───────────────────────────────┘
```

### Key Innovation: Static Members

By introducing the concept of **static members**, Java achieved:

- ✅ **Pure OOP** - Everything is inside classes
- ✅ **No Circular Dependency** - Entry point doesn't require an object
- ✅ **Clean Design** - Clear separation between static (class-level) and non-static (instance-level) members

### Summary

| Language | Is Pure OOP? | Entry Point | Reason |
|----------|-------------|-------------|---------|
| **C++** | ❌ No | `int main()` outside class | Main function exists independently of classes |
| **Java** | ✅ Yes | `public static void main()` inside class | Everything is in a class; static allows execution without object |
| **C#** | ✅ Yes | `static void Main()` inside class | Follows Java's model with static entry point |

Java's use of **static methods** was the breakthrough that allowed it to be a **fully object-oriented language** while still providing a practical entry point for program execution. This design pattern was later adopted by C# and other modern OOP languages.


## C# Program Structure - A Pure OOP Language

Like Java, C# is a **pure object-oriented language** where **everything must be inside a class**, including the `Main()` method. C# solves the circular dependency problem by using **static members**.

```
┌────────────────────────────────┐    ┌────────────────────────────────┐    ┌────────────────────────────────┐
│         C PROGRAM              │    │        C++ PROGRAM             │    │        C# PROGRAM              │
├────────────────────────────────┤    ├────────────────────────────────┤    ├────────────────────────────────┤
│                                │    │  class Example                 │    │  class Example                 │
│  -Members (Variables &         │    │  {                             │    │  {                             │
│   Functions)                   │    │    -Members (Variables &       │    │    -Static Members             │
│                                │    │     Functions)                 │    │    -Non-Static Members         │
│                                │    │  };                            │    │                                │
│                                │    │                                │    │    static void Main() <= Entry │
│                                │    │                                │    │    {                           │
│                                │    │                                │    │      -Call static members      │
│                                │    │                                │    │       (ClassName.Member)       │
│                                │    │                                │    │      -Create instance for      │
│                                │    │                                │    │       non-static members       │
│                                │    │                                │    │    }                           │
│                                │    │                                │    │  }                             │
├────────────────────────────────┤    ├────────────────────────────────┤    ├────────────────────────────────┤
│  void main() <= Entry Point    │    │  void main() <= Entry Point    │    │                                │
│  {                             │    │  {                             │    │  Main() is INSIDE the class!   │
│    -Call members directly      │    │    -Create object of class     │    │  No code exists outside.       │
│                                │    │    -Call members via object    │    │                                │
│  }                             │    │  }                             │    │                                │
└────────────────────────────────┘    └────────────────────────────────┘    └────────────────────────────────┘
```

### Static vs Non-Static Members in C#

| Aspect | Static Members | Non-Static Members |
|--------|----------------|-------------------|
| **Keyword** | Declared with `static` | No `static` keyword |
| **Access** | Via class name: `ClassName.Member` | Via object: `obj.Member` |
| **Object Required?** | ❌ No | ✅ Yes |
| **Memory** | One copy shared by all | Each object has its own copy |

### C# Example

```csharp
class Math
{
    // Static member - can be called without creating object
    public static int Add(int a, int b)
    {
        return a + b;
    }
    
    // Non-static member - requires object to call
    public int Subtract(int a, int b)
    {
        return a - b;
    }
    
    // Entry point - MUST be static (inside the class!)
    static void Main()
    {
        // Call static member directly using class name
        int sum = Math.Add(100, 50);
        Console.WriteLine("Addition: " + sum);
        
        // Create object for non-static member
        Math obj = new Math();
        int diff = obj.Subtract(100, 50);
        Console.WriteLine("Subtraction: " + diff);
    }
}
```

### How C# Solves the Circular Dependency Problem

In C++, putting `main()` inside a class creates a paradox (need object to call `main()`, but need `main()` to create object).

**C# solves this with the `static` keyword:**

| Problem in C++ | Solution in C# |
|----------------|----------------|
| `main()` inside class needs object to call | `Main()` is **static** - no object needed |
| Can't create object without running `main()` first | Static members belong to the **class itself**, not objects |

```
┌─────────────────────────────────────────────────────────────┐
│  C# - How static solves the problem                         │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  class Program                                              │
│  {                                                          │
│      static void Main()  ←── CLR calls this directly!       │
│      {                       No object needed because       │
│          ...                 it's STATIC                    │
│      }                                                      │
│  }                                                          │
│                                                             │
│  Static members belong to the CLASS, not to objects.        │
│  The CLR can invoke Main() via: Program.Main()              │
│  without creating an instance of Program.                   │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

### Key Differences Summary - All Languages

| Aspect | C (Procedural) | C++ (OOP) | Java (Pure OOP) | C# (Pure OOP) |
|--------|----------------|-----------|-----------------|---------------|
| **Organization** | Members directly in program | Members in classes | Everything in classes | Everything in classes |
| **Entry Point** | `void main()` outside | `int main()` outside | `public static void main()` inside class | `static void Main()` inside class |
| **Member Types** | Functions & Variables | All non-static | Static + Non-static | Static + Non-static |
| **Pure OOP?** | ❌ No | ❌ No (main outside) | ✅ Yes | ✅ Yes |
| **Runtime** | OS directly | OS directly | JVM | CLR (.NET) |

> **Note:** In Java or .NET (C#), if a class contains **only the `Main()` method** (and no other non-static members), we **don't need to create an object or instance** of that class to run the program. Since `Main()` is static, the runtime (JVM/CLR) can call it directly using the class name without instantiation.
>
> ```csharp
> // C# - No object needed when class only has static Main()
> class Program
> {
>     static void Main()
>     {
>         Console.WriteLine("Hello World!");
>         // No need to write: Program obj = new Program();
>         // Because Main() is static and there are no non-static members to access
>     }
> }
> ```
>
> **What if we don't want Main() to be static?**
>
> If you want your entry point logic to be in a **non-static method**, you still need a **static Main()** as the entry point (CLR requirement). The static Main() then creates an object and calls the non-static method:
>
> ```csharp
> // C# - Using non-static method for main logic
> class Program
> {
>     // Non-static method containing the main logic
>     void Run()
>     {
>         Console.WriteLine("Hello World from non-static method!");
>         // Here you can access other non-static members
>     }
>     
>     // Static entry point - REQUIRED by CLR
>     static void Main()
>     {
>         Program obj = new Program();  // Create instance
>         obj.Run();                     // Call non-static method
>     }
> }
> ```
>
> This pattern is useful when:
> - You want to access non-static members from your main logic
> - You're using dependency injection or need instance-level state
> - You're following certain design patterns that require instance methods


### Complete Example - Static and Non-Static Members in C#

Here's a complete example demonstrating when you **need** an object and when you **don't**:

```csharp
using System;

class Calculator
{
    // ============ STATIC MEMBERS ============
    // Belong to the CLASS itself - no object needed
    
    public static string Version = "1.0";  // Static variable
    
    public static int Add(int a, int b)    // Static method
    {
        return a + b;
    }
    
    public static int Multiply(int a, int b)  // Static method
    {
        return a * b;
    }
    
    // ============ NON-STATIC MEMBERS ============
    // Belong to INSTANCES (objects) - object required
    
    public int LastResult;  // Non-static variable (each object has its own copy)
    
    public int Subtract(int a, int b)  // Non-static method
    {
        LastResult = a - b;
        return LastResult;
    }
    
    public int Divide(int a, int b)  // Non-static method
    {
        LastResult = a / b;
        return LastResult;
    }
    
    // ============ ENTRY POINT ============
    // Static - so CLR can call it without creating object
    
    static void Main()
    {
        // -------- Calling STATIC members --------
        // NO object needed! Use ClassName.Member
        
        Console.WriteLine("Calculator Version: " + Calculator.Version);
        
        int sum = Calculator.Add(100, 50);
        Console.WriteLine("100 + 50 = " + sum);
        
        int product = Calculator.Multiply(10, 5);
        Console.WriteLine("10 * 5 = " + product);
        
        // -------- Calling NON-STATIC members --------
        // MUST create object first!
        
        Calculator calc = new Calculator();  // Create instance
        
        int diff = calc.Subtract(100, 50);   // Call via object
        Console.WriteLine("100 - 50 = " + diff);
        Console.WriteLine("Last Result stored: " + calc.LastResult);
        
        int quotient = calc.Divide(100, 5);  // Call via object
        Console.WriteLine("100 / 5 = " + quotient);
        Console.WriteLine("Last Result stored: " + calc.LastResult);
        
        // -------- Multiple Objects - Each has own non-static data --------
        
        Calculator calc2 = new Calculator();
        calc2.Subtract(200, 75);
        
        Console.WriteLine("\ncalc.LastResult = " + calc.LastResult);   // 20 (from Divide)
        Console.WriteLine("calc2.LastResult = " + calc2.LastResult);  // 125 (from Subtract)
        // Each object maintains its own LastResult!
    }
}
```

**Output:**
```
Calculator Version: 1.0
100 + 50 = 150
10 * 5 = 50
100 - 50 = 50
Last Result stored: 50
100 / 5 = 20
Last Result stored: 20

calc.LastResult = 20
calc2.LastResult = 125
```

### Quick Reference

| Member Type | Declaration | How to Call | Object Needed? |
|-------------|-------------|-------------|----------------|
| Static Variable | `public static string Version;` | `Calculator.Version` | ❌ No |
| Static Method | `public static int Add(...)` | `Calculator.Add(10, 5)` | ❌ No |
| Non-Static Variable | `public int LastResult;` | `calc.LastResult` | ✅ Yes |
| Non-Static Method | `public int Subtract(...)` | `calc.Subtract(10, 5)` | ✅ Yes |
