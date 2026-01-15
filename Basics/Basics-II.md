## ➤ What is the difference between struct and class in C++ and C#?

### C++
- **Struct**: In C++, a `struct` is similar to a `class`, but its members are public by default. Example:
  ```cpp
  struct Point {
      int x, y;
      void display() {
          printf("Point(%d, %d)\n", x, y);
      }
  };
  int main() {
      Point p = {10, 20};
      p.display();
      return 0;
  }
  ```
- **Class**: A `class` in C++ has its members private by default. Example:
  ```cpp
  class Point {
  private:
      int x, y;
  public:
      Point(int x, int y) : x(x), y(y) {}
      void display() {
          printf("Point(%d, %d)\n", x, y);
      }
  };
  int main() {
      Point p(10, 20);
      p.display();
      return 0;
  }
  ```

### C#
- **Struct**: In C#, a `struct` is a value type. Example:
  ```csharp
  struct Point {
      public int X, Y;
      public void Display() {
          Console.WriteLine($"Point({X}, {Y})");
      }
  }
  class Program {
      static void Main(string[] args) {
          Point p = new Point { X = 10, Y = 20 };
          p.Display();
      }
  }
  ```
- **Class**: A `class` in C# is a reference type. Example:
  ```csharp
  class Point {
      public int X, Y;
      public void Display() {
          Console.WriteLine($"Point({X}, {Y})");
      }
  }
  class Program {
      static void Main(string[] args) {
          Point p = new Point { X = 10, Y = 20 };
          p.Display();
      }
  }
  ```

### ➤ Summary
| Language | Struct                          | Class                          |
|----------|---------------------------------|--------------------------------|
| C++      | Public members by default       | Private members by default     |
| C#       | Value type, stored on stack     | Reference type, stored on heap |