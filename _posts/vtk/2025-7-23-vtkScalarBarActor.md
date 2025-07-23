---
layout: post
title: vtkScalarBarActor
category: vtk
tags: Essay
keywords: 
description: 
---

```cpp
    scalarBar->SetPosition(0.40, 0.10);   // 最下角位置
    scalarBar->SetPosition2(0.60, 0.80);  // 宽 60%，高 80%
    // 上述代码应该贴串口右侧，但是看上去没有，因为背景设置的透明，可以打开看到整个
    scalarBar->DrawFrameOff();         // 关闭外边框
    scalarBar->DrawBackgroundOn();     // 开启背景（默认透明）
    scalarBar->GetBackgroundProperty()->SetColor(0.2, 0.2, 0.2); // 显示背景区域
    // 获取bar的位置
    scalarBar->GetBarRatio();
```

### 将归一化坐标显示为窗口坐标
```cpp
    // 转换为显示坐标（像素）
    vtkNew<vtkCoordinate> coordL, coordR;
    coordL->SetCoordinateSystemToNormalizedViewport();
    coordR->SetCoordinateSystemToNormalizedViewport();
    coordL->SetValue(x_left, y_norm);
    coordR->SetValue(x_right, y_norm);

    int* p1 = coordL->GetComputedDisplayValue(renderer);
    int* p2 = coordR->GetComputedDisplayValue(renderer);
```
