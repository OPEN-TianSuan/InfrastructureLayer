**English** | [Chinese](README.zh-CN.md)

Operating systems for satellite onboard computers and payloads.

## [RROS · Dual-kernel operating system](https://github.com/OPEN-TianSuan/RROS)

RROS is a dual-kernel operating system developed by BUPT-OS for satellite onboard computers and payloads. It pairs a **real-time kernel written in Rust** with a **general-purpose Linux kernel**. This design lets satellite systems run tasks with strict timing requirements alongside applications from the Linux ecosystem.

![RROS dual-kernel architecture](https://bupt-os.github.io/website/docs/introduction/architecture.jpg)

RROS aims to improve the reliability of onboard software. One goal is to keep time-critical tasks running when a fault affects the Linux kernel. RROS also aims to improve support for running multiple tasks in parallel, so onboard computers can process data from several sensors while handling other spacecraft workloads.

The [Tianyi-33 satellite carrying RROS](https://bupt-os.github.io/website/news/2023_12_9/satellite_launch/) entered orbit on December 9, 2023. The flight experiment plan included running TensorFlow and Kubernetes and testing real-time file systems and network transmission.

[RROS source code and documentation](https://github.com/OPEN-TianSuan/RROS)
