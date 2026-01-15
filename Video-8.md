## .NET Runtime Software - CLI (Common Language Infrastructure) Specifications

.NET Runtime Software is built based on a set of specifications called **CLI (Common Language Infrastructure) Specifications**. Under this Spec's we have 4 important things to understand:

### 1. CLS: Common Language Specification
According to this, all languages in .NET should generate the same type of output code after the compilation and we call that code as **CIL (Common Intermediate Language) Code**, so that if any 2 .NET Languages want to interoperate with each other then compiled code mis-match will not occur.

### 2. CTS: Common Type System
According to this, all languages in .NET should follow a rule regarding the Data-Types i.e., **Uniform Data-Type Structure** which means similar types should always be same in size, so that if any 2 .NET Languages want to interoperate with each other then Data-Type mis-match will not occur.

### 3. MetaData
This is data about data.

### 4. VES: Virtual Execution System
Also called as **CLR (Common Language Runtime)**, which is the execution engine of .NET's Runtime that is responsible for execution of .NET Applications by providing the features like:
- Portability
- Security
- Automatic Memory Management

---

## Libraries and Header Files

### What are Libraries?
A **library** is a collection of pre-written code (functions, classes, modules) that developers can reuse in their programs. Libraries help avoid "reinventing the wheel" by providing ready-made solutions for common tasks like file I/O, networking, math operations, etc.

**Types of Libraries:**
- **Static Libraries**: Linked at compile-time, become part of the executable
- **Dynamic Libraries**: Linked at runtime, shared across multiple programs (.dll, .so, .dylib)
- **Standard Libraries**: Built-in libraries provided by the language

### What are Header Files?
**Header files** contain declarations of functions, classes, macros, and constants that can be shared across multiple source files. They act as an interface/contract telling the compiler what functions exist without providing the implementation.

---

## Including Libraries in Different Languages

### 1. C Language

**Header Files**: Use `.h` extension (e.g., `stdio.h`, `stdlib.h`)

**How to Include:**
```c
#include <stdio.h>      // Standard library header (searches in system directories)
#include <stdlib.h>     // Standard library for memory allocation, etc.
#include <string.h>     // String manipulation functions
#include "myheader.h"   // User-defined header (searches in current directory first)
```

**Sample Program:**
```c
#include <stdio.h>    // For printf(), scanf()
#include <math.h>     // For sqrt(), pow()

int main() {
    double num = 16.0;
    printf("Square root of %.2f is %.2f\n", num, sqrt(num));
    printf("2 raised to power 3 is %.2f\n", pow(2, 3));
    return 0;
}
```

**Compilation (linking math library):**
```bash
gcc program.c -o program -lm
```

---

### 2. C++ Language

**Header Files**: Modern C++ uses headers without `.h` extension for standard library

**How to Include:**
```cpp
#include <iostream>     // For cin, cout (C++ standard)
#include <vector>       // For std::vector
#include <string>       // For std::string
#include <cmath>        // C math library in C++ (note: no .h)
#include "myclass.h"    // User-defined header
```

**Sample Program:**
```cpp
#include <iostream>   // For input/output streams
#include <vector>     // For dynamic arrays
#include <algorithm>  // For sort(), find(), etc.

using namespace std;  // To avoid writing std:: prefix

int main() {
    vector<int> numbers = {5, 2, 8, 1, 9};
    
    // Using algorithm library to sort
    sort(numbers.begin(), numbers.end());
    
    cout << "Sorted numbers: ";
    for(int num : numbers) {
        cout << num << " ";
    }
    cout << endl;
    
    return 0;
}
```

**Compilation:**
```bash
g++ program.cpp -o program
```

---

### 3. C# Language

**Libraries**: Called **Assemblies** (`.dll` files) and organized into **Namespaces**

**How to Include:**
```csharp
using System;                    // Core types (Console, String, etc.)
using System.Collections.Generic; // Collections (List, Dictionary, etc.)
using System.Linq;               // LINQ query operations
using System.IO;                 // File operations
using System.Net.Http;           // HTTP client
```

**Sample Program:**
```csharp
using System;                      // For Console class
using System.Collections.Generic;  // For List<T>
using System.Linq;                 // For LINQ methods

namespace MyApplication
{
    class Program
    {
        static void Main(string[] args)
        {
            // Using List from System.Collections.Generic
            List<int> numbers = new List<int> { 5, 2, 8, 1, 9 };
            
            // Using LINQ from System.Linq
            var sortedNumbers = numbers.OrderBy(n => n).ToList();
            
            // Using Console from System
            Console.WriteLine("Sorted numbers: " + string.Join(", ", sortedNumbers));
        }
    }
}
```

**Adding External Libraries (NuGet):**
```bash
dotnet add package Newtonsoft.Json
```

Then use:
```csharp
using Newtonsoft.Json;
```

---

### 4. Python Language

**Libraries**: Called **Modules** and **Packages**

**How to Include:**
```python
import math                      # Import entire module
from math import sqrt, pow       # Import specific functions
from datetime import datetime    # Import specific class
import numpy as np               # Import with alias
from collections import *        # Import all (not recommended)
```

**Sample Program:**
```python
import math                        # Math functions
from datetime import datetime      # Date/time handling
import os                          # Operating system interface
import json                        # JSON parsing

# Using math module
number = 16
print(f"Square root of {number} is {math.sqrt(number)}")

# Using datetime module
current_time = datetime.now()
print(f"Current date and time: {current_time}")

# Using os module
print(f"Current working directory: {os.getcwd()}")

# Using json module
data = {"name": "John", "age": 30}
json_string = json.dumps(data)
print(f"JSON string: {json_string}")
```

**Installing External Libraries (pip):**
```bash
pip install requests
pip install pandas numpy
```

Then use:
```python
import requests
import pandas as pd
import numpy as np
```

---

## Comparison Table

| Aspect | C | C++ | C# | Python |
|--------|---|-----|----|----|
| **Keyword** | `#include` | `#include` | `using` | `import` / `from` |
| **File Extension** | `.h` | `.h` or none | N/A (namespaces) | `.py` |
| **Standard Lib Syntax** | `<stdio.h>` | `<iostream>` | `using System;` | `import os` |
| **User-defined** | `"myfile.h"` | `"myfile.h"` | `using MyNamespace;` | `import mymodule` |
| **Package Manager** | N/A | vcpkg, Conan | NuGet | pip, conda |
| **Library Files** | `.a`, `.so`, `.lib` | `.a`, `.so`, `.lib` | `.dll` (assemblies) | `.py`, `.pyc` |

