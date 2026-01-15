### How to use Visual Studio IDE to program in C# 

```
┌─────────────────────────────────────────────────────────────┐
│                      SOLUTION (.sln)                        │
│         (Container for one or more projects)                │
│                                                             │
│  ┌───────────────────────────────────────────────────────┐  │
│  │                  PROJECT (.csproj)                    │  │
│  │           (Compiles into .exe or .dll)                │  │
│  │                                                       │  │
│  │  ┌─────────────────────────────────────────────────┐  │  │
│  │  │              NAMESPACE                          │  │  │
│  │  │      (Logical grouping of classes)              │  │  │
│  │  │                                                 │  │  │
│  │  │  ┌───────────────────────────────────────────┐  │  │  │
│  │  │  │            CLASS (.cs file)               │  │  │  │
│  │  │  │       (Blueprint for objects)             │  │  │  │
│  │  │  │                                           │  │  │  │
│  │  │  │   • Fields (variables)                    │  │  │  │
│  │  │  │   • Properties                            │  │  │  │
│  │  │  │   • Methods (functions)                   │  │  │  │
│  │  │  │   • Main() → Entry point                  │  │  │  │
│  │  │  └───────────────────────────────────────────┘  │  │  │
│  │  │                                                 │  │  │
│  │  │  ┌───────────────────────────────────────────┐  │  │  │
│  │  │  │         Another CLASS (.cs file)          │  │  │  │
│  │  │  └───────────────────────────────────────────┘  │  │  │
│  │  │                                                 │  │  │
│  │  └─────────────────────────────────────────────────┘  │  │
│  │                                                       │  │
│  └───────────────────────────────────────────────────────┘  │
│                                                             │
│  ┌───────────────────────────────────────────────────────┐  │
│  │              Another PROJECT (.csproj)                │  │
│  └───────────────────────────────────────────────────────┘  │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

### Hierarchy Summary

| Level | File Extension | Purpose |
|-------|----------------|---------|
| **Solution** | `.sln` | Groups related projects |
| **Project** | `.csproj` | Builds into executable or library |
| **Class** | `.cs` | Contains code (fields, methods, etc.) |

### Quick Example

```
MySolution.sln
    └── MyProject.csproj
                ├── Program.cs      ← Contains Main()
                ├── Calculator.cs
                └── Helper.cs
```

### Key Points
- **Solution** = Folder/container for projects
- **Project** = Compiles to one output (`.exe` or `.dll`)
- **Class** = Code unit with data + behavior
- One project must have `Main()` method as entry point


- Create a new project in Visual Studio using "Console App" template 
- Enter Project name and Location , Solution name can be ignored if you are creating single project
- Framework selection can be left as default (.NET 8.0 or latest version available)
- Click Create button to create project
- Visual Studio will create default Program.cs file with Main method

When you select .net 5.0 and option Do not use top-level statements selected, Visual Studio will create Program.cs file with Main method inside a class named Program as shown below

```csharp
using System;
namespace MyFirstApp
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello, World!");
        }
    }
}
```
- You can run the program by clicking on Start button or pressing Ctrl+ F5 key (This will run program without debugging, Compile and Execute)

- Namespace is logical grouping of classes. By default Visual Studio will create Namespace with project name. You can change namespace name as per your requirement. For example System is a namespace , just like that you are creating your own namespace. And Classes are created inside namespaces. In the above example Program is a class inside MyFirstApp namespace. 

- Internal is access modifier which means this class is accessible only within this assembly (project).

    Internal classes are not accessible from other assemblies. If you want to access this class from other assemblies (projects) then you need to change access modifier to public. 

    Public classes are accessible from other assemblies. 

    Private classes are not accessible outside the containing class. 

    By default, if no access modifier is specified for a class, it is considered internal. 

- Default Scope for members(fields, variables, methods, properties) of a class is private. For example if you create a field or method inside a class without any access modifier, it will be private by default and accessible only within that class. 

- Default scope for a type (class, struct, interface, enum, delegate) is internal. For example if you create a class without any access modifier, it will be internal by default and accessible only within that assembly (project).

- You can create multiple classes inside a project. Each class should be in its own .cs file. For example you can create Calculator.cs file with Calculator class inside it.

```csharp
using System;
namespace MyFirstApp
{
    public class Calculator
    {
        public int Add(int a, int b)
        {
            return a + b;
        }
    }
}
```
- You can create objects of Calculator class inside Main method of Program class and call Add method as shown below

```csharp
using System;
namespace MyFirstApp
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Calculator calc = new Calculator();
            int result = calc.Add(5, 10);
            Console.WriteLine("Addition Result: " + result);
        }
    }
}
```
- Save all files and run the program again. You should see output as Addition Result: 15
- You can add more classes as per your requirement. Each class should be in its own .cs file.
- This is how you can use Visual Studio IDE to create and run C# programs using classes
---

### Mental Map: Visual Studio C# Project Structure

```
                    ┌─────────────────────────────────────┐
                    │         VISUAL STUDIO IDE           │
                    └─────────────────┬───────────────────┘
                                      │
                                      ▼
                    ┌─────────────────────────────────────┐
                    │        SOLUTION (.sln)              │
                    │   "The Big Container/Folder"        │
                    └─────────────────┬───────────────────┘
                                      │
                    ┌─────────────────┴─────────────────┐
                    ▼                                   ▼
        ┌───────────────────┐               ┌───────────────────┐
        │ PROJECT (.csproj) │               │ PROJECT (.csproj) │
        │  → .exe or .dll   │               │  → .exe or .dll   │
        └─────────┬─────────┘               └─────────┬─────────┘
                  │                                   │
                  ▼                                   │
        ┌───────────────────┐                         │
        │ NAMESPACE         │                         │
        │ (Logical Group)   │                         │
        └─────────┬─────────┘                         │
                  │                                   │
        ┌─────────┴─────────┐                         │
        ▼                   ▼                         │
