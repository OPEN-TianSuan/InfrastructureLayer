<div align="center">

SateLight 是一款卫星应用更新框架，收录于卫星基础设施的软件维护方向。

[![README](https://img.shields.io/badge/README-English-blue?style=flat-square)](README.md)

[English](README.md) | **中文**

</div>

---

## 📂 收录内容

本目录介绍 **SateLight**，一款面向受限星地链路的卫星应用更新框架。源代码由独立的 [OPEN-TianSuan/SateLight 仓库](https://github.com/OPEN-TianSuan/SateLight)维护；本目录直接链接到该仓库，不复制代码。

SateLight 在地面端对容器化应用的新旧版本进行内容感知的差异分析，再由星上完成更新应用的重建，同时提供基于容器镜像分层的容错回滚机制。

## 🚀 功能特性

| 能力 | 说明 |
| --- | --- |
| 内容感知差异更新 | 支持镜像层、文件和内容三种粒度的应用变更表示。 |
| 星上应用重建 | 在星上应用细粒度变更，同时保持更新一致性。 |
| 容错回滚 | 基于容器镜像分层，在更新失败后恢复到先前的应用状态。 |
| 修改量评估 | 支持量化不同应用版本之间的代码修改程度。 |

## 📄 论文信息

**SateLight: A Satellite Application Update Framework for Satellite Computing**

Jinfeng Wen, Jianshu Zhao, Zixi Zhu, Xiaomin Zhang, Qi Liang, Ao Zhou, Shangguang Wang. Proceedings of the IEEE/ACM International Conference on Automated Software Engineering (ASE), 2025: 117–128.

论文研究受限星地链路下的容器化卫星应用更新问题。SateLight 不传输完整的新镜像，而是将应用新旧版本之间的语义变化编码为紧凑的更新表示，再由星上完成应用重建；论文在十个代表性卫星应用上，对 10%、20% 和 50% 的代码修改量进行了评估。

## 🚀 使用方法

克隆源码仓库以获取实现代码和使用说明：

```bash
git clone https://github.com/OPEN-TianSuan/SateLight.git
cd SateLight
```

地面端更新包生成、星上应用重建与回滚的完整流程、脚本和运行环境要求请参阅 [SateLight 源码仓库](https://github.com/OPEN-TianSuan/SateLight)。

## 📌 来源与许可

源代码仓库：[https://github.com/OPEN-TianSuan/SateLight](https://github.com/OPEN-TianSuan/SateLight)。

本目录仅收录项目介绍并链接到源代码，不镜像代码。当前许可证和版权归属信息请以源代码仓库为准。
