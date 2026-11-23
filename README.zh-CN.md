<div align="center">

由 **[OPEN-TianSuan](https://github.com/OPEN-TianSuan)** 社区维护的卫星软件开源资源汇总仓库。

[![Total views](https://raw.githubusercontent.com/OPEN-TianSuan/.github/main/traffic/SatelliteSoftware.svg)](https://github.com/OPEN-TianSuan/.github/blob/main/traffic/SatelliteSoftware.csv "Cumulative recorded repository views; updated hourly")
[![README](https://img.shields.io/badge/README-English-blue?style=flat-square)](README.md)

[English](README.md) | **中文**

</div>

---

## 📋 关于本仓库

卫星软件按层构建。本仓库按主题划分目录，把操作系统、运行时系统与应用软件放在一起，便于集中查阅与比较。每个目录保留自己的 README 和完整资源清单。

## 📂 仓库结构

| 目录 | 内容 | 来源 |
| --- | --- | --- |
| [OperatingSystems](OperatingSystems/README.zh-CN.md) | 面向星载计算机与载荷的开源操作系统、标准与参考资料。 | `SatelliteOperatingSystem` |
| [RuntimeSystems](RuntimeSystems/README.zh-CN.md) | 面向卫星工作负载的运行时系统，暂为预留目录。 | — |
| [ApplicationSoftware](ApplicationSoftware/README.zh-CN.md) | SateLight 更新框架中使用的十个卫星应用（App1–App10）。 | `ApplicationSoftwareCode` |

## 📁 目录说明

### OperatingSystems — 操作系统

卫星操作系统资料。`docs/` 目录收录行业标准与社区文档，目录 README 还梳理了 RROS、Apache NuttX、RTEMS 以及运行在 COTS 硬件上的 Linux 等常用开源方案。入口：[OperatingSystems/README.zh-CN.md](OperatingSystems/README.zh-CN.md)。

### RuntimeSystems — 运行时系统

预留用于承载卫星工作负载的运行时系统，例如大模型推理运行时。目前目录为空，详见 [RuntimeSystems/README.zh-CN.md](RuntimeSystems/README.zh-CN.md)。

### ApplicationSoftware — 应用软件

ASE 2025 论文 *SateLight: a satellite application update framework for satellite computing* 中使用的十个应用（App1–App10），覆盖姿态确定、变化检测、客户端缓存、核心网、数据压缩、多阶段图像压缩、图像编码、目标检测、舰船检测与目标跟踪。入口：[ApplicationSoftware/README.zh-CN.md](ApplicationSoftware/README.zh-CN.md)。

## 🔗 相关仓库

- [EngineeringTools](https://github.com/OPEN-TianSuan/EngineeringTools) —— 开发、仿真与评估工具
- [SatelliteData](https://github.com/OPEN-TianSuan/SatelliteData) —— 遥感影像、轨道、遥测与通信数据
- [TechnicalLiterature](https://github.com/OPEN-TianSuan/TechnicalLiterature) —— 研究论文、标准与技术文档

## 🤝 参与贡献

欢迎研究人员、开发者、学生和卫星爱好者参与贡献。如需补充内容，欢迎提交 pull request 或发起讨论。

## 📄 许可

各目录所收录材料的许可证与版权仍归其原作者与原始仓库所有。