┌─────────────┐     ┌─────────────┐                   │
│ CLASS (.cs) │     │ CLASS (.cs) │                   │
│ Program.cs  │     │ Calculator  │◄──────────────────┘
│ ┌─────────┐ │     │ (public)    │  ✓ Accessible if public
│ │ Main()  │ │     │ (internal)  │  ✗ NOT accessible if internal
│ └─────────┘ │     └─────────────┘
└─────────────┘


        ACCESS MODIFIERS CHEAT SHEET
        ─────────────────────────────
        
        TYPES (class, struct, etc.)
        ┌─────────────────────────────┐
        │ Default = internal          │
        │ public  = everywhere        │
        │ internal= same project only │
        └─────────────────────────────┘
        
        MEMBERS (fields, methods)
        ┌─────────────────────────────┐
        │ Default = private           │
        │ public  = everywhere        │
        │ private = same class only   │
        │ internal= same project only │
        └─────────────────────────────┘

        
        CROSS-PROJECT ACCESS
        ─────────────────────
        ┌─────────────────────────────────────────────┐
        │ To access Calculator from another project:  │
        │  1. Add project reference                   │
        │  2. Calculator class must be PUBLIC         │
        │  3. Methods must also be PUBLIC             │
        │                                             │
        │ internal = same project only (default)      │
        │ public   = accessible from other projects   │
        └─────────────────────────────────────────────┘


        HOW TO ACCESS (Examples)
        ────────────────────────
        
        Same Project, Same Namespace:
        ┌─────────────────────────────────────────────┐
        │ Calculator calc = new Calculator();         │
        │ calc.Add(5, 10);                            │
        └─────────────────────────────────────────────┘
        
        Same Project, Different Namespace:
        ┌─────────────────────────────────────────────┐
        │ using OtherNamespace;                       │
        │ // OR                                       │
        │ OtherNamespace.Calculator calc = new();     │
        └─────────────────────────────────────────────┘
        
        Different Project (public class required):
        ┌─────────────────────────────────────────────┐
        │ Step 1: Right-click project → Add →         │
        │         Project Reference → Select project  │
        │                                             │
        │ Step 2: Add using statement:                │
        │         using MyFirstApp;                   │
        │                                             │
        │ Step 3: Use the class:                      │
        │         Calculator calc = new Calculator(); │
        └─────────────────────────────────────────────┘


        WORKFLOW REMINDER
        ─────────────────
        
        [New Project] → Console App → Name → Create
                              │
                              ▼
                    Program.cs (auto-created)
                              │
                              ▼
                    [Ctrl+F5] = Run without debug or F5 = Run with debug 
