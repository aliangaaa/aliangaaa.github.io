---
layout: post
title: treeview拖拽
category: QT
tags: Essay
keywords: 
description: 
---

```
setDragEnabled(true);
setAcceptDrops(true);
setDragDropMode(QAbstractItemView::InternalMove);
setDropIndicatorShown(true);
setDragDropOverwriteMode(true);
```
```
startDrag(...);
dragMoveEvent();
dragEnterEvent();
// 可以在上面使用ignore忽略事件，不进入dropevent
dropEvent();
```
