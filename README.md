# 100 C++ Interview Questions


---

## Theory Questions

1. **What is the difference between C++ and C?**
   - **Explanation**: C++ is an extension of C with additional features like classes, inheritance, polymorphism, and more. C is procedural, while C++ supports both procedural and object-oriented programming.

2. **What are the basic features of C++?**
   - **Explanation**: Key features include object-oriented programming, encapsulation, inheritance, polymorphism, templates, and exception handling.

3. **What is encapsulation in C++?**
   - **Explanation**: Encapsulation is the concept of wrapping data (variables) and functions (methods) into a single unit called a class. It hides the internal state and only exposes the necessary functionality.

4. **Explain inheritance in C++.**
   - **Explanation**: Inheritance is a mechanism where a new class derives properties and behavior (methods) from an existing class. It helps in code reusability and establishing a hierarchical relationship between classes.

5. **What is polymorphism in C++?**
   - **Explanation**: Polymorphism allows objects of different classes to be treated as objects of a common base class. It supports method overriding and overloading, enabling methods to have different implementations based on the object’s class.

6. **What are constructors and destructors in C++?**
   - **Explanation**: Constructors are special member functions that initialize objects when they are created. Destructors are special member functions that clean up resources when an object is destroyed.

7. **What is the purpose of the `virtual` keyword?**
   - **Explanation**: The `virtual` keyword allows for dynamic method resolution, enabling polymorphism. It ensures that the correct overridden method is called at runtime.

8. **What is the difference between a class and a struct in C++?**
   - **Explanation**: In C++, the primary difference is access control: members of a class are private by default, while members of a struct are public by default.

9. **What is the role of the `static` keyword in C++?**
   - **Explanation**: The `static` keyword defines variables or methods that are shared across all instances of a class or function. Static members have a single instance that is shared among all objects.

10. **What is a namespace in C++?**
    - **Explanation**: Namespaces prevent name conflicts by encapsulating identifiers (e.g., functions, classes) into distinct logical groups. They help avoid naming collisions in larger projects.

11. **Explain exception handling in C++.**
    - **Explanation**: Exception handling in C++ involves using `try`, `catch`, and `throw` keywords to manage runtime errors. `try` blocks contain code that may throw an exception, `catch` blocks handle exceptions, and `throw` is used to generate exceptions.

12. **What is a pure virtual function?**
    - **Explanation**: A pure virtual function is a function declared in a base class that has no implementation and is meant to be overridden in derived classes. It makes the base class abstract.

13. **What are templates in C++?**
    - **Explanation**: Templates allow for writing generic and reusable code. They enable functions and classes to operate with different data types without being rewritten for each type.

14. **What is operator overloading?**
    - **Explanation**: Operator overloading allows developers to define custom behavior for operators (e.g., `+`, `-`) when used with user-defined types (e.g., classes).

15. **What is RAII (Resource Acquisition Is Initialization)?**
    - **Explanation**: RAII is a programming idiom where resources are acquired and released through object lifetimes. This ensures resource management is handled automatically.

16. **What is a smart pointer in C++?**
    - **Explanation**: Smart pointers are objects that manage the lifetime of dynamically allocated resources. They include `std::unique_ptr`, `std::shared_ptr`, and `std::weak_ptr`, and help prevent memory leaks and dangling pointers.

17. **What is the difference between `new` and `malloc`?**
    - **Explanation**: `new` is an operator that allocates memory and calls the constructor, while `malloc` is a C-style function that allocates raw memory without calling constructors.

18. **What is a lambda function in C++?**
    - **Explanation**: A lambda function is an anonymous function that can be defined inline. It allows for defining local functions in a concise manner, especially useful for callbacks and STL algorithms.

19. **What is multiple inheritance?**
    - **Explanation**: Multiple inheritance allows a class to inherit from more than one base class. It can lead to complexities like the diamond problem, where ambiguity arises from multiple inheritance paths.

20. **What is the diamond problem in C++?**
    - **Explanation**: The diamond problem occurs in multiple inheritance when two base classes of a derived class have a common base class, leading to ambiguity in which base class’s members should be used.

21. **What is dynamic casting in C++?**
    - **Explanation**: `dynamic_cast` is used for safe downcasting and cross-casting between polymorphic types. It performs runtime checks and returns `nullptr` if the cast is invalid.

22. **What is a virtual destructor?**
    - **Explanation**: A virtual destructor ensures that the derived class’s destructor is called when an object is deleted through a base class pointer. This prevents resource leaks.

