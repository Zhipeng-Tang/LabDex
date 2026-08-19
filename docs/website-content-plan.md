# LabDex 项目主页内容规划

本文档用于规划 LabDex 项目主页的内容。页面整体参考轻量的论文项目页，例如 VGGT-Ω：单列布局、较多留白、少量导航链接，以项目视觉素材和清晰的研究介绍为主。

## 页面目标

主页需要让访问者在几分钟内了解：

- LabDex 解决了什么问题；
- Benchmark 的层级结构是什么；
- 数据集包含哪些任务、场景和模态；
- 如何下载和使用数据；
- 如何引用、贡献或联系项目作者。

## 推荐页面结构

```text
标题与链接
主视觉
Abstract
Benchmark Overview
Task Examples
Dataset
Evaluation Protocol
Benchmark Results
Quick Start
Citation
Acknowledgements / License
```

首版可以先实现以下部分：

```text
Title + Links
Hero Image / Video
Abstract
Benchmark Overview
Task Examples
Dataset
Citation
```

## 1. 标题与链接

### 页面内容

- 项目名称：`LabDex`
- 完整标题：`A Hierarchical Benchmark for Dexterous Manipulation in Laboratories`
- 作者列表和所属机构；
- 论文状态，例如 `Under Review`、`Coming Soon` 或会议名称；
- 项目资源链接：`Paper`、`Code`、`Dataset`、`Documentation`。

### 建议文案

```text
LabDex: A Hierarchical Benchmark for Dexterous Manipulation in Laboratories

Authors coming soon
Affiliations coming soon
```

### 待准备信息

- 作者姓名、作者主页链接；
- 通讯作者邮箱；
- 论文或预印本链接；
- 代码仓库链接；
- Dataset 链接：<https://huggingface.co/datasets/serandt/LabDex>。

## 2. 主视觉

主视觉是页面进入后的第一张图片或视频，应当让访问者直接理解 LabDex 与机器人、实验室和灵巧操作有关。

### 推荐素材

- 实验室机器人执行任务的横幅图；
- 机器人操作试管、瓶子、移液器或实验仪器的短视频；
- 一张展示多个任务层级的总览图；
- 一段 10 至 30 秒、无需声音即可理解的演示视频。

### 实现建议

- 图片或视频宽度与正文一致；
- 优先使用真实项目素材，不使用与项目无关的装饰图；
- 视频应提供 poster 图片和暂停状态；
- 所有图片添加有意义的 `alt` 文本；
- 移动端避免过大的固定高度。

## 3. Abstract

Abstract 用一到两段话说明研究问题、方法和贡献。主页版本不必完全照搬论文摘要，可以比论文更容易阅读。

### 建议写作模板

```text
Dexterous manipulation in laboratory environments requires robots to perform
fine-grained actions while following multi-step procedures. Existing benchmarks
often focus on isolated skills or a narrow set of tasks, making it difficult to
measure progress toward reliable laboratory automation.

LabDex introduces a hierarchical benchmark for evaluating robotic manipulation
from atomic skills to short-horizon tasks and long-horizon laboratory procedures.
The benchmark provides [数据规模] demonstrations across [任务数量] tasks,
with [数据模态] and standardized evaluation protocols.
```

### 待补充信息

- LabDex 面向的核心问题；
- 与已有数据集或 Benchmark 的差异；
- 数据规模；
- 层级数量和各层级定义；
- 主要贡献数量，建议控制在三点以内。

## 4. Benchmark Overview

这是 LabDex 主页的核心解释区域，建议用一张总览图配合简短文字说明。

### 层级结构示例

```text
Atomic Skills -> Short-Horizon Tasks -> Long-Horizon Experiments
```

### 每一层需要说明

#### Atomic Skills

单个、可复用的基础操作，例如抓取、移动、旋转、插入、倾倒或按压。

#### Short-Horizon Tasks

由多个基础操作组成的短任务，例如拿取试管并放入指定位置，或打开容器后完成一次倾倒。

#### Long-Horizon Experiments

包含多个阶段和条件的完整实验流程，需要机器人持续执行、纠错并维护任务状态。

### 推荐统计卡片

```text
[数据集规模]          Demonstrations
[任务数量]            Tasks
[层级数量]            Hierarchy Levels
[场景数量]            Laboratory Scenes
```

统计数字确定后再展示；在数据尚未最终确定前，使用 `Coming soon` 比虚构数字更合适。

## 5. Task Examples

用图片或短视频展示代表性任务。每个样例只需要任务名称、层级标签和一句说明。

### 推荐任务类别

- Grasping laboratory objects；
- Opening and closing containers；
- Pouring and transferring liquids；
- Pipetting or fine insertion；
- Placing objects into constrained locations；
- Multi-step laboratory procedures。

### 样例卡片模板

