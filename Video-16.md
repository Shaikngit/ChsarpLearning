# Video 16 - Convert vs Parse in C#

## Difference Between Convert and Parse Classes

### Parse
- **What it does**: Converts a **string** to another data type
- **Handles null**: ❌ Throws exception if input is `null`
- **Example**:
```csharp
string str = "123";
int num = int.Parse(str);  // Works! num = 123

string nullStr = null;
int num2 = int.Parse(nullStr);  // ❌ Throws ArgumentNullException
```

### Convert
- **What it does**: Converts **any data type** to another data type
- **Handles null**: ✅ Returns default value (like 0 for int) if input is `null`
- **Example**:
```csharp
string str = "123";
int num = Convert.ToInt32(str);  // Works! num = 123

string nullStr = null;
int num2 = Convert.ToInt32(nullStr);  // ✅ Returns 0 (no exception)
```

---

## Quick Comparison Table

| Feature | Parse | Convert |
|---------|-------|---------|
| Input Type | String only | Any type |
| Null Handling | Throws exception | Returns default value (0, false, etc.) |
| Speed | Slightly faster | Slightly slower |
| Use When | You're sure input is valid string | Input might be null or different types |

---

## TryParse (Bonus - Safest Option)
- Returns `true/false` instead of throwing exception
- Best for user input validation

```csharp
string input = "abc";
bool success = int.TryParse(input, out int result);
// success = false, result = 0 (no exception thrown!)
```

---

## Simple Rule to Remember
- **Parse** = Fast but crashes on null
- **Convert** = Safe with null, works with any type
- **TryParse** = Safest, never crashes

---

# String Interpolation in C#

## What is String Interpolation?
String interpolation is a cleaner, more readable way to embed variables and expressions inside strings using the `$` prefix.

## Syntax
```csharp
$"Your text {variable} more text"
```

## Examples

### Basic Usage
```csharp
string name = "Naeem";
int age = 30;

// Old way (concatenation)
string old = "My name is " + name + " and I am " + age + " years old.";

// String Interpolation ✅
string modern = $"My name is {name} and I am {age} years old.";
```

### With Expressions
```csharp
int a = 10, b = 20;
Console.WriteLine($"Sum of {a} and {b} is {a + b}");
// Output: Sum of 10 and 20 is 30
```

### With Method Calls
```csharp
string name = "naeem";
Console.WriteLine($"Hello, {name.ToUpper()}!");
// Output: Hello, NAEEM!
```

### Formatting Numbers
```csharp
decimal price = 123.456m;
Console.WriteLine($"Price: {price:C}");      // Currency: $123.46
Console.WriteLine($"Price: {price:F2}");     // Fixed 2 decimals: 123.46

int number = 42;
Console.WriteLine($"Padded: {number:D5}");   // Padded: 00042
```

### Formatting Dates
```csharp
DateTime now = DateTime.Now;
Console.WriteLine($"Date: {now:yyyy-MM-dd}");  // Date: 2026-01-10
Console.WriteLine($"Time: {now:HH:mm:ss}");    // Time: 14:30:45
```

### Alignment (Padding)
```csharp
string item = "Apple";
decimal price = 1.5m;

Console.WriteLine($"|{item,-10}|{price,10:C}|");
// Output: |Apple     |     $1.50|
// -10 = left-align in 10 chars, 10 = right-align in 10 chars
```

---

## String Interpolation vs Other Methods

| Method | Example | Readability |
|--------|---------|-------------|
| Concatenation | `"Hello " + name` | ❌ Hard to read |
| `String.Format` | `String.Format("Hello {0}", name)` | ⚠️ Medium |
| **Interpolation** | `$"Hello {name}"` | ✅ Best |

---

## Verbatim + Interpolation (`$@` or `@$`)
Combine `$` and `@` for multi-line strings with variables:

```csharp
string path = "Users";
string combined = $@"C:\{path}\Documents\file.txt";
// Output: C:\Users\Documents\file.txt
```

---

## Key Points to Remember
- Start string with `$` prefix
- Variables go inside `{curly braces}`
- Can include expressions: `{a + b}`
- Can call methods: `{name.ToUpper()}`
- Format specifiers after colon: `{value:format}`
- Alignment with comma: `{value,width}`

---

# All Operators in C#

