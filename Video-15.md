## Null Assignment: Reference Types vs Value Types

```csharp
string s = null;       // Valid
object o = null;       // Valid

int i = null;          // Invalid
double d = null;       // Invalid
```

### Why?

| Type | Can be `null`? | Reason |
|------|----------------|--------|
| `string` | ✅ Yes | Reference type - stored in Heap, variable holds address (can be "no address" = null) |
| `object` | ✅ Yes | Reference type - stored in Heap |
| `int` | ❌ No | Value type - stored directly in Stack, must have a value |
| `double` | ❌ No | Value type - stored directly in Stack, must have a value |

### Visual Explanation

```
Reference Types (CAN be null):
┌─────────────────┐
│  string s = null │  →  Points to NOTHING (no address)
│  object o = null │  →  Points to NOTHING (no address)
└─────────────────┘
     Stack                    Heap
┌──────────────┐         ┌──────────────┐
│  s = null    │    ✗    │              │
│  (no address)│─ ─ ─ ─ ─│  (nothing)   │
└──────────────┘         └──────────────┘


Value Types (CANNOT be null):
┌─────────────────┐
│  int i = ???    │  →  MUST have a value (0, 1, -5, etc.)
│  double d = ??? │  →  MUST have a value (0.0, 3.14, etc.)
└─────────────────┘
     Stack
┌──────────────┐
│  i = 100     │  ← Value stored DIRECTLY here
│  d = 3.14    │  ← Value stored DIRECTLY here
└──────────────┘
```

### Key Rule 📌

> **Reference types** can be `null` because they store an **address** (which can be "nothing").
> 
> **Value types** cannot be `null` because they store the **actual value** directly - there's no concept of "no value".

### Making Value Types Nullable

If you need a value type to accept `null`, use **Nullable<T>** or the shorthand `?`:

```csharp
int? i = null;          // Valid - Nullable<int>
double? d = null;       // Valid - Nullable<double>

// Shorthand is same as:
Nullable<int> i = null;
Nullable<double> d = null;
```

### How Nullable Value Types Are Stored in Memory

`Nullable<T>` is actually a **struct** (value type) that contains **two fields**:

```csharp
// Internally, Nullable<int> looks like this:
struct Nullable<int>
{
    bool hasValue;    // Flag: true if has value, false if null
    int value;        // The actual value (if hasValue is true)
}
```

### Memory Layout - ASCII Diagram

```
Regular int (4 bytes):
┌─────────────────────────┐
│   Stack                 │
├─────────────────────────┤
│   int i = 100           │
│   ┌───────────────────┐ │
│   │  100 (4 bytes)    │ │
│   └───────────────────┘ │
└─────────────────────────┘


Nullable<int> or int? (5+ bytes - typically 8 due to alignment):
┌─────────────────────────────────────────────┐
│   Stack                                     │
├─────────────────────────────────────────────┤
│   int? x = 100;                             │
│   ┌─────────────┬─────────────────────────┐ │
│   │ hasValue    │  value                  │ │
│   │ true (1 bit)│  100 (4 bytes)          │ │
│   └─────────────┴─────────────────────────┘ │
├─────────────────────────────────────────────┤
│   int? y = null;                            │
│   ┌─────────────┬─────────────────────────┐ │
│   │ hasValue    │  value                  │ │
│   │ false       │  0 (ignored/undefined)  │ │
│   └─────────────┴─────────────────────────┘ │
└─────────────────────────────────────────────┘
```

### Key Points About Nullable<T> Memory

