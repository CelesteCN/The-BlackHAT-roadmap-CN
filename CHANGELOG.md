# 变更日志

本文档记录 The BlackHAT Roadmap 的所有重要变更。

格式大致遵循 [Keep a Changelog](https://keepachangelog.com/en/1.1.0/)。

## [1.2.2] - 2026-10-30

### 新增
- **极致匿名工作流（`black-bag/Max_Anonymity_Workflow.md`）**：完整匿名栈的速查架构蓝图。把 Phase -1 与生存战术手册整合为一份清晰的端到端指南：
  - 完整流量链（本地机器 -> XMR 付费 VPS 上的 WireGuard -> Tor 网络 -> 目标）。
  - 多对手暴露面分析（你的 ISP、VPN 提供商、Tor 节点与目的地分别能看到什么）。
  - OPSEC 失败金字塔（人、网络、物理与取证四层）。
  - 极致匿名的七层结构（第 0 层到第 7 层）。
  - 三重身份分隔学说（真实身份、研究身份、作战身份）。
  - Whonix 架构的防泄漏隔离机制。
  - 威胁模型层级校准（第 1 层到第 4 层）。
  - 7 步行动前验证清单。
  - 取证失败复盘矩阵，逐项说明单点故障。
- **架构图（`assets/diagrams/Max_Anonymity_Workflow/`）**：
  - `1._The_Complete_Anonymity_Chain.png`：从物理位置经 Tor 出口的 9 节点执行流程图。
  - `2._The_Seven_Layers_of_Maximum_Anonymity.png`：纵深防御的分层堆叠总览。
  - `3._Verification_Flow.png`：行动前放行/中止验证决策树。
- **课程整合**：在 `README.md`、`PHASE_-1.md`、`BlackHat_Long-Term_Survival_Tactics.md`、`FAQ.md`、`Final_Word.md`、`assets/README.md` 与 `.github/TRACKER.md` 中同步了配套引用。

---

## [1.2.1] - 2026-10-16

### 新增
- **双许可框架**：正式的双许可架构，把课程文档与可执行工程代码库分离：
  - `LICENSE-DOCS` 中的 `CC BY-SA 4.0`，覆盖第一卷、第二卷、各类实战指南、追踪表以及 150+ 张架构图中全部 45,000+ 行书面课程内容。
  - 根目录 `LICENSE` 中的纯 `MIT`，覆盖源代码、实验 harness、C/Rust 载荷与构建自动化。
- **SPDX 源码头**：在武器化载荷（`main.c`、`main.rs`、`Makefile` 与 `Cargo.toml`）中统一加入 3 行作者信息与 `SPDX-License-Identifier: MIT` 元数据。
- **署名与防盗锚点**：在各主配套指南中嵌入规范仓库引用与指向精选进攻安全生态的交叉链接。

---

## [1.2.0] - 2026-09-26

### 首次公开发布

完整的零基础到精英进攻安全工程课程。

**核心课程**
- 8 个递进阶段（Phase -1：OPSEC 到 Phase 6：特种作战）
- 44,900+ 行高密度进攻工程文档
- 15 个主模块中共 440+ 个主要章节、1,120+ 个子章节
- 覆盖 13+ 种语言的 1,080+ 个已核验代码块

**技术覆盖**
- 按 18 个作战类别编目的 300+ 个进攻工具
- 映射 200+ 项 MITRE ATT&CK 技术（Enterprise v15、ICS、ATLAS）
- 150+ 张原创高分辨率示意图与架构可视化图
- 5 条推荐学习方向（漏洞利用研究员、红队、植入体开发、硬件、特种作战）

**可编译载荷**
- `01_dynamic_api_resolver`：C 实现的内存内 PEB 遍历与 DJB2 导出哈希
- `02_offensive_rust_loader`：Rust 实现的 RW 到 RX 内存状态翻转与二进制加固

**实战指南**
- 全面 FAQ（职业现实、硬件套件、量子迁移）
- 实验环境搭建指南（多层 AD、虚拟机管理程序蓝图、恶意软件沙箱）
- 理念：黑帽思维（认知学说、对抗性思维）
- MITRE ATT&CK 速查手册（Enterprise v15、ICS、ATLAS 战术矩阵）
- 工具清单（按阶段与类别索引的 300+ 工具）
- 资源汇总（权威文献、白皮书、实验存档）
- 结语（核验统计、研究者署名、2027-2028 前沿）

**黑袋卷**
- BlackHat 长期生存战术：3,000+ 行的反监视与全生命周期 OPSEC 手册

**社区基础设施**
- 带质量门槛的贡献指南
- 议题模板（课程修正、资源建议）
- 含技术验证清单的拉取请求模板
- 操作员成长追踪表（`.github/TRACKER.md`）：含日期追踪、并行学习配套、9 个 Phase 4 专业方向与精通关卡检查点的综合进度面板
- 安全策略与负责任披露流程
- 用于学术署名的 CITATION.cff
