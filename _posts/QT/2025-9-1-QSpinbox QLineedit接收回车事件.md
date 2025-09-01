---
layout: post
title: QSpinbox QLineedit接收回车事件
category: QT
tags: Essay
keywords: 
description: 
---

### 发现QSpinBox或者QLineedit接收回车事件时，会触发同页面的QPushbutton的回车事件
```
gpt推荐关闭pushbutton的auto设置，无效
```

```
通过下面四步解决
ui->valuespin->setKeyboardTracking(false);
ui->valuespin->installEventFilter(this);
connect(ui->valuespin, QOverload<int>::of(&QSpinBox::valueChanged), this, &ContourFilterMeshDialog1::slotValueChanged);
bool ContourFilterMeshDialog1::eventFilter(QObject *watched, QEvent *event)
{
    if(watched==ui->valuespin)
    {
        if(event->type()==QEvent::Wheel)
        {
            return true;
        }
        if (event->type() == QEvent::KeyPress) {
            QKeyEvent* keyEvent = static_cast<QKeyEvent*>(event);
            if (keyEvent->key() == Qt::Key_Return || keyEvent->key() == Qt::Key_Enter) {
                ui->valuespin->interpretText();
                return true;
            }
        }
    }
    return QWidget::eventFilter(watched,event);
}
```
