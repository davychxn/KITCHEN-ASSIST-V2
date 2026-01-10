# KITCHEN-ASSIST-V2

[English](./README.md) | [中文](./README_CN.md)

## 项目概述

Kitchen Assistant V2 是一个用于厨房炊具检测和分类的计算机视觉项目，采用基于YOLO的目标检测和时序分类模型。

## 项目结构

### 文档
- **`README.md`** - 项目文档（英文）
- **`README_CN.md`** - 项目文档（中文）
- **`FINE_TUNING_JOURNEY.md`** - 模型微调过程文档（英文）
- **`FINE_TUNING_JOURNEY_CN.md`** - 模型微调过程文档（中文）

### 模型
- **`pan_pot_classifier_temporal.pth`** - 训练好的平底锅/炒锅时序分类PyTorch模型

### 脚本
- **`verify_yolo.py`** - YOLO模型验证脚本
- **`verify_temporal_on_originals.py`** - 在原始图像上进行时序模型验证

### 目录

#### `yolo_training/`
YOLO模型训练结果和产物。
- **`kitchenware_detector/`** - 第一次训练运行结果
  - 训练指标和曲线（F1、PR、P、R）
  - 混淆矩阵
  - 训练批次可视化
  - 模型权重（best.pt、last.pt、各轮次检查点）
  - 配置文件（args.yaml）
- **`kitchenware_detector2/`** - 第二次训练运行结果
  - 与kitchenware_detector相同的结构
  - 使用更多训练数据的改进模型

#### `verification_results_on_originals/`
在原始图像上的模型验证输出。
- 标注/注释图像，显示检测结果
- `verification_results_on_originals.json` - 验证指标和结果
- 测试类别：boiling（沸腾）、on_fire（着火）、smoking（冒烟）

## 主要功能

- **YOLO目标检测** - 使用YOLOv8/v11进行实时厨具检测
- **时序分类** - 使用时序信息增强分类能力
- **多类别检测** - 检测和分类各种厨房炊具及其状态
- **全面的训练指标** - 详细的F1、精确率、召回率曲线评估
- **验证流程** - 在多样化图像集上进行自动化测试

## 模型性能

### YOLO检测器
在 `yolo_training/kitchenware_detector/` 和 `yolo_training/kitchenware_detector2/` 中查看训练结果：
- 训练曲线和指标
- 混淆矩阵
- 验证批次预测
- 各个训练轮次的模型检查点

### 时序分类器
- 模型：`pan_pot_classifier_temporal.pth`
- 验证结果：`verification_results_on_originals/`
- JSON格式的性能指标

## 使用方法

### 验证YOLO模型
```bash
python verify_yolo.py
```

### 验证时序模型
```bash
python verify_temporal_on_originals.py
```

## 文档

有关微调过程的详细信息：
- 英文：[FINE_TUNING_JOURNEY.md](FINE_TUNING_JOURNEY.md)
- 中文：[FINE_TUNING_JOURNEY_CN.md](FINE_TUNING_JOURNEY_CN.md)

## 仓库内容

本仓库包含：
- ✅ 训练好的模型（PyTorch权重）
- ✅ 训练结果和指标
- ✅ 验证脚本和结果
- ✅ 文档（英文和中文）

**注意**：训练数据、标注工具（X-AnyLabeling、ChatRex）和实用脚本未包含在版本控制中。

## 依赖要求

```bash
# 核心依赖
pip install torch torchvision
pip install ultralytics  # 用于YOLO
pip install opencv-python
pip install numpy pandas matplotlib
```

## 许可证

详见各个组件的许可证。
