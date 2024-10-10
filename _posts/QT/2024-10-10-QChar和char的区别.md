---
layout: post
title: QChar和char的区别
category: QT
tags: Essay
keywords: 
description: 
---
QChar* 和 char* 是两种指向字符数据的指针类型，主要区别在于它们所指向的数据类型不同，代表着不同的编码和字符集。具体来说：

1. QChar*（Qt 类型）
类型：QChar 是 Qt 框架中的字符类型，代表一个 16 位的 Unicode 字符。
编码：QChar 使用 UTF-16 编码方式，每个字符占用两个字节（16 位）。
适用场景：QChar 主要用于处理 Unicode 字符串，在 Qt 中，QString 是使用 QChar 来存储字符的类。因此，QChar* 指针通常用于指向 Qt 的 Unicode 字符串数据。

2. char*（标准 C/C++ 类型）
类型：char 是标准的 C++ 字符类型，代表一个 8 位字符，每个字符占用一个字节（8 位）。
编码：char* 通常用于表示 ASCII 或 UTF-8 编码的字符串。ASCII 是 7 位字符集，而 UTF-8 是一种可变长度的编码格式，它兼容 ASCII，但对于非 ASCII 字符则使用多个字节进行表示。
适用场景：char* 通常用于处理传统的 C 风格字符串（null 结尾的字节数组）。这种字符串处理方式在处理简单的英文字符或兼容系统 API 时仍然广泛使用。

char*是8位数据的一个指针， QChar*是16位数据的一个指针。所以不能混用
