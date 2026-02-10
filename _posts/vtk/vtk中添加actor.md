---
layout: post
title: vtk中添加actor
category: vtk
tags: Essay
keywords: 
description: 
---

## 在vtk中几种actor添加的注意

### 二维视图中
#### vtkActor
vtkActor主要是ploydata的显示载体，有深度测试，所以会被遮挡

### vtkImageActor
作为vtkImageData的显示载体，显示成二维切片。会被遮挡。如果做颜色渲染，则需要借助vtkMapToColors，问题是会把标量值改成0-255。所以很多时候颜色变暗是因为窗宽窗位不是按照0-255去设置的。这个类不需要特意设置mapper，可以直接getMapper

### vtkImageSlice
作用同vtkImageActor，但是需要手动new vtkImageSliceMapper，这个类可以进行颜色映射，不需要借助别的。但是问题是对于label少量的数据来说，不设置颜色映射时不足255的label会被映射成特别黑，不像上面的颜色时均匀映射到灰到白。
比如只有012的数据，vtkImageActor会把2映射成白色，1映射成灰色，0是黑色。但是这个类会把整个图变成黑色，虽然说可能是对的。但是自动的效果不如上面。


### 三维视图
### vtkActor
polydata
### vtkVolume
vtkVolume 是体渲染专用对象
### vtkLODProp3D
多种几何模型的 LOD 切换
