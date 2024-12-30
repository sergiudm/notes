Smart pointers in C++ are a type of pointer that provides automatic, dynamic memory management. They are a key feature of modern C++ programming, and they help to prevent common memory-related bugs such as memory leaks, dangling pointers, and double free errors.

There are three main types of smart pointers in C++:

1. `std::shared_ptr`: This is a smart pointer that retains shared ownership of an object through a pointer. Several `std::shared_ptr` objects may own the same object, and the object is destroyed and its memory deallocated when the last `std::shared_ptr` owning it is destroyed.
2. `std::unique_ptr`: This is a smart pointer that owns and manages another object through a pointer and disposes of that object when the `std::unique_ptr` goes out of scope. The object is owned by only one `std::unique_ptr` at a time, and the ownership can be transferred from one `std::unique_ptr` to another, but not shared.
3. `std::weak_ptr`: This is a smart pointer that does not control the lifetime of the object it points to. It can be used to access an object managed by a `std::shared_ptr`, but it does not prevent the object from being destroyed. This is useful for implementing caches or observer patterns.

Here's an example of how to use `std::unique_ptr`:

```cpp
#include <memory>
#include <string>

struct MyClass {
    MyClass(const std::string& name) : name_(name) {}
    std::string name_;
};

int main() {
    auto ptr = std::make_unique<MyClass>("Hello, World!");
    // ptr is a std::unique_ptr<MyClass> that points to a MyClass object
    // with the name_ "Hello, World!"
    return 0;
}
```

In this example, `std::make_unique` creates a `MyClass` object with the argument `"Hello, World!"` and returns a `std::unique_ptr` to that object. When `ptr` goes out of scope, the `MyClass` object will be automatically destroyed.

Smart pointers are a powerful feature of C++, and they can help to make your code safer and easier to maintain. However, they do have some overhead compared to raw pointers, so they should be used judiciously. In general, you should use smart pointers for dynamic memory management, and you should use raw pointers for non-owning pointers or for low-level programming.