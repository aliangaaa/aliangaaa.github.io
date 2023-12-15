---
layout: post
title: 编译verilator
category: C++
tags: Essay
keywords: 
description: 
---

1.编译64位exe，使用cygwin64

cd vecilator-5.006/

autoconf

./configure

make

make install

2、编译32位exe 使用msys2

步骤同上

&#x20;autoconf

./configure --enable-m32

make -j4    //make clean

make install

查看依赖库

ldd exe
