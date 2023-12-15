---
layout: post
title: QBytearray
category: QT
keywords: QBytearray
---
1、QBytearray从16进制字符串转化

```cpp
QByteArray bytes = QByteArray::fromHex("55AA0200000000000002");
```

2、从char\*中截取一部分成为QBytearray

```cpp
char* buff
QByteArray  buf = QByteArray(buff, size);
```

3、QBytearray中有两位表示某个数字

```cpp
(uint8_t)crc[1] * 256 + (uint8_t)crc[0]    // 大端
```

4、QBytearray中的某一位和数字比较

```cpp
bytes.at(0) == 0
```

5、QBytearray添加一个数字一个字符

```cpp
bytes.append(1)
bytes.appedn('a')
int b = 0;
bytes.append(static_cast<char>(b))
```

6、Qbytearray中取数字时，需要加上（uint8\_t）来保证取出的数字可以超过127

```cpp
QBytearray bytes;
bytes.append(255);
bytes.at(0) == 255  false  bytes.at(0) == -1 true
(uint8_t)bytes.at(0) == 255 true
```

计算机底层是二进制的，存储进Qbytearray的每一位是一个8进制数据，你用char读出它就是-128 - 127；你用unsigned char读出它就是0-255（FF），如果底层传输的数据是负数，第一位表示符号位，那就约定好上层用signed 来接收的道理
