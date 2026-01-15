# Differences Between `for` and `foreach` Loop in C#

In C#, both `for` and `foreach` loops are used to iterate through collections like arrays, lists, etc. However, they have some key differences in terms of syntax, usage, and capabilities.

## Key Differences
- In for loop the index variable i is index of the array where as in foreach loop the variable item represents the actual value at that index. 
- In for loop irrespective of type of array , the index variable i is always of type int
- In for loop we can modify the elements of the array using the index where as in foreach loop we cannot modify the elements of the array since it is read only.

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
```

```csharp           
// Use 'foreach' for simple read-only iteration
foreach (var item in arr)
{
    Console.WriteLine(item);  // Just reading
}
```

---

# Array Memory Storage in C#

Arrays in C# are **reference types** and are always stored in **heap memory**. The variable (reference) is stored on the stack, but the actual array data is allocated on the heap.

## Value Type Array: `int[] numbers = new int[4] {10, 20, 30, 40};`

```
        STACK                              HEAP
    ┌──────────────┐                ┌─────────────────────────────────┐
    │              │                │                                 │
    │   numbers    │                │   Array Object                  │
    │ ┌──────────┐ │                │  ┌───────────────────────────┐  │
    │ │ 0x7F2A00 │─┼───────────────►│  │ Type: System.Int32[]      │  │
    │ └──────────┘ │                │  │ Length: 4                 │  │
    │  (reference) │                │  ├───────────────────────────┤  │
    │              │                │  │ [0] │  10                 │  │
    └──────────────┘                │  ├─────┼─────────────────────┤  │
                                    │  │ [1] │  20                 │  │
                                    │  ├─────┼─────────────────────┤  │
                                    │  │ [2] │  30                 │  │
                                    │  ├─────┼─────────────────────┤  │
                                    │  │ [3] │  40                 │  │
                                    │  └─────┴─────────────────────┘  │
                                    │         (actual values)         │
                                    └─────────────────────────────────┘
```

**Key Point:** For value type arrays (`int[]`, `double[]`, `bool[]`), the actual values are stored **contiguously** in the heap.

---

## Reference Type Array: `string[] names = new string[3] {"Ali", "Bob", "Cat"};`

```
        STACK                              HEAP
    ┌──────────────┐                ┌─────────────────────────────────────────────┐
    │              │                │                                             │
    │    names     │                │   Array Object                              │
    │ ┌──────────┐ │                │  ┌─────────────────────────┐                │
    │ │ 0x8A1B00 │─┼───────────────►│  │ Type: System.String[]   │                │
    │ └──────────┘ │                │  │ Length: 3               │                │
    │  (reference) │                │  ├─────────────────────────┤                │
    │              │                │  │ [0] │ 0x8A2000 │────────┼──► "Ali"       │
    └──────────────┘                │  ├─────┼──────────┤        │    (String obj)│
                                    │  │ [1] │ 0x8A3000 │────────┼──► "Bob"       │
                                    │  ├─────┼──────────┤        │    (String obj)│
                                    │  │ [2] │ 0x8A4000 │────────┼──► "Cat"       │
                                    │  └─────┴──────────┘        │    (String obj)│
                                    │       (references)                          │
                                    └─────────────────────────────────────────────┘
```

**Key Point:** For reference type arrays (`string[]`, `object[]`), the array stores **references/pointers** to objects, which themselves are also stored on the heap.

---

## Summary Table

| Array Type | Stack Contains | Heap Contains |
|------------|----------------|---------------|
| Value type (`int[]`) | Reference to array | Array metadata + actual values |
| Reference type (`string[]`) | Reference to array | Array metadata + references → actual objects |

---

# Array Class in C#

The `Array` class is the **base class for all arrays** in C# and is part of the `System` namespace. It provides methods for creating, manipulating, searching, and sorting arrays.

## Commonly Used Array Class Methods

| Method | Description |
|--------|-------------|
| `Array.Sort(arr)` | Sorts the elements in ascending order (original array is modified) |
| `Array.Reverse(arr)` | Reverses the order of elements (original array is modified) |
| `Array.IndexOf(arr, value)` | Returns the index of the first occurrence of a value |
| `Array.LastIndexOf(arr, value)` | Returns the index of the last occurrence of a value |
| `Array.Copy(source, dest, length)` | Copies elements from one array to another (original array is not modified) |
| `Array.Clear(arr, index, length)` | Sets a range of elements to default values (original array is modified) |
| `Array.Resize(ref arr, newSize)` | Resizes the array to a new size (creates a new array) |
| `Array.Find(arr, predicate)` | Finds the first element matching a condition |
| `Array.FindAll(arr, predicate)` | Finds all elements matching a condition (returns new array) |
| `Array.Exists(arr, predicate)` | Checks if any element matches a condition |
| `Array.BinarySearch(arr, value)` | Searches a sorted array using binary search |
| `Array.GetLength(dimension)` | Gets the length of a specific dimension |
| `Array.GetValue(index)` | Gets the value at a specific index |
| `Array.SetValue(value, index)` | Sets a value at a specific index (original array is modified) |

## Example Usage

```csharp
int[] numbers = { 5, 2, 8, 1, 9 };

