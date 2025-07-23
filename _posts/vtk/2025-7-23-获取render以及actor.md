---
layout: post
title: 获取render以及actor
category: vtk
tags: Essay
keywords: 
description: 
---
渲染串口可以添加多个render
```cpp
  vtkScalarBarActor* scalarBar = nullptr;
  vtkRendererCollection* renderers = ui->widget_color->GetRenderWindow()->GetRenderers();
  renderers->InitTraversal();
  while (vtkRenderer* renderer = renderers->GetNextItem()) {
      vtkActorCollection* actors = renderer->GetActors();
      actors->InitTraversal();
      while (vtkActor* actor = actors->GetNextItem()) {
          scalarBar = vtkScalarBarActor::SafeDownCast(actor);
          if (scalarBar) {
              break;
          }
      }
  }
```
