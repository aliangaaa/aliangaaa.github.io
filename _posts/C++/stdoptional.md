---
layout: post
title: optional
category: CPP
tags: Essay
keywords: 
description: 
---
```
c++17中支持std::optional
定义:
  std::optional<T> 是一个模板类型,其中 T 是可以存储的值的类型。
  std::optional 可以存储 T 类型的值,也可以表示"无值"的状态。

std::nullopt 是 C++17 引入的一个特殊的值,用于初始化或赋值给 std::optional 类型的变量,表示"没有值"的状态

#include <iostream>
#include <optional>

std::optional<int> getnum()
{
    return std::nullopt;
}

int main()
{
    std::optional<int> a = getnum();
    if (a.has_value()) {
        std::cout << "has value" << std::endl;
    }
    else {
        std::cout << a.value_or(-1) << std::endl;    // 如果没有值返回-1
        std::cout << a.value() << std::endl;         // 没有值的情况下取值会出错
        std::cout << *a << std::endl;                // 没有值的情况下取值会出错
        std::cout << "nullopt" << std::endl;
    }
}
```
