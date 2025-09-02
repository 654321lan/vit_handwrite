# Vision Transformer (ViT) 用于 MNIST 手写数字识别

本项目使用 **Vision Transformer (ViT)** 架构在 MNIST 数据集上实现了图像分类任务。作为深度学习入门项目，它验证了将前沿的Transformer模型应用于经典计算机视觉任务的能力。

## 🎯 项目概述

本项目核心目标是：
- **模型实践**：实现并理解Vision Transformer模型架构。
- **领域适配**：修改原始ViT模型（针对ImageNet设计）以适应MNIST数据集（1通道灰度图，10分类）。
- **完整流程**：构建一个包含数据加载、模型训练、评估的完整深度学习管道。
- **效率工具**：利用AI工具辅助代码编写与调试，提升开发效率。

## 📊 最终性能

在经过 **10个Epoch** 的训练后，模型在MNIST测试集上达到了以下性能：

| 指标 | 结果 |
| :--- | :--- |
| **测试准确率** | **~98.18%** (具体数值以实际运行为准) |
| **训练时间** | ~分钟/epoch (CPU) |
| **超参数** | LR=0.003, Batch Size=100, Dim=64, Depth=6, Heads=8 |

*注：此项目为原理验证，旨在熟悉ViT架构及其工作流程。由于ViT参数量大且MNIST任务简单，传统CNN可能以更少参数达到相近精度。*

## 🏗️ 模型架构

本项目实现的ViT关键特性：
- **Patch Embedding**: 将28x28图像分割为7x7的patch（共16个）。
- **可学习位置编码**: 使用`nn.Parameter`学习patch的位置信息。
- **[CLS] Token分类**: 采用BERT风格的分类方式，使用额外可学习的`cls_token`聚合全局信息用于分类。
- **Transformer Encoder**: 包含6层编码块，每块含多头自注意力机制（8头）和MLP前馈网络（128维）。
- **自适应修改**: 将输入通道从3（RGB）修改为1（Grayscale）以适配MNIST。

## 🚀 快速开始

### 环境依赖

确保安装以下Python库：
```bash
pip install torch torchvision einops
