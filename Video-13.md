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
Instead of using `System.Console.WriteLine`, we can use `using System;` at the top of the program and then directly call `Console.WriteLine` as shown below.

```csharp
using System;

class FirstProgram

{
static void Main()

 {
   Console.Clear();
   Console.WriteLine("My First C# program using notepad.");
 }

}
```
using `using` directive helps to reduce the length of the code and makes it more readable.

This is called importing a namespace in C#. Here, we are importing the `System` namespace which contains the `Console` class.

## Syntax for `using` Directive

```csharp
using <namespace>;
```

### Examples:

```csharp
using System;                      // Core types (Console, String, etc.)
using System.Collections.Generic;  // Collections (List, Dictionary, etc.)
using System.Linq;                 // LINQ query operations
using System.IO;                   // File operations
using System.Net.Http;             // HTTP client
```

### Key Points:
- The `using` directive must be placed at the **top of the file**, before any class definitions
- It allows you to use types from the specified namespace without fully qualifying them
- Multiple `using` directives can be declared

What is a directive?
A directive is a instruction to the compiler to include certain namespaces or libraries in the program. 

You can import classes, methods, properties, etc. from the imported namespace and use them in your program without fully qualifying their names. 

```csharp
using static System.Console;  // Importing static members of Console class

class FirstProgram

{
static void Main()

 {
   Clear();
   WriteLine("My First C# program using notepad.");
 }

}
```

## Syntax for `using static` Directive

```csharp
using <namespace.type>;
```
### Example:

```csharp
using static System.Math;  // Importing static members of Math class
class MathExample

{                               
static void Main()

 {
   double result = Sqrt(16); // No need to use Math.Sqrt
   Console.WriteLine("Square root of 16 is: " + result);
 }

}
```
### Key Points:
- The `using static` directive allows you to import static members (methods, properties, fields) of a type
- It helps to reduce code verbosity by allowing direct access to static members without qualifying them with the type name

drawbacks of using `using static` directive:
- you are restricted to only static members of the specified type.
- you are restricted to only one type per `using static` directive. 

Note:- If there are multiple namespaces containing a type with the same name, then its not possible to consume those types by importing the namespace and in such cases its mandatory to refer to each type with its fully qualified name.

e.g

```csharp   
using System.Text;
using MyCustomNamespace.Text; // Both namespaces contain a class named 'StringBuilder'
class Example
{
    static void Main()
    {
        StringBuilder sb1 = new StringBuilder(); // Error: Ambiguous reference
        MyCustomNamespace.Text.StringBuilder sb2 = new MyCustomNamespace.Text.StringBuilder(); // Valid
    }
}
```

## Datatypes in C#

C# is a strongly typed language, which means that every variable and constant has a specific data type. The data type determines the size and layout of the variable's memory, the range of values that can be stored, and the operations that can be performed on it.

### C# Data Types Reference Table

| C# Types | CIL Types | Size/Capacity | Default Value |
|----------|-----------|---------------|---------------|
| **Integer Types** ||||
| byte | System.Byte | 1 byte (0 - 255) | 0 |
| short | System.Int16 | 2 bytes (-2^15 to 2^15 - 1) | 0 |
| int | System.Int32 | 4 bytes (-2^31 to 2^31 - 1) | 0 |
| long | System.Int64 | 8 bytes (-2^63 to 2^63 - 1) | 0 |
| sbyte | System.SByte | 1 byte (-128 to 127) | 0 |
| ushort | System.UInt16 | 2 bytes (0 to 2^16 - 1) | 0 |
| uint | System.UInt32 | 4 bytes (0 to 2^32 - 1) | 0 |
| ulong | System.UInt64 | 8 bytes (0 to 2^64 - 1) | 0 |
| **Decimal Types** ||||
| float | System.Single | 4 bytes | 0 |
| double | System.Double | 8 bytes | 0 |
| decimal | System.Decimal | 16 bytes | 0 |
| **Boolean Type** ||||
| bool | System.Boolean | 1 byte | False |
| **DateTime Type** ||||
| DateTime | System.DateTime | 8 bytes | 01/01/0001 00:00:00 |
| **Unique Identifier Type** ||||
| Guid | System.Guid | 32 bytes | 00000000-0000-0000-0000-000000000000 |
| **Character Types** ||||
| char | System.Char | 2 bytes | \0 |
| string | System.String | | Null |
| **Base Type** ||||
| object | System.Object | | Null |

### Common Data Types in C#:
- `int`: Represents a 32-bit signed integer. Example: `int age = 25;`
- `float`: Represents a single-precision 32-bit floating point number. Example: `float pi = 3.14f;`
- `double`: Represents a double-precision 64-bit floating point number. Example: `double distance = 123.45;`

ASCII Representation:

Good Video on this refer [ASCII Representation](https://www.youtube.com/watch?v=GMF2Z1EZHXk&t=64s)

What is Base Type?
In C#, `object` is the base type from which all other types derive. It is the root of the type hierarchy in C#. Every type in C# (both value types and reference types) ultimately inherits from `object`. This means that any variable of any type can be assigned to a variable of type `object`.

CIL Types: Just like int is struct in C, in the same way System.Int32 is also a struct in CIL (Common Intermediate Language) which represents a 32-bit signed integer. This is predefined type under namespace System.

All Datatypes are structs except string and object, the other way to identify if it is struct or not, all the datatypes which has fixed size are structs except string and object. The datatypes which doesn't have fixed size are classes. 

