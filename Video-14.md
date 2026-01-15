Datatypes 

- All above types are known as `primitive` or `built-in` or `simple` or `scalar` or `predefined` data types. They are defined under the libraries of our language which can be consumed anywhere 

- All `C# types` after compilation of source code gets converted into `CIL types` and `CIL Format` these types are either `classes` or `structures` defined under the `System` namespace. `String` and `Object` types are `classes` whereas rest of the other `15` types are `structures`

- `short`, `int`, `long` and `sbyte` types can store **signed** integer (Positive or Negative) values whereas `ushort`, `uint`, `ulong` and `byte` types can store **un-signed** integer (Pure Positive) values only.

- `Guid` is a type used for storing **Unique Identifier** values that are loaded from SQL Server Database, which is a 32-byte alpha-numeric string holding a **Global Unique Identifier** value and it will be in the following format: `00000000-0000-0000-0000-000000000000`.

- The size of `char` type has been increased to 2 bytes for giving support to **Unicode** characters i.e., characters of languages other than English.

- We are aware that every English language character has a numeric value representation known as **ASCII**; characters of languages other than English also have that numeric value representation and we call it as **Unicode**.

```csharp
char ch = 'A'; // => ASCII (65) => Binary (1000001)
char ch = 'अ'; // => Unicode (2309) => Binary (100100000101)
```

## Difference between `int i = 6` and `char ch = '6'`

| Aspect | `int i = 6` | `char ch = '6'` |
|--------|-------------|-----------------|
| **Type** | Integer (numeric value) | Character (text symbol) |
| **Size** | 4 bytes (32 bits) | 2 bytes (16 bits) |
| **Value stored** | Numeric 6 | ASCII/Unicode code for '6' which is **54** |

### Memory Representation

```
int i = 6;
┌────────────────────────────────────────────────────┐
│  Memory (4 bytes / 32 bits)                        │
│  00000000 00000000 00000000 00000110               │
│                              ↑                     │
│                         Binary for 6              │
└────────────────────────────────────────────────────┘

char ch = '6';
┌────────────────────────────┐
│  Memory (2 bytes / 16 bits) │
│  00000000 00110110          │
│           ↑                 │
│      Binary for 54 (ASCII/Unicode of '6')         │
└────────────────────────────┘
```

### Key Points

1. **`int i = 6`** - Stores the **actual numeric value 6** in binary
   - Binary: `110` (padded to 32 bits)
   - Can perform arithmetic: `i + 1 = 7`

2. **`char ch = '6'`** - Stores the **character code** for the symbol '6'
   - ASCII/Unicode value: **54**
   - Binary of 54: `110110` (padded to 16 bits)
   - It's a **symbol**, not the number itself

### Quick Demonstration in C#

```csharp
int i = 6;
char ch = '6';

Console.WriteLine(i);              // Output: 6
Console.WriteLine((int)ch);        // Output: 54 (ASCII value)
Console.WriteLine(i + 1);          // Output: 7 (arithmetic)
Console.WriteLine(ch + 1);         // Output: 55 (next ASCII code, which is '7')
Console.WriteLine((char)(ch + 1)); // Output: 7 (the character '7')
```

### Summary Table

| Variable | Stored Value | Binary Representation |
|----------|--------------|----------------------|
| `int i = 6` | 6 | `00000000 00000000 00000000 00000110` |
| `char ch = '6'` | 54 | `00000000 00110110` |

The character `'6'` looks like the number 6 visually, but internally it's stored as **54** (its ASCII/Unicode code point), not as 6!

## Field vs Variable (Scope)

A **Field** is declared at the class level and has global scope within the class, whereas a **Variable** is declared inside a method and has local scope only within that method.

```csharp
class Test
{
    int x = 100;            // Field (Global in scope)
    
    static void Main()
    {
        int y = 50;         // Variable (Local in scope)
    }
}
```

| Term | Declaration Location | Scope |
|------|---------------------|-------|
| **Field** | Inside class, outside methods | Global - accessible throughout the class |
| **Variable** | Inside a method/block | Local - accessible only within that method/block |

> **Note:** Only **Fields** can have default values in C#. If you don't initialize a field, it automatically gets a default value (e.g., `0` for numeric types, `null` for reference types, `false` for bool). **Variables** (local variables declared inside methods) do **not** have default values — they must be explicitly initialized before use, otherwise the compiler will throw an error.

### Syntax for declaring Field and Variable:

    [<modifiers>] [const] [readonly]<type> <var>[=default>][,....n];

### Explanation of Each Part

