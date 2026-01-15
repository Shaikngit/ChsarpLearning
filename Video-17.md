# Video-17: Jump Statements in C#

Jump statements **transfer control** to another part of the program, breaking the normal sequential flow.

| Statement | Purpose | Use Case |
|-----------|---------|----------|
| `break` | Exits the **nearest** loop or switch | Stop a loop early when condition is met |
| `continue` | Skips **current iteration**, moves to next | Skip specific items in a loop |
| `return` | Exits the **method** and optionally returns a value | End function execution |
| `goto` | Jumps to a **labeled statement** | Rarely used; can make code hard to read |
| `throw` | Transfers control to **exception handler** | Raise an error condition |

## Quick Examples

```csharp
// break - exits loop entirely
for (int i = 0; i < 10; i++)
{
    if (i == 5) break;    // Loop stops at 5
    Console.WriteLine(i); // Prints 0,1,2,3,4
}

// continue - skips to next iteration
for (int i = 0; i < 5; i++)
{
    if (i == 2) continue; // Skips 2
    Console.WriteLine(i); // Prints 0,1,3,4
}

// return - exits method
int Add(int a, int b)
{
    return a + b;  // Exits and returns value
}
```

## Key Difference: `break` vs `continue`

| `break` | `continue` |
|---------|------------|
| **Exits** the entire loop | **Skips** current iteration only |
| No more iterations run | Loop continues with next iteration |

> **Tip:** Avoid `goto` in modern code—use structured loops and methods instead.

---

# Arrays in C#

## What is an Array?

An **array** is a data structure that stores a **fixed-size collection of elements of the same data type** in contiguous memory locations. Arrays allow you to store multiple values in a single variable, accessed using an **index** (starting from 0).

**Key Characteristics:**
- Fixed size (determined at creation)
- Elements are of the same type
- Zero-based indexing
- Stored in contiguous memory

## Array Declaration Syntax: C/C++ vs C#

### Syntax Comparison: C/C++ vs C#/Java

| Aspect | C/C++ | C#/Java |
|--------|-------|---------|
| **Syntax** | `int arr[10];` | `int[] arr = new int[10];` |
| **Bracket Position** | After variable name | After data type |
| **Declaration & Init** | Together | Can be separated |
| **Default Values** | Garbage (uninitialized) | Zero-initialized |

---

### C# Array Declaration Methods

**Method 1: Declaration Only**
```csharp
int[] arr;  // No memory allocated yet
```

**Method 2: Declaration + Initialization**
```csharp
int[] arr = new int[5];  // Creates array of 5 zeros
```

**Method 3: Declaration with Values**
```csharp
int[] arr = {1, 2, 3, 4, 5};  // Size inferred (5 elements)
```

**Method 4: Explicit Type + Values**
```csharp
int[] arr = new int[] {1, 2, 3, 4, 5};
```

---

### C/C++ Array Declaration (for comparison)

```cpp
int arr[5];                    // Uninitialized (garbage values)
int arr[5] = {1, 2, 3, 4, 5};  // Initialized with values
int arr[] = {1, 2, 3, 4, 5};   // Size inferred from values
```

> **Why C# chose this syntax?** In C/C++, declaration and initialization happen together and cannot be split like in C# and Java.

## Memory Efficiency: C++ vs C# (Side-by-Side)

<table>
<tr>
<th>C++ (Memory Allocated Immediately)</th>
<th>C# (Memory Allocated Only When Needed)</th>
</tr>
<tr>
<td>

```cpp
#include <iostream>
using namespace std;

class Program {
public:
    // Memory allocated immediately
    int arr[1000];  // 4000 bytes

    void Function1() {
        arr[0] = 10;
        cout << "Function1: Using array";
    }

    void Function2() {
        arr[1] = 20;
        cout << "Function2: Using array";
    }

    void Function3() {
        // Array NOT used, but memory
        // is STILL allocated!
        cout << "Function3: 4000 bytes wasted!";
    }
};

int main() {
    Program p;
    p.Function3();  // Memory wasted
    return 0;
}
```

</td>
<td>

```csharp
using System;

class Program
{
    // No memory allocated yet
    static int[] arr;

    static void Function1()
    {
        arr = new int[1000];  // Allocated now
        arr[0] = 10;
        Console.WriteLine("Function1: Using array");
    }

    static void Function2()
    {
        arr = new int[1000];  // Allocated now
        arr[1] = 20;
        Console.WriteLine("Function2: Using array");
    }

    static void Function3()
    {
        // Array never initialized
        // NO memory allocated!
        Console.WriteLine("Function3: No memory wasted!");
    }

    static void Main()
    {
        Function3();  // No array memory used
    }
}
```

</td>
</tr>
</table>

### Quick Comparison

| Aspect | C++ | C# |
|--------|-----|-----|
| **Declaration** | `int arr[1000];` | `int[] arr;` |
| **Memory Allocation** | **Immediate** at declaration | **Deferred** until `new` |
| **When `Function3()` runs** | 4000 bytes **wasted** | **0 bytes** used for array |

> **Takeaway:** C#'s separation of declaration and initialization allows **lazy allocation**, saving memory when arrays aren't actually used.

## Iterating Through Arrays in C#

### Using `for` Loop (Index-Based)

```csharp
int[] numbers = {10, 20, 30, 40, 50};

for (int i = 0; i < numbers.Length; i++)
{
    Console.WriteLine($"Index {i}: {numbers[i]}");
}
```

### Using `foreach` Loop (Recommended for Read-Only)

```csharp
int[] numbers = {10, 20, 30, 40, 50};

foreach (int num in numbers)
{
    Console.WriteLine(num);
}
```

### Comparison: `for` vs `foreach`

| Feature | `for` Loop | `foreach` Loop |
|---------|------------|----------------|
| **Access Index** | ✅ Yes (`i`) | ❌ No direct access |
| **Modify Elements** | ✅ Yes (`arr[i] = value`) | ❌ No (read-only) |
| **Syntax** | More verbose | Cleaner, simpler |
| **Best For** | When index needed or modifying | Simple iteration |

### When to Use Which?

```csharp
// Use 'for' when you need the index or want to modify
for (int i = 0; i < arr.Length; i++)
{
    arr[i] = arr[i] * 2;  // Modifying elements
}

// Use 'foreach' for simple read-only iteration
foreach (var item in arr)
{
    Console.WriteLine(item);  // Just reading
}
```