23. **What is the difference between `const` and `constexpr`?**
    - **Explanation**: `const` defines constants whose values are known at runtime, while `constexpr` defines constants whose values are known at compile-time and can be used in constant expressions.

24. **What is a move constructor?**
    - **Explanation**: A move constructor transfers ownership of resources from a temporary object to a new object, optimizing performance by avoiding unnecessary copies.

25. **What are the main differences between stack and heap memory?**
    - **Explanation**: Stack memory is used for static memory allocation with a last-in, first-out (LIFO) order, while heap memory is used for dynamic memory allocation with manual management.

## Code-Based Questions

26. **What is the output of the following code?**
    ```cpp
    #include <iostream>
    using namespace std;
    
    class Base {
    public:
        virtual void show() { cout << "Base class" << endl; }
    };
    
    class Derived : public Base {
    public:
        void show() override { cout << "Derived class" << endl; }
    };
    
    int main() {
        Base* b;
        Derived d;
        b = &d;
        b->show();
        return 0;
    }
    ```
    **Output**: `Derived class`
    **Explanation**: The `show` method is overridden in the `Derived` class, and the base class pointer `b` points to a `Derived` object. Thus, the overridden method in `Derived` is called.

27. **What does the following code print?**
    ```cpp
    #include <iostream>
    using namespace std;
    
    void func(int x) {
        cout << x << endl;
    }
    
    void func(double x) {
        cout << x << endl;
    }
    
    int main() {
        func(5);
        func(5.5);
        return 0;
    }
    ```
    **Output**:
    ```
    5
    5.5
    ```
    **Explanation**: Function overloading allows for multiple `func` definitions with different parameter types.

28. **What is the output of this code?**
    ```cpp
    #include <iostream>
    using namespace std;
    
    int main() {
        int x = 10;
        int* p = &x;
        cout << *p << endl;
        *p = 20;
        cout << x << endl;
        return 0;
    }
    ```
    **Output**:
    ```
    10
    20
    ```
    **Explanation**: The pointer `p` points to `x`. Changing the value via the pointer affects the original variable.

29. **What does the following code do?**
    ```cpp
    #include <iostream>
    using namespace std;
    
    class Test {
    public:
        Test() { cout << "Constructor called" << endl; }
        ~Test() { cout << "Destructor called" << endl; }
    };
    
    int main() {
        Test t;
        return 0;
    }
    ```
    **Output**:
    ```
    Constructor called
    Destructor called
    ```
    **Explanation**: The constructor is called when the object `t` is created, and the destructor is called when `t` goes out of scope.

30. **What is the result of this code?**
    ```cpp
    #include <iostream>
    using namespace std;
    
    int add(int a, int b) {
        return a + b;
    }
    
    double add(double a, double b) {
        return a + b;
    }
    
    int main() {
        cout << add(1, 2) << endl;
        cout << add(1.1, 2.2) << endl;
        return 0;
    }
    ```
    **Output**:
    ```
    3
    3.3
    ```
    **Explanation**: Function overloading allows for the same function name with different parameter types.

31. **What will this code output?**
    ```cpp
    #include <

iostream>
    using namespace std;
    
    int main() {
        int arr[3] = {1, 2, 3};
        for (int i : arr) {
            cout << i << " ";
        }
        return 0;
    }
    ```
    **Output**: `1 2 3 `
    **Explanation**: Range-based for loop iterates through the array and prints each element.

32. **What does this code print?**
    ```cpp
    #include <iostream>
    using namespace std;
    
    void func(int x) {
        x = x + 10;
        cout << x << endl;
    }
    
    int main() {
        int num = 5;
        func(num);
        cout << num << endl;
        return 0;
    }
    ```
    **Output**:
    ```
    15
    5
    ```
    **Explanation**: `func` modifies a copy of `num`, not the original variable.

33. **What is the output of this code?**
    ```cpp
    #include <iostream>
    using namespace std;
    
    class A {
    public:
        virtual void func() { cout << "A::func" << endl; }
    };
    
    class B : public A {
    public:
        void func() override { cout << "B::func" << endl; }
    };
    
    int main() {
        A* a = new B();
        a->func();
        delete a;
        return 0;
    }
    ```
    **Output**: `B::func`
    **Explanation**: Virtual functions allow derived class methods to be called through a base class pointer.

34. **What will be the output of this code?**
    ```cpp
    #include <iostream>
    using namespace std;
    
    void swap(int &a, int &b) {
        int temp = a;
        a = b;
        b = temp;
    }
    
    int main() {
        int x = 5, y = 10;
        swap(x, y);
        cout << x << " " << y << endl;
        return 0;
    }
    ```
    **Output**: `10 5`
    **Explanation**: The `swap` function exchanges the values of `x` and `y` using reference parameters.

