<div align="center">

SateLight 卫星应用更新框架，收录于卫星基础设施的软件维护方向。

[![README](https://img.shields.io/badge/README-English-blue?style=flat-square)](README.md)

[English](README.md) | **中文**

</div>

---

## 📂 收录内容

`SateLightCode/` 为 SateLight 项目的应用更新框架代码，迁移自上游仓库 [WenJinfeng/SateLight](https://github.com/WenJinfeng/SateLight) 的 `SateLightCode/` 目录。

## 📄 论文信息

**SateLight: A Satellite Application Update Framework for Satellite Computing**

Jinfeng Wen, Jianshu Zhao, Zixi Zhu, Xiaomin Zhang, Qi Liang, Ao Zhou, Shangguang Wang.
Proceedings of the IEEE/ACM International Conference on Automated Software Engineering (ASE), 2025: 117–128.

论文研究受限星地链路下的容器化卫星应用更新问题。SateLight 不传输完整的新镜像，而是在地面端对应用的新旧版本进行内容感知的差异分析，将语义变化编码为紧凑的元数据表示，再由星上完成应用重建；同时提供基于容器镜像分层的容错回滚机制。

论文的主要贡献包括：

1. 一种内容感知的差异更新方法，支持镜像层、文件与内容三种粒度。
2. 星上细粒度重建流程，在应用变更的同时保持更新一致性。
3. 基于镜像分层的容错恢复机制，可在更新失败时回滚到先前状态。
4. 在十个代表性卫星应用上，针对 10%、20% 与 50% 代码修改量开展评估。

## 📁 代码结构

| 文件 | 作用 |
| --- | --- |
| `write_diff.py` | 地面端差异分析与更新包生成。 |
| `myers.py` | 差异分析使用的 Myers 行级 diff。 |
| `substitute.py` | 星上重建与回滚。 |
| `detection.py` | 容器运行状态监控与失败处理。 |
| `file_change.py`、`file_change_js.py`、`file_change_m.py` | 生成文件级更新变体。 |
| `dir_change.py`、`dir_change_js.py`、`dir_change_m.py` | 生成目录级更新变体。 |
| `get_change_rate.py` | 量化两个版本之间的代码修改程度。 |

## 🚀 使用方法

运行环境需要 Python 3、`tar` 与 `gzip`；`detection.py` 还需要 Python Docker SDK，OCI 镜像转换需要 `skopeo`。

脚本要求工作目录中包含 `diff_content/`、`workspace/diff_content/` 以及 `workspace/tmp/{extract_dir,staged_diff_content,staged_layer}`。这些路径在脚本中定义，可按实际环境调整。

### 地面站

生成差异更新包：

```bash
python write_diff.py layer   # 镜像层粒度
python write_diff.py all     # 文件粒度
python write_diff.py inc     # 内容粒度
```

脚本会在当前目录生成 `diff_content.tar.gz`。若工作目录结构不同，请调整传入 `write_diff` 的路径。

### 星上

应用更新：

```bash
python substitute.py <更新模式> <备份模式>
```

支持的组合：

- `layer none`
- `all none`
- `inc none`
- `inc layer`
- `inc file`
- `inc patch`

### 失败检测

在 `detection.py` 中配置镜像路径、容器名与处理脚本，并在更新后的容器运行期间启动它。当容器以非零状态退出或被终止时，脚本会调用 `substitute.py` 执行回滚。

### 变体生成与修改率

`file_change.py` 与 `dir_change.py` 及其 `_js`、`_m` 变体用于生成修改后的应用版本；`get_change_rate.py` 用于统计两个版本之间的代码修改率。

## 📌 来源与许可

上游仓库：https://github.com/WenJinfeng/SateLight（`SateLightCode/` 目录）。

上游仓库未提供许可证文件，版权归原作者所有；如需复用，请联系原作者确认授权条款。