C# provides a rich set of operators categorized as follows:

---

## 1. Arithmetic Operators

| Operator | Description | Example |
|----------|-------------|---------|
| `+` | Addition | `5 + 3` = 8 |
| `-` | Subtraction | `5 - 3` = 2 |
| `*` | Multiplication | `5 * 3` = 15 |
| `/` | Division | `5 / 3` = 1 (int), `5.0 / 3` = 1.666... |
| `%` | Modulus (remainder) | `5 % 3` = 2 |
| `++` | Increment | `x++` or `++x` |
| `--` | Decrement | `x--` or `--x` |

```csharp
int a = 10, b = 3;
Console.WriteLine(a + b);  // 13
Console.WriteLine(a - b);  // 7
Console.WriteLine(a * b);  // 30
Console.WriteLine(a / b);  // 3 (integer division)
Console.WriteLine(a % b);  // 1

int x = 5;
Console.WriteLine(x++);  // 5 (post-increment)
Console.WriteLine(++x);  // 7 (pre-increment)
```

---

## 2. Assignment Operators

| Operator | Description | Equivalent To |
|----------|-------------|---------------|
| `=` | Assign | `x = 5` |
| `+=` | Add and assign | `x = x + 5` |
| `-=` | Subtract and assign | `x = x - 5` |
| `*=` | Multiply and assign | `x = x * 5` |
| `/=` | Divide and assign | `x = x / 5` |
| `%=` | Modulus and assign | `x = x % 5` |
| `&=` | Bitwise AND and assign | `x = x & 5` |
| `\|=` | Bitwise OR and assign | `x = x \| 5` |
| `^=` | Bitwise XOR and assign | `x = x ^ 5` |
| `<<=` | Left shift and assign | `x = x << 2` |
| `>>=` | Right shift and assign | `x = x >> 2` |
| `??=` | Null-coalescing assign | `x = x ?? 5` |

```csharp
int num = 10;
num += 5;   // 15
num -= 3;   // 12
num *= 2;   // 24
num /= 4;   // 6
num %= 4;   // 2

string name = null;
name ??= "Default";  // name = "Default"
```

---

## 3. Comparison (Relational) Operators

| Operator | Description | Example |
|----------|-------------|---------|
| `==` | Equal to | `5 == 5` → true |
| `!=` | Not equal to | `5 != 3` → true |
| `>` | Greater than | `5 > 3` → true |
| `<` | Less than | `5 < 3` → false |
| `>=` | Greater than or equal | `5 >= 5` → true |
| `<=` | Less than or equal | `5 <= 3` → false |

```csharp
int a = 10, b = 20;
Console.WriteLine(a == b);  // false
Console.WriteLine(a != b);  // true
Console.WriteLine(a > b);   // false
Console.WriteLine(a < b);   // true
Console.WriteLine(a >= 10); // true
Console.WriteLine(a <= 5);  // false
```

---

## 4. Logical Operators

| Operator | Description | Example |
|----------|-------------|---------|
| `&&` | Logical AND (short-circuit) | `true && false` → false |
| `\|\|` | Logical OR (short-circuit) | `true \|\| false` → true |
| `!` | Logical NOT | `!true` → false |
| `&` | Logical AND (no short-circuit) | `true & false` → false |
| `\|` | Logical OR (no short-circuit) | `true \| false` → true |

```csharp
bool a = true, b = false;

Console.WriteLine(a && b);  // false
Console.WriteLine(a || b);  // true
Console.WriteLine(!a);      // false

// Short-circuit: second condition not evaluated if first determines result
int x = 0;
if (x != 0 && 10 / x > 1)  // Safe! Second part not evaluated
    Console.WriteLine("OK");
```

---

## 5. Bitwise Operators

| Operator | Description | Example |
|----------|-------------|---------|
| `&` | Bitwise AND | `5 & 3` = 1 |
| `\|` | Bitwise OR | `5 \| 3` = 7 |
| `^` | Bitwise XOR | `5 ^ 3` = 6 |
| `~` | Bitwise NOT (complement) | `~5` = -6 |
| `<<` | Left shift | `5 << 1` = 10 |
| `>>` | Right shift | `5 >> 1` = 2 |
| `>>>` | Unsigned right shift | `5 >>> 1` = 2 |