35. **What does this code print?**
    ```cpp
    #include <iostream>
    using namespace std;
    
    class Base {
    public:
        Base() { cout << "Base constructor" << endl; }
        virtual ~Base() { cout << "Base destructor" << endl; }
    };
    
    class Derived : public Base {
    public:
        Derived() { cout << "Derived constructor" << endl; }
        ~Derived() { cout << "Derived destructor" << endl; }
    };
    
    int main() {
        Base* b = new Derived();
        delete b;
        return 0;
    }
    ```
    **Output**:
    ```
    Base constructor
    Derived constructor
    Derived destructor
    Base destructor
    ```
    **Explanation**: Proper destruction order ensures derived class destructor is called before the base class destructor.

36. **What is the result of this code?**
    ```cpp
    #include <iostream>
    using namespace std;
    
    class Test {
    private:
        int value;
    public:
        Test(int v) : value(v) {}
        int getValue() const { return value; }
    };
    
    int main() {
        const Test t(10);
        cout << t.getValue() << endl;
        return 0;
    }
    ```
    **Output**: `10`
    **Explanation**: The `const` keyword ensures that the object `t` cannot be modified, and `getValue` returns the value.

37. **What does this code print?**
    ```cpp
    #include <iostream>
    using namespace std;
    
    int main() {
        int* ptr = new int(10);
        cout << *ptr << endl;
        delete ptr;
        return 0;
    }
    ```
    **Output**: `10`
    **Explanation**: Dynamically allocated memory is managed using `new` and `delete`. The pointer `ptr` points to the value `10`, which is printed.

38. **What is the output of this code?**
    ```cpp
    #include <iostream>
    using namespace std;
    
    void print(const char* str) {
        cout << str << endl;
    }
    
    int main() {
        print("Hello, world!");
        return 0;
    }
    ```
    **Output**: `Hello, world!`
    **Explanation**: The function `print` takes a constant character pointer and prints the string.

39. **What does this code output?**
    ```cpp
    #include <iostream>
    using namespace std;
    
    class Base {
    public:
        virtual void show() { cout << "Base class" << endl; }
    };
    
    class Derived : public Base {
    public:
        void show() override { cout << "Derived class" << endl; }
    };
    
    void display(Base* b) {
        b->show();
    }
    
    int main() {
        Derived d;
        display(&d);
        return 0;
    }
    ```
    **Output**: `Derived class`
    **Explanation**: The function `display` uses polymorphism to call the `show` method of `Derived`.

40. **What is the result of this code?**
    ```cpp
    #include <iostream>
    using namespace std;
    
    int main() {
        const int arr[3] = {1, 2, 3};
        cout << arr[1] << endl;
        return 0;
    }
    ```
    **Output**: `2`
    **Explanation**: `arr` is a constant array, but its elements can be accessed and read.

41. **What does the following code print?**
    ```cpp
    #include <iostream>
    using namespace std;
    
    class Test {
    public:
        Test() { cout << "Constructor called" << endl; }
        ~Test() { cout << "Destructor called" << endl; }
    };
    
    int main() {
        Test* t = new Test();
        delete t;
        return 0;
    }
    ```
    **Output**:
    ```
    Constructor called
    Destructor called
    ```
    **Explanation**: The constructor and destructor are called for dynamically allocated `Test` object.

42. **What is the output of this code?**
    ```cpp
    #include <iostream>
    using namespace std;
    
    int factorial(int n) {
        if (n <= 1) return 1;
        return n * factorial(n - 1);
    }
    
    int main() {
        cout << factorial(5) << endl;
        return 0;
    }
    ```
    **Output**: `120`
    **Explanation**: The `factorial` function calculates the factorial of a number recursively.

43. **What does this code print?**
    ```cpp
    #include <iostream>
    using namespace std;
    
    void func(int x) {
        cout << "int" << endl;
    }
    
    void func(double x) {
        cout << "double" << endl;
    }
    
    void func(int x, double y) {
        cout << "int and double" << endl;
    }
    
    int main() {
        func(1);
        func(1.0);
        func(1, 1.0);
        return 0;
    }
    ```
    **Output**:
    ```
    int
    double
    int and double
    ```
    **Explanation**: Function overloading resolves to the most specific matching signature.

44. **What is the result of the following code?**
    ```cpp
    #include <iostream>
    using namespace std;
    
    int main() {
        int x = 10;
        int& ref = x;
        ref = 20;
        cout << x << endl;
        return 0;
    }
    ```
    **Output**: `20`
    **Explanation**: The reference `ref` is an alias for `x`, so modifying `ref` affects `x`.

