## Overview
- Templates in C++ allow us to use generic types when writing function, thus making our code more expressive
	- The `typename` keywords lets the compiler know we are writing a polymorphic function
	- The next keyword, `<typename T>` defines the generic type
	- The return type of the function follows

```cpp
template <typename T> T myMax(T x, T y) {
	return (x > y) ? x : y;
}
```