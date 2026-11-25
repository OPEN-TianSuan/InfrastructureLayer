<div align="center">

Rover 是一款支持断点恢复的本地多模态推理引擎，收录于面向卫星与边缘计算的运行时支撑方向。

[![README](https://img.shields.io/badge/README-English-blue?style=flat-square)](README.md)

[English](README.md) | **中文**

</div>

---

## 📂 收录内容

本目录介绍 **Rover**，一款用于本地运行模型的通用推理引擎。源代码由独立的 [OPEN-TianSuan/Rover 仓库](https://github.com/OPEN-TianSuan/Rover)维护；本目录直接链接到该仓库，不复制代码。

Rover 面向单机与边缘计算环境，适用于推理耗时较长、内存资源受限或进程需要暂停后继续执行的场景。当前模型后端支持 Qwen3-VL，模型权重从本地目录加载。

## 🚀 功能特性

| 能力 | 说明 |
| --- | --- |
| 多模态推理 | 通过命令行或 Python API 接收文本与静态图像输入。 |
| 会话恢复 | 持久化推理进度，并从最近一次已提交的步骤继续已暂停或中断的请求。 |
| 分块预填充 | 将长提示词按可配置的块处理，支持按块优先、按层优先和协同调度模式。 |
| KV 缓存格式 | 支持 Dense、KIVI 和 TurboQuant 缓存；量化缓存的 CUDA 路径需要编译项目内核。 |
| 本地执行 | 从本地磁盘加载模型文件；默认 Dense 缓存支持 CPU，也支持 CUDA GPU。 |

## 🏗️ 系统架构

Rover 按输入准备、预填充和自回归解码的阶段执行推理。它会保存会话状态与 KV 缓存，使任务能够从最近一次已提交的进度继续运行。运行时还会协调模型计算与存储 I/O，并提供不同内存占用和性能特性的缓存格式。

组件说明和执行流程请参阅 [Rover 架构文档](https://github.com/OPEN-TianSuan/Rover/blob/main/doc/architecture.md)。

## 🚀 使用方法

运行环境需要 Python 3.10–3.13 和 [uv](https://docs.astral.sh/uv/)。推荐使用支持 CUDA 的 GPU；默认 Dense 缓存也支持 CPU 执行。

克隆源码仓库并安装依赖：

```bash
git clone https://github.com/OPEN-TianSuan/Rover.git
cd Rover
uv sync
```

下载受支持的模型，例如 Qwen3-VL-2B-Instruct，并将 `/path/to/model` 替换为模型所在的本地目录：

```bash
uv run rover generate \
  --model /path/to/model \
  --prompt '描述这张图片。' \
  --image /path/to/photo.jpg \
  --state-dir runs/example \
  --device cuda \
  --max-new-tokens 128
```

如需在生成固定数量的词元后暂停，可添加 `--stop-after-tokens 16`。使用以下命令继续已保存的会话：

```bash
uv run rover resume --state-dir runs/example
```

在搭载 JetPack 6 和 CUDA 12.6 的 Jetson Orin 上，可运行 `python3 scripts/setup_jetson.py` 安装兼容的设备依赖。完整安装说明、Python API、配置选项和限制请参阅 [Rover 中文 README](https://github.com/OPEN-TianSuan/Rover/blob/main/README.zh-CN.md)。

## 📌 来源与许可

源代码仓库：[https://github.com/OPEN-TianSuan/Rover](https://github.com/OPEN-TianSuan/Rover)。

源代码由该仓库提供，并采用 Apache-2.0 许可证。本目录仅收录项目介绍并链接到源代码，不镜像代码。