45. **What does this code print?**
    ```cpp
    #include <iostream>
    using namespace std;
    
    class A {
    public:
        A() { cout << "A constructor" << endl; }
        ~A() { cout << "A destructor" << endl; }
    };
    
    class B : public A {
    public:
        B() { cout << "B constructor" << endl; }
        ~B() { cout << "B destructor" << endl; }
    };
    
    int main() {
        B b;
        return 0;
    }
    ```
    **Output**:
    ```
    A constructor
    B constructor
    B destructor
    A destructor
    ```
    **Explanation**: Constructors and destructors are called in the order of inheritance.

46. **What will be the output of this code?**
    ```cpp
    #include <iostream>
    using namespace std;
    
    void print(int* ptr) {
        cout << *ptr << endl;
    }
    
    int main() {
        int val = 30;
        print(&val);
        return 0;
    }
    ```
    **Output**: `30`
    **Explanation**: The `print` function dereferences the pointer to output the value.

47. **What is the result of the following code?**
    ```

cpp
    #include <iostream>
    using namespace std;
    
    class A {
    public:
        virtual void func() { cout << "A::func" << endl; }
    };
    
    class B : public A {
    public:
        void func() override { cout << "B::func" << endl; }
    };
    
    void callFunc(A& a) {
        a.func();
    }
    
    int main() {
        B b;
        callFunc(b);
        return 0;
    }
    ```
    **Output**: `B::func`
    **Explanation**: The function `callFunc` uses polymorphism to call the overridden method in `B`.

48. **What does this code print?**
    ```cpp
    #include <iostream>
    using namespace std;
    
    int main() {
        int arr[] = {1, 2, 3, 4, 5};
        cout << sizeof(arr) / sizeof(arr[0]) << endl;
        return 0;
    }
    ```
    **Output**: `5`
    **Explanation**: The expression calculates the number of elements in the array.

49. **What is the result of this code?**
    ```cpp
    #include <iostream>
    using namespace std;
    
    void print(const int& x) {
        cout << x << endl;
    }
    
    int main() {
        int num = 50;
        print(num);
        return 0;
    }
    ```
    **Output**: `50`
    **Explanation**: The function `print` accepts a constant reference, allowing read-only access to the argument.

50. **What does this code print?**
    ```cpp
    #include <iostream>
    using namespace std;
    
    class Base {
    public:
        Base() { cout << "Base constructor" << endl; }
        virtual ~Base() { cout << "Base destructor" << endl; }
    };
    
    class Derived : public Base {
    public:
        Derived() { cout << "Derived constructor" << endl; }
        ~Derived() { cout << "Derived destructor" << endl; }
    };
    
    int main() {
        Base* b = new Derived();
        delete b;
        return 0;
    }
    ```
    **Output**:
    ```
    Base constructor
    Derived constructor
    Derived destructor
    Base destructor
    ```
    **Explanation**: Correct order of constructors and destructors ensures that the derived class’s destructor is called first.

51. **What will this code output?**
    ```cpp
    #include <iostream>
    using namespace std;
    
    int main() {
        int x = 100;
        const int* p = &x;
        cout << *p << endl;
        // *p = 200; // Error: assignment of read-only location
        return 0;
    }
    ```
    **Output**: `100`
    **Explanation**: `p` is a pointer to a constant integer, so the value cannot be modified through `p`.

52. **What is the result of this code?**
    ```cpp
    #include <iostream>
    using namespace std;
    
    class Test {
    private:
        int value;
    public:
        Test(int v) : value(v) {}
        int getValue() { return value; }
    };
    
    int main() {
        Test t(42);
        cout << t.getValue() << endl;
        return 0;
    }
    ```
    **Output**: `42`
    **Explanation**: The `getValue` method returns the value set by the constructor.

53. **What does this code print?**
    ```cpp
    #include <iostream>
    using namespace std;
    
    class A {
    public:
        A() { cout << "A constructor" << endl; }
    };
    
    class B : public A {
    public:
        B() { cout << "B constructor" << endl; }
    };
    
    int main() {
        B b;
        return 0;
    }
    ```
    **Output**:
    ```
    A constructor
    B constructor
    ```
    **Explanation**: Constructors of base classes are called before constructors of derived classes.

