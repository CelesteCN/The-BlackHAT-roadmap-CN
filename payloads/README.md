# 进攻工程载荷

## 作战概览

本目录收录可直接编译的武器化源码实现，面向底层研究、获授权的红队行动与防御性遥测验证。

这些代码库不依赖会触发静态特征的公开自动化工具，而是从第一性原理出发演示原语工程：直接分发原生 API、翻转内存保护状态，以及遍历进程环境块（PEB）。

---

## 载荷索引

| 标识 | 重点 | 语言 | 关键机制 |
| :---: | :--- | :---: | :--- |
| **[01_dynamic_api_resolver](01_dynamic_api_resolver/)** | 内存内动态 API 解析 | C | 通过 `GS:[0x60]` 遍历 PEB、解析 EAT、DJB2 函数哈希、与静态 IAT 解耦 |
| **[02_offensive_rust_loader](02_offensive_rust_loader/)** | 规避 EDR 的内存加载器 | Rust | 内存状态翻转（`PAGE_READWRITE` 到 `PAGE_EXECUTE_READ`）、不使用 RWX 分配标志、二进制剥离 |

---

## 基础设施与实验环境前置条件

> 📖 **虚拟化与靶场搭建**：  
> 完整的 hypervisor 架构（Proxmox / ESXi）、多层 Active Directory 拓扑（GOAD）与隔离的恶意软件分析沙箱（FlareVM / REMnux），请参阅**[实验环境搭建指南](../field-guides/Lab_Setup_Guide.md)**。

### 工具链要求

- **C / C++ 工具链**：
  - Linux/WSL 交叉编译：`x86_64-w64-mingw32-gcc`（MinGW-w64）
  - Windows 原生：Microsoft Visual C++ Build Tools（`cl.exe`）或 Clang/LLVM
- **Rust 工具链**：
  - 带 `x86_64-pc-windows-msvc` target 的 `rustup`
  - Cargo profile 优化（`opt-level = "z"`、`lto = true`、`strip = true`）

---

## 法律与安全声明

所有载荷代码仅限用于获授权的教育研究，以及明确授权的渗透测试项目。只可在隔离的虚拟化沙箱中测试。

---

## 许可

本目录内所有可执行源代码、加载器、harness 与构建清单均依据 [MIT License](../LICENSE) 授权。

- **作者：** Sagar Biswas ([@SagarBiswas-MultiHAT](https://github.com/SagarBiswas-MultiHAT))
- **仓库：** [https://github.com/SagarBiswas-MultiHAT/The-BlackHAT-roadmap](https://github.com/SagarBiswas-MultiHAT/The-BlackHAT-roadmap)