| Aspect | Description |
|--------|-------------|
| **Storage Location** | Still on **Stack** (it's a struct, not a reference type!) |
| **Size** | Larger than T (adds boolean flag + padding for alignment) |
| **When null** | `hasValue = false`, value field exists but is ignored |
| **When has value** | `hasValue = true`, value field contains the actual data |

### Comparison: Reference Type null vs Nullable Value Type null

```
string s = null;                    int? i = null;
┌──────────────┐                    ┌──────────────────────┐
│    Stack     │                    │       Stack          │
├──────────────┤                    ├──────────────────────┤
│ s = 0x0000   │ → Points nowhere   │ hasValue = false     │
│ (null addr)  │                    │ value = (garbage/0)  │
└──────────────┘                    └──────────────────────┘
       │                                     │
       ▼                                     ▼
    NO Heap                            NO Heap
    allocation                         (stays on Stack!)
```

### Code Example

```csharp
int? x = 100;
int? y = null;

Console.WriteLine(x.HasValue);  // Output: True
Console.WriteLine(x.Value);     // Output: 100

Console.WriteLine(y.HasValue);  // Output: False
// Console.WriteLine(y.Value); // ❌ Throws InvalidOperationException!

// Safe way to get value:
int result = y ?? 0;            // Use null-coalescing: returns 0 if null
int result2 = y.GetValueOrDefault(); // Returns 0 if null
```

---

## Implicitly Typed Variables (C# 3.0)

The `var` keyword allows the compiler to **infer the type** from the assigned value at compile time.

```csharp
var i = 100;        // i is of type int
var f = 3.14f;      // f is of type float
var b = true;       // b is of type bool
var s = "Hello";    // s is of type string
var c = 'A';        // c is of type char

var x;              // ❌ Invalid - must be initialized!
```

### Key Rules for `var`

| Rule | Description |
|------|-------------|
| **Must initialize** | `var x;` is invalid - compiler needs a value to infer the type |
| **Compile-time typing** | Type is determined at compile time, NOT runtime (still strongly typed) |
| **Cannot change type** | Once inferred, the type is fixed: `var i = 10; i = "hello";` ❌ |
| **Local variables only** | Cannot use `var` for fields, parameters, or return types |

### How `var` Works

```
Code:                          Compiler sees it as:
─────────────────────────────────────────────────────
var i = 100;          →        int i = 100;
var f = 3.14f;        →        float f = 3.14f;
var b = true;         →        bool b = true;
var s = "Hello";      →        string s = "Hello";
var c = 'A';          →        char c = 'A';
```

### Why `var x;` is Invalid

```
var x;    // ❌ Error: Implicitly-typed variables must be initialized

// Compiler thinks: "What type should x be? int? string? bool? I don't know!"
```

The compiler **cannot infer** the type without a value!

---

## Dynamic Type (C# 4.0)

The `dynamic` keyword allows a variable to hold **any type** and the type is resolved at **runtime**, not compile time.

```csharp
dynamic d;          // Valid - no initialization required!
d = 100;            // d is of type int
d = 34.56;          // d is of type double
d = true;           // d is of type bool
d = 'A';            // d is of type char
d = "Hello";        // d is of type string
```

### Key Characteristics of `dynamic`

| Feature | Description |
|---------|-------------|
| **No initialization required** | `dynamic d;` is valid (unlike `var`) |
| **Can change types** | Same variable can hold int, then string, then bool |
| **Runtime type resolution** | Type checking happens at runtime, not compile time |
| **No IntelliSense** | IDE cannot help with auto-complete (type unknown at design time) |
| **Runtime errors** | Invalid operations throw exceptions at runtime, not compile time |

### Visual: How `dynamic` Changes Type at Runtime

```
dynamic d;

d = 100;      →  d is now:  ┌─────────────┐
                            │ int: 100    │
                            └─────────────┘

d = 34.56;    →  d is now:  ┌─────────────┐
                            │ double: 34.56│
                            └─────────────┘

d = true;     →  d is now:  ┌─────────────┐
                            │ bool: true  │
                            └─────────────┘

d = 'A';      →  d is now:  ┌─────────────┐
                            │ char: 'A'   │
                            └─────────────┘

d = "Hello";  →  d is now:  ┌─────────────┐
                            │ string: Hello│
                            └─────────────┘
```

### `var` vs `dynamic` - Complete Comparison

| Aspect | `var` | `dynamic` |
|--------|-------|-----------|
| **Introduced in** | C# 3.0 | C# 4.0 |
| **Type resolution** | Compile time | Runtime |
| **Initialization** | Required | Not required |
| **Can change type** | ❌ No | ✅ Yes |
| **IntelliSense** | ✅ Yes | ❌ No |
| **Error detection** | Compile time | Runtime |
| **Performance** | Faster (static typing) | Slower (runtime binding) |

### Code Example

```csharp
// var - type is fixed at compile time
var x = 10;
// x = "Hello";  // ❌ Error: Cannot convert string to int

// dynamic - type can change at runtime
dynamic d = 10;
Console.WriteLine(d.GetType());  // Output: System.Int32

d = "Hello";
Console.WriteLine(d.GetType());  // Output: System.String

d = true;
Console.WriteLine(d.GetType());  // Output: System.Boolean
```

### ⚠️ Warning: Runtime Errors with `dynamic`

```csharp
dynamic d = "Hello";
int result = d + 10;  // ❌ Runtime Error! Cannot add string and int

// This compiles fine, but crashes at runtime!
```

---

## Boxing and Unboxing

**Boxing** and **Unboxing** are mechanisms to convert between **value types** and **reference types** in C#.

### Boxing

Boxing is the process of converting a **value type** (like `int`, `float`, `struct`) to a **reference type** (`object` or an interface).

```csharp
int num = 42;           // Value type (stored on stack)
object obj = num;       // Boxing: value is copied to heap, wrapped in object
```

**What happens internally:**
1. Memory is allocated on the **heap**
2. The value is **copied** from the stack to the heap
3. A reference to the heap location is returned

### Visual: Boxing Process

```
Before Boxing:
┌─────────────────┐
│     Stack       │
├─────────────────┤
│  int num = 42   │
│  ┌───────────┐  │
│  │    42     │  │
│  └───────────┘  │
└─────────────────┘

After Boxing (object obj = num):
┌─────────────────┐         ┌─────────────────┐
│     Stack       │         │      Heap       │
├─────────────────┤         ├─────────────────┤
│  int num = 42   │         │  ┌───────────┐  │
│  ┌───────────┐  │         │  │ Object    │  │
│  │    42     │  │         │  │ Header    │  │
│  └───────────┘  │         │  ├───────────┤  │
│                 │         │  │    42     │  │
│  obj = 0xABC ───┼────────►│  └───────────┘  │
│  (reference)    │         │    @ 0xABC      │
└─────────────────┘         └─────────────────┘
```

### Unboxing

Unboxing is the reverse — extracting the **value type** from the **object**.

```csharp
object obj = 42;        // Boxed integer
int num = (int)obj;     // Unboxing: explicit cast required
```

**What happens internally:**
1. The runtime verifies the object contains the correct type
2. The value is **copied** from the heap back to the stack

### Visual: Unboxing Process

```
Before Unboxing:
┌─────────────────┐         ┌─────────────────┐
│     Stack       │         │      Heap       │
├─────────────────┤         ├─────────────────┤
│  obj = 0xABC ───┼────────►│  ┌───────────┐  │
│                 │         │  │    42     │  │
│                 │         │  └───────────┘  │
└─────────────────┘         └─────────────────┘

After Unboxing (int num = (int)obj):
┌─────────────────┐         ┌─────────────────┐
│     Stack       │         │      Heap       │
├─────────────────┤         ├─────────────────┤
│  obj = 0xABC ───┼────────►│  ┌───────────┐  │
│                 │         │  │    42     │  │
│  int num = 42   │◄─ copy ─│  └───────────┘  │
│  ┌───────────┐  │         └─────────────────┘
│  │    42     │  │
│  └───────────┘  │
└─────────────────┘
```

### Key Points

| Aspect | Boxing | Unboxing |
|--------|--------|----------|
| Direction | Value → Reference | Reference → Value |
| Cast | Implicit | Explicit (required) |
| Memory | Allocates on heap | Copies from heap to stack |
| Performance | Has overhead | Has overhead |

### ⚠️ Unboxing Type Must Match

```csharp
object obj = 42;          // Boxed as int

int i = (int)obj;         // ✅ Valid
long l = (long)obj;       // ❌ InvalidCastException! Must unbox to exact type

// Correct way to convert:
long l = (long)(int)obj;  // ✅ Unbox to int first, then convert to long
```

### Performance Impact

```csharp
// ❌ Inefficient - causes boxing in each iteration
ArrayList list = new ArrayList();
for (int i = 0; i < 1000; i++)
{
    list.Add(i);  // Boxing occurs here!
}

// ✅ Efficient - no boxing with generics
List<int> list = new List<int>();
for (int i = 0; i < 1000; i++)
{
    list.Add(i);  // No boxing!
}
```

### Common Boxing Scenarios

| Scenario | Example |
|----------|---------|
| Non-generic collections | `ArrayList.Add(42)` |
| Methods accepting `object` | `Console.WriteLine(42)` |
| String formatting | `string.Format("{0}", 42)` |
| Interface casting | `IComparable c = 42;` |

### Best Practices

- ✅ Use **generics** (`List<T>`, `Dictionary<K,V>`) instead of non-generic collections
- ✅ Avoid unnecessary conversions to `object`
- ✅ Be mindful of boxing in performance-critical code paths
- ✅ Use `struct` constraints in generics to prevent boxing when possible