54. **What is the result of the following code?**
    ```cpp
    #include <iostream>
    using namespace std;
    
    class A {
    public:
        virtual void func() { cout << "A::func" << endl; }
    };
    
    class B : public A {
    public:
        void func() override { cout << "B::func" << endl; }
    };
    
    int main() {
        A* a = new B();
        a->func();
        delete a;
        return 0;
    }
    ```
    **Output**: `B::func`
    **Explanation**: The `func` method is overridden in `B`, and the base class pointer calls the derived class’s method.

55. **What will this code output?**
    ```cpp
    #include <iostream>
    using namespace std;
    
    int main() {
        int a = 5;
        int& b = a;
        b = 10;
        cout << a << endl;
        return 0;
    }
    ```
    **Output**: `10`
    **Explanation**: The reference `b` is an alias for `a`, so modifying `b` also modifies `a`.

56. **What does this code print?**
    ```cpp
    #include <iostream>
    using namespace std;
    
    class Base {
    public:
        void show() { cout << "Base class" << endl; }
    };
    
    class Derived : public Base {
    public:
        void show() { cout << "Derived class" << endl; }
    };
    
    int main() {
        Derived d;
        d.show();
        return 0;
    }
    ```
    **Output**: `Derived class`
    **Explanation**: The `Derived` class overrides the `show` method, so its implementation is called.

57. **What is the result of this code?**
    ```cpp
    #include <iostream>
    using namespace std;
    
    int multiply(int a, int b) {
        return a * b;
    }
    
    int multiply(double a, double b) {
        return a * b;
    }
    
    int main() {
        cout << multiply(5, 6) << endl;
        cout << multiply(5.5, 6.6) << endl;
        return 0;
    }
    ```
    **Output**:
    ```
    30
    36
    ```
    **Explanation**: Function overloading resolves to the appropriate function based on parameter types.

58. **What does this code print?**
    ```cpp
    #include <iostream>
    using namespace std;
    
    int main() {
        int* arr = new int[5]{1, 2, 3, 4, 5};
        for (int i = 0; i < 5; ++i) {
            cout << arr[i] << " ";
        }
        delete[] arr;
        return 0;
    }
    ```
    **Output**: `1 2 3 4 5 `
    **Explanation**: Dynamically allocated array elements are printed, and memory is deallocated with `delete[]`.

59. **What will this code output?**
    ```cpp
    #include <iostream>
    using namespace std;
    
    void func(int x) {
        cout << x << endl;
    }
    
    int main() {
        func(10);
        return 0;
    }
    ```
    **Output**: `10`
    **Explanation**: The `func` function takes an integer parameter and prints it.

60. **What is the output of this code?**
    ```cpp
    #include <iostream>
    using namespace std;
    
    int main() {
        int x = 10;
        int* ptr = &x;
        *ptr = 20;
        cout << x << endl;
        return 0;
    }
    ```
    **Output**: `20`
    **Explanation**: The pointer `ptr` is used to modify the value of `x`.

61. **What does this code print?**
    ```cpp
    #include <iostream>
    using namespace std;
    
    void func(int& x) {
        x = x + 5;
    }
    
    int main() {
        int num = 10;
        func(num);
        cout << num << endl;
        return 0;
    }
    ```
    **Output**: `15`
    **Explanation**: The function `func` modifies the original variable `num` through reference.

62. **What is the result of this code?**
    ```cpp
    #include <iostream>
    using namespace std;
    
    class Test {
    public:
        Test() { cout << "Constructor" << endl; }
        ~Test() { cout << "Destructor" << endl; }
    };
    
    int main() {
        Test t1, t2;
        return 0;
    }
    ```
    **Output**:
    ```
    Constructor
    Constructor
    Destructor
    Destructor
    ```
    **Explanation**: Constructors and destructors are called for each object in the order of their creation and destruction.

63. **What does this code print?**
    ```cpp
    #include <iostream>
    using namespace std;
    
    void print(int a) {
        cout << a << endl;
    }
    
    void print(double a) {
        cout << a << endl;
    }
    


    int main() {
        print(10);
        print(10.5);
        return 0;
    }
    ```
    **Output**:
    ```
    10
    10.5
    ```
    **Explanation**: The `print` function is overloaded to handle both integer and double types.

64. **What is the result of this code?**
    ```cpp
    #include <iostream>
    using namespace std;
    
    class Base {
    public:
        void show() { cout << "Base class" << endl; }
    };
    
    class Derived : public Base {
    public:
        void show() { cout << "Derived class" << endl; }
    };
    
    int main() {
        Base* b = new Derived();
        b->show();
        delete b;
        return 0;
    }
    ```
    **Output**: `Base class`
    **Explanation**: The base class pointer calls the base class method because it’s not virtual.

