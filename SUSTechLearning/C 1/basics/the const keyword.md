In C++, `const` is a keyword used to declare variables, function parameters, and member functions as constant. When a variable or object is declared as `const`, its value cannot be modified after it is initialized.

For example, consider the following code snippet:
```c
int num = 10;
const int *ptr = &num;
```
In this code, `num` is a regular variable, but `ptr` is a pointer to a constant integer. This means that the value of `num` cannot be modified through the `ptr` pointer. If you try to modify the value of `num` through `ptr`, the compiler will generate an error.

Similarly, when a function parameter is declared as `const`, the function cannot modify the value of the argument passed to it. This is useful for ensuring that a function does not modify its input arguments.

In the context of member functions, `const` is used to indicate that a member function does not modify the state of the object it is called on. A member function declared as `const` cannot modify any non-`mutable` data members of the object, and it cannot call any non-`const` member functions. This is useful for ensuring that a function does not modify the object it is called on, and allows the function to be called on `const` objects.

For example, consider the following class:
```csharp
class MyClass {
public:
    MyClass(int val) : value(val) {}

    int getValue() const {
        return value;
    }

private:
    int value;
};
```
In this class, the `getValue()` member function is declared as `const`, which means that it cannot modify the `value` data member of the object it is called on. This allows the function to be called on `const` objects of the `MyClass` type, like this:
```scss
const MyClass obj(42);
int val = obj.getValue();
```
Here, the `obj` object is declared as `const`, which means that its `value` data member cannot be modified. However, since the `getValue()` member function is declared as `const`, it can be called on `const` objects, and it returns the value of the `value` data member without modifying it.

## const and pointers:
```cpp
int num = 1, another = 2;
const int* p1 = &num;
*p1 = 3//error 
int *const p2 = &num;
*p2 = 3//okay

```