<div align="center">

A consolidated home for the open-source software that runs on satellites, maintained by the **[OPENSAT](https://github.com/OPEN-TianSuan)** community.

[![README](https://img.shields.io/badge/README-%E4%B8%AD%E6%96%87-blue?style=flat-square)](README.zh-CN.md)

**English** | [中文](README.zh-CN.md)

</div>

---

## 📋 About This Repository

Satellite software is built in layers. This repository keeps the layers side by side, with one directory per topic, so that operating systems, runtime systems and application software can be studied and compared in one place. Each directory keeps its own README and the full list of the resources it collects.

## 📂 Repository Layout

| Directory | Contents | Origin |
| --- | --- | --- |
| [OperatingSystems](OperatingSystems/) | Open-source operating systems, standards and reference material for onboard computers and payloads. | `SatelliteOperatingSystem` |
| [RuntimeSystems](RuntimeSystems/) | Runtime systems for satellite workloads. Reserved; content will be added later. | — |
| [ApplicationSoftware](ApplicationSoftware/) | Ten satellite application cases (App1–App10) used in the SateLight update framework. | `ApplicationSoftwareCode` |

## 📁 Directories

### OperatingSystems — 操作系统

Material on satellite operating systems. The `docs/` directory holds industry standards and community documents, and the directory README surveys widely used open-source choices such as RROS, Apache NuttX, RTEMS and Linux on COTS hardware. Start at [OperatingSystems/README.md](OperatingSystems/README.md).

### RuntimeSystems — 运行时系统

Reserved for runtime systems that host satellite workloads, for example inference runtimes for large models. The directory is intentionally empty for now; see [RuntimeSystems/README.md](RuntimeSystems/README.md).

### ApplicationSoftware — 应用软件

Ten applications (App1–App10) used in the ASE 2025 paper *SateLight: a satellite application update framework for satellite computing*, covering attitude determination, change detection, client cache, core network, data compression, image encoding, object detection, ship detection and tracking. Start at [ApplicationSoftware/README.md](ApplicationSoftware/README.md).

## 🔗 Related Repositories

- [EngineeringTools](https://github.com/OPEN-TianSuan/EngineeringTools) — development, simulation and evaluation tooling
- [SatelliteData](https://github.com/OPEN-TianSuan/SatelliteData) — remote sensing imagery, orbital, telemetry and communication data
- [TechnicalLiterature](https://github.com/OPEN-TianSuan/TechnicalLiterature) — research papers, standards and documentation

## 🤝 Contributing

Researchers, developers, students and satellite enthusiasts are welcome. If you would like to add material, open a pull request or start a discussion.

## 📄 License

Licenses and copyrights for the material collected in each directory remain with its original authors and repositories.
