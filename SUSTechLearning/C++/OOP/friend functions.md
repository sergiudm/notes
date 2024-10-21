# what are friend functions

In C++, a friend function is a function that is not a member of a class, but has access to the private and protected members of the class. Friend functions are declared inside the class definition using the `friend` keyword.

Here's an example of a class with a friend function:
```cpp
class MyClass {
private:
    int x;
public:
    MyClass(int x) : x(x) {}
    friend void printX(const MyClass& obj);
};

void printX(const MyClass& obj) {
    std::cout << "x = " << obj.x << std::endl;
}
```
In this example, the `printX` function is declared as a friend of the `MyClass` class. The `printX` function is not a member of the `MyClass` class, but it has access to the private member `x` of `MyClass`. The `printX` function takes a constant reference to a `MyClass` object as its parameter, and prints the value of `x` to the console.

Friend functions can be useful in situations where you want to allow a function to access the private or protected members of a class, but you don't want to make the function a member of the class. For example, you might want to define a function that compares two objects of a class based on their private members, but you don't want to make the comparison function a member of the class.

It's important to use friend functions judiciously, because they can break the encapsulation of a class and make the code more difficult to maintain. In general, you should only use friend functions when they are necessary to achieve a specific design goal, and you should carefully consider the implications of granting a function access to the private members of a class.