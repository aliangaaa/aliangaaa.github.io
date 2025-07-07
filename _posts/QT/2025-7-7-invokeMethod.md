---
layout: post
title: invokeMethod
category: QT
tags: Essay
keywords: 
description: 
---
### 使用thread时
```cpp
std::thread t[&](){
  // 直接运行函数时,函数运行于子线程
  update()
  // 通过信号发送时，函数运行于主线程
  emit update();
}
如果需要函数运行于主线程，比如刷新ui
可以使用
invokeMethod[this](&){
  update();
}; // 默认autoconnection，可以看情况更改
update()函数会运行于this所在线程
```
####1. 线程亲和性（Thread Affinity）
Qt 中每个 QObject 都有一个关联的线程（即创建该对象的线程）。

QMetaObject::invokeMethod 会根据目标对象（this）的线程亲和性，决定在哪个线程执行函数。

####2. 默认行为（Qt::AutoConnection）
如果调用 invokeMethod 的线程和 this 的线程不同，Qt 会自动将调用转为 QueuedConnection（异步队列调用），即函数会在 this 的线程事件循环中执行。

如果调用线程和 this 的线程相同，则直接同步调用（DirectConnection）。
