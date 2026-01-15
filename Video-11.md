## Struct vs Class Comparison

| Struct | Class |
|--------|-------|
| <pre>struct Student<br>{<br>    int Id;<br>    char Name[30];<br>    float Marks, Fees;<br>};</pre> | <pre>class Employee<br>{<br>    int Id;<br>    string Name, Job;<br>    float Salary;<br>    // Functions can be defined<br>};</pre> |

## Key Differences

| Feature | Struct | Class |
|---------|--------|-------|
| **Type** | Value type | Reference type |
| **Functions** | Cannot define functions (in C-style struct) | Functions can be defined |
| **Data Types** | Uses primitive types like `char[]` | Uses managed types like `string` |
| **Memory** | Stored on stack | Stored on heap |
| **Inheritance** | Does not support inheritance | Supports inheritance |

> **Note:** In C#, structs can also have methods, but the image illustrates the traditional C-style struct compared to a C# class.

## Why Do We Have Both Structs and Classes in C#?

While both structs and classes in C# can have methods, properties, constructors, and events, they serve **different purposes** due to fundamental differences:

| Aspect | Struct | Class |
|--------|--------|-------|
| **Type** | Value type | Reference type |
| **Memory** | Stored on **stack** (faster access) | Stored on **heap** (managed by GC) |
| **Assignment** | Creates a **copy** of data | Copies the **reference** (pointer) |
| **Inheritance** | ❌ Cannot inherit from other structs/classes | ✅ Supports inheritance |
| **Default value** | Cannot be `null` (unless nullable) | Can be `null` |
| **Performance** | Better for **small, short-lived** data | Better for **complex, long-lived** objects |

### When to Use Struct
- Data is **small** (typically < 16 bytes)
- Data is **immutable** or rarely changes
- You need **value semantics** (each variable has its own copy)
- Performance is critical (avoids heap allocation/GC overhead)
- Examples: `Point`, `DateTime`, `Color`, `Guid`

### When to Use Class
- Data is **large or complex**
- You need **inheritance** or polymorphism
- You need **reference semantics** (multiple variables point to same object)
- Object has a **longer lifetime**
- Examples: `Employee`, `Customer`, `HttpClient`

### Example: Value vs Reference Semantics

```csharp
struct PointStruct { public int X, Y; }
class PointClass { public int X, Y; }

var s1 = new PointStruct { X = 1, Y = 2 };
var s2 = s1;      // s2 is a COPY
s2.X = 99;        // s1.X is still 1

var c1 = new PointClass { X = 1, Y = 2 };
var c2 = c1;      // c2 points to SAME object
c2.X = 99;        // c1.X is now 99 too!
```

> **Bottom line**: Structs exist for **performance optimization** with small, value-based data, while classes provide **flexibility** for complex object-oriented designs.

---

## How to Consume a Type

To use (consume) any type in C#, you follow a fundamental pattern:

1. **Type Definition** → The blueprint (e.g., `int`, `string`, or a custom class)
2. **Instance Creation** → Create a copy/instance of that type in memory
3. **Consumption** → Use that instance (assign values, call methods, etc.)

### Value Types Example
```csharp
int i;        // Declaration - memory allocated for 'i' (copy of type int)
i = 10;       // Consumption - assigning a value

// Or combined:
int j = 20;   // Declaration + initialization in one step
```

### Reference Types Example
```csharp
// Type: Person (class definition is the blueprint)
class Person { public string Name; }

// Create instance (copy of the type in heap memory)
Person p = new Person();

// Consume it
p.Name = "John";
```

### Memory Location Summary

| Type Category | Memory Location | What's Stored |
|---------------|-----------------|---------------|
| Value types (`int`, `bool`, `struct`) | Stack | Actual value |
| Reference types (`class`, `string`) | Heap (reference on stack) | Reference to object |

> **Key Point**: The variable name (`i`, `p`, etc.) is essentially a **handle** to access that memory location where your "copy" of the type lives.

---

## Program Structure Comparison: C vs C++ vs C#

Here's a side-by-side comparison showing how code is structured differently - **standalone functions** in C/C++ vs **everything wrapped inside a class** in C#:

| C | C++ | C# |
|---|-----|-----|
| <pre>#include &lt;stdio.h&gt;<br><br>// ┌─────────────────────────────┐<br>// │ Functions are STANDALONE    │<br>// │ (outside any class)         │<br>// └─────────────────────────────┘<br>int add(int a, int b) {<br>    return a + b;<br>}<br><br>int subtract(int a, int b) {<br>    return a - b;<br>}<br><br>// ┌─────────────────────────────┐<br>// │ main() is STANDALONE        │<br>// │ (outside any class)         │<br>// └─────────────────────────────┘<br>int main() {<br>    int x = 10, y = 5;<br>    printf("Add: %d\n", add(x, y));<br>    printf("Subtract: %d\n", subtract(x, y));<br>    return 0;<br>}</pre> | <pre>#include &lt;iostream&gt;<br>using namespace std;<br><br>// ┌─────────────────────────────┐<br>// │ Functions are STANDALONE    │<br>// │ (outside any class)         │<br>// └─────────────────────────────┘<br>int add(int a, int b) {<br>    return a + b;<br>}<br><br>int subtract(int a, int b) {<br>    return a - b;<br>}<br><br>// ┌─────────────────────────────┐<br>// │ main() is STANDALONE        │<br>// │ (outside any class)         │<br>// └─────────────────────────────┘<br>int main() {<br>    int x = 10, y = 5;<br>    cout &lt;&lt; "Add: " &lt;&lt; add(x, y) &lt;&lt; endl;<br>    cout &lt;&lt; "Subtract: " &lt;&lt; subtract(x, y) &lt;&lt; endl;<br>    return 0;<br>}</pre> | <pre>using System;<br><br>// ┌─────────────────────────────────┐<br>// │ EVERYTHING inside a CLASS!     │<br>// └─────────────────────────────────┘<br>class Program<br>{<br>    // ┌─────────────────────────────┐<br>    // │ Functions INSIDE class      │<br>    // │ (called Methods)            │<br>    // └─────────────────────────────┘<br>    static int Add(int a, int b)<br>    {<br>        return a + b;<br>    }<br><br>    static int Subtract(int a, int b)<br>    {<br>        return a - b;<br>    }<br><br>    // ┌─────────────────────────────┐<br>    // │ Main() INSIDE class         │<br>    // └─────────────────────────────┘<br>    static void Main()<br>    {<br>        int x = 10, y = 5;<br>        Console.WriteLine("Add: " + Add(x, y));<br>        Console.WriteLine("Subtract: " + Subtract(x, y));<br>    }<br>}<br>// ⬆️ Closing brace of class</pre> |

### Key Structural Difference

| Aspect | C / C++ | C# |
|--------|---------|-----|
| **Functions** | Standalone (outside any class) | Must be inside a class (called **Methods**) |
| **main()** | Standalone (outside any class) | Must be inside a class (`Main()`) |
| **Class Required** | ❌ Optional | ✅ Mandatory |
| **Code Organization** | Procedural - functions exist independently | Object-Oriented - everything belongs to a class |

**Output (all three):**
```
Add: 15
Subtract: 5
```

---

## Static vs Non-Static Members

In C#, class members (variables and methods) can be either **static** or **non-static**. Here's an example showing the difference:

```csharp
class Math
{
    int x = 100;                  // Non-Static Variable
    static int y = 50;            // Static Variable

    int Add(int a, int b)         // Non-Static Method
    {
        int c = a + b;
        return c;
    }

    static int Sub(int a, int b)  // Static Method
    {
        int c = a - b;
        return c;
    }

    static void Main()
    {
        // Accessing static and non-static members will be explained below
        System.Console.WriteLine("Math.y = " + y); // Accessing static variable directly
        int resultSub = Sub(20, 10); // Accessing static method directly
        
        Math mathInstance = new Math(); // Creating instance to access non-static members
        System.Console.WriteLine("Math.x = " + mathInstance.x); // Accessing non-static variable
        int resultAdd = mathInstance.Add(10, 20); // Accessing non-static method    
    }

}
```

- Non static members of a class require object or instance of that class to access them.

- static members belong to the class itself and can be accessed without creating an instance.

In the above example, to access `x` or `Add()`, you need to create an instance of `Math`:

```csharp
Math mathInstance = new Math();
int sum = mathInstance.Add(10, 20); 
int valueX = mathInstance.x;  // as you can see x is non-static and needs instance to access 
```

- Static members belong to the class itself and can be accessed without creating an instance.

You can access `y` or `Sub()` directly using the class name:

```csharp
int difference = Math.Sub(30, 10);
int valueY = Math.y; // accessing static variable y directly using class name no need of instance Math required
```

---



