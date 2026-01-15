# Video-7: Running .NET Applications

## How to Run a .NET Application on a Machine?

### .NET Languages

A .NET application can be developed using any of the .NET languages:

| Language | Description |
|----------|-------------|
| **C#** | Most popular, general-purpose |
| **F#** | Functional-first programming |
| **VB.NET** | Visual Basic for .NET |
| **IronPython** | Python implementation for .NET |
| **ML.NET** | Machine Learning framework |

### Compilation Process

All these languages generate **CIL (Common Intermediate Language) Code** after compilation of source code.

```
C# Source Code      ─┐
F# Source Code      ─┤
VB.NET Source Code  ─┼──→ [Language Compiler] ──→ CIL Code (.dll / .exe)
IronPython Code     ─┤
ML.NET Code         ─┘
```

### Key Point

> Regardless of which .NET language you use, the compiled output is always **CIL Code** — this is what makes .NET language-interoperable.

---

## Compilation Flow: Different Languages Comparison

### C++ (Native Compilation)
```
C++ Source Code → Compiled by C++ Compiler → Machine Code
```
> **Direct compilation** — No intermediate step, platform-specific binary.

### Java (JVM-based)
```
Java Source Code → Compiled by Java Compiler → Byte Code → JVM → Machine Code
```
> Uses **JVM (Java Virtual Machine)** as runtime to convert byte code to machine code.

### Python (Interpreted with PVM)
```
Python Source Code → Compiled by Python Compiler → Byte Code → PVM → Machine Code
```
> Uses **PVM (Python Virtual Machine)** to execute byte code.

### .NET (CLR-based)
```
.NET Lang's Source Code → Compiled by Language Compiler → CIL Code → CLR → Machine Code
```
> Uses **CLR (Common Language Runtime)** to convert CIL code to machine code.

### Summary Table

| Language | Compiler Output | Runtime | Final Output |
|----------|-----------------|---------|--------------|
| **C++** | Machine Code | None (native) | Machine Code |
| **Java** | Byte Code | JVM | Machine Code |
| **Python** | Byte Code | PVM | Machine Code |
| **.NET** | CIL Code | CLR | Machine Code |

To run dotnet application client has to install .Net runtime on their machine. 
To run dotnet application client has to install .Net runtime on their machine. 

![.NET Runtime](../attachments/dotnetflow.png)

For Developers: They have to install .Net SDK (Software Development Kit) on their machine to develop and run .Net applications. runtime is already included in the SDK.

For Users/Clients: They have to install .Net Runtime on their machine to run .Net applications. 

---

## What is .NET Runtime?

**Ans:** It is a software required for execution of a .NET Application on any machine. This software will mask the functionalities of an OS and run's .NET Application's under it's control.

### Why Does .NET Use Runtime Instead of Direct OS Execution?

Unlike languages like **C/C++** which convert source code directly to machine code that runs under the OS, languages like **C#** generate **CIL code** which is then converted to machine code inside the **Runtime**. This means .NET applications don't run directly under the OS — they run under the **.NET Runtime**.

#### Advantages of Running Under .NET Runtime

| Advantage | Description |
|-----------|-------------|
| **Portability** | Write once, run anywhere — CIL code can execute on any platform with the appropriate .NET Runtime (Windows, Linux, macOS) |
| **Security** | Runtime provides a managed execution environment with features like code access security, type safety verification, and memory safety |
| **Automatic Memory Management** | Garbage Collection automatically manages memory allocation and deallocation, preventing memory leaks and reducing manual memory management errors |

> The Runtime acts as an **abstraction layer** between your application and the operating system, providing consistent behavior across different platforms and adding security guarantees that native code execution cannot provide.

---