```csharp
int a = 5;  // Binary: 0101
int b = 3;  // Binary: 0011

Console.WriteLine(a & b);   // 1  (0001)
Console.WriteLine(a | b);   // 7  (0111)
Console.WriteLine(a ^ b);   // 6  (0110)
Console.WriteLine(~a);      // -6
Console.WriteLine(a << 1);  // 10 (1010)
Console.WriteLine(a >> 1);  // 2  (0010)
```

---

## 6. Ternary (Conditional) Operator

| Operator | Description |
|----------|-------------|
| `? :` | Returns one of two values based on condition |

```csharp
int a = 10, b = 20;

// Syntax: condition ? value_if_true : value_if_false
int max = (a > b) ? a : b;
Console.WriteLine(max);  // 20

string result = (a % 2 == 0) ? "Even" : "Odd";
Console.WriteLine(result);  // Even
```

---

## 7. Type Operators

| Operator | Description | Example |
|----------|-------------|---------|
| `is` | Type check | `obj is string` |
| `as` | Safe type cast (returns null if fails) | `obj as string` |
| `typeof` | Gets Type object | `typeof(int)` |
| `sizeof` | Gets size in bytes | `sizeof(int)` = 4 |

```csharp
object obj = "Hello";

// is - check type
if (obj is string)
    Console.WriteLine("It's a string!");

// is with pattern matching
if (obj is string str)
    Console.WriteLine(str.Length);  // 5

// as - safe cast
string text = obj as string;  // "Hello"
int? num = obj as int?;       // null (cast failed)

// typeof
Type t = typeof(int);
Console.WriteLine(t.Name);  // Int32

// sizeof (only for value types)
Console.WriteLine(sizeof(int));     // 4
Console.WriteLine(sizeof(double));  // 8
```

---

# Conditional Statements & Loops

## Conditional Statements

| Statement | Syntax | Use Case | Example |
|-----------|--------|----------|---------|
| `if` | `if (condition) { }` | Single condition check | `if (x > 5) { }` |
| `if-else` | `if (condition) { } else { }` | Two-way decision | `if (x > 5) { } else { }` |
| `else if` | `if () { } else if () { } else { }` | Multiple conditions | `if (x > 10) { } else if (x > 5) { }` |
| `switch` | `switch (value) { case: break; }` | Multiple exact matches | `switch (day) { case 1: break; }` |
| `switch expression` | `var result = x switch { };` | Pattern matching (C# 8+) | `var r = x switch { 1 => "One" };` |
| Ternary `?:` | `condition ? true : false` | Inline if-else | `var max = a > b ? a : b;` |

---

## Loops

| Loop | Syntax | Use Case | When to Use |
|------|--------|----------|-------------|
| `for` | `for (init; condition; increment)` | Known iteration count | When you know exact iterations |
| `foreach` | `foreach (var item in collection)` | Iterate collections | Arrays, Lists, IEnumerable |
| `while` | `while (condition) { }` | Unknown iterations | Check condition BEFORE loop |
| `do-while` | `do { } while (condition);` | At least one execution | Check condition AFTER loop |

---

## Key Differences

| Feature | `for` | `foreach` | `while` | `do-while` |
|---------|-------|-----------|---------|------------|
| Counter variable | ✅ Built-in | ❌ No | ❌ Manual | ❌ Manual |
| Modify collection | ✅ Yes | ❌ No | ✅ Yes | ✅ Yes |
| Minimum executions | 0 | 0 | 0 | **1** |
| Best for | Index-based | Read-only iteration | Condition-based | Validate after action |

---

## Loop Control Statements

| Statement | Purpose |
|-----------|---------|
| `break` | Exit loop immediately |
| `continue` | Skip current iteration, go to next |
| `return` | Exit entire method |

---

## Quick Examples

```csharp
// for loop
for (int i = 0; i < 5; i++) { Console.WriteLine(i); }

// foreach loop
foreach (var item in list) { Console.WriteLine(item); }

// while loop
while (count < 10) { count++; }

// do-while loop
do { count++; } while (count < 10);

// switch
switch (grade) {
    case 'A': Console.WriteLine("Excellent"); break;
    case 'B': Console.WriteLine("Good"); break;
    default: Console.WriteLine("Try harder"); break;
}

// ternary
string result = score >= 50 ? "Pass" : "Fail";
```

---





