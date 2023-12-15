---
layout: post
title: atomic
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