65. **What does this code print?**
    ```cpp
    #include <iostream>
    using namespace std;
    
    class A {
    public:
        void show() { cout << "A class" << endl; }
    };
    
    class B : public A {
    public:
        void show() { cout << "B class" << endl; }
    };
    
    int main() {
        B b;
        b.show();
        return 0;
    }
    ```
    **Output**: `B class`
    **Explanation**: The method `show` in `B` overrides the method `show` in `A`.

66. **What will be the output of this code?**
    ```cpp
    #include <iostream>
    using namespace std;
    
    void func(double x) {
        cout << "double" << endl;
    }
    
    void func(int x) {
        cout << "int" << endl;
    }
    
    int main() {
        func(1.0);
        func(1);
        return 0;
    }
    ```
    **Output**:
    ```
    double
    int
    ```
    **Explanation**: The function `func` is overloaded to handle both `double` and `int` types.

67. **What is the result of this code?**
    ```cpp
    #include <iostream>
    using namespace std;
    
    class Test {
    private:
        int value;
    public:
        Test(int v) : value(v) {}
        int getValue() const { return value; }
    };
    
    int main() {
        const Test t(30);
        cout << t.getValue() << endl;
        return 0;
    }
    ```
    **Output**: `30`
    **Explanation**: The method `getValue` is called on a constant object, and it returns the value stored in the object.

68. **What does this code print?**
    ```cpp
    #include <iostream>
    using namespace std;
    
    void func(int x, int y = 5) {
        cout << x << " " << y << endl;
    }
    
    int main() {
        func(10);
        func(10, 20);
        return 0;
    }
    ```
    **Output**:
    ```
    10 5
    10 20
    ```
    **Explanation**: The function `func` uses default argument values if not provided.

69. **What is the output of this code?**
    ```cpp
    #include <iostream>
    using namespace std;
    
    int main() {
        int* p = nullptr;
        if (p == nullptr) {
            cout << "Pointer is null" << endl;
        } else {
            cout << "Pointer is not null" << endl;
        }
        return 0;
    }
    ```
    **Output**: `Pointer is null`
    **Explanation**: The pointer `p` is explicitly set to `nullptr`, so the condition is true.

70. **What does this code print?**
    ```cpp
    #include <iostream>
    using namespace std;
    
    int main() {
        int x = 0;
        cout << ++x << " " << x++ << " " << x << endl;
        return 0;
    }
    ```
    **Output**: `1 1 2`
    **Explanation**: `++x` increments `x` before printing, `x++` prints `x` before incrementing, and the final `x` shows the updated value.

71. **What is the result of this code?**
    ```cpp
    #include <iostream>
    using namespace std;
    
    class Test {
    public:
        Test() { cout << "Test constructor" << endl; }
        ~Test() { cout << "Test destructor" << endl; }
    };
    
    int main() {
        Test* t = new Test();
        delete t;
        return 0;
    }
    ```
    **Output**:
    ```
    Test constructor
    Test destructor
    ```
    **Explanation**: The constructor and destructor are called for a dynamically allocated `Test` object.

72. **What does this code print?**
    ```cpp
    #include <iostream>
    using namespace std;
    
    int main() {
        int x = 42;
        const int* p = &x;
        // *p = 50; // Error: assignment of read-only location
        cout << *p << endl;
        return 0;
    }
    ```
    **Output**: `42`
    **Explanation**: `p` is a pointer to a constant integer, so its value cannot be modified through `p`.

73. **What is the result of this code?**
    ```cpp
    #include <iostream>
    using namespace std;
    
    class A {
    public:
        void show() { cout << "A::show" << endl; }
    };
    
    class B : public A {
    public:
        void show() { cout << "B::show" << endl; }
    };
    
    int main() {
        B b;
        A* a = &b;
        a->show();
        return 0;
    }
    ```
    **Output**: `A::show`
    **Explanation**: The `show` method in `A` is not virtual, so the base class method is called.

74. **What does this code print?**
    ```cpp
    #include <iostream>
    using namespace std;
    
    int main() {
        int arr[3] = {10, 20, 30};
        cout << sizeof(arr) / sizeof(arr[0]) << endl;
        return 0;
    }
    ```
    **Output**: `3`
    **Explanation**: The expression calculates the number of elements in the array.

75. **What is the result of this code?**
    ```cpp
    #include <iostream>
    using namespace std;
    
    void print(const char* str) {
        cout << str << endl;
    }
    
    int main() {
        print("Hello, world!");
        return 0;
    }
    ```
    **Output**: `Hello, world!`
    **Explanation**: The function `print` takes a `const char*` and prints the string.