| Part | Description | Required? |
|------|-------------|-----------|
| `<modifiers>` | Access modifiers like `public`, `private`, `protected`, `internal`, `static` | Optional |
| `const` | Makes the value constant (compile-time, cannot be changed) | Optional |
| `readonly` | Makes the field read-only (can only be assigned at declaration or in constructor) | Optional |
| `<type>` | Data type like `int`, `string`, `bool`, `double`, etc. | **Required** |
| `<var>` | Name of the variable/field | **Required** |
| `=<default>` | Initial value assignment | Optional |
| `[,....n]` | Multiple variables of the same type can be declared | Optional |

### Examples

```csharp
// Simple variable declaration
int age;

// Variable with initialization
int count = 10;

// Multiple variables of same type
int x = 5, y = 10, z = 15;

// Field with access modifier
public string name = "John";

// Private field (default for class members)
private double salary = 50000.00;

// Static field (shared across all instances)
static int totalCount = 0;

// Constant field (value fixed at compile-time)
const double PI = 3.14159;

// Readonly field (assigned once, at declaration or constructor)
readonly int maxLimit = 100;

// Combining modifiers
public static readonly string AppName = "MyApp";
private const int MaxRetries = 3;
```

### Key Differences: `const` vs `readonly`

| Aspect | `const` | `readonly` |
|--------|---------|------------|
| **Assignment** | At declaration only | At declaration or in constructor |
| **Compile-time** | Yes (value embedded) | No (evaluated at runtime) |
| **Static by default** | Yes (implicitly static) | No (instance-level unless marked `static`) |

```csharp
class Example
{
    const int MaxValue = 100;           // Must be initialized here
    readonly int minValue;              // Can be initialized in constructor
    
    public Example()
    {
        minValue = 10;                  // Valid for readonly
        // MaxValue = 50;               // ❌ Error: cannot modify const
    }
}
```

## 🧠 Easy Way to Remember Modifiers

### The Full Formula

```
[access] [modifier] [type] [name] = [value];
```

Example: `public static int count = 0;`

---

### Think of it as **2 Questions** 🤔

| Question | Keywords | Simple Answer |
|----------|----------|---------------|
| **WHO can see it?** | `public`, `private`, `protected`, `internal` | Access level |
| **HOW does it behave?** | `static`, `const`, `readonly` | Behavior |

---

### Question 1: WHO Can See It? (Access Modifiers) 🔐

```
┌─────────────────────────────────────────────────────┐
│  private  ──► Only ME (same class)         🔒      │
│  public   ──► EVERYONE can see             🌍      │
│  protected──► Me + My CHILDREN (inherited) 👨‍👧     │
│  internal ──► Only my PROJECT/Assembly     🏢      │
└─────────────────────────────────────────────────────┘
```

**Memory Trick:**
- **Private** = Your **private** diary (only you can read)
- **Public** = **Public** park (everyone can enter)
- **Protected** = Family secret (only kids inherit it)

**Default Rule:** If you don't write anything, it's `private` inside a class!

---

### Question 2: HOW Does It Behave? (Other Modifiers) ⚙️

| Keyword | Meaning | Memory Trick |
|---------|---------|--------------|
| `static` | Belongs to CLASS, not object; no instance needed to access | "**Static** = **Shared** by all, no object required" |
| `const` | NEVER changes, set at compile time | "**Const**ant = **Carved in stone**" |
| `readonly` | Set once (in constructor), then locked | "**Read** only, no **write**" |

```csharp
class Example
{
    const double PI = 3.14159;        // Carved in stone forever
    readonly int createdYear;          // Set once in constructor
    static int totalCount = 0;         // Shared by ALL objects
    
    public Example()
    {
        createdYear = 2026;            // OK - set in constructor
        totalCount++;                  // Every new object adds to SAME counter
    }
}
```

---

### The "Real World" Cheat Sheet 🎯

| Scenario | Use This |
|----------|----------|
| Hide from outside | `private` (default, safest) |
| Let everyone use | `public` |
| Value NEVER changes (like PI) | `const` |
| Set once, read many | `readonly` |
| Same value for ALL objects | `static` |
| Utility method (no object needed) | `static` |

---

### Order of Keywords 📋

```csharp
// Correct order:
public static readonly int MaxSize = 100;
│       │      │        │    │       │
│       │      │        │    │       └── Value
│       │      │        │    └── Name
│       │      │        └── Type
│       │      └── Behavior modifier
│       └── Behavior modifier  
└── Access modifier (WHO)
```

---

### 90% of the Time, You'll Use Just This:

```csharp
private int x = 10;              // Hidden variable
public int Y { get; set; }       // Exposed property
public static int Count = 0;     // Shared counter
public const double PI = 3.14;   // Never changes
```

---

### ✨ One-Line Summary

> **WHO sees it?** (`public`/`private`) + **HOW it behaves?** (`static`/`const`/`readonly`) + **type** + **name**

Example demo program combining all concepts:

