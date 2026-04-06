---
title: "示例：基于 ROS2 的移动机器人导航系统"
date: 2026-04-07
categories: ["机器人系统"]
tags: ["ROS2", "导航", "SLAM"]
summary: "这是一篇示例文章，展示如何在博客中插入图片、链接和视频。"
---

## 前言

这是一篇示例文章，用于演示博客的各种内容写法。你可以参考这篇文章的 Markdown 源码来写自己的博客。

## 插入图片

Markdown 标准语法：

![ROS2 架构图](https://docs.ros.org/en/humble/_static/humble-small.png)

使用 figure shortcode（支持标题、缩放等）：

{{< figure src="https://docs.ros.org/en/humble/_static/humble-small.png" caption="ROS2 Humble 版本 Logo" >}}

## 插入外部链接

- [ROS2 官方文档](https://docs.ros.org/en/humble/)
- [Navigation2 项目](https://github.com/ros-planning/navigation2)

## 嵌入 Bilibili 视频

{{< bilibili bvid="BV1xW4y1S7WR" >}}

## 代码块

```python
import rclpy
from rclpy.node import Node

class MinimalPublisher(Node):
    def __init__(self):
        super().__init__('minimal_publisher')
        self.get_logger().info('Hello ROS2!')

def main():
    rclpy.init()
    node = MinimalPublisher()
    rclpy.spin(node)

if __name__ == '__main__':
    main()
```

## 小结

以上演示了图片、链接、视频嵌入和代码块的用法。写文章时直接参考这个模板即可。
