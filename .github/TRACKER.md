# The BlackHAT Roadmap：操作员成长追踪表

Fork 本仓库，用来追踪你在课程中的进度。在掌握理论概念、搭建可操作的实验环境、实现可运行的代码时，逐项勾掉里程碑。

**作者：** Sagar Biswas ([@SagarBiswas-MultiHAT](https://github.com/SagarBiswas-MultiHAT))  
**规范仓库：** [The BlackHAT Roadmap](https://github.com/SagarBiswas-MultiHAT/The-BlackHAT-roadmap)  
**精选生态：** [Awesome Cybersecurity Paths](https://github.com/SagarBiswas-MultiHAT/awesome-cybersecurity-paths) · [Penetration Testing Roadmap](https://github.com/SagarBiswas-MultiHAT/penetration-testing-roadmap) · [Awesome Cybersecurity Books](https://github.com/SagarBiswas-MultiHAT/awesome-cybersecurity-books)  
**许可协议：** [CC BY-SA 4.0](https://github.com/SagarBiswas-MultiHAT/The-BlackHAT-roadmap/blob/main/LICENSE-DOCS)

---

## 个人档案与目标操作员方向

- **操作员代号**： 
- **主方向**： [ ] Track A：漏洞利用研究员 | [ ] Track B：企业红队 | [ ] Track C：隐蔽植入体开发 | [ ] Track D：硬件/基础设施 | [ ] Track E：特种作战
- **副方向**： 
- **开始日期**： 
- **预计完成**： 

---

## 进度总览

| Phase | 状态 | 开始日期 [date] | 完成日期 [date] |
|:------|:------:|:-------:|:---------:|
| Phase -1: OPSEC 与基础设施 | [ ] | | |
| Phase 0: 底层基础 | [ ] | | |
| Phase 1: Web 应用安全 | [ ] | | |
| Phase 2: 网络与基础设施 | [ ] | | |
| Phase 3: 系统与内核利用 | [ ] | | |
| Phase 4: 专业方向（主） | [ ] | | |
| Phase 4: 专业方向（副） | [ ] | | |
| Phase 4 精通关卡 | [ ] | | |
| Phase 5: GREATEST | [ ] | | |
| Phase 6: 特种作战 | [ ] | | |

---

## Phase -1：OPSEC 与基础设施
*强化的作战纪律、分隔原则与匿名基础设施。*

- [ ] 完成威胁建模与身份隔离学说
- [ ] 配置非持久化研究操作系统（Tails OS / Whonix Gateway）
- [ ] 部署多跳代理链并防止 DNS 泄漏
- [ ] 使用非 KYC 加密货币建立匿名 VPS 托管
- [ ] 建立安全 PGP 通信与硬件净化流程
- [ ] **Phase -1 结业项目**：构建完全分隔、无个人归因的研究堡垒主机

**并行学习配套：**
- [ ] 阅读[极致匿名工作流](../black-bag/Max_Anonymity_Workflow.md)，了解端到端流量链蓝图
- [ ] 在本阶段同步阅读[长期生存战术](../black-bag/BlackHat_Long-Term_Survival_Tactics.md)
- [ ] 在本阶段同步阅读[理念：黑帽思维](../field-guides/Philosophy_The_BlackHat_Mindset.md)
- [ ] 阅读[常见问题](../field-guides/FAQ.md)，获取节奏建议与常见疑问

---

## Phase 0：底层基础
*计算机体系结构、x86/x64 汇编、内存布局，以及从裸机出发的 C 编程。*

- [ ] 理解 CPU 寄存器（RAX、RBX、RCX、RDX、RSI、RDI、RSP、RBP、RIP）
- [ ] 用 NASM 原生编写 32 位与 64 位汇编程序
- [ ] 掌握 C 内存管理：指针、指针算术、结构体对齐与堆分配（`malloc`/`free`）
- [ ] 在 Ghidra / IDA Free 中反汇编并逆向 C 二进制
- [ ] 理解 PE/ELF 二进制结构：DOS 头、NT 头、节头、导入/导出表
- [ ] 跟踪 Windows 原生 API 与系统调用分发（`ntdll.dll` -> 内核分发）
- [ ] **Phase 0 结业项目**：用 C 写一个自定义 PE 解析器，从磁盘和内存中转储节与导出函数

**并行学习配套：**
- [ ] 使用[实验环境搭建指南](../field-guides/Lab_Setup_Guide.md)搭建你的研究环境

---

## Phase 1：Web 应用安全
*现代 Web 应用架构、API 测试与复杂逻辑缺陷。*

- [ ] 掌握 HTTP/2、WebSockets 与现代认证（OAuth 2.0、OpenID Connect、SAML）
- [ ] 利用服务端请求伪造（SSRF）获取云实例元数据（AWS IMDSv2、GCP）
- [ ] 在 Python、Java 与 PHP 中识别并武器化不安全的反序列化
- [ ] 检测并利用条件竞争、TOCTOU 缺陷与 GraphQL 注入
- [ ] **Phase 1 结业项目**：完成 PortSwigger Web Security Academy 的 Practitioner 级别

---

## Phase 2：网络与基础设施
*网络测绘、Active Directory 攻击路径与多网段跳板。*

- [ ] 掌握 Active Directory 内部原理：Kerberos 票据（TGT、TGS、PAC）、LDAP、RPC、SMB
- [ ] 执行 Kerberoasting 与 AS-REP roasting，并掌握哈希破解策略
- [ ] 审计并利用 Active Directory 证书服务（ADCS）的错误配置（ESC1 到 ESC8）
- [ ] 执行跨林认证强制（PetitPotam、DFSCoerce）
- [ ] 通过 Chisel、Ligolo-ng 与 SSH 隧道配置多跳网络跳板
- [ ] **Phase 2 结业项目**：攻陷多层级 Active Directory 林，并通过证书滥用取得 Enterprise Admin

---

## Phase 3：系统与内核利用
*内存破坏、缓解措施绕过、shellcode 编写与操作系统内核内部原理。*

- [ ] 编写自定义 x86_64 位置无关 shellcode（无空字节、动态 API 解析）
- [ ] 使用返回导向编程（ROP）击败 ASLR、DEP/NX 与栈金丝雀
- [ ] 分析与利用 Windows 堆内部机制（Segment Heap、LFH 分配原语）
- [ ] 理解 Windows 内核架构（EPROCESS、令牌窃取、DKOM）
- [ ] 分析驱动攻击面：通过存在漏洞的已签名驱动实现任意读/写原语（BYOVD）
- [ ] **Phase 3 结业项目**：编写可用的本地提权利用程序，绕过 DEP 与 ASLR

**并行学习配套：**
- [ ] 对照 [MITRE ATT&CK 速查手册](../field-guides/MITRE_ATT%26CK_Quick_Reference.md)交叉核对技术
- [ ] 从[工具清单（300+）](../field-guides/Tools_Inventory.md)确认所需工具
- [ ] 用[资源汇总](../field-guides/Resources_Aggregated.md)中的论文与实验补充学习

---

## Phase 4：专业操作员方向

**在下面选定你的主方向与副方向。** 进入 Phase 5 之前，至少需要在 2 个方向上达到精通。

### Phase 4A：植入体开发
- [ ] 构建自定义 shellcode 加载器与反射式 DLL 注入原语
- [ ] 实现进程注入技术（进程镂空、APC 注入、early bird）
- [ ] 设计并实现 C2 协议通信通道
- [ ] **4A 里程碑**：构建可用的自定义植入体加载器

### Phase 4B：C2 作战
- [ ] 在 Sliver 与 Havoc C2 框架上达到操作员深度
- [ ] 以 CRTO 水平研究 Cobalt Strike 作业手法
- [ ] 设计带重定向器的多层 C2 基础设施
- [ ] 实现域前置与基于 CDN 的 C2 通道
- [ ] **4B 里程碑**：部署生产级规避型 C2 基础设施

### Phase 4C：EDR 与杀毒软件规避
- [ ] 实现直接与间接系统调用，绕过用户态钩子
- [ ] 利用异步定时器构建睡眠混淆（SilentMoonwalk、Cronos、Ekko）
- [ ] 执行合成调用栈伪造，击败 EDR 栈展开
- [ ] 将 BYOVD 攻击武器化，针对内核级 EDR 组件
- [ ] 实现 AMSI 与 ETW 绕过技术
- [ ] **4C 里程碑**：执行能通过内存扫描器与栈检查的 shellcode

### Phase 4D：漏洞研究
- [ ] 使用 AFL++、LibFuzzer 或自定义 QEMU 钩子构建模糊测试 harness
- [ ] 为闭源目标建立一套代码审计方法论
- [ ] 理解 0-day 发现与 CVE 披露流程
- [ ] 对闭源目标执行逆向工程与定向模糊测试
- [ ] **4D 里程碑**：在开源软件中发现并记录一个新型漏洞

### Phase 4E：持久化与 Rootkit
- [ ] 为进攻行动开发 Windows 内核驱动
- [ ] 实现直接内核对象操纵（DKOM）技术
- [ ] 研究 UEFI bootkit 持久化机制
- [ ] 实现 macOS 持久化（LaunchAgent、TCC 绕过）
- [ ] 构建 Linux LKM rootkit，并理解 eBPF tracepoint 挂钩
- [ ] **4E 里程碑**：构建一个概念验证级的内核态持久化机制

### Phase 4F：云与 AI 攻击
- [ ] 执行云厂商攻击链（AWS、Azure、GCP）
- [ ] 利用 Entra ID 与 M365 攻击面（PRT 窃取、Azure Arc 滥用）
- [ ] 研究 AI 智能体利用技术
- [ ] 实现间接提示注入与 RAG 投毒攻击
- [ ] **4F 里程碑**：在实验环境中完成端到端的云或 AI 定向攻击链

### Phase 4G：硬件与嵌入式
- [ ] 执行 JTAG 提取与硬件调试
- [ ] 对嵌入式设备固件进行逆向
- [ ] 执行 CAN 总线与车载协议攻击
- [ ] 开展 SDR 攻击（GPS 欺骗、蓝牙/BLE 拦截）
- [ ] **4G 里程碑**：从真实嵌入式设备中提取并分析固件

### Phase 4H：供应链攻击
- [ ] 测绘并利用 CI/CD 流水线攻击面
- [ ] 在实验环境中执行依赖混淆攻击
- [ ] 攻陷构建系统与软件包仓库基础设施
- [ ] 利用 GitHub Actions 及类似自动化平台
- [ ] **4H 里程碑**：在受控环境中演示完整的供应链攻击链

### Phase 4I：Active Directory 深度
- [ ] 掌握 ADCS ESC1 到 ESC15 的利用
- [ ] 利用 Kerberos 委派滥用（约束委派、非约束委派、RBCD）
- [ ] 执行林与域信任攻击
- [ ] 从本地 AD 向 Azure/Entra ID 横向移动
- [ ] 实现域持久化技术（Golden Ticket、Diamond Ticket、AdminSDHolder）
- [ ] **4I 里程碑**：通过证书与委派滥用来攻陷多林环境

### Phase 4 精通关卡

> 完成度检查点：推进之前，你必须至少完成 **1 个主方向** 与 **1 个副方向**。

- [ ] 已完成主方向：______
- [ ] 已完成副方向：______
- [ ] **关卡通过**：可以进入 Phase 5 和/或 Phase 6

---

## Phase 5：GREATEST（前 0.001%）
*独立的漏洞研究、零日工程与新型进攻武器化。*

- [ ] 对浏览器与操作系统的 1-day 漏洞做补丁差分
- [ ] 使用 AFL++、LibFuzzer 或自定义 QEMU 钩子构建模糊测试 harness
- [ ] 研究并记录针对现代操作系统缓解措施（HVCI、CET、VBS）的新型绕过
- [ ] 发表原创安全研究或负责任披露公告
- [ ] **Phase 5 里程碑**：在商业或企业软件中发现、工程化并负责任披露一个原创漏洞

**并行学习配套：**
- [ ] 阅读[结语](../field-guides/Final_Word.md)，了解课程统计、研究者署名与前沿研究方向

---

## Phase 6：特种作战
*物理红队、隐蔽潜入、高级社会工程、无人机侦察与量子迁移威胁建模。*

> **说明：** Phase 6 与 Phase 5 并行推进，而不是在其之后顺序执行。

- [ ] 掌握非破坏性进入：弹子锁开启、旁路工具、印模开锁与撞匙
- [ ] 审计电子门禁控制（EAC）系统：Wiegand 协议拦截、OSDP 缺陷与门禁卡克隆（125 kHz / 13.56 MHz RFID/NFC）
- [ ] 执行物理硬件投放：带外蜂窝网络桥（Hak5 LAN Turtle、Packet Squirrel）
- [ ] 开展无人机空中侦察：光学警卫巡逻测绘与暖通空调/机房热分布分析
- [ ] 构建心理诱导、电话钓鱼话术与多层身份掩护架构
- [ ] 审计“先存储、后解密”（SNDL）与后量子密码学（PQC）混合协商的回退漏洞
- [ ] 在 TIBER-EU / CBEST 框架下规划并执行模拟红队行动，并完整清理行动后的数字足迹
- [ ] **Phase 6 里程碑**：执行端到端全谱对手模拟，串起物理绕过、硬件植入投放、内部域攻陷与取证清理

**并行学习配套：**
- [ ] 阅读[结语](../field-guides/Final_Word.md)，了解前沿研究与 2027-2028 威胁格局

---

<div align="right">

*The BlackHAT Roadmap：操作员成长追踪表*<br/>
*维护者：Sagar Biswas ([@SagarBiswas-MultiHAT](https://github.com/SagarBiswas-MultiHAT)) · 规范仓库：https://github.com/SagarBiswas-MultiHAT/The-BlackHAT-roadmap*<br/>
*依据 Creative Commons Attribution-ShareAlike 4.0 International（CC BY-SA 4.0）许可发布*

</div>
