---
title: "高铁动车智能巡检机器人系统研发"
date: 2023-01-01
tags: ["机器人", "深度学习", "缺陷检测", "Ascend 310P"]
summary: "北京铁道所校企合作项目，本人担任项目学生负责人进行整体项目推进、项目探讨，资源协调以及迭代优化。，研制高铁检修车间坑道内 RGV 轨道巡检机器人，已在武汉、深圳、上海等多地部署应用，且已中标中铁多个重大项目。"
---

## 项目背景

**时间**：2023.01 - 2025.10

研制高铁检修车间坑道内的RGV轨道机器人，设计两阶段巡检任务：第一阶段从车头到车尾，采用线阵相机进行线扫图像采集；第二阶段从车尾移动到车头，进行红外激光定位轮毂位置后利用机械臂进行转向架信息采集，最后进行缺陷检测并将结果上传至 MySQL 数据库。目前已在武汉动车段、黄黄高铁、深圳北、上海虹桥、湖南怀化等多地进行实地部署应用（本人深入现场参与）。
{{< figure src="/robot/机器人系统整体架构.png" caption="机器人系统整体架构" >}}

## 主要工作

- **可视化软件框架开发**：基于 PyQt 设计 AI 巡检服务器工业软件，实现程序一键运行、运行状态实时显示以及检测结果可视化。
{{< figure src="/robot/软件框架.png" caption="软件页面" >}}
{{< figure src="/robot/pyqt_img.png" caption="软件页面" >}}

- **零部件缺陷整体算法流程设计**：设计多模态零部件缺陷检测算法框架。利用结合正交注意力机制及改进多尺度融合策略的 DETR 检测器进行零部件检测，将检测结果与标准图的先验标注进行语义点云抽象；通过ICP配准算法在类别和尺度约束下消除定位误差，建立匹配关系后获取先验信息，同时将未匹配零部件标记为丢失（解决无视觉纹理丢失缺陷及检测器漏检问题）。
{{< figure src="/robot/整体框架.png" caption="算法层整体流程框架" >}}
{{< figure src="/robot/自研检测框架.png" caption="零部件检测网络框架图" >}}

- **零部件缺陷检测算法设计**：
  - 测量类零部件：点云配准 → 相似度快速筛分 → 形态学操作及 RANSAC 提取边界 → 点云映射完成测量
  - 表面缺陷（格栅及漏油）：创新的将缺陷检测转化为变化分割地问题，也就是说，和标准图进行差异对比，根据相应差别区域进行缺陷输出。通过STN姿态归一化变换预处理＋孪生神经网络进行无监督缺陷区域定位，达到国铁集团高精度要求。
  - 铁丝断裂缺陷：利用D-Former跨模态双分支分割算法，分别对RGB模态以及点云模态进行特征提取以及特征交互，提高铁丝分割的准确性，避免了工业相机曝光以及铁丝细粒度物体边界模糊影响。
{{< figure src="/robot/点云螺栓测量.png" caption="螺栓缺陷检测" >}}


- **Text2SQL智能问答系统设计**：在Web层面搭建设计搭建查询工作流及数据库Agent，通过客户端与私有部署Qwen3模型交互，返回数据库相关查询信息。

- **国产替代之昇腾服务器部署**：在昇腾310P服务器上进行模型训练及推理，进行Nvidia TensorRT算子迁移，通过利用MindSpore对模型进行训练，并利用MINDIE推理引擎对深度学习模型进行推理加速运算，完成整体算法国产替代，自主可控！

- **支持误检数据迭代优化**：参与Vision China2024，受百度智能云启发，利用上海AI lab开源的InternImage视觉大模型进行误检数据迭代优化，逐渐提升分类网络的准确性。

## 研究成果
ICRA顶级会议

《Detection of EMU Components Based on Optical Flow Attention Prior and Multi-modal RGBD RTDETR》

SCI期刊

《High Speed Train Bogie Component Detection Network with Dual-Branch Architecture Based on Tensor Fusion of Prior Structural Knowledge》

《The Multimodal Defect Detection Based on Position-Prior for Smart High-Speed Railway Inspection》

EI会议（最佳论文候选）

《An EMU Bogie Defect Detection Method Based on Similarity Comparison》

《基于深度学习的动车组转向架螺栓缺陷检测方法》

国家发明专利

《一种机器人巡检部件缺陷检测方法及其应用》

## 实际效果


{{< figure src="/高铁巡检.jpg" caption="项目效果图" >}}



**视频演示：高铁动车智能巡检系统运行实况**
{{< bilibili bvid="BV1bBDYBPE3a" >}}
**视频演示：机器人仿真视频**
{{< bilibili bvid="BV12rDYBcEhK" >}}
