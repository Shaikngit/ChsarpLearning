# Video 4 - Code Types and Compilation

## Key Definitions

### Source Code
Source code is the human-readable code written by programmers using a programming language (like C#, Java, Python). It contains instructions written in a high-level language that humans can understand and modify.

**Example:** A `.cs` file containing C# code is source code.

---

### Machine Code
Machine code (also called native code) is the lowest-level code that the CPU can directly execute. It consists of binary instructions (0s and 1s) specific to a particular processor architecture (x86, ARM, etc.). Machine code is not human-readable.

**Characteristics:**
- Directly executable by the CPU
- Platform/hardware specific
- Extremely fast execution
- Not portable across different architectures

---

### CIL Code (Common Intermediate Language)
CIL (Common Intermediate Language), formerly known as MSIL (Microsoft Intermediate Language), is an intermediate, platform-independent code that .NET languages compile to. It sits between source code and machine code.

**Key Points:**
- Generated when you compile C# source code
- Stored in assemblies (`.exe` or `.dll` files)
- Platform-independent (can run on any system with .NET runtime)
- Converted to machine code at runtime by the JIT (Just-In-Time) compiler

**Compilation Flow:**
```
Source Code (.cs) → [C# Compiler] → CIL Code (.exe/.dll) → [JIT Compiler] → Machine Code
```

---

### Compiler
A compiler is a software program that translates source code written in a high-level programming language into another form of code (typically lower-level code like CIL or machine code).

---

## Procedural Languages vs Object Oriented Languages

### Procedural Languages
Procedural languages follow a **top-down, step-by-step** approach where the program is a sequence of instructions (procedures/functions) that execute one after another.

**Characteristics:**
- Focus on **functions/procedures**
- Data and functions are separate
- Less secure (data is exposed)
- Limited code re-usability

**Examples:** C, COBOL, FORTRAN, Pascal

---

### Object Oriented Languages (OOP)
OOP organizes code around **objects** (which contain both data and methods). It focuses on "what objects do" rather than "how to do it step-by-step".

**Characteristics:**
- Focus on **objects and classes**
- Data and functions are bundled together (Encapsulation)
- More secure (data hiding)
- High code re-usability (Inheritance)

**Examples:** C++, Java, Python, C#, VB.NET, F#

---

### Function Reusability vs Code Reusability (Why C has limited reusability?)

**Question:** C has `printf`, `scanf` etc. that can be reused. So why is C considered to have limited reusability?

**Answer:** There are **two types of reusability**:

| Type | Description | Example |
|------|-------------|---------|
| **Function Reusability** | Reusing individual functions | `printf()`, `scanf()` in C |
| **Code/Object Reusability** | Reusing and **extending** entire code structures | Inheritance in OOP |

**C has Function Reusability:**
- You can call `printf()` multiple times
- You can include header files and use library functions
- But you **cannot extend or modify** existing code without rewriting

**OOP has Code Reusability (through Inheritance):**
- You can create a new class **based on** an existing class
- The new class **inherits** all features of the parent class
- You can **add new features** or **modify existing** behavior without touching original code

**Simple Example:**
```
In C: If you want a modified printf, you must write a completely new function.

In OOP: If you want a modified Car class, you can inherit from Car and just add/change what you need.
        class SportsCar : Car { // Inherits everything from Car, add only new features }
```

**Key Difference:** OOP allows you to **reuse + extend** existing code. C only allows you to **call** existing functions but not extend them.

---

## Object Oriented Programming

- All languages of .NET are Object Oriented i.e., these language's provides Security & Re-usability.

- Examples of Object Oriented Languages: C++, Java, Python and all .NET Language's, so all these languages provide Security & Re-usability.

---

## What is Re-usability?

Re-usability means the compiled code (intermediate code) of one program can be re-used from another program written in the same language.

### Compilation and Re-usability Examples:

**C++ Source Code** → Compiled by C++ Compiler → Object Code → Can be re-used from another C++ Program.

**Java Source Code** → Compiled by Java Compiler → Byte Code → Can be re-used from another Java Program.

**Python Source Code** → Compiled by Python Compiler → Byte Code → Can be re-used from another Python Program.

**C# Source Code** → Compiled by C# Compiler → CIL Code → Can be re-used from another C# Program.(or any .NET Language)

**VB Source Code** → Compiled by VB Compiler → CIL Code → Can be re-used from another VB Program. (or any .NET Language)

**F# Source Code** → Compiled by F# Compiler → CIL Code → Can be re-used from another F# Program. (or any .NET Language)

---

CIL Code generated from any .NET language can be re-used from another .NET language because all .NET languages compile to the same intermediate language (CIL). This is a key feature of the .NET framework that promotes interoperability and code reusability across different programming languages within the .NET ecosystem.

---

- Reusability in C++, Java, Python is limited to the same language only.
- Reusability in .NET languages is across all .NET languages. 

--- 

- If any two languages want to interoperate with each other, they should pass two hurdles 

    1. Both languages should compile to the same intermediate code.
    2. Both languages should not have any mismatch in data types. 
        for eg., int in one language should be equivalent to int in another language.

What is a Platform? 
A platform is an environment in which a piece of software is executed. It can refer to the underlying hardware (like x86, ARM) or the software framework (like .NET, Java Virtual Machine) that provides the necessary services and libraries for running applications. 

its a combination of two things 

    1. Microprocessor Architecture (like x86, ARM)
    2. Operating System (like Windows, Linux, macOS)

```
+------------------------------------------+
|                                          |
|          Operating System                |
|     (Windows, Linux, macOS, etc.)        |
|                                          |
|    +------------------------------+      |
|    |                              |      |
|    |       Microprocessor         |      |
|    |      (x86, ARM, etc.)        |      |
|    |                              |      |
|    +------------------------------+      |
|                                          |
|               Platform                   |
+------------------------------------------+
```

**Platform = Operating System + Microprocessor**

Platform Dependence vs Platform Independence

If a program can run only on a specific platform (combination of OS and hardware), it is called Platform Dependent.

If a program can run on multiple platforms without modification, it is called Platform Independent.

All languages before 1995 were Platform Dependent. because they compiled to Machine code which is specific to a particular microprocessor architecture. 

Java introduced the concept of Platform Independence in 1995 by compiling source code to Bytecode, which can run on any platform with a Java Virtual Machine (JVM).

Java, C# , Python are Platform Independent languages because they compile to intermediate code (Bytecode for Java, CIL for C#, Bytecode for Python) which can run on any platform with the respective runtime environment (JVM for Java, .NET runtime for C#, Python interpreter for Python).

---


