---
title: "中兴未来菁英训练营（大模型算法方向）"
date: 2025-05-01
tags: ["Agent", "多Agent编排"]
summary: "中兴未来菁英训练营项目，通过对用户输入的PDF文档及PPT模板进行解析，利用多Agent编排实现固定页数PPT幻灯片的自动生成。"
---

## 项目背景

**时间**：2025.05 - 2025.08

通过对用户输入的PDF文档以及PPT模板进行解析，获取结构化文本信息以及PPT模板信息，并利用多Agent编排进行固定页数PPT幻灯片的生成。整体系统实现了从非结构化文档到专业PPT的端到端自动化生成流程，大幅降低人工制作PPT的时间成本。

{{< figure src="/zte-ppt/图1.png" caption="PPT自动生成系统整体架构" >}}

## 主要工作

- **基础理论学习**：参与基础理论学习课程，系统学习大模型基础架构（Transformer、注意力机制、位置编码）、大模型推理应用（KV Cache、投机采样、量化推理）以及知识蒸馏范式（logit蒸馏、特征蒸馏）等大语言模型核心理论。

- **文档解析模块开发**：利用marker库对用户输入PDF文档进行深度解析，提取具体文本、图片以及元数据信息，再利用Qwen3大语言模型按照语义边界进行细粒度切割，得到层次化的结构化文本（标题、段落、要点等）。该模块支持多种PDF格式，能够准确保留文档的逻辑结构与层级关系。
{{< figure src="/zte-ppt/图2.png" caption="顶级标题提取" >}}
{{< figure src="/zte-ppt/图3.png" caption="提取文档流程" >}}
- **PPT模板智能解析与聚类**：遍历每页PPT模板进行特征提取与聚类分析，按照PPT内容进行功能页划分（封面页、目录页、内容页、结尾页等），利用内容页图像embedding相似度进行内容页聚类，自动识别不同布局风格的模板页面，为后续模板选择提供结构化的模板库。

{{< figure src="/zte-ppt/图4.png" caption="PPT模板解析与聚类流程" >}}

- **PPT多Agent系统设计**：设计主从式多Agent架构进行PPT生成。在主PPT生成Agent中编排五个子任务Agent协同工作：
  - 大纲生成Agent：利用Prompt模板结合文档结构信息，生成符合用户指定页数的PPT大纲框架
  - 要点提取Agent：遍历大纲各节点，从源文档中精准提取对应的关键内容与数据
  - 模板选择Agent：根据每页内容的类型与信息量，从聚类后的模板库中智能匹配最合适的版式
  - 文字填充Agent：将提取的要点内容按照模板布局进行排版填充，生成对应位置的PPT文字
  - 代码生成Agent：利用Qwen3结合预定义的python-pptx API代码库，生成可执行的PPT构建代码，执行代码并保存得到最终的PPT输出文件

{{< figure src="/zte-ppt/图5.png" caption="多Agent编排架构" >}}

{{< figure src="/zte-ppt/图片1.png" caption="生成效果1" >}}
{{< figure src="/zte-ppt/图片2.png" caption="生成效果2" >}}

{{< figure src="/zte-ppt/评价1.jpg" caption="中兴技术负责人评价" >}}
{{< figure src="/zte-ppt/评价3.jpg" caption="中兴技术负责人评价" >}}