76. **What does this code print?**
    ```cpp
    #include <iostream>
    using namespace std;
    
    int main() {
        int x = 10;
        int* p = &x;
        cout << *p << endl;
        return 0;
    }
    ```
    **Output**: `10`
    **Explanation**: The pointer `p` points to `x`, and dereferencing it prints the value of `x`.

77. **What is the output of this code?**
    ```cpp
    #include <iostream>
    using namespace std;
    
    void print(int* p) {
        cout << *p << endl;
    }
    
    int main() {
        int val = 100;
        print(&val);
        return 0;
    }
    ```
    **Output**: `100`
    **Explanation**: The `print` function takes a pointer to an integer and prints the value it points to.

78. **What does this code print?**
    ```cpp
    #include <iostream>
    using namespace std;
    
    int main() {
        const int x = 100;
        int* p = const_cast<int*>(&x);
        *p = 200;
        cout << x << endl;
        return 0;
    }
    ```
    **Output**: Undefined behavior
    **Explanation**: Modifying a constant value through a `const_cast` results in undefined behavior.

79. **What is the result of this code?**
    ```cpp
    #include <iostream>
    using namespace std;
    
    class Test {
    private:
        int value;
    public:
        Test(int v) : value(v) {}
        int getValue() const { return value; }
    };
    
    int main() {
        Test t(50);
        cout << t.getValue() << endl;
        return 0;
    }
    ```
    **Output**: `50`
    **Explanation**: The `getValue` method returns the value initialized in the constructor.

80. **What does this code print?**
    ```cpp
    #include <iostream>
    using namespace std;
    
    class A {
    public:
        A() { cout << "A constructor" << endl; }
        ~A() { cout << "A destructor" << endl; }
    };
    
    class B :

 public A {
    public:
        B() { cout << "B constructor" << endl; }
        ~B() { cout << "B destructor" << endl; }
    };
    
    int main() {
        B b;
        return 0;
    }
    ```
    **Output**:
    ```
    A constructor
    B constructor
    B destructor
    A destructor
    ```
    **Explanation**: The constructors and destructors are called in the order of inheritance.

81. **What is the result of this code?**
    ```cpp
    #include <iostream>
    using namespace std;
    
    void print(char c) {
        cout << c << endl;
    }
    
    void print(int i) {
        cout << i << endl;
    }
    
    int main() {
        print(10);
        print('A');
        return 0;
    }
    ```
    **Output**:
    ```
    10
    A
    ```
    **Explanation**: Function overloading resolves to the appropriate function based on argument types.

82. **What does this code print?**
    ```cpp
    #include <iostream>
    using namespace std;
    
    int main() {
        int x = 1;
        int y = 2;
        int* p = &x;
        p = &y;
        cout << *p << endl;
        return 0;
    }
    ```
    **Output**: `2`
    **Explanation**: The pointer `p` is redirected to point to `y`, so `*p` gives the value of `y`.

83. **What is the output of this code?**
    ```cpp
    #include <iostream>
    using namespace std;
    
    int main() {
        int a = 5;
        int b = 10;
        cout << (a > b ? a : b) << endl;
        return 0;
    }
    ```
    **Output**: `10`
    **Explanation**: The ternary operator selects the greater value between `a` and `b`.

84. **What does this code print?**
    ```cpp
    #include <iostream>
    using namespace std;
    
    int main() {
        int a = 0;
        int b = 1;
        cout << (a || b) << endl;
        return 0;
    }
    ```
    **Output**: `1`
    **Explanation**: The logical OR operator (`||`) returns true if either operand is true.

85. **What is the result of this code?**
    ```cpp
    #include <iostream>
    using namespace std;
    
    int main() {
        int a = 5;
        int b = 10;
        cout << (a != b) << endl;
        return 0;
    }
    ```
    **Output**: `1`
    **Explanation**: The not-equal-to operator (`!=`) returns true (1) because `a` is not equal to `b`.

86. **What does this code print?**
    ```cpp
    #include <iostream>
    using namespace std;
    
    int main() {
        int x = 10;
        int* p = &x;
        (*p)++;
        cout << x << endl;
        return 0;
    }
    ```
    **Output**: `11`
    **Explanation**: The pointer `p` is used to increment the value of `x`.

87. **What is the output of this code?**
    ```cpp
    #include <iostream>
    using namespace std;
    
    int main() {
        int x = 5;
        int& ref = x;
        ref++;
        cout << x << endl;
        return 0;
    }
    ```
    **Output**: `6`
    **Explanation**: The reference `ref` modifies the value of `x`, so `x` is incremented.

