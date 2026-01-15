How to define a Class?

## Syntax to define a class in C# is as shown below

```csharp
    [<modifiers>] class Name
    {
        // members of the class
    }
```
[] --> Optional
<> --> Any 

- Modifiers: Access specifiers for the class (public, private, protected, internal)
- class: Keyword to define a class
- Name: Name of the class (should follow naming conventions)
- Members: Variables, methods, properties, events, etc. that belong to the class


## Rules and Conventions for Writing C# Programs

- All keywords are in lowercase (C# has 81 keywords) — **rule**
- When consuming libraries, use **PascalCase** for class names and method names — **rule**  
    - Examples: `WriteLine`, `ReadLine`, `Console`, `Math`
- When defining your own class, you can use any name, but **PascalCase** is recommended
- A C# program should be saved with the `.cs` extension
- Any file name can be used, but using the **class name as the file name** is suggested for better understanding
- To write C# programs, use an IDE (Integrated Development Environment) or a text editor such as:
    - Notepad
    - Notepad++
    - VS Code

- To compile and run C# programs, use the **.NET SDK** (Software Development Kit) which includes the C# compiler (`csc.exe`) and the .NET runtime
- The command to compile a C# program is:
    ```
    csc FileName.cs
    ``` 
- The command to run the compiled program is:
    ```         
    FileName.exe
    ```
- Every C# program must have a `Main` method as the entry point of the application

## Syntax to define the `Main` method is as shown below

```csharp
    static void Main(string[] args)
    {
        // code to be executed
    }
```
- static: Keyword used to declare a member as `static member`, and if a member is declared as `static`, instance of class is not required to `call` or `execute` it. In c#, the `Main` method must be `static` because it is called by the runtime without creating an instance of the class
- void: Keyword used to specify that the method does not return any value
- Main: Name of the method (should be exactly `Main` with an uppercase 'M')
- string[] args: Parameter that represents command-line arguments passed to the program as an array of strings
- The `Main` method can have different signatures, such as:
    - `static void Main()`
    - `static int Main(string[] args)`
    - `static async Task Main(string[] args)` (for asynchronous programming)

- The `Main` method is the starting point of the program, and the code inside it is executed when the program runs

## Example: First C# Program to Print Some Text

```csharp
class FirstProgram

{
static void Main()

 {
   System.Console.Clear();
   System.Console.WriteLine("My First C# program using notepad.");
 }

}
```

### Output

```
My First C# program using notepad.

```

### Steps to Compile and Run

1. Save the file as `FirstProgram.cs`
2. Open a developer command prompt
3. Compile: `csc FirstProgram.cs`
4. Run: `FirstProgram.exe`


## Explanation of the Example
- `class FirstProgram`: Defines a class named `FirstProgram`
- `static void Main()`: Defines the `Main` method as the entry point of the
program
- `System.Console.Clear();`: Clears the console screen
- `System.Console.WriteLine("My First C# program using notepad.");`: Prints the specified text to the console followed by a newline
- `Console` is a predefined class (type) from the libraries and this class provides a set of methods to perform IO operations on standard IO Devices like console, keyboard, monitor etc. 
  `Console` has many `static` methods like `Clear()`, `Write()`, `WriteLine()`, `Read()`, `ReadKey()`, `ReadLine()` etc., to perform various IO operations. Thats why we are calling `WriteLine()` method using `Console` class to print text on the console without creating an instance of the `Console` class.

- `System` is a namespace and a namespace is a logical container of types (classes, interfaces, structs, enums, and delegates). 

- Just like `Console` there are 15000 predefined classes available in .Net libraries to perform various operations. All these predefined classes are grouped under different namespaces based on their functionality.

## Namespaces Allow Same Class Names in Different Containers

You can have **classes with the same name** in different namespaces without conflict:

```
+------------------------------------------------------------------+
|                           Project                                |
|  +---------------------------+  +---------------------------+    |
|  |           NSP1            |  |           NSP2            |    |
|  |  +---------------------+  |  |  +---------------------+  |    |
|  |  |                     |  |  |  |                     |  |    |
|  |  |    class First      |  |  |  |    class First      |  |    |
|  |  |                     |  |  |  |                     |  |    |
|  |  +---------------------+  |  |  +---------------------+  |    |
|  +---------------------------+  +---------------------------+    |
+------------------------------------------------------------------+
```

### Mental Model: Folder and File Structure Analogy

```
+------------------------------------------------------------------+
|                         MyProject/                               |
|  +---------------------------+  +---------------------------+    |
|  |         Folder1/          |  |         Folder2/          |    |
|  |  +---------------------+  |  |  +---------------------+  |    |
|  |  |                     |  |  |  |                     |  |    |
|  |  |      First.cs       |  |  |  |      First.cs       |  |    |
|  |  |                     |  |  |  |                     |  |    |
|  |  +---------------------+  |  |  +---------------------+  |    |
|  +---------------------------+  +---------------------------+    |
+------------------------------------------------------------------+
```

### Tree View Comparison

```
+----------------------------------+    +----------------------------------+
|        NAMESPACE CONCEPT         |    |      FOLDER/FILE ANALOGY         |
+----------------------------------+    +----------------------------------+
|                                  |    |                                  |
|  Project/                        |    |  MyProject/                      |
|  ├── NSP1/                       |    |  ├── Folder1/                    |
|  │   └── class First             |    |  │   └── First.cs                |
|  │                               |    |  │                               |
|  └── NSP2/                       |    |  └── Folder2/                    |
|      └── class First             |    |      └── First.cs                |
|                                  |    |                                  |
+----------------------------------+    +----------------------------------+

  NSP1.First  ≠  NSP2.First              Folder1/First.cs ≠ Folder2/First.cs
  (Different namespaces)                 (Different folders)
```

| Namespace Concept | Folder/File Analogy |
|-------------------|---------------------|
| `NSP1.First` | `Folder1/First.cs` |
| `NSP2.First` | `Folder2/First.cs` |
| Different namespaces | Different folders |

**Key Points:**
- Just like you can have files with the **same name in different folders**, you can have classes with the **same name in different namespaces**
- To access a class, you specify the full path: `NamespaceName.ClassName` (like `Folder/FileName`)
- This prevents naming conflicts in large projects with thousands of classes 


- If you want to consume any predefined type then you need to refer to it by prefixing the namespace. That is the reason we are using `System.Console` to refer to `Console` class. Because `Console` class is defined inside the `System` namespace.

## Understanding `System.Console.Clear()` - Namespace, Type, and Method

```
+-----------------------------------------------------------------------+
|                        System.Console.Clear()                         |
+-----------------------------------------------------------------------+
|                                                                       |
|   System          .         Console        .        Clear()           |
|   ------                    -------                 -------           |
|     |                          |                       |              |
|     v                          v                       v              |
| +-----------+            +------------+          +------------+       |
| | NAMESPACE |            |    TYPE    |          |   METHOD   |       |
| +-----------+            +------------+          +------------+       |
| | Container |            |   Class    |          |  Action/   |       |
| | for Types |            | (Console)  |          | Behavior   |       |
| +-----------+            +------------+          +------------+       |
|                                                                       |
+-----------------------------------------------------------------------+
```

### Breakdown:

```
+------------------------------------------------------------------+
|                          System (Namespace)                      |
|  +------------------------------------------------------------+  |
|  |                     Console (Type/Class)                   |  |
|  |  +-------------------------+  +-------------------------+  |  |
|  |  |    Clear() - Method     |  |  WriteLine() - Method   |  |  |
|  |  +-------------------------+  +-------------------------+  |  |
|  |  +-------------------------+  +-------------------------+  |  |
|  |  |    Write() - Method     |  |  ReadLine() - Method    |  |  |
|  |  +-------------------------+  +-------------------------+  |  |
|  +------------------------------------------------------------+  |
+------------------------------------------------------------------+
```

| Component | Name | Role |
|-----------|------|------|
| **Namespace** | `System` | Logical container that groups related types |
| **Type** | `Console` | Class that provides IO operations |
| **Method** | `Clear()` | Action that clears the console screen |

**Syntax Pattern:** `Namespace.Type.Method()`



Note:- Class can be interchanged with Type. Because Class is a type in C#. Similarly Struct is also a type in C#. So, we can say Class is a reference type and Struct is a value type in C#. There are two types in C#. One is user-defined types and another is predefined types. Class and Struct are user-defined types in C#. int, float, Console, String, Array, List, etc., are predefined types in C#. 

