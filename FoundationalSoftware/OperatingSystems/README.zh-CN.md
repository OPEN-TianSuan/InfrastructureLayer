[English](README.md) | **中文**

面向星载计算机与载荷的操作系统。

## [RROS · 双内核操作系统](https://github.com/OPEN-TianSuan/RROS)

RROS 是 BUPT-OS 面向星载计算机和载荷开发的双内核操作系统，由 **Rust 实时内核**和 **Linux 通用内核**组成。这一架构让卫星既能执行有严格时限的任务，也能运行 Linux 生态中的通用应用。

![RROS 双内核架构](https://bupt-os.github.io/website/docs/introduction/architecture.jpg)

RROS 关注星上软件的运行可靠性，目标之一是在 Linux 内核发生故障时维持关键实时任务的运行。RROS 也着眼于提升星上系统的并行处理能力，使星载计算机能够在处理多路传感器数据的同时执行其他星上任务。

[搭载 RROS 的天仪33星](https://bupt-os.github.io/website/news/2023_12_9/satellite_launch/)于 2023 年 12 月 9 日入轨。在轨试验计划包括运行 TensorFlow 和 Kubernetes，以及测试实时文件系统和实时网络传输。

[RROS 源码与文档](https://github.com/OPEN-TianSuan/RROS)