88. **What does this code print?**
    ```cpp
    #include <iostream>
    using namespace std;
    
    int main() {
        int x = 10;
        int* p = &x;
        int** pp = &p;
        cout << **pp << endl;
        return 0;
    }
    ```
    **Output**: `10`
    **Explanation**: `**pp` dereferences the pointer to pointer `pp`, giving the value of `x`.

89. **What is the result of this code?**
    ```cpp
    #include <iostream>
    using namespace std;
    
    int main() {
        int arr[4] = {1, 2, 3, 4};
        int* p = arr;
        cout << *(p + 2) << endl;
        return 0;
    }
    ```
    **Output**: `3`
    **Explanation**: `p + 2` points to the third element of the array, and dereferencing it gives the value `3`.

90. **What does this code print?**
    ```cpp
    #include <iostream>
    using namespace std;
    
    int main() {
        int a = 10;
        int b = 20;
        cout << (a < b && b < 30) << endl;
        return 0;
    }
    ```
    **Output**: `1`
    **Explanation**: The logical AND operator (`&&`) returns true because both conditions are true.

91. **What is the result of this code?**
    ```cpp
    #include <iostream>
    using namespace std;
    
    int main() {
        int x = 7;
        int y = 3;
        cout << x / y << endl;
        return 0;
    }
    ```
    **Output**: `2`
    **Explanation**: Integer division truncates the result, so `7 / 3` yields `2`.

92. **What does this code print?**
    ```cpp
    #include <iostream>
    using namespace std;
    
    int main() {
        int x = 5;
        int y = 3;
        cout << x % y << endl;
        return 0;
    }
    ```
    **Output**: `2`
    **Explanation**: The modulus operator (`%`) returns the remainder of division.

93. **What is the result of this code?**
    ```cpp
    #include <iostream>
    using namespace std;
    
    int main() {
        int x = 15;
        int y = 4;
        cout << x / y << endl;
        return 0;
    }
    ```
    **Output**: `3`
    **Explanation**: Integer division yields the quotient without the remainder.

94. **What does this code print?**
    ```cpp
    #include <iostream>
    using namespace std;
    
    int main() {
        int x = 10;
        int y = 20;
        cout << (x < y ? y : x) << endl;
        return 0;
    }
    ```
    **Output**: `20`
    **Explanation**: The ternary operator selects the greater value between `x` and `y`.

95. **What is the result of this code?**
    ```cpp
    #include <iostream>
    using namespace std;
    
    int main() {
        int x = 10;
        int y = 5;
        cout << (x > y ? x : y) << endl;
        return 0;
    }
    ```
    **Output**: `10`
    **Explanation**: The ternary operator selects the greater value between `x` and `y`.

96. **What does this code print?**
    ```cpp
    #include <iostream>
    using namespace std;
    
    int main() {
        int x = 10;
        int y = 20;
        cout << (x == y) << endl;
        return 0;
    }
    ```
    **Output**: `0`
    **Explanation**: The equality operator (`==`) returns false (0) because `x` is not equal to `y`.

97. **What is the result of this code?**
    ```cpp
    #include <iostream>
    using namespace std;
    
    int main() {
        int x = 15;
        int y = 10;
        cout << (x <= y) << endl;
        return 0;
    }
    ```
    **Output**: `0`
    **Explanation**: The less-than-or-equal-to operator (`<=`) returns false (0) because `x` is not less than or equal to `y`.

98. **What does this code print?**
    ```cpp
    #include <iostream>
    using namespace std;
    
    int main() {
        int x = 3;
        cout << x * 2 << endl;
        return 0;
    }
    ```
    **Output**: `6`
    **Explanation**: Multiplying `x` by `2` yields `6`.

99. **What is the result of this code?**
    ```cpp
    #include <iostream>
    using namespace std;
    
    int main() {
        int x = 7;
        cout << x << endl;
        x += 3;
        cout << x << endl;
        return 0;
    }
    ```
    **Output**:
    ```
    7
    10
    ```
    **Explanation**: `x` is incremented by `3` after the first print statement.


100. **What does this code print?**

```cpp
#include <iostream>
using namespace std;

int main() {
    int x = 5;
    int y = 10;
    cout << (x > y ? "x is greater" : "y is greater") << endl;
    return 0;
}
```

**Output**: `y is greater`

**Explanation**: The code uses the ternary operator `?:` to evaluate the condition `x > y`. Since `x` (5) is not greater than `y` (10), the condition evaluates to `false`. Therefore, the expression after the colon (`:`) is chosen, which is `"y is greater"`. This result is printed to the console.