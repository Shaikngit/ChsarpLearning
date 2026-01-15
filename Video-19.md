# Initializing and Displaying Jagged Array with Foreach Loop

A **jagged array** is an array of arrays, where each inner array can have a different length.

## Example Code

```csharp
using System;

class Program
{
    static void Main()
    {
        // Initialize a jagged array
        int[][] jaggedArray = new int[3][];
        
        jaggedArray[0] = new int[] { 1, 2, 3 };
        jaggedArray[1] = new int[] { 4, 5 };
        jaggedArray[2] = new int[] { 6, 7, 8, 9 };

        // Display contents using foreach loop
        foreach (int[] innerArray in jaggedArray)
        {
            foreach (int element in innerArray)
            {
                Console.Write(element + " ");
            }
            Console.WriteLine();
        }
    }
}
```

## Output

```
1 2 3 
4 5 
6 7 8 9 
```

## Key Points

- **Outer foreach** iterates through each inner array
- **Inner foreach** iterates through elements of each inner array
- Each row can have a different number of elements

## Variations

### Foreach (Outer) with For (Inner) Loop

```csharp
foreach (int[] innerArray in jaggedArray)
{
    for (int j = 0; j < innerArray.Length; j++)
    {
        Console.Write(innerArray[j] + " ");
    }
    Console.WriteLine();
}
```

### For (Outer) with Foreach (Inner) Loop

```csharp
for (int i = 0; i < jaggedArray.Length; i++)
{
    foreach (int element in jaggedArray[i])
    {
        Console.Write(element + " ");
    }
    Console.WriteLine();
}
```

### For (Outer) with For (Inner) Loop

```csharp
for (int i = 0; i < jaggedArray.Length; i++)
{
    for (int j = 0; j < jaggedArray[i].Length; j++)
    {
        Console.Write(jaggedArray[i][j] + " ");
    }
    Console.WriteLine();
}
```

## When to Use Each

| Variation | Use Case |
|-----------|----------|
| `foreach` + `foreach` | Simple iteration, no index needed |
| `foreach` + `for` | Need inner index only |
| `for` + `foreach` | Need outer index only |
| `for` + `for` | Need both indices for element access or modification |

## Quick Recall: Variable vs Array vs Jagged Array

| Concept | What It Is | Declaration | Visual |
|---------|-----------|-------------|--------|
| **Variable** | Single value | `int x = 5;` | `[5]` |
| **Array** | Multiple values in a row | `int[] arr = {1, 2, 3};` | `[1][2][3]` |
| **Jagged Array** | Array of arrays (rows can vary) | `int[][] jagged = new int[2][];` | `[1][2][3]`<br>`[4][5]` |

### One-Liner Summary
- **Variable** = 1 box
- **Array** = 1 row of boxes
- **Jagged Array** = multiple rows, each row can have different boxes

---

## Cheat Sheet

### Variable

```csharp
// int
int x = 5;
int y = new int();   // → 0 (default)
int z;               // Uninitialized (must assign before use)

// string
string name = "Alice";
string s = new string("");  // → ""
string t;                   // Uninitialized (null if class field)

// double
double price = 19.99;
double d = new double();    // → 0.0 (default)
```

**Default values (when not assigned):**
- `int` → `0`
- `double` → `0.0`
- `string` → `null`
- `bool` → `false`

---

### Array

```csharp
// int
int[] numbers = { 1, 2, 3 };
int[] nums = new int[3];     // → {0, 0, 0}
numbers[0]                   // → 1

// string
string[] names = { "Alice", "Bob", "Charlie" };
string[] strs = new string[3];  // → {null, null, null}
names[1]                        // → "Bob"

// double
double[] prices = { 9.99, 19.99, 29.99 };
double[] dbls = new double[3];  // → {0.0, 0.0, 0.0}
prices[2]                       // → 29.99
```

**Default values (when using `new type[size]`):**
- `int[]` → all elements `0`
- `double[]` → all elements `0.0`
- `string[]` → all elements `null`

---

### Jagged Array

```csharp
// int
int[][] intJagged = {
    new int[] { 1, 2, 3 },
    new int[] { 4, 5 },
    new int[] { 6, 7, 8, 9 }
};
int[][] emptyJagged = new int[3][];  // → {null, null, null}
emptyJagged[0] = new int[2];         // → {0, 0}
intJagged[0][1]                      // → 2

// string
string[][] stringJagged = {
    new string[] { "A", "B" },
    new string[] { "C", "D", "E" }
};
stringJagged[1][2]                   // → "E"

// double
double[][] doubleJagged = {
    new double[] { 1.1, 2.2, 3.3 },
    new double[] { 4.4, 5.5 }
};
doubleJagged[0][2]                   // → 3.3
```

**Default values (when using `new type[rows][]`):**
- Inner arrays → `null` (must initialize each row)
- After `new int[cols]` → elements are `0`

---

### Memory Tip 🧠

| Type | Pattern |
|------|---------|
| Variable | `type name = value;` or `type name = new type();` |
| Array | `type[] name = new type[size];` |
| Jagged | `type[][] name = new type[rows][];` then `name[i] = new type[cols];` |

### Default Values Summary

| Type | Default Value |
|------|---------------|
| `int` | `0` |
| `double` | `0.0` |
| `bool` | `false` |
| `string` | `null` |
| `object` / Reference types | `null` |


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
│  │  │              CLASS (.cs file)                   │  │  │
│  │  │         (Blueprint for objects)                 │  │  │
│  │  │                                                 │  │  │
│  │  │   • Fields (variables)                          │  │  │
│  │  │   • Properties                                  │  │  │
│  │  │   • Methods (functions)                         │  │  │
│  │  │   • Main() → Entry point                        │  │  │
│  │  └─────────────────────────────────────────────────┘  │  │
│  │                                                       │  │
│  │  ┌─────────────────────────────────────────────────┐  │  │
│  │  │           Another CLASS (.cs file)              │  │  │
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
