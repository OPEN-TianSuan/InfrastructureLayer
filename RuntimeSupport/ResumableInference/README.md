<div align="center">

Rover is a local multimodal inference engine with resumable execution, collected under runtime support for satellite and edge computing.

[![README](https://img.shields.io/badge/README-Chinese-blue?style=flat-square)](README.zh-CN.md)

**English** | [Chinese](README.zh-CN.md)

</div>

---

## 📂 What Is Here

This directory introduces **Rover**, a general-purpose inference engine for running models locally. The source code is maintained in the standalone [OPEN-TianSuan/Rover repository](https://github.com/OPEN-TianSuan/Rover); it is linked directly rather than copied into this directory.

Rover targets single-machine and edge environments where inference can take a long time, memory is constrained, or a process may need to pause and resume. Its current model backend supports Qwen3-VL, with model weights loaded from a local directory.

## 🚀 Capabilities

| Capability | Description |
| --- | --- |
| Multimodal inference | Accepts text and still-image inputs through the command line or Python API. |
| Resumable sessions | Persists inference progress and resumes a paused or interrupted request from committed steps. |
| Chunked prefill | Processes long prompts in configurable chunks, with chunk-first, layer-first, and scheduled execution options. |
| KV cache formats | Supports Dense, KIVI, and TurboQuant caches; the quantized CUDA paths require building the project kernels. |
| Local execution | Loads model files from disk and supports CPU execution with Dense cache as well as CUDA-capable GPUs. |

## 🏗️ Architecture

Rover runs inference through input preparation, prefill, and autoregressive decoding. It saves session state and KV cache data so execution can continue from the latest committed progress. The runtime also coordinates model computation with storage I/O and supports cache formats with different memory and performance trade-offs.

See the [Rover architecture document](https://github.com/OPEN-TianSuan/Rover/blob/main/doc/architecture_en.md) for component details and execution flows.

## 🚀 Usage

Requirements: Python 3.10–3.13 and [uv](https://docs.astral.sh/uv/). A CUDA-capable GPU is recommended; CPU execution is available with the default Dense cache.

Clone the source repository and install its dependencies:

```bash
git clone https://github.com/OPEN-TianSuan/Rover.git
cd Rover
uv sync
```

Download a supported model, such as Qwen3-VL-2B-Instruct, and replace `/path/to/model` with its local directory:

```bash
uv run rover generate \
  --model /path/to/model \
  --prompt 'Describe this image.' \
  --image /path/to/photo.jpg \
  --state-dir runs/example \
  --device cuda \
  --max-new-tokens 128
```

To pause after a fixed number of generated tokens, add `--stop-after-tokens 16`. Continue the saved session with:

```bash
uv run rover resume --state-dir runs/example
```

On Jetson Orin with JetPack 6 and CUDA 12.6, use `python3 scripts/setup_jetson.py` to install compatible device dependencies. See the [Rover README](https://github.com/OPEN-TianSuan/Rover/blob/main/README.md) for the complete installation guide, Python API, configuration options, and limitations.

## 📌 Source and License

Source code: [https://github.com/OPEN-TianSuan/Rover](https://github.com/OPEN-TianSuan/Rover).

The source repository provides the implementation and is licensed under Apache-2.0. This directory contains project information and links to that source; it does not mirror the code.
