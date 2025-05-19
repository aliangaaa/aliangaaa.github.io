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
```
shared_ptr本身是线程安全的，即引用计数和对象的删除是线程安全的，
管理的对象线程安全性靠自己保证
```
### 当类中存在一个智能指针时
#### 当用另一个指针指向类指针时，并不会使引用+1， 引用变化是操作智能指针本身才会
```
Myclass {
  pricate:
    shared_ptr<int> a;
}

Myclass * class_1 = new Myclass;
Myclass* class_2 = class_1;
计数依然是1
```
#### 当类释放了，如果智能指针计数没有降低到0，指针指向的内存依然存在，会在降低到0后释放
```
Myclass* class_3 = new Myclass;
shared_ptr<int> p = class_3;
delete class_3;
std::cout << p.getrefrencecout;    // = 1
// 内存数据依然存在，可以访问，直到p释放，内存随之结束，并非随着类析构而消失（重要）
```
#### 类不必在析构中将智能指针=nullptr
```
智能指针 = nullptr 或者reset 都是将计数减去1
类所掌握的智能指针会在类释放时自动计数-1，不必重复的在析构中-1
```
