---
layout: post
title: std::function
category: CPP
tags: Essay
keywords: 
description: 
---

`std::function` 是 C++11 中的一个函数对象封装类，它可以用来保存任意可调用对象（函数指针、函数对象、成员函数指针等），并且可以在需要的时候调用这些可调用对象。下面是一个简单的示例来演示如何使用 `std::function`：

```cpp
#include <iostream>
#include <functional>

void sayHello() {
    std::cout << "Hello, world!" << std::endl;
}

int add(int a, int b) {
    return a + b;
}

class Multiplier {
public:
    int operator()(int a, int b) {
        return a * b;
    }
};

int main() {
    // 使用函数指针
    std::function<void()> func1 = sayHello;
    func1();

    // 使用lambda表达式
    std::function<int(int, int)> func2 = [](int a, int b) { return a * b; };
    std::cout << "3 * 4 = " << func2(3, 4) << std::endl;

    // 使用普通函数
    std::function<int(int, int)> func3 = add;
    std::cout << "5 + 6 = " << func3(5, 6) << std::endl;

    // 使用函数对象
    Multiplier multiplier;
    std::function<int(int, int)> func4 = multiplier;
    std::cout << "7 * 8 = " << func4(7, 8) << std::endl;

    // bind
    std::function<int(int)> func5 = bind(add, 1, std::placeholders::_1);
    func5(2);        //表示add的第一个参数是1， 第二个参数是func5输入的第一个参数

    return 0;
}

```

在这个示例中，我们使用了不同的可调用对象（函数指针、lambda表达式、普通函数、函数对象）来初始化 `std::function` 对象，并且调用了这些 `std::function` 对象来执行相应的操作。

希望这个示例能够帮助你理解如何使用 `std::function`
