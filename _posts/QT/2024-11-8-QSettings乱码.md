---
layout: post
title: QSettings乱码
category: QT
tags: Essay
keywords: 
description: 
---

```
在文件中存在中文或者℃等特殊字符时，实测QFile，read是能正常读取出来。
怀疑是因为直接读出来的是QString，QString中带编码格式，详见QCHar解析
```
```
QSettings settings("file", QSettings::IniFormat);
settings.value("temperature/data").toString()
出现了乱码，怀疑是第一步得到的QVariant,丢失了编码

取值前加个
settings.setIniCodec("utf-8");
```
