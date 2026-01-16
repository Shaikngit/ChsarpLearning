# Four Pillars of OOP

The four fundamental principles that every OOP language should follow are:

## 1. Encapsulation
Bundling data (fields) and methods that operate on that data within a single unit (class), and restricting direct access to some components. This is typically achieved through access modifiers (public, private, protected).

## 2. Abstraction
Hiding complex implementation details and showing only the necessary features of an object. This is implemented through abstract classes and interfaces.

## 3. Inheritance
The mechanism where a new class (derived/child class) inherits properties and behaviors from an existing class (base/parent class), promoting code reusability.

## 4. Polymorphism
The ability of objects to take multiple forms. This allows methods to do different things based on the object they are acting upon, implemented through method overloading (compile-time) and method overriding (runtime).

---

These four pillars form the foundation of object-oriented programming and are essential concepts in languages like C#, Java, C++, Python, and others.

## What is a Class?

A class is a user-defined type which is, in turn, a collection of members:
- **Fields** - Variables that hold data
- **Methods** - a set of statements that perform actions that may or may not return a value
- **Constructors** - Initialize object instances
- **Finalizers** - Clean up resources when objects are destroyed
- **Properties** - Provide controlled access to fields
- **Indexers** - Allow array-like access to objects
- **Events** - Enable notification and communication between objects
- **Destructors** - Handle cleanup of resources

---

Fields:- Fields are variables that hold data associated with a class or object. They represent the state or attributes of the object.

Syntax to write a field:

    [access_modifier] <data_type> <field_name>;

    [] -> Optional
    <> -> Mandatory

    Example: int age;

Methods:- Methods are named blocks of code that perform specific actions or operations. They define the behavior of the object.It contains a set of instructions that are executed when the method is called.

   Functions: Its a named block of code that performs a specific task and can return a value. 

   Methods vs Functions: Methods and Functions are same but functions must return a value where as methods may or may not return a value. 

Methods are of 4 types 

1. Value returning methods: These methods return a value after execution. The return type is specified in the method signature. (Functions)

2. Value returning methods with parameters: These methods accept input parameters and return a value after execution. The parameters are specified in the method signature along with the return type. (Functions)

3. Non-value returning methods: These methods do not return any value after execution. They are called as Sub-Routines 

4. Non-value returning methods with parameters: These methods accept input parameters but do not return any value after execution. They are also called as Sub-Routines




Syntaxt to write a method:

    [<access_modifier>] void|type <method_name>([parameter_list])
    {
        // Method body
    }

    [] -> Optional
    <> -> Mandatory
    () -> Mandatory (even if there are no parameters)
    | -> Either-or

    Eg:- public int Add(int a, int b)
    {
        return a + b;
    }

## Examples of Different Method Types

### 1. Value Returning Methods with Parameters (Functions)
These methods accept parameters and return a value.

    public int Multiply(int x, int y)
    {
        return x * y;
    }

    public double CalculateArea(double radius)
    {
        return 3.14 * radius * radius;
    }

    public string Greet(string name)
    {
        return "Hello, " + name;
    }

### 2. Value Returning Methods without Parameters (Functions)
These methods do not accept parameters but return a value.

    public int GetCount()
    {
        return 42;
    }

    public string GetCurrentDate()
    {
        return DateTime.Now.ToString();
    }

    public bool IsValid()
    {
        return true;
    }

### 3. Non-Value Returning Methods with Parameters (Sub-Routines)
These methods accept parameters but do not return any value.

    public void PrintMessage(string message)
    {
        Console.WriteLine(message);
    }

    public void SetAge(int age)
    {
        this.age = age;
    }

    public void DisplayDetails(string name, string email)
    {
        Console.WriteLine("Name: " + name);
        Console.WriteLine("Email: " + email);
    }

### 4. Non-Value Returning Methods without Parameters (Sub-Routines)
These methods do not accept parameters and do not return any value.

    public void DisplayGreeting()
    {
        Console.WriteLine("Welcome!");
    }

    public void ResetValues()
    {
        age = 0;
        name = "";
    }

    public void ShowMenu()
    {
        Console.WriteLine("1. Add");
        Console.WriteLine("2. Subtract");
    }

---

## Understanding Methods in Detail

**Method:** It is a named block of code which performs an action whenever it is called and after completion of that action it may or may not return any result of that action, and they are divided into 2 categories:

1. **Value returning method (Function)**
2. **Non-value returning method (Sub-Routine)**

### Syntax to Define a Method

```csharp
[<modifiers>] void|type <Name>([<Parameter List>])
{
    // Stmt's or Logic
}
```

