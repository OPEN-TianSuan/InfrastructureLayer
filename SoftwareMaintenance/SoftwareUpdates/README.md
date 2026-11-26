<div align="center">

The SateLight application update framework, collected under software maintenance for satellite infrastructure.

[![README](https://img.shields.io/badge/README-Chinese-blue?style=flat-square)](README.zh-CN.md)

**English** | [Chinese](README.zh-CN.md)

</div>

---

## 📂 What Is Here

`SateLightCode/` contains the application update framework from the SateLight project. The code is migrated from the upstream repository [WenJinfeng/SateLight](https://github.com/WenJinfeng/SateLight), directory `SateLightCode/`.

## 📄 Paper

**SateLight: A Satellite Application Update Framework for Satellite Computing**

Jinfeng Wen, Jianshu Zhao, Zixi Zhu, Xiaomin Zhang, Qi Liang, Ao Zhou, Shangguang Wang.
Proceedings of the IEEE/ACM International Conference on Automated Software Engineering (ASE), 2025: 117–128.

The paper studies how to update containerized satellite applications over constrained ground–space links. Instead of transferring a complete new image, SateLight performs a content-aware differential analysis between the original and updated application versions on the ground, encodes the semantic changes into a compact metadata representation, and reconstructs the updated application onboard. It also provides a fault-tolerant rollback mechanism based on container image layers.

The main contributions are:

1. A content-aware differential update method operating at layer, file, and content granularity.
2. An onboard reconstruction process that applies fine-grained changes while preserving update consistency.
3. A layer-based fault-tolerant recovery mechanism that can roll back to a previous application state.
4. An evaluation on ten representative satellite applications with 10%, 20%, and 50% code modifications.

## 📁 Code Layout

| File | Role |
| --- | --- |
| `write_diff.py` | Ground-side differential analysis and update payload generation. |
| `myers.py` | Myers-based line diff used by the differential analysis. |
| `substitute.py` | Onboard reconstruction and rollback. |
| `detection.py` | Container runtime monitoring and failure handling. |
| `file_change.py`, `file_change_js.py`, `file_change_m.py` | Generate file-level update variants. |
| `dir_change.py`, `dir_change_js.py`, `dir_change_m.py` | Generate directory-level update variants. |
| `get_change_rate.py` | Quantify the extent of code changes between two versions. |

## 🚀 Usage

Requirements: Python 3, `tar` and `gzip`, the Docker SDK for Python for `detection.py`, and `skopeo` for OCI image conversion.

The scripts expect a workspace with `diff_content/`, `workspace/diff_content/`, and `workspace/tmp/{extract_dir,staged_diff_content,staged_layer}`. These paths are defined in the scripts and can be adjusted.

### Ground station

Generate the differential payload:

```bash
python write_diff.py layer   # layer-level diff
python write_diff.py all     # file-level diff
python write_diff.py inc     # content-level diff
```

The script writes `diff_content.tar.gz` in the current directory. Adjust the paths passed to `write_diff` when the workspace layout differs.

### Satellite

Apply the update:

```bash
python substitute.py <update-mode> <backup-mode>
```

Supported combinations:

- `layer none`
- `all none`
- `inc none`
- `inc layer`
- `inc file`
- `inc patch`

### Failure detection

Configure the image path, container name, and handler in `detection.py`, then run it while the updated container is active. On a non-zero exit or kill event it invokes `substitute.py` for rollback.

### Variant generation and change rate

`file_change.py` and `dir_change.py`, together with their `_js` and `_m` variants, generate modified application versions. `get_change_rate.py` reports the change rate between two versions.

## 📌 Source and License

Upstream: https://github.com/WenJinfeng/SateLight (directory `SateLightCode/`).

The upstream repository does not include a license file. Copyright remains with the original authors; contact them for reuse terms.
