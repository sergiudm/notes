在 C++ 中，作用域解析运算符（Scope Resolution Operator）由两个冒号 `::` 组成。这个运算符用于指定一个作用域，通常用于全局作用域、命名空间、类或结构体的作用域中。它允许你访问在特定作用域中定义的变量、函数、类或其他实体。

作用域解析运算符有以下几种用途：

1. **全局作用域**：当你在一个函数或类内部，想要引用全局作用域中的变量或函数时，你需要使用作用域解析运算符。

   ```cpp
   int globalVar = 10; // 在全局作用域

   void function() {
       int localVar = 20; // 在函数作用域
       std::cout << ::globalVar; // 访问全局变量
       std::cout << localVar; // 错误：localVar 在局部作用域
   }
   ```

2. **命名空间**：在命名空间中，作用域解析运算符用于访问特定命名空间中的成员。

   ```cpp
   namespace MyNamespace {
       int value = 30;
   }

   int main() {
       std::cout << MyNamespace::value; // 访问命名空间中的变量
       return 0;
   }
   ```

3. **类和对象**：在类的定义中，作用域解析运算符用于指定类成员的初始值，或者在类外部定义成员函数的实现。

   ```cpp
   class MyClass {
   public:
       MyClass() : myVar(0) {} // 使用作用域解析运算符设置成员变量的初始值

       void setVar(int value) {
           myVar = value;
       }

   private:
       int myVar;
   };

   void setMyClassVar(MyClass& obj, int value) {
       obj.setVar(value); // 在类外部调用成员函数
   }
   ```

4. **类型定义**：在类或命名空间中，作用域解析运算符也用于指定类型的完整作用域名称。

   ```cpp
   namespace MyNamespace {
       struct MyStruct {
           int value;
       };
   }

   int main() {
       MyNamespace::MyStruct myStruct; // 指定完整的类型名称
       return 0;
   }
   ```

作用域解析运算符是 C++ 中一个非常重要的特性，它使得程序员能够精确地控制变量和函数的作用域，从而避免命名冲突，并提供更清晰的代码结构。