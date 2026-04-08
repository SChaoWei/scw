---
title: "示例：STM32 最小系统板设计"
date: 2026-04-06
categories: ["硬件电路"]
tags: ["嵌入式"]
summary: "一篇硬件电路方向的示例文章。"
---

## 概述

本文记录 STM32F103C8T6 最小系统板的设计过程，包括原理图设计、PCB 布局和调试。

## 原理图

{{< figure src="https://via.placeholder.com/800x400?text=Schematic+Placeholder" caption="STM32 最小系统原理图（示例占位图）" >}}

## 参考资料

- [STM32F103 数据手册](https://www.st.com/resource/en/datasheet/stm32f103c8.pdf)
- [立创 EDA 在线设计工具](https://lceda.cn/)

## 调试记录

使用逻辑分析仪抓取 SPI 通信波形：

```
CLK:  ‾‾|__|‾‾|__|‾‾|__|‾‾|__
MOSI: ____|‾‾‾‾|____|‾‾‾‾|____
CS:   ‾‾‾‾|__________________|‾‾
```

调试过程中发现时钟极性配置错误，修改 SPI 初始化代码后通信正常。