// Sort the array
Array.Sort(numbers);  // Result: {1, 2, 5, 8, 9}

// Reverse the array
Array.Reverse(numbers);  // Result: {9, 8, 5, 2, 1}

// Find index of element
int index = Array.IndexOf(numbers, 5);  // Returns index of 5

// Copy array
int[] copy = new int[5];
Array.Copy(numbers, copy, numbers.Length);

// Search in sorted array
Array.Sort(numbers);
int pos = Array.BinarySearch(numbers, 5);

// Find element with condition
int firstEven = Array.Find(numbers, x => x % 2 == 0);
```

Syntax for Single Dimensional Array:

```csharp   
datatype[] arrayName = new datatype[size];
// Example:
int[] numbers = new int[5];
string[] names = new string[3];
```
Syntax for Two Dimensional Array:

```csharp
datatype[,] arrayName = new datatype[rows, columns];
// Example:
int[,] matrix = new int[3, 4];
string[,] grid = new string[2, 5];
```

## Array Initialization with Values

```csharp
// Single Dimensional Array with values
int[] numbers = new int[] { 10, 20, 30, 40, 50 };
// Or simplified syntax:
int[] numbers2 = { 10, 20, 30, 40, 50 };

string[] names = { "Alice", "Bob", "Charlie" };

// Two Dimensional Array with values
int[,] matrix = new int[,] { 
    { 1, 2, 3 }, 
    { 4, 5, 6 }, 
    { 7, 8, 9 } 
};
// Or simplified:
int[,] matrix2 = { 
    { 1, 2, 3 }, 
    { 4, 5, 6 } 
};
```
## Accessing 2D Array Valuesjjj

### Using `for` Loop (with index access)

```csharp
int[,] matrix = { 
    { 1, 2, 3 }, 
    { 4, 5, 6 }, 
    { 7, 8, 9 } 
};

// Using nested for loops - gives you row and column indices
for (int i = 0; i < matrix.GetLength(0); i++)  // Rows
{
    for (int j = 0; j < matrix.GetLength(1); j++)  // Columns
    {
        Console.Write(matrix[i, j] + " ");
    }
    Console.WriteLine();
}
```

### Using `foreach` Loop (simple iteration)

```csharp
int[,] matrix = { 
    { 1, 2, 3 }, 
    { 4, 5, 6 }, 
    { 7, 8, 9 } 
};

// foreach iterates through all elements in row-major order
foreach (int item in matrix)
{
    Console.Write(item + " ");
}
// Output: 1 2 3 4 5 6 7 8 9
```

### Key Differences for 2D Arrays

| Feature | `for` Loop | `foreach` Loop |
|---------|------------|----------------|
| **Row/Column Index** | ✅ Yes (`matrix[i,j]`) | ❌ No |
| **Control Over Traversal** | ✅ Row-wise, column-wise, etc. | ❌ Only row-major order |
| **Modify Elements** | ✅ Yes | ❌ No (read-only) |
| **GetLength()** | Uses `GetLength(0)` for rows, `GetLength(1)` for columns | Not needed |

## How Nested `for` Loops Work

For each **single iteration** of the outer loop, the inner loop completes its **entire cycle** (all iterations).

### Visualization

```
Outer Loop i=0  →  Inner Loop: j=0, j=1, j=2 (complete cycle)
Outer Loop i=1  →  Inner Loop: j=0, j=1, j=2 (complete cycle)
Outer Loop i=2  →  Inner Loop: j=0, j=1, j=2 (complete cycle)
```

### Example with 2D Array

```csharp
int[,] matrix = { 
    { 1, 2, 3 }, 
    { 4, 5, 6 } 
};

