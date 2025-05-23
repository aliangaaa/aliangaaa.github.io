---
layout: post
title: qRegisterMetaType
category: QT
tags: Essay
keywords: 
description: 
---

```cpp
如果非QMetaType内置类型要在 Qt 的属性系统中使用
如果非QMetaType内置类型要在 queued 信号与槽 中使用
qRegisterMetaType<QSerialPort::DataBits>("QSerialPort::DataBits");
当然在不跨线程时使用自定义类型signal/slot来传递，可能不会出现什么问题；一旦涉及跨线程就很容易出错，回想下信号槽的作用就是用来对象与对象之间通信的，难免会跨线程，建议在使用自定义类型利用信号槽通信时，最好先通过qRegisterMetaType()将自定义类型进行注册，以免出错。
```

传递结构体
另外QVector也是无法经过信号槽传递的，必须要注册
信号槽通过QVariant传递

```
Q_DECLARE_TYPE(QVector<struct>)
```

```
- Q_DECLARE_METATYPE 宏用于声明自定义类型，告诉元对象系统关于这个类型的一些信息，比如类型的名称、大小等。这样做的目的是为了让元对象系统能够识别和处理这个类型。通常情况下，你需要在类的定义中使用 Q_DECLARE_METATYPE，以便能够在信号槽机制中使用这个类型。
- qRegisterMetaType 函数用于注册自定义类型，将这个类型注册到元对象系统中。这样做的目的是为了确保这个类型能够被正确地处理，比如能够正确地放入事件队列中，以便在信号槽连接中使用。通常情况下，你需要在使用这个类型的地方之前调用 qRegisterMetaType 来进行注册。
QVariant如果要进行转化就需要通过Q_DECLARE_METATYPE就行。
如果需要把某类型用于信号槽就要qRegisterMetaType进行注册
```

<https://blog.csdn.net/xinqingwuji/article/details/123557682?spm=1001.2101.3001.6650.2&utm_medium=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7ERate-2-123557682-blog-82107880.235%5Ev38%5Epc_relevant_anti_t3&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7ERate-2-123557682-blog-82107880.235%5Ev38%5Epc_relevant_anti_t3&utm_relevant_index=4>

```
- 24-10-21更新
对于同线程的类型是什么无所谓，自定义类型也可以传递。
但是对于不同线程的，无法直接传递。可以通过qRegisterMetaType<QSerialPort::DataBits>("QSerialPort::DataBits");
或者通过QVariant传递, 使用Q_DECLARE_METATYPE。
```
