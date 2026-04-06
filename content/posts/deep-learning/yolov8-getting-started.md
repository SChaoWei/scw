---
title: "示例：YOLOv8 目标检测入门"
date: 2026-04-05
categories: ["深度学习"]
tags: ["YOLO", "目标检测", "PyTorch"]
summary: "深度学习方向的示例文章，演示训练相关内容的写法。"
---

## 简介

YOLOv8 是 Ultralytics 推出的最新目标检测框架，支持检测、分割、分类等多种任务。

## 环境配置

```bash
pip install ultralytics
```

## 训练示例

```python
from ultralytics import YOLO

model = YOLO('yolov8n.pt')
results = model.train(data='coco128.yaml', epochs=100, imgsz=640)
```

## 训练结果

{{< figure src="https://via.placeholder.com/800x400?text=Training+Results+Placeholder" caption="训练损失曲线（示例占位图）" >}}

## 参考链接

- [Ultralytics YOLOv8 文档](https://docs.ultralytics.com/)
- [COCO 数据集](https://cocodataset.org/)
