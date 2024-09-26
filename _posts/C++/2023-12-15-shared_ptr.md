---
layout: post
title: shared_ptr
category: CPP
tags: Essay
keywords: 
description: 
---

```cpp
在对象使用周期内始终有效
shared_ptr<class name> = shared_ptr<class name>(new class name);

shared_ptr<class name> = make_shared<class name>(参数)
// 下面一种不可以， 看他的头文件时在make中申请的空间
shared_ptr<class name> = make_shared<class name>(new class name(参数))
```
```
两个智能指针指向同一个地址
int* a = new int(5);
shared_ptr<int> ptr = shared_ptr<int>(a);
shared_ptr<int> ptr2 = ptr;     // 引用计算数会增加是可以的。unique_ptr不能这么操作
shared_ptr<int> ptr3 = shared_ptr<int>(a)   // 引用计数各为1， 任意一个离开作用域都会导致内存释放。
```
