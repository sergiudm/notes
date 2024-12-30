# how to apply inheritance in C++
In C++, inheritance is a mechanism by which one class can acquire the properties and methods of another class. To apply inheritance in C++, you can use the following steps:

1. Define a base class: The base class (also called the parent class or superclass) is a class that contains common properties and methods that you want to share among multiple derived classes. Here's an example of a base class:
```csharp
class Shape {
public:
    Shape(double width, double height) : width(width), height(height) {}
    virtual double area() const = 0;
protected:
    double width;
    double height;
};
```
In this example, the `Shape` class has a constructor that takes a width and height, and a pure virtual function `area()` that must be implemented by any derived classes. The `width` and `height` members are declared as protected, so they can be accessed by derived classes.

2. Define a derived class: The derived class (also called the child class or subclass) is a class that inherits properties and methods from the base class, and can also add its own properties and methods. Here's an example of a derived class:
```csharp
class Rectangle : public Shape {
public:
    Rectangle(double width, double height) : Shape(width, height) {}
    double area() const override {
        return width * height;
    }
};
```
In this example, the `Rectangle` class is derived from the `Shape` class using the `public` access specifier. The `Rectangle` class has a constructor that takes a width and height, and overrides the `area()` function to calculate the area of a rectangle.

3. Create objects of the derived class: Once you have defined a derived class, you can create objects of that class and use them just like any other object. Here's an example:
```vbnet
Rectangle rect(4.0, 5.0);
double area = rect.area();
std::cout << "The area of the rectangle is: " << area << std::endl;
```
In this example, we create a `Rectangle` object with a width of 4.0 and a height of 5.0, and then call the `area()` function to calculate its area. The output will be:
```vbnet
The area of the rectangle is: 20
```

That's a basic overview of how to apply inheritance in C++. Inheritance is a powerful mechanism that can help you create more modular and reusable code. However, it's important to use inheritance judiciously, and to carefully consider the design of your base and derived classes.

## when declaring attributes in a class, if there is no access specifier, who will be able to access the attribute?
In C++, if there is no access specifier specified for an attribute (or member variable) in a class, the attribute is considered to have "private" access by default. This means that the attribute can only be accessed by member functions of the same class, and not by functions or objects outside of the class.

## multiple inheritance 
```cpp
class <派生类名>:<继承方式1><基类名1>,<继承方式2><基类名2>,…
{
<派生类类体>
};
```
example :
```cpp
#include <iostream>
 
using namespace std;
 
// 基类 Shape
class Shape 
{
   public:
      void setWidth(int w)
      {
         width = w;
      }
      void setHeight(int h)
      {
         height = h;
      }
   protected:
      int width;
      int height;
};
 
// 基类 PaintCost
class PaintCost 
{
   public:
      int getCost(int area)
      {
         return area * 70;
      }
};
 
// 派生类
class Rectangle: public Shape, public PaintCost
{
   public:
      int getArea()
      { 
         return (width * height); 
      }
};
 
int main(void)
{
   Rectangle Rect;
   int area;
 
   Rect.setWidth(5);
   Rect.setHeight(7);
 
   area = Rect.getArea();
   
   // 输出对象的面积
   cout << "Total area: " << Rect.getArea() << endl;
 
   // 输出总花费
   cout << "Total paint cost: $" << Rect.getCost(area) << endl;
 
   return 0;
}
```

## the "explicit" keyword
In C++, the `explicit` keyword is used to prevent implicit type conversions when constructing objects or calling functions with a single argument.

When a constructor or a function is declared with the `explicit` keyword, it means that the compiler cannot perform implicit type conversions to call that constructor or function. Instead, the programmer must provide an explicit conversion.

For example, consider the following class:
```csharp
class MyClass {
public:
    explicit MyClass(int val) : value(val) {}

    int getValue() const {
        return value;
    }

private:
    int value;
};
```
In this class, the constructor is declared with the `explicit` keyword, which means that the compiler cannot perform implicit type conversions to construct a `MyClass` object from an integer value.

If you try to pass an integer value to a function that expects a `MyClass` object, the compiler will generate an error, like this:
```c
void printValue(const MyClass& obj) {
    std::cout << obj.getValue() << std::endl;
}

int main() {
    int val = 42;
    printValue(val);  // Error: cannot convert int to MyClass
    return 0;
}
```
To fix this error, you need to provide an explicit conversion from `int` to `MyClass`, like this:
```c
int main() {
    int val = 42;
    MyClass obj(val);
    printValue(obj);  // OK
    return 0;
}
```
The `explicit` keyword can help prevent unintended implicit conversions and make the code more explicit and easier to understand. It is especially useful when defining constructors or functions that take a single argument, as it can prevent unexpected behavior when passing arguments of different types.