```csharp

using System;

class TypesDemo
{
  static int i; 
  static void Main()
    {
        int j= 1;
        Console.WriteLine("Value of i: " + i); // Error: Use of unassigned local variable 'i' , because i is a field and needs an instance to access Thats why making static
        Console.WriteLine("Type Value of i: " + i.GetType()); // Output: System.Int32
        
        Console.WriteLine("Value of j: " + j); // Error: Use of unassigned local variable 'j' , because j is a variable and needs to be initialized before use 
        Console.WriteLine("Type Value of j: " + j.GetType()); // Output: System.Int32

        //GetType() method is used to get the type of the variable at runtime

        float f = 5.5f; // f is suffix for float datatype , by default decimal values are considered as double in C# hence if you want to store decimal values in float datatype we need to use f suffix 

        //float f = 5.5; // Error: Cannot implicitly convert type 'double' to 'float'. An explicit conversion exists (are you missing a cast?)

        Console.WriteLine("Value of f: " + f);
        Console.WriteLine("Type Value of f: " + f.GetType()); // Output: System.Single

        double d = 9.99; // double datatype can hold decimal values by default
        Console.WriteLine("Value of d: " + d);
        Console.WriteLine("Type Value of d: " + d.GetType()); // Output: System.Double
        
        decimal dec = 19.99m; // m is suffix for decimal datatype , by default decimal values are considered as double in C# hence if you want to store decimal values in decimal datatype we need to use m suffix

        //decimal dec2 = 19.99; // Error: Cannot implicitly convert type 'double' to 'decimal'. An explicit conversion exists (are you missing a cast?)
        Console.WriteLine("Value of dec: " + dec);
        Console.WriteLine("Type Value of dec: " + dec.GetType()); // Output:

        
    }

}

Value of i: 0
Type Value of i: System.Int32
Value of j: 1
Type Value of j: System.Int32
Value of f: 5.5
Type Value of f: System.Single      
Value of d: 9.99
Type Value of d: System.Double
Value of dec: 19.99
Type Value of dec: System.Decimal
```

### Value Types vs Reference Types

First lets understand Stack and Heap memory concepts

check this video very good explanation: [Stack vs Heap Memory](https://www.youtube.com/watch?v=_8-ht2AKyH4)

stack memory - fixed memory length
heap memory - dynamic memory length

int, float, double, char, bool etc.. are value types and they are stored in stack memory

string, object, arrays, class objects etc.. are reference types and they are stored in heap memory

### Stack and Heap Memory - ASCII Diagram

```
    STACK MEMORY                              HEAP MEMORY
    (Fixed Size)                              (Dynamic Size)
┌─────────────────────┐                 ┌─────────────────────────────┐
│                     │                 │                             │
│  s = 0x7F2A ────────┼────────────────►│  "Hello"                    │
│  (reference/address)│                 │  (String object at 0x7F2A) │
├─────────────────────┤                 │                             │
│                     │                 │                             │
│  d = 34.56          │                 │                             │
│  (double - 8 bytes) │                 │                             │
├─────────────────────┤                 │                             │
│                     │                 │                             │
│  ch = 'A'           │                 │                             │
│  (char - 2 bytes)   │                 │                             │
├─────────────────────┤                 │                             │
│                     │                 │                             │
│  i = 100            │                 │                             │
│  (int - 4 bytes)    │                 │                             │
└─────────────────────┘                 └─────────────────────────────┘

     VALUE TYPES                              REFERENCE TYPES
     (stored directly)                        (stored here, accessed
                                               via address/pointer)
```

### Key Concepts

| **Stack** | **Heap** |
|-----------|----------|
| Stores **value types** (int, double, char, bool, struct) | Stores **reference types** (string, arrays, objects, classes) |
| Fixed size, fast access | Dynamic size, slower access |
| Memory auto-released when scope ends | Managed by **Garbage Collector** |
| LIFO (Last In, First Out) | No specific order |

### How It Works

```
Code:
    int i = 100;        // Value stored directly in Stack
    char ch = 'A';      // Value stored directly in Stack  
    double d = 34.56;   // Value stored directly in Stack
    string s = "Hello"; // Address stored in Stack, actual data in Heap

Memory Flow:
    
    Stack Variable 's'          Heap Memory
    ┌──────────────┐           ┌─────────────┐
    │ Address:     │           │             │
    │ 0x7F2A   ────┼──────────►│  H e l l o  │
    └──────────────┘           └─────────────┘
         │                            │
         └── Only holds              └── Actual string
             the reference               content lives here
```

### Why This Matters

1. **Value types** → Copied when assigned (independent copies)
2. **Reference types** → Only address copied (both variables point to same data)

```csharp
int a = 10;
int b = a;       // b gets its OWN copy of 10

string s1 = "Hello";
string s2 = s1;  // s2 points to SAME "Hello" in heap
```

Note:- Class objects are reference types and they are stored in heap memory.
Struct objects are value types and they are stored in stack memory.