for (int i = 0; i < 2; i++)      // Outer loop (rows)
{
    for (int j = 0; j < 3; j++)  // Inner loop (columns)
    {
        Console.Write($"[{i},{j}]={matrix[i,j]} ");
    }
    Console.WriteLine();
}
```

### Execution Flow

```
i=0 (Row 0):
    j=0 → [0,0]=1
    j=1 → [0,1]=2
    j=2 → [0,2]=3
    (inner loop complete, move to next outer iteration)

i=1 (Row 1):
    j=0 → [1,0]=4
    j=1 → [1,1]=5
    j=2 → [1,2]=6
    (inner loop complete, outer loop ends)
```

### Output
```
[0,0]=1 [0,1]=2 [0,2]=3 
[1,0]=4 [1,1]=5 [1,2]=6 
```

**Total iterations** = Outer loop count × Inner loop count = 2 × 3 = **6**

---

# Jagged Arrays in C#

A **jagged array** is an "array of arrays" where each inner array can have a **different length**. Unlike a 2D rectangular array (`int[,]`), jagged arrays allow rows of varying sizes.

## Syntax

```csharp
// Declaration
datatype[][] arrayName = new datatype[numberOfRows][];

// Example
int[][] jagged = new int[3][];  // 3 rows, column size not fixed yet
```

## Initialization

```csharp
// Initialize each row separately with different lengths
int[][] jagged = new int[3][];
jagged[0] = new int[] { 1, 2 };           // Row 0: 2 elements
jagged[1] = new int[] { 3, 4, 5, 6 };     // Row 1: 4 elements
jagged[2] = new int[] { 7, 8, 9 };        // Row 2: 3 elements

// Or initialize inline
int[][] jagged2 = new int[][] {
    new int[] { 1, 2 },
    new int[] { 3, 4, 5, 6 },
    new int[] { 7, 8, 9 }
};
```

## Memory Representation

```
        STACK                              HEAP
    ┌──────────────┐                ┌─────────────────────────────────────┐
    │              │                │                                     │
    │   jagged     │                │  Array of References                │
    │ ┌──────────┐ │                │ ┌─────────────────┐                 │
    │ │ 0x5A0000 │─┼───────────────►│ │ [0] │ 0x5B0000 │──► { 1, 2 }     │
    │ └──────────┘ │                │ ├─────┼──────────┤                  │
    │              │                │ │ [1] │ 0x5C0000 │──► { 3, 4, 5, 6 }│
    └──────────────┘                │ ├─────┼──────────┤                  │
                                    │ │ [2] │ 0x5D0000 │──► { 7, 8, 9 }  │
                                    │ └─────┴──────────┘                  │
                                    └─────────────────────────────────────┘
```

## Accessing Jagged Array Elements

### Using Nested `for` Loops

```csharp
int[][] jagged = new int[][] {
    new int[] { 1, 2 },
    new int[] { 3, 4, 5, 6 },
    new int[] { 7, 8, 9 }
};

for (int i = 0; i < jagged.Length; i++)           // Outer array length
{
    for (int j = 0; j < jagged[i].Length; j++)    // Inner array length (varies)
    {
        Console.Write(jagged[i][j] + " ");
    }
    Console.WriteLine();
}
```

### Using `foreach` Loop

```csharp
foreach (int[] row in jagged)
{
    foreach (int item in row)
    {
        Console.Write(item + " ");
    }
    Console.WriteLine();
}
```

## Jagged vs 2D Rectangular Array

| Feature | Jagged Array (`int[][]`) | 2D Array (`int[,]`) |
|---------|--------------------------|---------------------|
| **Row Lengths** | Can vary | Must be same |
| **Memory** | Non-contiguous (array of references) | Contiguous block |
| **Access Syntax** | `arr[i][j]` | `arr[i, j]` |
| **Length Property** | `arr.Length` (rows), `arr[i].Length` (columns) | `arr.GetLength(0)`, `arr.GetLength(1)` |
| **Flexibility** | More flexible | Fixed structure |
| **Use Case** | Irregular data (e.g., triangular matrix) | Regular grid data |