---
layout: post
title: weak_ptr
category: CPP
tags: Essay
keywords: 
description: 
---

std::shared_ptr 在 C++ 中是一种智能指针，它用于共享资源的所有权。当多个 shared_ptr 拥有同一对象时，智能指针会自动管理对象的生命周期，并在最后一个指针被销毁时删除对象。然而，std::shared_ptr 也有一个潜在的问题——循环引用（circular reference），它可能导致内存泄漏。
```
#include <iostream>
#include <memory>

class B;  // 提前声明

class A {
public:
    std::shared_ptr<B> b;
    ~A() { std::cout << "A destroyed\n"; }
};

class B {
public:
    std::shared_ptr<A> a;
    ~B() { std::cout << "B destroyed\n"; }
};

int main() {
    std::shared_ptr<A> a = std::make_shared<A>();
    std::shared_ptr<B> b = std::make_shared<B>();

    a->b = b;
    b->a = a;

    // 这里没有手动释放 a 和 b，它们之间相互持有对方的 shared_ptr
    // 导致它们的引用计数不会归零
}
```
如何避免或解决循环引用？
1、使用 std::weak_ptr：

解决循环引用的一种常用方法是使用 std::weak_ptr。std::weak_ptr 是一种不增加引用计数的智能指针，它提供了对对象的弱引用。std::weak_ptr 不会阻止对象被销毁，因此可以用它来打破循环引用。

在循环引用的例子中，可以把其中一个 shared_ptr 替换为 weak_ptr，使得这个引用不再增加引用计数，从而打破循环引用。
```
#include <iostream>
#include <memory>

class B;  // 提前声明

class A {
public:
    std::weak_ptr<B> b;  // 使用 weak_ptr 来打破循环引用
    ~A() { std::cout << "A destroyed\n"; }
};

class B {
public:
    std::shared_ptr<A> a;
    ~B() { std::cout << "B destroyed\n"; }
};

int main() {
    std::shared_ptr<A> a = std::make_shared<A>();
    std::shared_ptr<B> b = std::make_shared<B>();

    a->b = b;
    b->a = a;

    // 现在没有循环引用，引用计数最终会归零，对象会被销毁
}
```
2、 手动打破循环引用
```
a->b.reset();  // 解除 A 对 B 的引用
b->a.reset();  // 解除 B 对 A 的引用
```
