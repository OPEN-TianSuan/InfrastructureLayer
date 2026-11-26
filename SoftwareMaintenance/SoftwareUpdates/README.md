<div align="center">

SateLight is a satellite application update framework, collected under software maintenance for satellite infrastructure.

[![README](https://img.shields.io/badge/README-Chinese-blue?style=flat-square)](README.zh-CN.md)

**English** | [Chinese](README.zh-CN.md)

</div>

---

## 📂 What Is Here

This directory introduces **SateLight**, a satellite application update framework for constrained ground–space links. The source code is maintained in the standalone [OPEN-TianSuan/SateLight repository](https://github.com/OPEN-TianSuan/SateLight); it is linked directly rather than copied into this directory.

SateLight performs content-aware differential analysis between original and updated containerized applications on the ground, then reconstructs the updated application onboard. It also provides fault-tolerant rollback based on container image layers.

## 🚀 Capabilities

| Capability | Description |
| --- | --- |
| Content-aware differential updates | Represents application changes at layer, file, and content granularity. |
| Onboard reconstruction | Applies fine-grained changes onboard while preserving update consistency. |
| Fault-tolerant rollback | Uses container image layers to recover a previous application state after an update failure. |
| Change evaluation | Supports measuring the extent of code changes between application versions. |

## 📄 Paper

**SateLight: A Satellite Application Update Framework for Satellite Computing**

Jinfeng Wen, Jianshu Zhao, Zixi Zhu, Xiaomin Zhang, Qi Liang, Ao Zhou, Shangguang Wang. Proceedings of the IEEE/ACM International Conference on Automated Software Engineering (ASE), 2025: 117–128.

The paper studies how to update containerized satellite applications over constrained ground–space links. Instead of transferring a complete new image, SateLight encodes semantic changes into a compact update representation and reconstructs the updated application onboard. The evaluation covers ten representative satellite applications with 10%, 20%, and 50% code modifications.

## 🚀 Usage

Clone the source repository to access the implementation and its usage instructions:

```bash
git clone https://github.com/OPEN-TianSuan/SateLight.git
cd SateLight
```

See the [SateLight repository](https://github.com/OPEN-TianSuan/SateLight) for the source code, scripts, environment requirements, and complete workflow for ground-side update generation, onboard reconstruction, and rollback.

## 📌 Source and License

Source code: [https://github.com/OPEN-TianSuan/SateLight](https://github.com/OPEN-TianSuan/SateLight).

This directory contains project information and links to that source; it does not mirror the code. Check the source repository for its current license and attribution information.