```text
Task: [任务名称]
Level: Atomic Skill / Short-Horizon / Long-Horizon
Description: [一句话说明任务目标]
```

### 实现建议

- 首版展示三到六个样例即可；
- 如果视频素材还没有准备好，可以先使用静态图片占位；
- 多个视频应使用统一尺寸，避免页面布局跳动；
- 每个视频提供 `controls`，并支持移动端播放。

## 6. Dataset

这一部分介绍数据集本身，主页只放最重要的信息，详细字段可以链接到 Hugging Face Dataset Card。

### 应包含的内容

- 数据来源和采集方式；
- 机器人平台与实验室环境；
- 任务和对象类别；
- 训练、验证、测试划分；
- 数据模态：RGB、深度、机器人状态、动作、语言指令等；
- 标注格式和目录结构；
- 数据许可和使用限制。

### 建议表格

| 项目 | 内容 |
| --- | --- |
| Modality | `[RGB / Depth / State / Action / Language]` |
| Tasks | `[任务数量]` |
| Demonstrations | `[演示数量]` |
| Environments | `[场景数量]` |
| Splits | `train / validation / test` |
| License | `[许可证名称]` |

### 数据格式示例

```text
LabDex/
├── train/
├── validation/
├── test/
├── annotations/
└── metadata.json
```

目录结构需要以实际发布格式为准，不要在主页中展示尚未确定的字段名称。

## 7. Evaluation Protocol

说明不同方法如何参与 Benchmark，以及结果如何计算。

### 需要回答的问题

- 输入是什么：图像、视频、语言指令或完整观测序列？
- 输出是什么：动作、轨迹、任务完成状态或策略？
- 每个层级使用什么评测方式？
- 是否允许使用额外训练数据？
- 测试集是否隐藏标签？
- 一次任务失败如何处理？

### 可考虑的指标

- Task Success Rate；
- Sub-task Completion Rate；
- Trajectory or Action Error；
- Completion Time；
- Recovery Success Rate；
- Long-horizon Completion Rate。

指标确定后再加入表格，并明确每个指标的计算方式。

## 8. Benchmark Results

展示基线方法和当前最佳结果。结果尚未准备好时，建议暂时隐藏整个区域，或只显示：

```text
Benchmark results are coming soon.
```

结果表建议包含：

| Method | Atomic Skills | Short-Horizon | Long-Horizon | Overall |
| --- | ---: | ---: | ---: | ---: |
| Baseline A | - | - | - | - |
| Baseline B | - | - | - | - |
| LabDex Baseline | - | - | - | - |

只有在实验设置、训练数据和评测协议一致时才比较结果。

## 9. Quick Start

提供一个最短可运行示例，降低数据集试用门槛。

### Hugging Face 示例

```python
from datasets import load_dataset

dataset = load_dataset("serandt/LabDex")
print(dataset)
```

### 还可以补充

- 安装依赖命令；
- 下载或缓存数据的命令；
- 查看一个样本的代码；
- 运行评测脚本的命令；
- 代码仓库中的完整教程链接。

示例必须在数据集正式发布后实际运行验证。

## 10. Citation

提供 BibTeX 代码块，并增加复制按钮。论文信息确定前可以暂时使用占位内容。

```bibtex
@article{labdex2026,
  title   = {LabDex: A Hierarchical Benchmark for Dexterous Manipulation in Laboratories},
  author  = {[Authors]},
  journal = {arXiv preprint arXiv:[ID]},
  year    = {2026}
}
```

## 11. Acknowledgements / License

### Acknowledgements

- 实验室和机器人平台；
- 数据采集与标注人员；
- 提供代码、模型或基础设施的项目；
- 资助机构和项目编号。

### License

明确列出：

- 数据集许可证；
- 代码许可证；
- 图片、视频和第三方数据的版权或使用限制；
- 数据中的隐私、安全和伦理注意事项。

## 实现顺序建议

1. 完成标题、作者和资源链接；
2. 加入一张项目总览图或一段演示视频；
3. 填写 Abstract；
4. 绘制并加入层级结构图；
5. 加入三到六个 Task Examples；
6. 根据正式数据格式填写 Dataset；
7. 补充 Quick Start 和 Citation；
8. 最后加入 Evaluation Protocol、Results 和致谢。

## 发布前检查清单

- [ ] 所有链接可以正常打开；
- [ ] Dataset 链接指向正确的 Hugging Face 仓库；
- [ ] 图片和视频在手机端不溢出；
- [ ] 视频有 poster 或加载失败时的替代内容；
- [ ] 统计数字与论文、README 和 Dataset Card 一致；
- [ ] 许可证、数据来源和引用信息明确；
- [ ] 代码示例已经实际运行；
- [ ] 页面在 GitHub Pages 的 `/docs` 发布源下可以正常加载。
