# Object-Oriented Programming in C++, Java, and C#

## What is a Class?
A **Class** is a user-defined type, similar to structures, which is a collection of members (variables and functions).

### Syntax:
```cpp
struct <Name>
{
    // variables
};

class <Name>
{
    // variables and functions
};
```

### Examples of Predefined Data Types:
```cpp
int i;
float f;
string s;
char ch;
bool b;
```
- `int`, `float`, `string`, `char`, `bool` are predefined data types.

### Predefined Structs and Classes:
```cpp
struct int 
{
    // ...
};

struct float 
{
    // ...
};

struct char 
{
    // ...
};

struct bool 
{
    // ...
};

class string 
{
    // ...
};
```

### User-Defined Types:
```cpp
struct Student 
{
    int id;
    char Name[30];
    float Marks, Fees;
};

class Employee
{
    int id;
    string Name, Job;
    float Salary;
    // Functions can also be defined here
};
```

### Scalar vs Complex Types:
- **Scalar Types**: `int`, `float`, `string`, `char`, `bool` (store a single value).
- **Complex Types**: `Student`, `Employee` (store multiple values).

### Consuming a Type:
Types cannot be consumed directly as they do not have memory allocated for storing values. To consume a type, create a copy of it:
```cpp
int i = 100;  // Valid (predefined and scalar type)
int = 100;   // Invalid (no memory allocated)
i = 100; // Invalid (no memory allocated)
char ch = 'A'; // Valid (predefined and scalar type)
string s;     // Copy of type string (user-defined type and complex type)
Student ss;   // Copy of type Student (user-defined type and complex type)
Employee emp; // Copy of type Employee (user-defined type and complex type)
```
- Copies of scalar types are called **Variables**.
- Copies of complex types are called **Objects** or **Instances**.

---

## C Program Example:
```c
int Add(int a, int b)
{
    int c = a + b;
    return c;
}

int Sub(int a, int b)
{
    int c = a - b;
    return c;
}

void main()
{
    int result1 = Add(100, 50);
    int result2 = Sub(75, 25);
}
```

## C++ Program Example:
```cpp
class Math 
{
    int Add(int a, int b)
    {
        int c = a + b;
        return c;
    }

    int Sub(int a, int b)
    {
        int c = a - b;
        return c;
    }
};

void main()
{
    Math obj;
    int result1 = obj.Add(100, 50);
    int result2 = obj.Sub(75, 25);
}
```

### Criticism of C++:
C++ faced criticism for not being fully object-oriented because the `main` function is not part of a class.

---

## Java: Static and Non-Static Members
In Java, members of a class are divided into two categories:
1. **Non-Static Members**: Members that require an object for initialization and execution. By default, all members are non-static unless specified STATIC explicitly.
2. **Static Members**: Prefixed with the `static` keyword and do not require an object for initialization and execution.

### Example:
```java
class Test 
{
    int x = 100;                 // Non-static variable
    static int y = 200;          // Static variable

    int Add(int a, int b)        // Non-static method
    {
        int c = a + b;
        return c;
    }

    static int Sub(int a, int b) // Static method
    {
        int c = a - b;
        return c;
    }

    public static void main(String[] args)
    {
        Test obj = new Test();   // Object of class should be created to access non-static members as Test is a non-static member
        int result1 = obj.Add(100, 50); // Non-static method call using object
        int result2 = Test.Sub(75, 25); 
    }
}
```

### Example of Static Function in C#:
```csharp
class Demo
{
    public static int staticVar = 10;
    public int instanceVar = 20;

    public static void StaticMethod()
    {
        Console.WriteLine("I'm static!");
    }

    public void InstanceMethod()
    {
        Console.WriteLine("I'm an instance method!");
    }

    static void Main()
    {
        // Static: accessed directly using class name
        Console.WriteLine(Demo.staticVar);
        Demo.StaticMethod();

        // Instance: need to create an object
        Demo obj = new Demo();
        Console.WriteLine(obj.instanceVar);
        obj.InstanceMethod();
    }
}

```


### Key Points:
- Non-static members require an object for execution.
- Static members can be accessed using the class name.

---

## Java Program Example:
```java
class Example 
{
    // Collection of Members (Static & Non-Static)
    public static void main(String[] args)
    {
        // Create the object of class
        // Call non-static members using the object
        // Call static members by prefixing the class name
    }
}
```

---

## C# Program Example:
```csharp
class Example 
{
    // Collection of Members (Static & Non-Static)
    static void Main()
    {
        // Create an instance of the class
        // Call non-static members using the instance
        // Call static members by prefixing the class name
    }
}
```

### Note:
The `Main` function in C# must always be static so that an instance is not required to execute it.
In Java or .Net languages, if all the class contains only Main method in it, we dont require creating object or instance of that class to run the class. 
In C# there is a special class called as Object thats why we dont call object instead we call instance of the class.
