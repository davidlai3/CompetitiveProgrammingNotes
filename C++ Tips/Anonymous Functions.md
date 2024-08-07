## Overview
- In modern versions of C++ (C++ 11 or newer), nested functions can be simulated by writing lambda expressions in C++
- The brackets next to the function arguments define the scoping of the lambda function
	- `[]` means the function has no access to outside variables 
	- `[&]` means it has access to outside variables by reference
	- `[=]` means it has access to outside variables by value

```cpp
int main() {
    // This declares a lambda, which can be called just like a function
    auto print_message = [](std::string message) { 
        std::cout << message << "\n"; 
    };

    // Prints "Hello!" 10 times
    for(int i = 0; i < 10; i++) {
        print_message("Hello!"); 
    }
}
```