Where:
- `[]` => Optional
- `<>` => Any/Mandatory

**Modifiers** are some special keywords which can be used on a method if required (optional) like:
- `public`, `internal`, `protected`, `private`
- `static`, `virtual`, `abstract`, `override`, `sealed`, `partial`

**void|type** is to tell whether our method is value returning or non-value returning:
- `void` implies that the method is non-value returning
- If we want our method to return any value, we need to specify the type of value it has to return by using the "type"

#### Examples of Non-Value Returning Methods:
```csharp
public static void Clear()
public static void WriteLine(<type> var)
```

#### Examples of Value Returning Methods:
```csharp
public static string ReadLine()
```

> **Note:** The return type of a method need not be any pre-defined type like `int`, `float`, `char`, `bool`, `DateTime`, `Guid`, `string`, `object`, etc., but it can also be any user-defined type.

**<Name>** refers to the "ID" of the method for identification.

**[<Parameter List>]:** If required, we can pass parameters to our methods for execution, and parameters of a method will make an action dynamic.

**For example:**
```csharp
GetLength(0)  // Returns rows	
GetLength(1)  // Returns columns
```

### Syntax to Pass Parameters to a Method

```csharp
[ref | out] [params] <type> <var> [= default value] [,...n]
```

---

## Method Definition and Execution

### Where Should We Define Methods?

**Answer:** As per the rule of Encapsulation, methods should be defined inside of a class.

### How to Execute a Method Defined Under a Class?

**Answer:** The methods that are defined in a class must be explicitly called for execution, except `Main` method because `Main` is implicitly called by CLR.

### How to Call a Method Defined in a Class?

**Answer:** Methods are of 2 types:

1. **Non-Static**
2. **Static**

> **Note:** By default, every method of a class is non-static only, and if we want to make it as static, we need to prefix the `static` modifier before the method as we are doing in case of `Main` method.

To call a method that is defined under any class:
- For **non-static methods**: We require to create instance of that class
- For **static methods**: We can call them directly by prefixing class name

**Example:** `WriteLine` and `ReadLine` are static methods in class `Console` which we are calling in our code as:
```csharp
Console.WriteLine()
Console.ReadLine()
```

---

## Creating Instance of a Class

### How to Create Instance of a Class?

**Syntax:**
```csharp
<class_name> <instance_name> = new <class_name>([<List of values>])
```

**Example:**
```csharp
// Declaration and Initialization
Program p = new Program();

// OR

// Declaration
Program p;
// Initialization
p = new Program();
```

> **Note:** Without using the `new` keyword we can't create the instance of a class in Java and .NET Languages.

### Where Should We Create the Instance of a Class?

**Answer:** Instance of a class can be created either within the same class or in other classes also.

**If instance is created in the same class:**
- It should be created under any static block
- Generally, we create instances in `Main` method because of 2 reasons:
  1. Entry Point of the program
  2. It is a static block

**If instance is created in another class:**
- Then it can be created in any block of that new class i.e., either static or non-static also

---

## Complete Example: Working with Methods

To try all the above concepts, create a new Console App project in Visual Studio naming it as **"OOPSProject"**, delete all the code that is present in the default file `Program.cs` and write the below code:

```csharp
namespace OOPSProject
{
  internal class Program
  {
    //Non-value returning method without parameters 
    public void Test1() //Static in behavior  
    {
      int x = 5;
      for (int i = 1; i <= 10; i++)
      {
        Console.WriteLine($"{x} * {i} = {x * i}");
      }
    }

    //Non-value returning method with parameters
    public void Test2(int x, int ub) //Dynamic in behavior      
    {
      for (int i = 1; i <= ub; i++)
      {
        Console.WriteLine($"{x} * {i} = {x * i}");
      }
    }

    //Value returning method without parameters
    public string Test3() //Static in behavior  
    {
      string str = "hello world";
      str = str.ToUpper();
      return str;
    }

    //Value returning method with parameters
    public string Test4(string str) //Dynamic in behavior  
    {
      str = str.ToUpper();
      return str;
    }

    static void Main()
    {
      //Creating instance of the class.
      Program p = new Program();

      //Calling non-value returning methods.
      p.Test1();
      Console.WriteLine();
      p.Test2(8, 15);
      Console.WriteLine();

      //Calling value returning methods
      string s1 = p.Test3();
      Console.WriteLine(s1);
      string s2 = p.Test4("hello india");
      Console.WriteLine(s2);
      Console.ReadLine();
    }
  }
}
```

---
