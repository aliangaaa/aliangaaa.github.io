---
layout: post
title: QProcess
category: QT
tags: Essay
keywords: 
description: 
---

- QProcess使用需要注意生命周期
```cpp
void init() {
  QProcess p;
  p.start("D:\a.exe");
}
```
在退出init时，p会自动释放，导致运行exe有问题

- 解决方法是添加
```cpp
p.waitForFinished();
```

- 但是这样会引入新的问题，阻塞主线程
- QProcess虽然是异步的，但是waitForFinished会阻塞
- 所以可以使用new
- 或者在子线程中使用，栈上定义并waitForFinished()

- 另外QProcess需要kill的时候，线程应当和QProcess在同一个
- 并且QProcess不能用waitForFinished，猜测kill以后就再也收不到Finished信号了。