```

---

### Solution Explorer in Visual Studio IDE

#### Creating a New Class

1. **Right-click** on the project name in Solution Explorer
2. Select **Add** → **Class**
3. Enter the class name (e.g., `Calculator.cs`)
4. Click **Add**

> This creates a new `.cs` file with the specified class inside your project.

---

#### Handling Multiple Main Methods

If your project contains **two or more classes with `Main()` methods**, the compiler won't know which one to use as the entry point, resulting in a build error.

**To resolve this:**

1. **Right-click** on the project name in Solution Explorer
2. Select **Properties**
3. Go to the **Application** tab
4. In the **Startup object** dropdown, select the class containing the desired `Main()` method
5. **Save** the project

```
┌─────────────────────────────────────────────────────────┐
│  Project Properties → Application Tab                   │
│  ─────────────────────────────────────────────────────  │
│                                                         │
│  Startup object:  [ Program ▼ ]                         │
│                     ├── Program                         │
│                     └── AnotherClass                    │
│                                                         │
│  ✓ Select the class with your desired Main() method    │
└─────────────────────────────────────────────────────────┘
```

Now when you run the program, Visual Studio will use the specified `Main()` method as the entry point.

### How program looks like in anything .net 6.0 and above with top-level statements enabled 

When you select .net 6.0 and above and use top-level statements, Visual Studio will create Program.cs file without Main method inside a class as shown below

```csharp

Console.WriteLine("Hello, World!");

```
- You can run the program by clicking on Start button or pressing Ctrl+ F5 key (This will run program without debugging, Compile and Execute)
- This is how you can use Visual Studio IDE to create and run C# programs using classes
---

### What are Top-Level Statements in C#?

**Top-level statements** is a feature introduced in **C# 9.0** that allows you to write simple programs without explicitly defining a `Main` method or a containing class. This feature simplifies syntax for small programs, scripts, and educational examples.

```
┌─────────────────────────────────────────────────────────────┐
│  TRADITIONAL (Before C# 9.0)    │  TOP-LEVEL (C# 9.0+)      │
│  ───────────────────────────────│──────────────────────────  │
│  using System;                  │  Console.WriteLine("Hi"); │
│  class Program                  │                           │
│  {                              │  // That's it!            │
│      static void Main()         │                           │
│      {                          │                           │
│          Console.WriteLine("Hi");│                          │
│      }                          │                           │
│  }                              │                           │
└─────────────────────────────────────────────────────────────┘
```

With top-level statements, you write code directly in the global scope. The C# compiler automatically generates the necessary boilerplate (`Main` method and class) behind the scenes.

#### Important Limitations

| Scenario | Top-Level Statements |
|----------|---------------------|
| Single entry point | ✅ Works perfectly |
| Multiple `Main` methods | ❌ Must disable |

> **Note:** If your project uses top-level statements and you create another class with a `Main` method, you'll get a compile-time error:  
> `'Program' already contains a definition for 'Main'`

#### When to Disable Top-Level Statements

- When you need **multiple `Main` methods** in your project
- When you want to **select a specific startup object**
- When working on **larger, more structured applications**

To disable, create a new project with the **"Do not use top-level statements"** option checked, or manually add a `Main` method inside a class structure.


#### Global Imports 
In .NET 6.0 and above, you can define global using directives that apply to all files in a project. This helps reduce redundancy and keeps your code cleaner.
To create a global using directive, you can add a file named `GlobalUsings.cs` (or any name you prefer) to your project and include the `global using` statements there. For example:

```csharp
global using System;
global using System.Collections.Generic;
global using System.Linq;
global using System.Threading.Tasks;
```

These namespaces become available throughout the entire project without individual `using` statements.




# 📌 `.csproj` File – Quick Summary (Notes)

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>net8.0</TargetFramework>
    <ImplicitUsings>enable</ImplicitUsings>
    <Nullable>enable</Nullable>
  </PropertyGroup>

</Project>
```

## Purpose
- Defines **how a .NET project is built and run**
- Used by **MSBuild** and the **.NET SDK**

---

## Core Elements Explained

### `<Project Sdk="Microsoft.NET.Sdk">`
- Uses the **modern .NET SDK**
- Enables simplified project files and `dotnet` CLI commands

---

### `<PropertyGroup>`
- Container for **project-wide configuration settings**

---

### `<OutputType>Exe</OutputType>`
- Builds a **console executable**
- Other options:
  - `Library` → DLL
  - `WinExe` → Windows GUI app

---

### `<TargetFramework>net8.0</TargetFramework>`
- Targets **.NET 8 (LTS)**
- Determines available APIs, runtime, and language features

---

### `<ImplicitUsings>enable</ImplicitUsings>`
- Automatically adds common `using` namespaces
- Reduces boilerplate code

---

### `<Nullable>enable</Nullable>`
- Enables **nullable reference types**
- Helps catch null-related bugs at compile time
- Improves code safety and reliability

---

## Key Takeaway
✔ Minimal, modern, and recommended `.csproj` setup  
✔ Suitable for learning, production, and long-term support

