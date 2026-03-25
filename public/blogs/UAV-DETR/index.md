
## Abstract

- 目的是：UAV-OD (Unmanned aerial vehicle object detection)
- 框架是：detection transformer (DETR) framework
- 数据集是：
  - VisDrone
  - UAVVaste dataset
- 达成效果：
  - AP 提升 3.1%
  - AP50 提升 4.2%（over the baseline）
- github链接：
  https://github.com/ValiantDiligent/UAV-DETR


## Introduction

### 先前方法的痛点
- rely on manually designed components

### 现有改进
- end-to-end models 能够解决上述问题

### DETR 的问题
- designed for natural images
- 在 UAV 场景下存在挑战：
  - 小目标
  - 遮挡
  - 光照变化

### UAV-DETR 做了什么
1. an efficient end-to-end detector transformer
2. multi-scale feature fusion with frequency enhancement module (MSFF-FE)
3. frequency-focused downsampling module (FD)
4. semantic alignment and calibration module (SAC)


## Related Work

### 1. 无人机目标检测现状
- 挑战：
  - detecting small objects
  - managing occlusions
  - real-time performance vs computational complexity

- 常见方法：
  - utilizing higher-resolution feature maps
  - leveraging contextual information

- 不足：
  - frequency domain is underutilized


### 2. 实时检测模型
- YOLO 系列：
  - 使用 NMS
  - 问题：
    - 减慢速度
    - 引入超参数

- RT-DETR：
  - 无需 NMS
  - 更适合实时检测


### 3. 特征融合
- 问题：
  - semantic gaps

- 改进：
  - 不仅使用 spatial domain
  - 还可以利用 frequency domain


## Method

### 1. Multi-Scale Feature Fusion with Frequency Enhancement (MSFF-FE)
- 使用 FFT 进行频域增强
- 强化小目标（高频信息）
- 多尺度特征提取
- 同时学习：
  - 空间信息
  - 频率信息
- 结构：
  - 大核
  - 小核
  - 残差连接


### 2. Frequency-Focused Downsampling
- 普通下采样：
  - 信息损失大

- 本文方法：
  - 使用 FF 模块捕捉高频
  - 使用池化寻找高频特征


### 3. SAC（Semantic Alignment and Calibration）
- 解决：
  - 特征错位
  - 语义不一致


## Experiments

### 1. Comparative Experiments
- 与其他方法对比性能

### 2. Ablation Studies
- 验证各模块作用：
  - MSFF-FE
  - FD Downsampling
  - SAC

- 具体结果：看表


## 总结

UAV-DETR 通过引入频域信息、多尺度特征融合以及语义对齐模块，
提升了无人机场景下的小目标检测能力，并保持了 DETR 的端到端优势。