# function templates 
Function templates in C++ are a powerful feature that allows you to create functions that can work with different data types. This is a form of generic programming. Here's a simple breakdown:

1. **Syntax**: A function template begins with the keyword `template` followed by a `typename` or `class` keyword, which is then followed by an identifier that represents the type parameter. The function declaration or definition then follows, where the type parameter can be used in place of actual data types.

   Here's an example:

   ```cpp
   template <typename T>
   T max(T a, T b) {
       return (a > b) ? a : b;
   }
   ```

   In this example, `T` is a type parameter that can be replaced by any actual data type when the function is called.

2. **Function Call**: When you call a function template, the compiler generates a specific version of the function based on the arguments you provide. This process is known as template argument deduction. For example:

   ```cpp
   int main() {
       int x = 10, y = 20;
       cout << "Max is: " << max(x, y) << endl;  // Calls max<int>

       double a = 10.5, b = 20.7;
       cout << "Max is: " << max(a, b) << endl;  // Calls max<double>

       return 0;
   }
   ```

   In this case, the compiler generates two versions of the `max` function: `max<int>` and `max<double>`.

3. **Advantages**: Function templates allow you to write generic code, which can reduce code duplication and improve maintainability. They also provide type safety, as the compiler generates specific versions of the function for each type.

4. **Limitations**: Function templates can't handle all types equally. For example, the `max` function above won't work with types that don't support the `>` operator. Also, function templates can lead to code bloat, as the compiler generates a new version of the function for each type.

# class templates 

Class templates in C++ are a feature of the language that allows you to create generic classes, similar to how function templates allow you to create generic functions. This is a key part of the language's support for generic programming. Here's a simple breakdown:

1. **Syntax**: A class template begins with the keyword `template` followed by a `typename` or `class` keyword, which is then followed by an identifier that represents the type parameter. The class definition then follows, where the type parameter can be used in place of actual data types.

   Here's an example:

   ```cpp
   template <typename T>
   class Stack {
   private:
       T data[100];
       int top;
   public:
       Stack() { top = 0; }
       void push(T value) { data[top++] = value; }
       T pop() { return data[--top]; }
   };
   ```

   In this example, `T` is a type parameter that can be replaced by any actual data type when an object of the class is created.

2. **Object Creation**: When you create an object from a class template, the compiler generates a specific version of the class based on the type you provide. This process is known as template argument deduction. For example:

   ```cpp
   int main() {
       Stack<int> intStack;  // Creates a stack of ints
       Stack<double> doubleStack;  // Creates a stack of doubles

       intStack.push(10);
       doubleStack.push(10.5);

       return 0;
   }
   ```

   In this case, the compiler generates two versions of the `Stack` class: `Stack<int>` and `Stack<double>`.

3. **Advantages**: Class templates allow you to write generic code, which can reduce code duplication and improve maintainability. They also provide type safety, as the compiler generates specific versions of the class for each type.

4. **Limitations**: Class templates can't handle all types equally. For example, the `Stack` class above won't work with types that can't be copied or assigned. Also, class templates can lead to code bloat, as the compiler generates a new version of the class for each type.