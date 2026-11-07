# BlackHat 长期生存策略手册

**完整作战安全手册 - 2027 年版**

**作者：** Sagar Biswas  
**版本：** v1.1.0 · 2027 版<br/> 
**配套文档：** The BlackHAT Roadmap（从 0 到 GREATEST）

> 📚 **配套路线图文档：**
> * **[The BlackHAT Roadmap（规范仓库）](https://github.com/SagarBiswas-MultiHAT/The-BlackHAT-roadmap)**：主课程体系、议题讨论与实时路线图更新。
> * **[主课程体系（阶段 -1 至 6）](../phases/PHASE_-1.md)**：从底层硬件到顶尖行动的零基础至精英级进攻工程课程大纲。
> * **[极致匿名工作流](Max_Anonymity_Workflow.md)**：完整匿名栈的架构蓝图——7 层、Whonix 与行动前验证。
> * **[理念：BlackHat 心智](../field-guides/Philosophy_The_BlackHat_Mindset.md)**：认知准则、对抗性假设排查与原始思维心智模型。
> * **[MITRE ATT&CK 速查](../field-guides/MITRE_ATT&CK_Quick_Reference.md)**：企业、ICS 与 ATLAS 技术映射、检测信号与攻击链蓝图。
> * **[工具清单](../field-guides/Tools_Inventory.md)**：与阶段对齐的 300+ 工具权威目录，覆盖从原始能力到工具的落地实现。
> * **[资源汇总](../field-guides/Resources_Aggregated.md)**：精选书籍、研究白皮书、会议演讲存档与动手实验平台。
> * **[实验环境搭建指南](../field-guides/Lab_Setup_Guide.md)**：多层级硬件规格与隔离的企业/内核实验室蓝图。
> * **[常见问题](../field-guides/FAQ.md)**：作战与职业转型常见问题大全。
> * **[结语](../field-guides/Final_Word.md)**：文档校验统计、研究者署名与前沿研究路线图。

> **推荐精选路线图资源：**
> * **[Awesome Cybersecurity Paths](https://github.com/SagarBiswas-MultiHAT/awesome-cybersecurity-paths)**：面向渗透测试人员、红队成员、蓝队成员与安全研究人员的精选学习路径。
> * **[Penetration Testing Roadmap](https://github.com/SagarBiswas-MultiHAT/penetration-testing-roadmap)**：实战评估流程、工具矩阵与项目方法论。
> * **[Awesome Cybersecurity Books](https://github.com/SagarBiswas-MultiHAT/awesome-cybersecurity-books)**：精选进攻性安全与底层系统文献。

---

> *"最好的行动，是没人发现它曾经发生过的那一次。"*
>
> *次好的，是确实发生了、但永远追不到你头上的那一次。*
>
> *没有第三名。*

---

## 目录

1. [写给初学者：从这里开始](#写给初学者从这里开始)
2. [威胁建模框架](#威胁建模框架)
3. [第 1 节：数字身份与人设架构](#第-1-节数字身份与人设架构)
4. [第 2 节：设备安全 - 操作系统与硬件](#第-2-节设备安全---操作系统与硬件)
5. [第 3 节：网络层作战安全](#第-3-节网络层作战安全)
6. [第 4 节：通信安全](#第-4-节通信安全)
7. [第 5 节：加密货币与资金安全](#第-5-节加密货币与资金安全)
8. [第 6 节：物理位置安全](#第-6-节物理位置安全)
9. [第 7 节：外貌与反监视](#第-7-节外貌与反监视)
10. [第 8 节：社会工程防御（自我保护）](#第-8-节社会工程防御自我保护)
11. [第 9 节：AI 驱动的监视规避（2027）](#第-9-节ai-驱动的监视规避2027)
12. [第 10 节：区块链取证威胁建模（2027）](#第-10-节区块链取证威胁建模2027)
13. [第 11 节：暗网作战安全](#第-11-节暗网作战安全)
14. [第 12 节：法律反情报](#第-12-节法律反情报)
15. [第 13 节：长期生存规划](#第-13-节长期生存规划)
16. [第 14 节：紧急撤离预案](#第-14-节紧急撤离预案)
17. [第 15 节：反执法（LE）意识](#第-15-节反执法le意识)
18. [第 16 节：2027 年国际司法辖区](#第-16-节2027-年国际司法辖区)
19. [第 17 节：作战安全黄金法则](#第-17-节作战安全黄金法则)
20. [第 18 节：案例研究](#第-18-节案例研究)
21. [第 19 节：高级硬件攻击防护](#第-19-节高级硬件攻击防护)
22. [第 20 节：内存取证与冷启动防御](#第-20-节内存取证与冷启动防御)
23. [第 21 节：服务端检测与 eBPF 意识](#第-21-节服务端检测与-ebpf-意识)
24. [快速参考行动清单](#快速参考行动清单)

---

## 写给初学者：从这里开始

本指南内容密集。在你读任何一项具体技术之前，先理解这套心智模型。每个被抓的初学者，原因都不是缺乏知识，而是有知识却不理解其背后的*为什么*。

### 长期生存的三大支柱

```
支柱 1：匿名
  行动期间，你不以真实身份存在。
  人设是一套戏服。穿就穿全，脱就脱净。
  只要有一条线把你的真实身份与某次行动连起来 = 被捕。

支柱 2：隔离分区（compartmentalization）
  不同行动 = 不同的一切。
  设备。网络。身份。钱包。通信渠道。
  在分区之间共用任何东西，都会让其他所有作战安全措施失效。

支柱 3：耐心
  最严重的错误都发生在快的时候。
  - 快速变现加密货币 = 链上分析标记你
  - 得手后到处乱说 = 线人找到你
  - 快速重复同一地点 = 监视识别出你
  慢的行动人员能活下来。没耐心的活不下来。
```

### 为什么大多数人会被抓（先学这一节）

研究这些内容。它们都是真实案件中的实际模式：

| 原因 | 被捕占比 | 如何避免 |
|-------|-------------|--------------|
| 吹嘘（线上或线下） | ~40% | 绝对的行动沉默 |
| 资金失误（过快套现、生活方式改变） | ~25% | 资金上保持耐心 + 不暴露生活方式的信号 |
| 技术失误（复用基础设施、未隐藏 IP） | ~20% | 隔离基础设施，并复盘本指南 |
| 被同伙出卖 | ~10% | 单独行动，或只使用极小规模、经过审查的团队 |
| 运气不好 / 物理监视 | ~5% | 反监视纪律 |

来源：对 2019-2026 年勒索软件/网络犯罪起诉案件的分析（DOJ、Europol 新闻稿）。

**最重要的一条洞见：** 大多数抓捕并非精密的侦查行动，而是*社交*层面的失败。行动人员开口说话了。或者花钱露了相。或者复用了同一个邮箱。技术层守住了；人的层面垮了。

### 如何使用本指南

- 第一次请按顺序阅读。每一节都建立在前一节之上。
- 初学者：重点关注第 1-5 节和快速参考清单。
- 进阶者：再加上第 6-12 节。
- 高级者：所有章节，尤其是第 13-21 节。
- 每次行动前后都复盘一遍清单。

---

## 威胁建模框架

在部署任何作战安全措施之前，你必须明白自己是在防*谁*。不同对手的能力天差地别。当你只面对本地警察时，却去建一座对抗民族国家级的掩体，既浪费资源又制造行动摩擦；而当你实际面对的就是民族国家对手时，准备不足则是致命的。

### 第 1 步：识别你的对手

<div align="center">
<table><tr><td>

<img src="../assets/diagrams/BlackHat_Long-Term_Survival_Tactics/1._Identify_Your_Adversaries.png" alt="Identify Your Adversaries" width="1400"/>

</td></tr></table>
</div>

### 第 2 步：明确你要保护什么

```
资产 1：身份
  是什么：你的真实姓名、位置、面孔、设备
  暴露途径：执法机构把真实身份与行动关联起来
  后果：被捕

资产 2：位置（当前）
  是什么：你人实际在哪里
  暴露途径：IP 泄露、刷卡交易、手机基站定位、CCTV
  后果：物理监视、被捕

资产 3：行动细节
  是什么：目标、技术、时机、同谋
  暴露途径：通信截获、线人、供述
  后果：起诉证据

资产 4：资金轨迹
  是什么：从行动流向你手中的资金
  暴露途径：区块链分析、银行记录、加密货币交易所 KYC
  后果：资产没收 + 证据

资产 5：基础设施
  是什么：行动中使用的服务器、域名、账号
  暴露途径：服务器查封、托管服务商配合
  后果：溯源归因 + 证据
```

### 第 3 步：绘制攻击路径

```
示例 - 身份暴露路径：
1. 行动期间 IP 泄露 -> 传唤 ISP -> 真实姓名（最常见）
2. 复用了作战安全建立之前的老邮箱/用户名 -> OSINT -> 真实身份
3. 支付方式被追查 -> 银行/交易所 -> KYC 记录

示例 - 位置暴露路径：
1. 行动期间手机放在口袋里 -> 运营商基站日志 -> 位置
2. 咖啡馆 CCTV + 人脸识别 -> IP 出现时刻的物理位置
3. 笔记本 WiFi 探测请求 -> 对设备移动的被动追踪
```

### 第 4 步：分配对策

把每条攻击路径对应到本指南中的一项对策。那套对应关系就是你的个人作战安全方案。

---

## 第 1 节：数字身份与人设架构

### 1.1 人设模型

<div align="center">
<table><tr><td>

<img src="../assets/diagrams/BlackHat_Long-Term_Survival_Tactics/2._DIGITAL_IDENTITY_AND_PERSONA_ARCHITECTURE.png" alt="The Persona Model" width="1400"/>

</td></tr></table>
</div>

每次行动都发生在某个人设之内。人设是：
- 一套完整、内部自洽的虚构身份
- 由与之匹配的基础设施支撑（邮箱、设备、网络、支付）
- 与你运营的其他所有人设相互隔离
- 绝不被你的真实身份触碰

### 1.2 搭建人设（分步进行）

**第 1 步：生成身份（离线完成）**
```
工具（本地运行，绝不用云端）：
- Fake Name Generator：https://www.fakenamegenerator.com（仅用于参考结构）
- 更好的做法：手工生成：符合目标国家的有真实感的姓名、
  合理年龄（25-40）、自洽的背景故事

在创建任何账号之前就要确定好背景要素：
- 姓名、出生日期、国籍
- 职业（IT 顾问、自由开发者 -> 便于解释技术层面的访问权限）
- 城市（你足够熟悉、能假装了解的地方）
- 教育背景
- "他们为何在网上活动"（需要时让社交媒体显得可信）
```

**第 2 步：搭建邮箱基础设施（经由 Tor）**
```bash
# 层级 1：匿名一次性邮箱（用于无关紧要的注册）
# 可选：Temp-Mail、Guerrilla Mail
# 切勿用于任何关键用途

# 层级 2：ProtonMail（用于需要长期存在但保持匿名的账号）
# 访问方式：Tor Browser -> proton.me
# 注册：不填手机号，不填找回邮箱
# 弱点：Proton 曾在 IP 问题上配合执法机构（Tor 可覆盖这一点）
# 要点：始终、只通过 Tor 访问

# 层级 3：自建邮件服务器（获得最大控制权）
# 要求：用 XMR 付款的 VPS + 从 Njalla 购买的域名
# 搭建：mailcow（基于 docker 的邮件服务器）
# 对多数人属于过度配置；对高价值行动则是必需品

# 安全邮箱替代方案（2027）：
# - Tutanota（德国，零知识加密，接受 XMR 付款）
#   https://tuta.com
# - Disroot（注重隐私的集体组织，XMPP + 邮箱）
#   https://disroot.org
```

**第 3 步：为该人设定下设备**
（完整设备搭建见第 2 节：每个人设配备自己的设备）

**第 4 步：为该人设构建网络层**
（见第 3 节：每个人设使用相互隔离的网络基础设施）

**第 5 步：为该人设创建加密货币钱包**
（见第 5 节：每个人设一个钱包，绝不复用）

**第 6 步：养人设（赶在它真正派上用场之前）**
```
可信人设至少需要 3-6 个月的养成期：
- 偶尔在相关论坛发帖（技术内容，不涉及任何行动信息）
- 一个有几个小提交的 GitHub 账号
- 一个有若干提问记录的 Stack Overflow 资料
- LinkedIn（可选：对企业间谍类人设有用）
- 目标：任何人搜索这个用户名/邮箱，都能看到一个可信的人

切勿：
- 建好人设就立刻用于行动
- 复用以往任何人设用过的用户名、邮箱或昵称
- 让人设的活动模式与你的真实活动模式吻合
  （时区、写作风格、发帖时段）
```

### 1.3 用户名与密码卫生

```bash
# 用户名生成（绝不跨平台复用）：
# 模式：[形容词][名词][2 位数字] 或 [单词][单词][3 位数字]
# 绝不用：真实姓名的首字母、出生年份、家乡城市

# 密码管理：
# KeePassXC（本地、加密、绝不上云）：
# https://keepassxc.org
# 数据库只存放在加密卷上
# 每一个账号都用不同的强密码

# 口令短语生成（Diceware 方法：真随机）：
# 5-7 个随机单词 = 无法破解但记得住
# 示例工具：
diceware  # apt install diceware
# 输出："correct horse battery staple lumber fence"
# 这每次都胜过 P@ssw0rd123! 这类复杂密码

# 绝对不要：
# - 会同步到云端的密码管理器（LastPass、1Password 云版）
# - Bitwarden 云模式（自建 Bitwarden/Vaultwarden 可以接受）
# - 浏览器保存的密码（可被提取）
# - 多个账号共用同一个密码（一处泄露 = 全部沦陷）
# - 任何行动用途的密码短于 16 个字符
```

---

## 第 2 节：设备安全 - 操作系统与硬件

### 2.1 操作系统选择（2027）

```
+------------+-------------------------+-------------------+-----------------+
| 系统       | 最适合                  | 优点              | 缺点            |
+------------+-------------------------+-------------------+-----------------+
| Tails OS   | 单次行动、              | 无痕（关机即      | 慢；            |
|            | 极致匿名的              | 清除）；默认      | 无持久化；      |
|            | 初学者                  | Tor；主机         | 软件受限        |
|            |                         | 无残留            |                 |
+------------+-------------------------+-------------------+-----------------+
| QubesOS    | 多人设行动、            | 按分区隔离        | 学习曲线        |
|            | 长期使用、              | 安全；每个人      | 陡峭；          |
|            | 高级行动人员            | 设独立 VM；       | 需 16GB+        |
|            |                         | 桌面安全          | 内存            |
|            |                         | 最佳              |                 |
+------------+-------------------------+-------------------+-----------------+
| Whonix     | 开发工作、              | Tor 网关          | 需宿主          |
| （Qubes）  | 需要持久化的            | 架构；工作站      | 系统；          |
|            | 行动                    | 相互隔离          | 裸机上存在      |
|            |                         |                   | 虚拟机逃逸      |
|            |                         |                   | 风险            |
+------------+-------------------------+-------------------+-----------------+
| Hardened   | 需要专业工具链          | 工具齐全；        | 默认非无痕；    |
| Kali Linux | 的渗透测试人员          | 界面熟悉          | 需自行加固      |
|            |                         |                   |                 |
|            |                         |                   |                 |
+------------+-------------------------+-------------------+-----------------+
```

**按技能水平推荐：**
- 初学者：**Tails OS** -- 从 USB 启动，不留任何痕迹
- 进阶者：**QubesOS** -- 操作系统内置隔离分区
- 高级者：**QubesOS + Whonix 虚拟机** -- 当前黄金标准（2027）

### 2.2 Tails OS - 搭建与使用（初学者路径）

```bash
# 第 1 步：下载 Tails
# https://tails.net - 校验 OpenPGP 签名
wget https://tails.net/tails-amd64-6.x.img
# 校验：
gpg --keyserver hkps://keyserver.ubuntu.com \
    --recv-keys A490D0F4D311A4153E2BB7CADBB802B258ACD84F
gpg --verify tails-amd64-6.x.img.sig tails-amd64-6.x.img

# 第 2 步：写入 USB（最小 8GB，推荐 16GB）
# Linux：
sudo dd if=tails-amd64-6.x.img of=/dev/sdX bs=16M status=progress
# Windows：使用 Rufus 或 balenaEtcher

# 第 3 步：从 USB 启动
# BIOS/UEFI：关闭 Secure Boot，把 USB 设为第一启动设备
# Tails 启动时：在启动菜单里选择 "Tails"

# 第 4 步：配置持久存储（可选，加密）
# 应用程序 -> Tails -> 持久存储
# 启用：个人数据、SSH 密钥、GnuPG、Tor Browser 书签
# 持久存储：AES-256 LUKS 加密
# 口令短语：使用 Diceware 生成 6 个以上单词

# Tails 的 Tor 连接：
# 启动时：Tails Tor 连接向导
# 选项 1：直连（Tor 未被封锁时）
# 选项 2：网桥（Tor 被封锁/被监控时）
#   网桥类型：obfs4（默认）或 Snowflake（更难被检测）

# 重要：绝不要在 Tails 中安装额外软件
# 额外的软件包 = 指纹识别面
# 只用 Tails 默认自带的软件
```

### 2.3 QubesOS - 搭建指南（进阶至高级）

```bash
# QubesOS 架构：
# - dom0：管理域（无网络访问）
# - sys-net：负责网络硬件
# - sys-firewall：网络与 AppVM 之间的防火墙
# - sys-whonix：Tor 网关（经由 Whonix）
# - AppVM：按人设/任务划分的独立分区

# 下载：https://www.qubes-os.org/downloads/
# 校验签名（关键：存在供应链攻击风险）：
gpg --with-fingerprint qubes-release-signing-key.asc
# 预期指纹：
# 427F 11FD 0FAA 4B08 0123 F01C DDFA 1A3E 3687 9494

# 安装：标准安装器，全盘加密（强制）
# 最低配置：8GB 内存（推荐 16GB）、64GB SSD

# QubesOS 隔离分区配置：
# 为每个人设创建一个 AppVM：
qvm-create --class AppVM --label red PersonaA
qvm-create --class AppVM --label orange PersonaB
qvm-create --class AppVM --label green LegalWork

# 让 PersonaA 经由 Whonix（Tor）出网：
qvm-prefs PersonaA netvm sys-whonix

# 让 LegalWork 经由标准防火墙（直连，可识别身份）：
qvm-prefs LegalWork netvm sys-firewall

# 一次性任务使用一次性虚拟机（关闭即自动销毁）：
# 右键点击 AppVM -> "Open in Disposable VM"
# 或者：
qvm-run --dispvm PersonaA

# 虚拟机之间的文件传输（不使用剪贴板交叉）：
# 始终使用 Qubes 文件复制（不要用剪贴板）：
qvm-copy-to-vm TargetVM /path/to/file
# 剪贴板：显式复制 -> Ctrl+Shift+C（由 dom0 拦截）

# 核心规则：绝不让 PersonaA 与任何处理真实身份的 VM 联网
# dom0 永不接入网络；物理隔离是架构性的
```

### 2.4 硬件选择（2027）

```
推荐硬件（兼容 Coreboot/LibreBoot）：

1. Lenovo ThinkPad X230 / T430（预算级，久经验证）：
   - 已刷 Libreboot（专有 BIOS 被完全替换）
   - 这一代不存在 Intel ME 主动管理引擎的问题
   - 价格：二手 60-150 美元
   - 弱点：硬件老旧，续航差

2. Lenovo ThinkPad X250 / T480（较新，仍兼容 Coreboot）：
   - 支持 Coreboot（不是完整的 LibreBoot：ME 只被部分中和）
   - 性能更好，有 USB-C，续航更长
   - 价格：二手 200-350 美元
   - 2027 年成本/能力/安全三者的最佳平衡

3. System76（新硬件，coreboot）：
   - https://system76.com - Linux 优先，开源固件
   - 更贵，但供应链尊重隐私

4. Purism Librem 14（WiFi、摄像头、麦克风的硬件断电开关）：
   - PureOS（基于 Debian，自由软件）
   - 断电开关 = 物理断开（无法通过软件关掉）
   - 价格：$1,400+
   - 注：Purism 曾出现发货延迟，并受到供应链方面的批评；
     购买前请核实当前订单状态与社区评价

避免：
- 任何带 Intel vPro 的机器（远程管理引擎，常开）
- 用可追溯支付方式购买的机器（信用卡、Amazon 账号）
- MacBook（专有固件，T2/T1 安全芯片让全盘擦除变得复杂）
- 任何来自与真实身份绑定的 eBay/Amazon 账号的二手设备
```

### 2.5 硬件拆改与预处理

```bash
# 第 1 步：物理改造
# 摄像头：先用胶带遮挡，再在 BIOS 中禁用（双重防护）
# 麦克风：物理禁用（要求严格就拆焊或切断连线）
# 蓝牙：BIOS 禁用，或物理拆除模块
# LTE 模块：如有则物理拆除（基带处理器是个黑盒）
# 序列号贴纸：全部撕除（机身、电池、电源适配器）

# 第 2 步：清除 BIOS 层面的标识信息
# 检查暴露了哪些信息：
sudo dmidecode | grep -i "serial\|uuid\|product"
# 输出：System Serial Number、Board Serial Number、UUID
# 这些都能被机器上运行的软件读取

# 通过 Coreboot/自定义 BIOS 替换（高级）：
# Coreboot 允许自定义字符串：把序列号替换为空值或随机值
# 没有 Coreboot：通过操作系统改这些的能力有限

# 第 3 步：伪造 MAC 地址（每次会话、联网前都要做）

# 临时伪造（重启即失效）：
sudo ip link set dev eth0 down
sudo ip link set dev eth0 address \
  $(openssl rand -hex 6 | sed 's/\(..\)/\1:/g; s/:$//')
sudo ip link set dev eth0 up

# 通过 NetworkManager 永久伪造：
nmcli connection modify "Connection-Name" \
  802-11-wireless.cloned-mac-address random
# 或者：802-3-ethernet.cloned-mac-address random

# macchanger（经典工具，依然有效）：
sudo macchanger -r eth0    # 随机 MAC
sudo macchanger -r wlan0   # 为 WiFi 使用随机 MAC
# -r：随机，-A：随机且厂商前缀合法，-p：恢复永久地址

# 第 4 步：主机名随机化（防止在本地网络被指纹识别）
# Tails 会自动完成这一步。
# 在其他系统上：
sudo hostnamectl set-hostname \
  $(cat /dev/urandom | tr -dc 'a-z' | fold -w 8 | head -n 1)

# 第 5 步：磁盘加密（没有商量余地）
# 使用 LUKS 全盘加密（Linux）：
# 必须在安装系统时就做：事后加装要困难得多
# Kali/Debian/Qubes 安装器默认即为 LUKS + LVM

# 验证加密：
sudo cryptsetup status /dev/mapper/luks-*
# 应显示：cipher: aes-xts-plain64, keysize: 512 bits

# VeraCrypt（用于便携加密容器，跨平台）：
# https://www.veracrypt.fr
# 为敏感文件创建加密容器：
veracrypt --create /path/to/container.vc --size=10G \
  --password="$(diceware -n 6)" --encryption=AES \
  --hash=SHA-512 --filesystem=ext4 --pim=0 -t -k "" \
  --random-source=/dev/urandom

# 合理推诿：VeraCrypt 隐藏卷
# 两个口令短语：外层（假）+ 内层（真）
# 遭胁迫时：交出外层口令 -> 只显示诱饵内容
# 内层卷在密码学上无法被检测出来
# 重要：各司法辖区的法律影响见第 12 节
# （英国 RIPA 及类似法律可强制解密 - 务必了解你所在地的法律环境）

# 挂载：
veracrypt /path/to/container.vc /mnt/secure_volume
# 卸载并清除内存中的痕迹：
veracrypt -d /mnt/secure_volume
```

### 2.6 安全擦除驱动器（已修正 - 关键章节）

**警告：本节推翻那条对 SSD 无效的常见 "shred" 建议。**

在你真正遭遇紧急情况之前，必须先弄明白*为什么* HDD 与 SSD 的擦除方式不同，这是必修课：

**机械硬盘（HDD）：**
```bash
# 依据 NIST SP 800-88（2014，现行标准），单遍覆写即足够
# 旧的 "DoD 7 遍" 方法源自 1995 年的指导文件，对现代 HDD 已经过时
# 对高密度现代硬盘，1 遍随机数据覆写在密码学上等效

# 单遍安全擦除（对 HDD 足够）：
sudo shred -vz /dev/sdX
# -v：详细输出（显示进度）
# -z：最后一遍写零（掩盖擦除痕迹）

# 符合 NIST 的单遍覆写：
sudo dd if=/dev/urandom of=/dev/sdX bs=4M status=progress

# 信任这次擦除之前，先验证硬盘：
sudo hexdump -C /dev/sdX | head -20
# 应显示全零或随机数据
```

**固态硬盘（SSD）- 规则完全不同：**
```bash
# 关键：shred 和 dd 无法可靠擦除 SSD
# 原因：SSD 采用磨损均衡与预留空间机制
#
# 磨损均衡：硬盘的闪存转换层（FTL）会把写入
# 导向新的存储单元以分散磨损。旧单元在覆写命令
# 执行之后仍保留数据。多数情况下 "shred /dev/sdX"
# 覆写的是与原始数据不同的物理位置。
#
# 预留空间：SSD 会预留 7-25% 的 NAND 作为备用块。
# 这些区域操作系统完全无法访问，但取证工具可以读取。
#
# 已有记录在案的案例中，执法机构对"已擦除"SSD 的取证恢复了数据。
# 不要相信对 SSD 的覆写。改用以下方法之一：

# 方法 1：密码学擦除（对 LUKS 加密盘最有效）
# 若 SSD 从一开始就是 LUKS 加密的，擦除 LUKS 头部即可：
sudo cryptsetup erase /dev/sdX
# 这会销毁加密密钥。所有数据在密码学上已不可访问。
# 数据在物理上仍然存在，但与随机噪声无法区分。
# 这是 NIST 认可的方法，只需几秒钟。

# 方法 2：ATA Secure Erase（使用硬盘内置的 SE 命令）
# 先确认硬盘是否支持：
sudo hdparm -I /dev/sdX | grep -i "erase"
# 若支持：
sudo hdparm --user-master u --security-set-pass TEMPPASS /dev/sdX
sudo hdparm --user-master u --security-erase TEMPPASS /dev/sdX
# 这会触发 SSD 内部的擦除例程 - 非破坏性方法中最彻底的一种

# 方法 3：NVMe Secure Erase（针对 NVMe SSD）
# 安装 nvme-cli：
sudo apt install nvme-cli
# 检查支持情况：
sudo nvme id-ctrl /dev/nvme0 | grep -i "fna"
# 执行带安全擦除的格式化：
sudo nvme format /dev/nvme0 --ses=1
# --ses=1：擦除用户数据；--ses=2：密码学擦除（若支持）

# 方法 4：物理销毁（高威胁场景下唯一有保证的方法）
# 任何硬盘内容可能导致被捕的紧急情况：
# 1. 从机器上拆下硬盘
# 2. 至少钻 5 个孔穿透 NAND 芯片（不只是 PCB 接口处）
# 3. 反复弯折 PCB 直至断裂
# 4. 分头丢弃在不同地点的不同垃圾桶
# 注：很多型号的 SSD 在 PCB 正反两面都有 NAND 芯片。
#       钻孔前先确认芯片位置。
#
# HDD 的物理销毁：
# 1. 在盘片上钻 5 个以上孔（透过外壳可以看到盘片）
# 2. 消磁（若条件允许）是不钻孔方案中最彻底的一种

# 内存擦除（关机时至关重要）：
# 冷启动防御见第 20 节。内存中的加密密钥与数据
# 在关机后仍会保留数秒至数分钟，时长取决于温度。
```

### 2.7 移动设备安全

```
绝不要用你的个人手机从事行动活动。
绝不。一次都不行。别拿"只是快速查一下"当借口。

原因：
- 个人手机 = 运营商实名登记 = 真实身份
- IMSI 通过运营商记录与你的身份永久绑定
- 即便开了飞行模式：WiFi 探测请求与蓝牙信标仍在工作
- Google/Apple 的位置历史：连续、精确、可依法调取
- 法拉第袋是真正让手机彻底静默的唯一可靠办法

行动用手机（如确有必要）：

方案 A：GrapheneOS（最安全的 Android，2027 年的标准做法）
  硬件：Google Pixel 7/8/9（唯一受支持的硬件）
  https://grapheneos.org

  购买提示：用现金在实体店购买。
  切勿网购（收货地址 = 真实身份）。
  刷入 GrapheneOS 之前，切勿用 Google 账号完成初始设置。
  首次开机应当发生在安装 GrapheneOS 的过程中或之后。

  特性：
  - 加固的内存分配器（针对堆的攻击更难奏效）
  - 按应用隔离网络（应用看不到其他应用的流量）
  - 沙箱化 Google Play（无需 Google 访问权限即可运行 Play 应用）
  - 自动重启（可配置 12/24 小时 -> 清空内存）
  - 胁迫 PIN（输错 PIN 即触发擦除）
  - 飞行模式真的有效（已验证）
  - 锁屏时可禁用 USB-C 接口
  - 提供仅 LTE 模式：防止 2G 降级攻击（防御 IMSI 捕获器）

  安装 GrapheneOS：
  # 网页安装器（基于 Chromium 的浏览器）：
  https://grapheneos.org/install/web
  # 或命令行安装器：
  https://grapheneos.org/install/cli

方案 B：CalyxOS（对初学者更友好，用 microG 兼容应用）
  硬件：Pixel 系列及部分 Fairphone
  安全性不如 GrapheneOS，但远好于原生 Android
  MicroG 用开源实现替代 Google Play 服务

绝对不要：
- 用 iPhone 从事行动（Apple 会配合执法机构，还有 iCloud 备份）
- 原生 Android（Google 遥测、运营商日志）
- 任何已 root、破坏了验证启动链的手机

行动手机配置（GrapheneOS）：
1. 用现金在实体店购买 Pixel；全程不牵涉个人账号
2. 首次开机之前就刷入 GrapheneOS（避免走 Google 初始设置）
3. 绝不插入登记在真实身份名下的 SIM 卡
4. 上网只使用 WiFi（公共场所，轮流更换地点）
5. 如需通话/短信：使用预付费 SIM（现金购买、虚假登记）
6. 安装：Tor Browser（经 Vanadium）、Signal、KeePassDX
7. 关闭：不需要时的蓝牙、NFC、WiFi 扫描
8. 启用：仅 LTE 模式（设置 -> 网络 -> 首选网络类型 -> LTE）
9. 自动锁屏：30 秒
10. 用完后：飞行模式、关机、放入法拉第袋

法拉第袋（物理屏蔽所有射频）：
- Mission Darkness（经测试，军用级）：https://www.mosequipment.com
- 省钱验证法：把手机放进金属饼干盒，然后拨打它。
  如果不响，说明有效。信它之前先测一次。
```

---

## 第 3 节：网络层作战安全

### 3.1 分层模型（2027）

<div align="center">
<table><tr><td>

<img src="../assets/diagrams/BlackHat_Long-Term_Survival_Tactics/3._The_Layering_Model_(2027).png" alt="The Layering Model (2027)" width="570"/>

</td></tr></table>
</div>

**为什么不用商业 VPN 链（ExpressVPN -> NordVPN）？**
- 有多起可查的配合执法机构案例（2017-2025）
- 尽管营销宣称"无日志"，实际仍在记录元数据（已有判例证实）
- 许多注册在美国/英属维尔京群岛辖区 -- 与五眼联盟关系密切
- 用信用卡付费 = 你的身份就是他们的第一条记录
- 绝不要用商业 VPN 链来保障作战安全

### 3.2 自建 VPN（正确做法）

```bash
# 第 1 步：获取一台匿名 VPS
# 接受 Monero 的服务商（无需 KYC，2027）：
# - Njalla：https://njal.la（瑞典，注重隐私，接受 XMR）
# - 1984 Hosting：https://1984.hosting（冰岛，接受 XMR）
# - FlokiNET：https://flokinet.is（冰岛/罗马尼亚，接受 XMR）
# - Alexhost：https://alexhost.com（摩尔多瓦，接受 XMR）
# - SporeStack：https://sporestack.com（XMR 支付，API 开通，痕迹极小）

# 切勿使用：AWS、Azure、GCP、DigitalOcean、Linode/Akamai
# 它们都要求信用卡 = 真实身份 = 传票 = 被捕

# 辖区优先级：
# 冰岛 > 摩尔多瓦 > 罗马尼亚 > 荷兰
# 避开：英国、美国、澳大利亚、加拿大、新西兰（五眼联盟）
# 避开：德国（与执法机构配合密切）、法国（ANSSI/DGSI 活跃）

# 第 2 步：只经由 Tor 访问 VPS 的设置页面
# 绝不用真实 IP 访问服务商控制台

# 第 3 步：部署 WireGuard（2027 年比 OpenVPN 更合适）
# 在 VPS 上（Ubuntu/Debian）：
apt update && apt install wireguard -y

# 生成服务端密钥：
wg genkey | tee /etc/wireguard/server_private.key \
  | wg pubkey > /etc/wireguard/server_public.key
chmod 600 /etc/wireguard/server_private.key

# /etc/wireguard/wg0.conf（服务端）：
cat > /etc/wireguard/wg0.conf << 'EOF'
[Interface]
PrivateKey = <SERVER_PRIVATE_KEY>
Address = 10.0.0.1/24
ListenPort = 51820
PostUp = iptables -A FORWARD -i wg0 -j ACCEPT; \
         iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
PostDown = iptables -D FORWARD -i wg0 -j ACCEPT; \
           iptables -t nat -D POSTROUTING -o eth0 -j MASQUERADE

[Peer]
PublicKey = <CLIENT_PUBLIC_KEY>
AllowedIPs = 10.0.0.2/32
EOF

# 启用：
systemctl enable wg-quick@wg0
systemctl start wg-quick@wg0

# 第 4 步：VPS 上零日志
# 日志销毁脚本（以 cron 每 30 分钟运行一次）：
cat > /usr/local/bin/logwipe.sh << 'SCRIPT'
#!/bin/bash
find /var/log/ -type f -name "*.log" -exec truncate -s 0 {} \;
find /var/log/ -type f -name "*.gz" -delete
journalctl --rotate --vacuum-time=1s 2>/dev/null
> /root/.bash_history
history -c
SCRIPT
chmod +x /usr/local/bin/logwipe.sh
echo "*/30 * * * * root /usr/local/bin/logwipe.sh" > /etc/cron.d/logwipe

# 第 5 步：SSH 加固
# /etc/ssh/sshd_config（现行写法，不使用已废弃指令）：
cat >> /etc/ssh/sshd_config << 'EOF'
PermitRootLogin no
PasswordAuthentication no
PubkeyAuthentication yes
AuthorizedKeysFile .ssh/authorized_keys
X11Forwarding no
AllowTcpForwarding no
MaxAuthTries 3
LoginGraceTime 30
Ciphers chacha20-poly1305@openssh.com,aes256-gcm@openssh.com
MACs hmac-sha2-512-etm@openssh.com
KexAlgorithms curve25519-sha256,curve25519-sha256@libssh.org
EOF
# 注：不需要 "Protocol 2"。所有现代 OpenSSH（7.6+）
# 默认只支持 SSHv2。加上它只会产生警告。
systemctl restart sshd

# 经由 Tor 连接 VPS（这样 VPS 永远看不到你的真实 IP）：
ssh -o "ProxyCommand=nc -x 127.0.0.1:9050 %h %p" \
    -i ~/.ssh/operation_key \
    -p 22 user@vps_ip_or_onion
```

### 3.3 Tor 网络 - 正确用法

```bash
# 安装 Tor：
apt install tor torsocks -y
# 或者：使用 Tor Browser（自带 Tor）

# torrc 配置（/etc/tor/torrc）：
# 网桥（所在国家封锁或监控 Tor 时使用）：
UseBridges 1
ClientTransportPlugin obfs4 exec /usr/bin/obfs4proxy
# 获取网桥：https://bridges.torproject.org（经由 Tor Browser）
# 或者：用 Gmail/Riseup 发邮件到 bridges@torproject.org

# ExcludeExitNodes（避免从特定国家出口）：
ExcludeExitNodes {US},{GB},{AU},{CA},{NZ}
StrictNodes 1
# 注：德国与法国的立场比较复杂；加入它们之前先查清
# 与你具体威胁建模对应的现状

# 增强流隔离（每个目标使用不同电路）：
IsolateDestAddr 1
IsolateDestPort 1

# Tor over VPN：你的设备 -> VPN -> Tor -> 目标
# 推荐这种做法：VPN 只看到 Tor 流量（看不到目标），
# Tor 入口看到的是 VPN 的 IP（不是你），目标看到的是 Tor 出口

# Tor 无法防护的情况：
# 1. 你设备上的恶意软件（在进入 Tor 之前就已外泄）
# 2. JavaScript 指纹识别（使用禁用 JS 的 Tor Browser）
# 3. 流量关联攻击（民族国家级别：时序分析）
#    时序攻击的详细防御见第 21 节
# 4. 出口节点对未加密流量的中间人攻击（始终使用 HTTPS）
# 5. 登录与真实身份绑定的账号（这会让一切努力作废）

# Tor Browser - 额外加固：
# 点击盾牌图标 -> 把安全级别设为 "Safest"
# about:config 设置：
# javascript.enabled = false（大多数网站会坏掉，但安全性最高）
# privacy.resistFingerprinting = true（Tor Browser 默认开启）
# webgl.disabled = true
# media.peerconnection.enabled = false  （防止 WebRTC 泄露）

# 泄露检测：
# https://www.dnsleaktest.com（经由 Tor Browser）
# https://ipleak.net（经由 Tor Browser）
# https://browserleaks.com（经由 Tor Browser）
# 三者都应显示 Tor 出口节点，而不是你的真实 IP
```

### 3.4 Proxychains4 - 配置（2027）

```bash
# /etc/proxychains4.conf:
dynamic_chain
proxy_dns
tcp_connect_timeout 5000
remote_dns_subnet 224
localnet 127.0.0.0/255.0.0.0
localnet 10.0.0.0/255.0.0.0

[ProxyList]
socks5 127.0.0.1 9050    # Tor SOCKS5（本地 Tor 守护进程）

# 用法示例：
proxychains4 -q curl https://target.com          # -q = 静默模式
proxychains4 -q nmap -sT -Pn -p 80,443 target.com
proxychains4 -q python3 exploit.py

# 经由 proxychains 做 DNS 泄露检测：
proxychains4 -q dig +short myip.opendns.com @resolver1.opendns.com
# 应返回 Tor 出口 IP，而不是你的 IP

# 注：nmap 的 UDP 扫描（-sU）无法通过 SOCKS5（不支持 UDP）
# 搭配 proxychains 时请使用纯 TCP 扫描方式
```

### 3.5 每次会话的反追踪

```bash
# 每次会话前轮换以下项目（已脚本化）：

#!/bin/bash
# session_start.sh - 每次行动会话前运行

# 1. 伪造 MAC 地址（两块网卡）
sudo ip link set eth0 down
sudo ip link set eth0 address \
  $(openssl rand -hex 6 | sed 's/\(..\)/\1:/g; s/:.$//')
sudo ip link set eth0 up
sudo macchanger -r wlan0 2>/dev/null

# 2. 随机化主机名
sudo hostnamectl set-hostname \
  "$(cat /dev/urandom | tr -dc 'a-z0-9' | head -c8)"

# 3. 设置尊重隐私的 DNS（不要用 ISP 的 DNS）
echo "nameserver 9.9.9.9
nameserver 149.112.112.112" | sudo tee /etc/resolv.conf

# 4. 清空 DNS 缓存（清除任何已缓存的查询）
sudo systemd-resolve --flush-caches 2>/dev/null \
  || sudo /etc/init.d/nscd restart 2>/dev/null

# 5. 继续之前先核验 IP
echo "=== Network Status ==="
curl -s https://check.torproject.org/api/ip
echo "=== DNS Leak Check ==="
dig +short myip.opendns.com @resolver1.opendns.com

# WebRTC 泄露是最常见的非 VPN 场景 IP 泄露：
# 即便用了 VPN，WebRTC 也能绕过并暴露真实 IP
# 检测：https://browserleaks.com/webrtc
# 修复：在 Firefox/Tor Browser 中设置 media.peerconnection.enabled = false
```

---

## 第 4 节：通信安全

### 4.1 安全即时通信 - 2027 年对比

```
层级 1：最高安全性（2027 黄金标准）

SimpleX Chat（推荐）：
  为何：没有用户 ID。没有手机号。没有用户名。
       服务器即使在元数据层面也无法把发送方与接收方关联起来。
       完全去中心化。中继服务器可自建。
  https://simplex.chat
  配置：下载应用 -> 无需注册 -> 分享你的地址链接
  用法：经 Tor 运行以获得最大匿名性
  状态（2027）：已审计，维护活跃，采用率持续上升

Signal：
  为何：端到端加密的黄金标准（Signal 协议）
  2027 年的弱点：
    - 需要手机号（与 SIM 卡绑定）
    - Signal 服务器能看到：你在和谁通信（元数据）
    - Signal 曾配合美国传票（提供了元数据：时间戳、
      手机号；但没有消息内容，因为他们本来就没有）
    - 注：自 2022-2023 年以来，Signal 服务端代码的更新节奏
      一直不稳定。加密本身仍然可靠；服务端行为
      的可审计性已不如从前。
  缓解措施：
    - 用预付费 SIM 注册（现金购买、虚假登记）
    - 启用：密封发送者（设置 -> 隐私 -> 高级 -> sealed sender）
    - 启用：屏幕锁、注册锁（PIN）
    - 阅后即焚：行动通信最长设为 1 小时
    - 记下安全码：当面或通过安全的旁路渠道核验
  状态（2027）：可用于不要求完全匿名的通信；
                 对匿名性至关重要的通信优先用 SimpleX

层级 2：去中心化 / 联邦式

Session：
  为何：无需手机号、无需邮箱。去中心化（洋葱路由）。
       构建在类 Tor 的覆盖网络（Lokinet）之上。
  https://getsession.org
  弱点：用户基数较小；元数据部分可获取
  用法：SimpleX 不可用时的备选

Briar：
  为何：点对点，无中心服务器。可经 Tor 工作。
       可离线工作（蓝牙/WiFi 网状组网）。
  https://briarproject.org
  最适合：互联网不可用或被监控时的通信
  弱点：双方必须同时在线（不支持存储转发）

层级 3：邮箱（仅在必要时使用）

ProtonMail（经由 Tor）：
  配置：Tor Browser -> proton.me -> 创建账号（不填手机号）
  加密：Proton 账号之间为端到端；对外使用 S/MIME/PGP
  弱点：Proton 会配合瑞士执法机构（他们是被命令这么做的）
             他们看不到内容（端到端加密）
             但他们能看到发件人/收件人的元数据
             解决办法：只经由 Tor 访问（他们看到的是 Tor 出口，不是你）

Tutanota（经由 Tor）：
  https://tuta.com
  与 ProtonMail 类似；德国辖区
  注：Tutanota 在 2021 年被强制安装监控（德国法院命令）
        监控针对的是某一个特定账号的元数据（不是内容）
        经由 Tor 访问即可免受此类监控影响

层级 4：应急 / 一次性

死信箱（最匿名：不经任何网络通信）：
  方法：共用一个邮箱账号：写草稿，永不发送
  双方都知道凭据 -> 读取草稿 -> 删除
  重要：多数邮箱服务商会记录草稿操作的元数据，包括
             IP 地址。使用此方法时务必经由 Tor 访问。
  用法：仅用于关键的一次性通信
```

### 4.2 PGP/GPG - 实用配置

```bash
# 生成密钥对：
gpg --batch --generate-key <<EOF
%no-protection
Key-Type: eddsa
Key-Curve: Ed25519
Key-Usage: sign
Subkey-Type: ecdh
Subkey-Curve: Curve25519
Subkey-Usage: encrypt
Name-Real: Handle_Only
Name-Email: anon@nowhere.invalid
Expire-Date: 1y
EOF

# 列出密钥：
gpg --list-secret-keys --keyid-format=long

# 为收件人加密文件：
gpg --encrypt --sign --armor -r recipient@address file.txt

# 解密：
gpg --decrypt file.txt.asc

# 对消息签名：
gpg --clearsign message.txt

# 导出用于分享的密钥（仅公钥）：
gpg --armor --export KEYID > my_pubkey.asc

# 备份私钥（离线保存，只存放在加密卷上）：
gpg --armor --export-secret-keys KEYID > KEEP_THIS_OFFLINE.asc
# -> 用 VeraCrypt 加密后存放在物理隔离的 USB 上

# 校验签名：
gpg --verify file.txt.sig file.txt
```

### 4.3 自建 C2 服务器（匿名 VPS）

```bash
# 切勿使用 AWS、Azure、GCP：都要信用卡 -> 可追溯
# 使用：Njalla、1984.hosting、FlokiNET（均接受 XMR，无 KYC）

# 第 1 步：经由 Tor 下单 VPS，用 XMR 付款
# 第 2 步：只经由 Tor + SSH 访问

# 经由 Tor 的 SSH 访问（用于 .onion 托管的 VPS）：
ssh -o "ProxyCommand=nc -x 127.0.0.1:9050 %h %p" \
    -i ~/.ssh/op_key \
    user@vpshostname.onion

# 生成 SSH 密钥（行动专用密钥，不是日常密钥）：
ssh-keygen -t ed25519 -a 200 -f ~/.ssh/op_key -C ""
# -a 200：密钥派生迭代次数（让暴力破解更慢）
# -C ""：不留注释（注释可能暴露密钥创建者）

# 日志销毁（在 VPS 上运行，每 30 分钟一次）：
cat > /usr/local/bin/logwipe.sh << 'SCRIPT'
#!/bin/bash
find /var/log/ -type f \( -name "*.log" -o -name "*.gz" \) \
  -exec truncate -s 0 {} \; 2>/dev/null
journalctl --rotate --vacuum-time=1s 2>/dev/null
truncate -s 0 /root/.bash_history /home/*/.bash_history 2>/dev/null
history -c
SCRIPT
chmod +x /usr/local/bin/logwipe.sh
(crontab -l 2>/dev/null; echo "*/30 * * * * /usr/local/bin/logwipe.sh") | crontab -
```

### 4.4 写作风格防御（文体计量分析）

```
AI 可以依据写作模式（句长、词汇、标点习惯、词频）以相当高的
准确率识别作者，尤其当手头有同一人的大量
样本时。

实用的反制措施：
- 相比你自然的语体，刻意缩短句子结构
- 避开你的特征词汇（你使用频率异常高的词）
- 采用与平时不同、但一致且人为的大小写习惯
- 段落长度比你自然状态下变化更大
- 先写行动帖，再翻译成另一种语言然后译回（机器
  翻译会打乱文体指纹，同时不丢失含义）
- 控制行动人设的发帖量（样本越少，分析越难）

2027 年可用的工具：
- Anonymouth 思路（当年的学术工具已过时；用它的原理）：
  写出文本，然后把词汇与句子分布与你已知的写作对比，
  手工修正偏离项
- 改写环节：写完草稿后，凭记忆用不同的词重写一遍。
  这比修改原文更有效。

不要使用任何需要把文本上传到云服务的文体计量工具。
```

---

## 第 5 节：加密货币与资金安全

### 5.1 加密货币作战安全模型（2027）

区块链分析能力已经有了长足进步。Chainalysis、Elliptic 与 CipherTrace 现在能以极高的置信度跨几十跳追踪资金。XMR（Monero）模式仍是最强的反制手段。理解他们*能*做什么、*不能*做什么，至关重要。

```
区块链分析能力（Chainalysis，2027）：

能追踪：
- 比特币，置信度高（区块链公开透明）
- BTC 进出交易所（来自配合的交易所的 KYC 数据）
- 混币（启发式分析有时能对 CoinJoin 去匿名化）
- 跨链桥（多数桥都会记录交易）
- 公链上的大多数代币（ETH、BNB、SOL）
- 闪电网络支付（通道的开启/关闭都在链上；
  路由启发式分析在某些情况下能部分去匿名化路径）

无法可靠追踪：
- Monero（环签名 + 隐匿地址 + RingCT = 没有输入输出关联）
- Zcash（仅限屏蔽交易；透明交易是可以被追踪的）
- 从未接触过 KYC 交易所的行动
- 通过线下一对一原子交换把 XMR 换成现金
```

<div align="center">
<table><tr><td>

<img src="../assets/diagrams/BlackHat_Long-Term_Survival_Tactics/4._Crypto_OPSEC_Model_(2027).png" alt="Crypto OPSEC Model (2027)" width="380"/>

</td></tr></table>
</div>

### 5.2 钱包架构

```bash
# 钱包类型：

# 热钱包（连接互联网）：
# 风险：设备被攻陷则密钥被盗
# 用途：只放少量行动资金
# 绝不：在热钱包里存放大额资金

# 冷钱包（硬件钱包，永不联网）：
# Trezor Model T：https://trezor.io（开源固件，可审计）
# Coldcard：https://coldcard.com（专注比特币，物理隔离签名）

# 关于 Ledger 的警告（不要使用）：
# 2023 年 5 月，Ledger 公布 "Ledger Recover" 功能，这证明了
# 其固件能够从安全元件中取出私钥，并把它
# 传送到外部服务器。这推翻了此前"安全元件使
# 密钥提取不可能"的架构声明。
# 这不是攻击者发起的远程利用；而是 Ledger 刻意
# 隐瞒的一项固件能力。
# Ledger 的信任模型已经破产。安全元件并不是信任边界。
# 物理提取需要专用设备（Kraken Security Labs 在 2020 年
# 披露过一项只需约 75 美元设备的硬件攻击）；
# 但固件层面的能力才是眼下更紧迫的威胁。
# 请改用 Trezor（开源固件）或 Coldcard。

# Monero 钱包（Feather Wallet，2027 年推荐）：
# https://featherwallet.org
# 支持离线/在线模式；内置 Tor；开源

# Monero 钱包配置：
# 第 1 步：尽可能在物理隔离的机器上下载 Feather Wallet
# 第 2 步：生成新钱包（记录 25 词助记种子：写在纸上，离线保存）
# 第 3 步：绝不以数字形式保存助记词（加密与否都不行）
# 第 4 步：只经由 Tor 访问钱包

# 钱包轮换（每次行动）：
# 每次不同的行动 -> 唯一的钱包地址（Monero 子地址）
# 一个主钱包 -> 多个子地址 = 链上无法关联
# XMR 子地址：由主种子确定性派生，完全私密
```

### 5.3 匿名收款

```bash
# Monero（XMR）- 最干净的做法：
# 直接提供你的 XMR 地址即可
# 无需 KYC 交易所。XMR 在协议层面就是匿名的。

# 比特币（BTC）- 如果非收 BTC 不可：
# 第 1 步：生成全新的 BTC 地址（绝不复用）
# 第 2 步：接收 BTC
# 第 3 步：立刻换成 XMR

# BTC -> XMR 兑换（无 KYC）：
# Haveno：https://haveno.exchange（P2P 去中心化交易所，原生 XMR，无 KYC）
# UnstoppableSwap：https://unstoppableswap.net
#   （BTC<->XMR 原子交换，无 KYC，无托管方）
# Trocador：https://trocador.app（去中心化交易所聚合器，注重隐私）

# UnstoppableSwap 原子交换（大额首选）：
./swap buy-xmr --seller SELLER_ADDRESS --receive-address XMR_ADDRESS
# 完全去中心化，基于密码学哈希时间锁定合约
# 无第三方、无日志、无 KYC
```

### 5.4 法币兑换方式（2027：已更新）

```
警告：自 2025 年以来，这一领域的格局已大幅变化。

比特币 ATM（2027 更新）：
现状：在多数辖区受到严格监管
- 英国：所有比特币 ATM 都需 FCA 注册（2023）；多数已关停
- 美国：多数州规定 200 美元以上的 ATM 交易需身份证明（FinCEN 2024 规则）
- 欧盟：5AMLD 要求所有等值 1,000 欧元以上的加密交易完成 KYC
- 仍可行：东欧、拉美部分辖区仍有
  门槛较低的 ATM；请自行核实当地法规

P2P（点对点）- Haveno：
- 基于 XMR 的 P2P 市场（替代 2024 年 11 月关停的 LocalMonero）
- https://haveno.exchange
- 无 KYC，基于托管，支持多种支付方式
- 当面现金、银行转账、礼品卡、邮寄现金
- 推荐：当面现金交易，隐私性最佳
  在公共场所见面，不带手机，先收现金，确认无误后再放 XMR

礼品卡兑换（小额风险较低）：
- 经 Bitrefill（https://bitrefill.com）用 XMR 换礼品卡 - 支持 XMR
- 可换：Amazon、iTunes、Google Play、Visa/Mastercard 预付卡
- 风险：礼品卡服务商会留存日志；只用于正常消费，
  不要用于规模化套现

房地产（2027 更新）：
现状：自 2024 年以来显著收紧
- 美国：《企业透明度法案》（2024）：所有 LLC 与空壳公司
  都需登记实际受益人
- 英国：《经济犯罪法》（2022-2024）：须登记海外实体
- 欧盟：反洗钱条例（AMLA，2024）：要求相同
- 仍可行：加勒比、海湾、东南亚的部分辖区

离岸银行（2027 更新）：
现状：欧盟的银行保密制度实际上已终结
- 马耳他、卢森堡：欧盟 AMLA（2024-2027）取消了银行隐私
- 仍可行（空间缩小）：开曼群岛、BVI，但 FATF 合规要求在提高
- 2027 年更可行：格鲁吉亚、阿联酋（有限）、黑山、塞尔维亚

拆分交易警告：
在多数辖区，刻意把存款控制在申报
门槛以下以规避执法机构注意（"化整为零"或称 "smurfing"）本身就
构成联邦重罪，无论其背后的资金是否合法
（美国：31 USC 5324）。本节目的是理解执法机构的侦测手段。
```

### 5.5 冷却期策略（2027）

```
推荐的冷却期：

低调行动（等值 5 万美元以下）：
  最短：6 个月
  推荐：12 个月

高调行动（5 万美元以上，攻击已公开）：
  最短：18 个月
  推荐：36 个月

民族国家 / 关键基础设施：
  最短：5 年
  推荐：永远不要经任何可追溯路径换成本国货币

冷却期规则：
1. 冷却期内：完全不要动资金（移动 = 交易 = 分析的抓手）
2. 只有小额（不超过总额 5%）才可打破冷却
3. 绝不提现到交易所（KYC = 链条闭合）
4. 超过总额 2% 的部分，只用 XMR -> P2P 现金
5. 监控：任何关联地址是否已被标记？（见第 10 节）
```

---

## 第 6 节：物理位置安全

### 6.1 地点选择层级

```
绝对规则：绝不在住处、工作场所或任何与真实身份
相关联的地点行动。没有商量余地。一次例外 = 被抓。

按安全性排序的地点：

层级 1 - 最佳：
  人流密集区的公共空间
  - 大型商场美食广场（出口多、人流大）
  - 有 WiFi 的公共交通枢纽（机场、火车站）
  - 大学图书馆（可自由进入，很多国家不强制查证件）
  轮换：2 周内绝不回到同一地点

层级 2 - 良好：
  咖啡馆与餐馆
  - 进入前先观察出口与 CCTV 覆盖情况
  - 选角落座位，背靠墙
  - 每个地点最长 20 分钟
  - 任何消费都用现金（不刷卡）
  - 绝不要成为店员认得出来的常客

层级 3 - 可接受：
  车载热点（预付费 SIM，停在中性地点）
  - 商场/大型停车场（车辆多，不显眼）
  - 绝不停在居民区附近（居民会看到同一辆车）
  - 每个地点最长 30 分钟
  - 两次会话之间至少移动 5 公里

层级 4 - 仅限应急：
  酒店大堂 WiFi（现金付费的酒店，绝不用房间 WiFi）
  - 现金付费的酒店：用假名登记入住
  - 使用大堂 WiFi（不是房间专用网络）
  - 在大堂行动，不在房间行动（门锁记录会精确指出你的位置）

应避开的地点：
  - 住处或公寓（任何时候都不行，一次也不行）
  - 工作场所网络（企业 SIEM 会记录一切）
  - 朋友或家人的网络（他们的身份 = 你的暴露）
  - 任何需要证件才能用 WiFi 的地方
  - 任何你是常客的地方（店员认得你的脸）
  - 任何存在能拍到屏幕的 CCTV 角度的地点
  - 任何需要生物识别（人脸扫描）才能进入的地点
```

### 6.2 地点作战安全流程

```
进入任何行动地点之前：

1. 先开车或步行经过（不要停留）：观察摄像头，找出出口
2. 记录：摄像头数量、朝向、可能的死角
3. 记录：已有的人员构成、平均人群特征
4. 首次经过后隔 10-15 分钟再进入
5. 不要与店员或其他顾客有眼神接触
6. 选座：面向入口、背靠墙、最近的出口
   能在 5 秒内到达
7. 离陌生人远一些（防范肩窥）

行动期间：
1. 屏幕亮度：调到最低可读程度
2. 防窥屏（物理贴膜，遮挡侧视角度）
3. 把包和装备挡在你与陌生人之间
4. 绝不让设备离身（连去洗手间也不行：合上盖子带走）
5. 若有人靠近或提问：合上盖子，含糊应答，离开
6. 计时：每个物理地点最长 20-30 分钟

行动之后：
1. 不要立刻沿来时的路线返回
2. 每次会话更换交通方式（坐公交来、步行离开等）
3. 留出时间间隔：不要直接前往下一个地点

地点内支付：
- 买咖啡/茶：一律现金，一律备好零钱
- 绝不用：信用卡、闪付、任何与身份绑定的支付方式
- 理由：刷卡记录 + 时间戳 + CCTV = 你的脸 + 地点 + 时间
```

---

## 第 7 节：外貌与反监视

### 7.1 外貌管理

2027 年的人脸识别 AI 能凭局部角度、侧脸，甚至步态识别你。只靠一顶普通棒球帽加墨镜，已越来越不够用。

```
有效的反制措施（2027）：

干扰面部特征：
- 阻隔红外线的化妆/粉底：可干扰许多基于红外的 CCTV
  （Adam Harvey 的 CV Dazzle 项目：https://cvdazzle.com；不对称妆容
   会打乱人脸检测算法）
- 口罩（2020 年后已常态化，在很多场合仍然有效）
- 宽檐帽（遮挡俯拍摄像头；多数商用 CCTV 都是高位安装）
- 带防反光镀膜的眼镜（可干扰某些基于光照的识别）

干扰步态（部分城市已部署 AI 步态识别）：
- 在不同地点更换鞋具（鞋底花纹不同）
- 刻意改变步幅（步长变短/变长、摆臂方式不同）
- 改变脚跟与脚尖的落地比例（要练：保持一致需要练习）
- 注：步态 AI 需要同一摄像头网络的多个样本
  才能建立画像；在网络之间移动就能打乱它

衣着：
- 中性、无辨识度的颜色（深蓝、灰、黑）
- 不要有 logo（容易被记住且可被检索）
- 分层穿衣（双面外套：几秒钟内从蓝色变灰色）
- 在同一区域的不同会话之间更换外层衣物
- 穿与当地人群相符的衣服（融入环境）
- 多备几双鞋（同款鞋 = 同款鞋底 = 可跨地点追踪）

发型：
- 自然的周期性变化（留胡子/剃胡子、头发长短变化）
- 高风险会话戴帽子/毛线帽
- 假发：关键行动使用硅胶底假发（比夹式更牢固）
```

### 7.2 CCTV 意识

```
现代 CCTV 系统（2027）：
- 高清（高价值区域为 4K）：光照良好时可在 30 米外拍到人脸
- 带红外：具备夜视能力，黑暗中也能看清
- 联网：执法机构可在数小时内集中调取录像
- AI 索引：Briefcam 这类平台会自动分析录像
  （可检索：人脸、衣着、行进方向、停留时长）

找出摄像头盲区：
1. 摄像头通常装在角落、入口、出口、收银台
2. 盲区：摄像头正下方、柱子背后、覆盖范围的边缘
3. 室内：留意天花板上的安装点，记录俯仰角度
4. 室外：夜间可顺着电源线找到摄像头位置

需要辨认的摄像头类型：
- 半球形（吊顶安装）：180 度覆盖，看不出朝向
- 枪机（壁装）：覆盖较窄，可看出朝向
- PTZ（云台变焦）：可主动跟踪你（按最大覆盖来假设）
- 随身执法记录仪（警察、保安）：一律假设正在录像

实操流程：
1. 每进入一个新的室内空间：停 3 秒，扫一遍角落与天花板
2. 找出主要摄像头的朝向
3. 选择面部正对镜头最少的路径
4. 记下出口（包括次要出口/员工通道）
```

### 7.3 反监视检测路线（SDR）

<div align="center">
<table><tr><td>

<img src="../assets/diagrams/BlackHat_Long-Term_Survival_Tactics/5._Surveillance_Detection_Route_(SDR).png" alt="Surveillance Detection Route (SDR)" width="1400"/>

</td></tr></table>
</div>

---

## 第 8 节：社会工程防御（自我保护）

### 8.1 关系安全模型

```
对你的行动而言，最危险的人是那种：
(a) 知道你的真实身份，并且
(b) 有动机或有机会告发你的人

执法机构*一定*会去接触你周围的人。他们是受过训练的
社会工程师，手里还有法律工具。请假设你生活中的任何人都
可能被争取过去，不是因为他们人品差，而是因为
执法机构施加的压力（逮捕、追究其自身
法律问题、金钱、意识形态）实在太大了。

解决办法不是疑神疑鬼，而是隔离分区。
什么都不知道的人，什么也交代不出来。
```

```
关系安全层级：

层级 0 - 真实身份圈的人（家人、老朋友）：
  他们知道的：你的真实姓名、面孔、过往经历
  风险：执法机构可利用他们确认你的行踪、生活方式、心理状态
  管理方式：
  - 绝不谈工作（说成「做网络安全咨询」或「自由开发」）
  - 对外呈现可信的收入水平（不高、能解释得清）
  - 没有来路不明的大额馈赠（执法机构会注意）
  - 降低联系频率（要维护的内容越少，露馅的机会越少）
  - 绝不经电子方式转账（会留下银行记录）
  - 绝不透露位置细节

层级 1 - 专业联系人（仅线上认识，使用化名）：
  他们知道的：你的昵称、你的一些技术作品
  风险：昵称关联、技术特征关联、可能是线人
  管理方式：
  - 一律只用化名
  - 绝不透露真实姓名、位置、国家
  - 每个社群用不同昵称（绝不跨平台复用昵称）
  - 保持怀疑：假设每 10 人里就有 1 个是执法机构/线人
  - 绝不与任何人讨论正在进行的行动
  - 通信：只用加密渠道，并假设所有消息最终都会被读到

层级 2 - 团队成员（行动层面）：
  他们知道的：行动细节，可能还有你的昵称
  风险：最高 -- 任何一人被捕 -> 审讯 -> 供出你的名字
  管理方式：
  - 越少越好：单独行动最安全
  - 必须组队时：隔离分区（每个成员只知道自己的角色）
  - 每个成员：经过数月而非数天的审查
  - 内建合理推诿空间
  - 通信：带外、加密、轮换渠道
  - 若有成员被捕：立即执行应急预案
```

### 8.2 掩护身份维护

```bash
# "伪造履历" - 你对真实身份联系人讲的那套掩护说辞
# 必须满足：
# - 内部自洽
# - 收入来源说得通
# - 生活方式可信
# - 不易被核实（避免需要文件佐证的说法）

# 好的掩护：「自由 IT 安全顾问」
#   - 收入：不稳定、按项目结算（可解释不规则收入）
#   - 不在场：「在客户现场」
#   - 技术知识：由职业本身解释
#   - 保密：「客户 NDA 不允许我谈细节」
#   - 出差："客户分布在不同的城市/国家"

# 维持掩护：
# - 备好 2-3 个「客户名」（虚构、无法核实）
# - 对基础 IT 安全懂到能应付闲聊提问的程度
# - 穿着/生活方式与中等顾问收入相符
# - 在所有层级 0 联系人面前保持同一套细节
```

### 8.3 消除数字足迹

```bash
# EXIF 数据（无声的背叛者）：
# 手机/相机拍摄的照片会内嵌：GPS 坐标、设备型号、
# 序列号、日期时间、相机参数
# 曾有人仅凭一张公开照片就被定位

# 分享任何图片之前先剥离 EXIF：
exiftool -all= photo.jpg              # 清除全部元数据
exiftool -all= *.jpg                  # 清除整个目录

# 确认没有残留：
exiftool photo.jpg | grep -iE "GPS|Serial|Make|Model|Software"
# 应当没有任何输出

# 剥离文档元数据：
mat2 document.docx                    # 清除 Word 元数据
mat2 document.pdf                     # 清除 PDF 元数据
# 安装：apt install mat2

# 要发到网上的图片：
# 先截图，再发布截图
# 截图会丢掉全部 EXIF

# 行动中的搜索习惯：
# 一律经由 Tor Browser（每个主题用全新会话）
# 绝不要：用非 Tor 浏览器搜索自己的昵称或目标
# 使用：经 Tor 访问 DuckDuckGo onion 或 Startpage

# 暗网监控（检查自己是否已暴露）：
# Intelligence X：https://intelx.io（检索你的化名、邮箱）
# HaveIBeenPwned：https://haveibeenpwned.com（泄露凭据）
# DeHashed：https://dehashed.com（凭据库检索）
# 以上全部只能经由 Tor Browser 访问
# 不要用 Telegram 上的查询机器人查行动地址 --
# Telegram 会记录用户数据，且自 2024 年起配合执法机构

# 检查 BTC 地址暴露情况：
# OXT：https://oxt.me（基于浏览器，经由 Tor Browser 访问）
# Blockchain.com：https://www.blockchain.com/explorer（经由 Tor Browser）
# AML 风险评分：只能经由 Tor Browser 访问，绝不用原生 App
```

---

## 第 9 节：AI 驱动的监视规避（2027）

### 9.1 人脸识别（2027 年现状）

```
当前部署情况（2024-2027 年有据可查）：
- 英国：对警察随身摄像头录像做回溯式 FRT；伦敦有实时 FRT 试点
- 美国：FBI 的 NGI 系统；Clearview AI（已抓取 2500 亿张以上图像）
- 中国：全城普遍部署，近乎实时
- 阿联酋：机场与市中心部署
- 印度：集成 FRT 的 CCTNS 系统

工作原理：
1. 摄像头拍到人脸
2. 算法生成「人脸特征值」（由面部几何得出的数值向量）
3. 与数据库比对（前科照、车管所、社交媒体、爬取的互联网图像）
4. 超过阈值即告警

准确率（2027）：正面、光照清晰的图像约 98.7% 的比对成功率
遇到以下情况会大幅下降：角度、光照、部分遮挡、化妆

有效的反制措施：
1. 口罩（仍然最有效：去掉约 70 个面部几何特征点）
2. 阻隔红外线的化妆（专门阻断夜间摄像头的红外补光）
   - HyperFace 围巾：生成假的「人脸」来干扰 AI
   - CV Dazzle 妆容：不对称图案打乱特征点检测
3. 宽檐帽：遮挡高位摄像头（这是主要的安装位置）
4. 尽可能完全避开摄像头（靠路线规划）
5. 数据库层面的对策：尽量减少自己在任何数据库中的存在
   - 绝不在网上发布清晰的正脸照片
   - 对带有你的标记照片发起 GDPR 删除请求（欧盟）

无效的做法：
- 只戴墨镜（很多角度下摄像头仍能拍到眼睛）
- 彩色隐形眼镜（摄像头对虹膜纹理的检测方式不同）
- 没有针对 AI 的专门反制的普通伪装
```

### 9.2 步态识别 AI

```
部署情况（2027）：中国（商汤/依图）、英国（试点）、迪拜
原理：分析你走路时独有的模式
准确率：条件良好时 50 米距离可达 94% 以上

反制措施：
1. 在不同地点更换鞋型（鞋跟高度会可测量地改变步态）
2. 换肩背重包（重量不对称会改变步态）
3. 刻意改变步幅（练出一套稳定但不同的步态）
4. 走人流密集处（人群遮挡会降低 AI 置信度）
```

### 9.3 伪基站（Stingray / IMSI 捕获器）

```
是什么：
伪装成手机基站的设备，强制附近的手机接入。
可捕获：IMSI（手机唯一标识）、IMEI、通话/短信元数据，有时还有内容。
使用者：FBI、DEA、地方警察、情报机构。
便携：可装进双肩包；也有车载型号。

检测工具（2027 年准确性说明）：

SnoopSnitch（Android）：https://opensource.srlabs.de/projects/snoopsnitch
  - 要求：已 root 的 Android 手机，且搭载特定的旧款高通芯片组
  - 重要限制：SnoopSnitch 需要通过 QMI 接口访问高通
    基带调制解调器。现代高通芯片组（骁龙 8 Gen 2 及以后）
    已收紧该接口。这个工具对老设备有效
    （骁龙 800/801/820 时代），但在 2023 年以后的大多数手机上会静默失效。
    大约 2021 年之后的手机不要依赖它。
  - 从 F-Droid 安装（不要用 Google Play）

2027 年防御 IMSI 捕获器的更好做法：
  1. Pixel 上的 GrapheneOS：启用仅 LTE 模式
     （设置 -> 网络 -> 首选网络类型 -> 仅 LTE）
     这可以阻止 IMSI 捕获器所依赖的 2G 降级攻击，
     它们靠这招获取高质量数据。捕获器仍能探到手机，
     但无法把协议降级去截取通话/短信内容。
  2. 干脆拔掉 SIM：没有 SIM = 没有 IMSI = 无可捕获
  3. 法拉第袋：物理屏蔽所有射频（验证方法：把手机
     放进袋子后拨打它；如果还响，说明袋子不合格）

首要对策：不要带你的个人手机。
这是唯一有保证的防护办法。
```

### 9.4 车牌识别（LPR/ANPR）

```
广泛部署（2027）：美国、英国、欧盟、澳大利亚
英国：每天约 1600 万次 ANPR 读取
数据库：读取到的车牌会保存 2-30 天，视辖区而定
（部分辖区：执法机构数据库会无限期保存）

反制措施：
1. 绝不用登记在真实身份名下的车辆行动（任何情况都不行）
2. 租车：可追溯（租车要信用卡 + 证件）
3. 以人设名义用现金购买便宜的、已上保险的车辆（高威胁模型下）
4. 摩托车：摄像头更难拍清车牌（角度 + 震动）
5. 路线规划：避开已知的 LPR 卡点（主干道、隧道、桥梁）
6. 最优选择：公共交通 -- 没有车牌，还能混在人群里
```

### 9.5 预测性警务与模式分析

```
在用的 AI 系统（2027）：PredPol/Geolitica、Palantir Gotham（广泛使用）

这些系统寻找以下模式：
- 同一部手机出现在多个与案件相关的地点
- 与已知高风险实体之间的资金往来
- 关系网络图分析（谁和谁联系 -> 因交往而被牵连）
- 行为异常检测（作息突然改变 = 打上标记）

反制措施：
1. 平民生活中保持稳定的行为模式
2. 绝不把行动行为与日常作息混在一起（隔离分区）
3. 绝不在行动地点使用个人手机
4. 资金行为：不要突变（不要大额消费，不要大额存入）
5. 关系网络：不要用真实账号与被标记过的人通信
6. 防御 AI 声音克隆（2027）：
   - AI 现在能凭 3 秒样本克隆声音
   - 与亲近联系人约定暗号，用于核实真实身份
   - 若行动敏感，绝不要仅凭一通电话就采取行动
```

---

## 第 10 节：区块链取证威胁建模（2027）

### 10.1 Chainalysis 的工作原理（2027）

```
Chainalysis Reactor、Elliptic Navigator、CipherTrace：被美国财政部
OFAC、FBI、DEA、Europol 以及多数大型交易所使用。

追踪方法：

1. 共同输入所有权启发式（CIOH）：
   同一笔交易中的多个输入很可能属于同一个钱包。

2. 找零地址识别：
   BTC 交易通常包含：付款输出 + 找零输出。
   分析工具识别出找零输出 -> 顺着链条追下去。

3. KYC 交易所关联：
   你把 BTC 转到交易所 -> 交易所掌握你的身份 -> 钱包被关联。
   哪怕只是向交易所发送测试金额，也会把钱包关联起来。

4. 粉尘攻击：
   向你的钱包发送极小额 BTC。
   当你花掉包含这笔粉尘的交易 -> 钱包即被关联。
   防御：不要花掉粉尘。使用支持币种控制的钱包软件。

5. 时序分析：
   交易广播时间与已知行动时间作对比。
   防御：通过批量处理或时间锁定来延迟交易。

6. 中心化交易所的数据共享：
   交易所会主动向执法机构共享可疑交易数据。

Chainalysis 无法追踪的：
- XMR 交易（环签名 + 隐匿地址）
- 正确执行的原子交换（没有交易所记录）
- 从未接触过 KYC 服务的交易
```

### 10.2 监控你的暴露面

```bash
# 检查你的 BTC 地址是否已被掌握/标记：
# 以下全部经由 Tor Browser 访问。绝不用普通浏览器。

# 1. OXT（比特币区块链分析，免费）：
# https://oxt.me - 检索你的钱包地址
# 可查看：交易图、聚类、关联到的已知实体

# 2. Blockchain.com：
# https://www.blockchain.com/explorer - 基础交易查询

# 3. AML 风险评分（基于浏览器的选项）：
# https://amlbot.com（网页版，经由 Tor Browser 访问）
# 检查地址是否被标记，或风险评分是否很高
# 绝不要用这个工具的 Telegram 机器人版本 --
# Telegram 会记录所有查询，且自 2024 年起配合执法机构

# 4. 检查钱包是否受到 OFAC 制裁（美国财政部名单）：
# https://www.treasury.gov/ofac/downloads/sdnlist.txt
# 检索你的地址
# 被制裁的钱包 = 任何从它收款的交易所都会冻结并上报

# 行动规则：如果对某个 BTC 地址的暴露情况存疑，
# 就当它已暴露。绝不复用。生成全新地址。

# Monero 核验：
# XMR 交易在公开浏览器中不会以有意义的形式出现
# https://localmonero.co/blocks - 只显示区块，不显示地址/金额
# 这正是关键所在：无从查起 = 无从追踪
```

---

## 第 11 节：暗网作战安全

### 11.1 安全访问暗网

```bash
# Tor Browser：必需，永远，没有例外
# 下载：https://www.torproject.org
# 运行前先校验签名

# 安全级别：设为「Safest」（点击盾牌图标）
# 这会禁用 JavaScript：阻止大多数去匿名化攻击
# 暗网上的 JS 漏洞利用：FBI 曾大量使用（Operation Torpedo，2011-2013）

# 加固后的 Tor Browser 设置（about:config）：
# javascript.enabled = false（在「Safest」级别已自动设置）
# network.proxy.socks_remote_dns = true  （DNS 走 Tor，不走本地）
# webgl.disabled = true  （WebGL 指纹识别）
# media.peerconnection.enabled = false  （WebRTC 泄露）
# browser.sessionstore.enabled = false  （不保留会话历史）

# 绝对不要：
# - 在线状态下打开从暗网下载的文件
#   （PDF、DOCX 会回连外网；只在物理隔离的虚拟机中打开）
# - 放大 Tor Browser 窗口（窗口尺寸 = 指纹）
# - 使用全屏
# - 通过 Tor Browser 登录任何明网账号
# - 在 Tor 上跑 BT（UDP 会绕过 SOCKS -> 真实 IP 泄露）

# 安全地打开下载的文件：
# 在 Tails 上：就在 Tails 中打开（关机即清，操作后断网）
# 在 Qubes 上：在禁用网络的一次性虚拟机中打开
qvm-run --dispvm PersonaA xdg-open /path/to/file
# 独立环境：在没有网络接口的物理隔离虚拟机中打开
```

### 11.2 暗网论坛 / 市场作战安全

```
账号卫生：
- 每个平台用唯一昵称（绝不跨市场/论坛复用）
- 每个平台用单独的 PGP 密钥（否则密钥本身会关联身份）
- 账号经 Tor 创建，并永远经 Tor 使用
- 不用真实邮箱注册任何账号

PGP 核验（在市场内）：
- 每个卖家：核验其商品页上的 PGP 签名
- 每条加密消息：用对方密钥加密，并用你的密钥签名
- 绝不粘贴你的真实 PGP 密钥（会把论坛身份与外部密钥关联）
- 每个平台生成新密钥

写作风格（文体计量分析）：
- 完整指引见第 4.4 节
- 在暗网与明网保持稳定且彼此不同的文风
- 在任何行动平台上都保持极低的发帖量

市场安全：
- 只使用有卖家 PGP 签名核验机制的市场
- 托管：一律使用托管（提前确认收货 = 诈骗切入点）
- 绝不提前确认收货（FE），即便对方是可信卖家
- 核验：信任之前，从多个来源比对市场 PGP 密钥
- 多签：优先选择支持多签托管的市场（不可能卷款跑路）
```

---

## 第 12 节：法律反情报

### 12.1 如果有人找上你（了解你的权利）

```
本节不构成法律意见。法律因辖区而异。
在任何调查开始*之前*，先咨询你所在辖区的
刑事辩护律师。本节仅供学习。

多数民主辖区通用的原则：

沉默权：
  美国：第五修正案（必须明确主张：
      「我行使我的沉默权」）
  英国：警告告知权（「你不必说任何话……」）
  欧盟：欧洲人权法院第 6 条：沉默权
  原则：你说的任何话都可能被用来对付你。
             你说的任何话都帮不到你。
  规则：什么都别说。永远。对任何执法机构人员都是如此。
        律师不在场时更是如此。
        「我要律师」是你唯一该说的话。

获得律师帮助的权利：
  美国：第六修正案：获得律师的权利；立即主张
  英国：1984 年 PACE：获得免费法律咨询的权利
  欧盟：Directive 2013/48/EU
  一旦主张：在多数辖区，审讯必须停止

不同意搜查：
  「我们看一下你的笔记本/手机，可以吗？」
  回答：「我不同意搜查。」
  他们凭搜查令可能照样搜，但在没有你同意的情况下，
  非法搜查所得的证据可能被排除。

边境口岸（特殊规则）：
  美国边境：第四修正案并不完全适用。
              CBP 可在边境要求解锁设备。
              若设备已加密：「我没有密码。」
              （如果是 Tails 或 VeraCrypt 隐藏卷，这确实是真话）
  英国：《2000 年反恐怖主义法》附表 7：可强制要求设备访问
  欧盟：各国不同
  实操：过高风险边境时，使用一台干净的设备。
              真正的行动设备不过边境。
```

### 12.2 强制解密 - 各辖区差异

```
关键：加密层面上的合理推诿，其法律含义
因辖区而异。在依赖它*之前*就要搞清楚。

美国：
  在许多巡回法院辖区，第五修正案禁止强制解密
  （不能强迫一个人说出他知道的东西，只能强制其交出他持有的东西）。
  当前状态：各巡回法院意见分裂；美国最高法院尚未作出定论。
  实践中：执法机构常常绕开这一点，转而向第三方
  （云服务商、邮箱等）索取未加密数据，而不是强制你本人。
  实际保护：在此合理推诿具有真实的法律价值。

英国（RIPA 第三部分）：
  《2000 年调查权力规制法》（第三部分）允许
  法院签发「披露通知」，要求你提供
  加密材料的密钥或明文。
  拒不配合：构成刑事犯罪，最高可判 5 年监禁
  （《2016 年调查权力法》将其提高至 5 年，适用于
  国家安全类案件）。
  VeraCrypt 隐藏卷抗辩：技术上你可以声称你已经
  交出了全部密钥（即外层诱饵卷）。这是一场高风险的
  法律赌博；依赖它之前请先咨询专业律师。

欧盟：
  欧盟没有统一规则，各国不同。
  德国：通常受不得自证其罪原则保护。
  法国：与德国类似，但设有国家安全例外。
  荷兰：已有法院判令强制解密。

实操规则：VeraCrypt 隐藏卷 + Tails（无痕）+ LUKS 仍是
正确的技术选择。但要知道，在英国以及某些
其他辖区，在法律命令之后拒绝解密本身就
构成犯罪。请把这一点纳入你的威胁建模与退出规划。
```

### 12.3 律师-当事人保密特权

```
你告诉律师的一切都受保密特权保护；执法机构无法获取。

关键规则：
1. 在需要之前就聘好律师。
   记住一位刑事辩护律师的姓名和电话。
   事先存在的关系 = 更快的响应、更好的辩护。

2. 律师姓名 + 电话：记在脑子里或纸上（不要存在手机里）
   被捕后的第一个动作：要求给律师打电话。不要打别的电话。

3. 律师-当事人保密特权只适用于你的律师。
   不适用于：律师助理、调查员、所谓「懂法」的朋友
   不适用于：有第三人在场时的谈话（特权可能被视为放弃）

4. 「犯罪-欺诈例外」：
   如果律师怀疑你在利用其建议实施未来的犯罪，
   特权可被击穿。只谈已经发生的事，绝不要谈未来的计划。

如何找到合格的刑事辩护律师：
   - 全国刑事辩护律师协会（美国）：nacdl.org
   - 律师协会刑法名录（英国）：solicitors.lawsociety.org.uk
   - 在需要之前就去面谈律师；具体询问其
     计算机犯罪 / 网络犯罪方面的经验
```

### 12.4 销毁证据的合法性

```
美国：妨碍司法（18 USC 1512）：在你明知或
    合理预计会有调查时销毁证据 = 联邦重罪。
    起算点：传票送达时、调查被知悉时。
    调查开始之前：删除文件、擦除硬盘、销毁设备都是合法的。
    调查开始之后：可能构成妨碍司法。

英国：妨碍司法公正；视具体情形而定。

实操建议：
- 收到任何法律程序文书之后，不要销毁证据
- 把例行擦除作为日常卫生的一部分（在任何调查之前）
- Tails / VeraCrypt 隐藏卷：「我不知道密码」在法律上
  与「我销毁了证据」是两回事（合理推诿，在美国有用）
- 数据留存制度：建立一套正当的旧数据清理惯例
  （被调查时，例行擦除看起来就不那么可疑）
```

---

## 第 13 节：长期生存规划

### 13.1 行动节奏与风险累积

```
风险不是恒定的；它会累积。

第 1 次行动：风险暴露 R
第 2 次行动：风险暴露 R + 第 1 次行动的残留
第 3 次行动：风险暴露 R + 前两次行动的残留
...
第 N 次行动：风险显著高于单独的 R

原因：
- 每次行动都可能留下你并未察觉的痕迹
- 每次行动都在为执法机构拼凑的画像添砖加瓦
- 线人一旦被招募，潜伏时间就越长
- 每个技术失误都会累积（跨行动复用 IP 等）

3-5 年规律（是模式，不是铁律）：
多数以中等作战安全水平运行的网络行动能维持 3-5 年。
此后，被攻陷的统计概率会大幅上升。

重要提醒：这条规律适用于有团队参与、或单独行动但作战安全不完美的
行动。一名严谨的独立行动人员，若能以极致的纪律
遵循本指南的全部内容，可以行动得久得多。这条规律
描述的是典型的行动人员，而非例外者。请把 3-5 年
作为你的基准退出时限。要在此之后继续行动，
就必须在每一个方面都展现出超常的纪律。

执法机构的调查会逐渐成熟：FBI 的网络犯罪调查平均持续 2-3 年。
看似微小的行为变化会累积成模式。
行动疲劳会导致失误。

不存在「再来一次行动」这回事。
成功的行动人员在开始之前就已经定好退出点。
```

### 13.2 定期作战安全评估（6 个月流程）

```
每 6 个月一次：这是强制要求，不是可选项。

数字层面评估：

1. 化名/昵称暴露检查：
   在以下渠道搜索你的行动昵称：
   - Google/DuckDuckGo（是否有新被收录的提及？）
   - Intelligence X（https://intelx.io）- 泄露数据库、论坛
   - 粘贴站（Pastebin、Ghostbin：是否有含你昵称的数据转储？）
   - 暗网论坛（是否有人提到你的用户名？）
   所有搜索：只经由 Tor Browser

2. 邮箱/凭据泄露检查：
   HaveIBeenPwned: https://haveibeenpwned.com
   DeHashed: https://dehashed.com
   检查：所有行动用邮箱地址

3. 区块链地址暴露：
   OXT、基于浏览器的 AML 工具（经 Tor）：行动钱包是否被标记？

4. 基础设施检查：
   你控制的域名：仍在注册状态？未被查封？
   服务器：是否干净？有无异常进程？日志是否干净？
   eBPF 监控防御见第 21 节。

5. 作战安全串线审计：
   是否有任何行动细节出现在真实身份的场合？

物理层面评估：

6. 新面孔检查：
   有新邻居吗？你的住处附近是否常有陌生车辆停放？
   有什么 6 个月前没有、现在却持续出现的东西？

7. 设备检查：
   设备上是否有被拆动过的迹象（贴纸移位、螺丝滑丝）？
   有无新进程在运行？休眠期间是否有网络活动？

8. 模式审计：
   你的作息是否出现了会形成可观察模式的变化？

轮换层面：

9. 设备轮换：
   每 6-12 个月：换新行动设备（旧的物理销毁）
   不要：出售、捐赠或回收（数据有可能被恢复）
   销毁：
     HDD：在盘片上钻 5 个孔，然后分处丢弃
     SSD：正确的 SSD 擦除见第 2.6 节；物理销毁
          是高威胁场景下唯一的绝对保证
     内存：见第 20 节（断电后内存仍保留数据）

10. SIM 轮换：
    每 3 个月：任何行动用手机都换新预付费 SIM
    旧 SIM：剪成两半，分处丢弃

11. 钱包轮换：
    每个行动阶段换新 XMR 钱包（经 Tor 把余额扫到新钱包）
    旧钱包：清零余额，不再使用

12. 通信轮换：
    新 Signal 账号（新预付费 SIM）
    新 SimpleX 身份（重新生成密钥）
    通过安全渠道通知行动联系人
```

### 13.3 退出策略（3-5 年时间表）

<div align="center">
<table><tr><td>

<img src="../assets/diagrams/BlackHat_Long-Term_Survival_Tactics/6._Exit_Strategy_(3-5_Year_Timeline).png" alt="Exit Strategy (3-5 Year Timeline)" width="800"/>

</td></tr></table>
</div>

```
第 1-2 年：建设（同时把退出所需的基础设施一并搭起来）
  - 建立合法的掩护收入来源
  - 开始通过合法途径积累离岸资产
  - 第 2 年缩减行动规模

第 3 年：收尾
  - 拒绝所有新的大型行动
  - 缩小资金足迹
  - 此时掩护收入应已足以解释你的生活方式

第 4 年：资产迁移
  - 把大额资产转移到境外（形式上合法）
  - 在无引渡条约的辖区购置房产（如可行）
  - 缩小数字足迹
  - 开始规划实地搬迁

第 5 年：彻底退休
  - 所有行动已停止（至少提前 12 个月；冷却期）
  - 实地搬迁至引渡风险低的辖区
  - 最后的加密资产变现为真实资产（长冷却期已结束）
  - 与过去的行动生活零接触
  - 开始完全合法的生活

这套时间表为什么可行：
  - 多数刑事调查在 3-7 年内以不予起诉结案
  - CFAA（美国）：多数罪名追诉期 5 年，损失超过 5,000 美元为 10 年
  - 英国《计算机滥用法》：追诉期一般为 3 年
  - 到第 5 年退出时：多数证据已退化，证人记忆已模糊
```

---

## 第 14 节：紧急撤离预案

### 14.1 被攻陷的迹象

```
触发信号（出现*任何*一条都要立即行动）：

数字层面信号（高）：
  - 行动服务器被查封 / 域名显示执法机构通告
  - 加密钱包被交易所标记（资金冻结）
  - 已知同伙毫无解释地失联
  - 暗网论坛突然下线（可能意味着执法机构收网）
  - 账号出现来自未知地点的登录（被攻陷或被执法机构进入）
  - 未知 IP 对你的 VPS 发起异常的 SSH 连接尝试

数字层面信号（中）：
  - 你控制的站点出现证书错误（中间人攻击尝试）
  - 行动连接出现异常的延迟尖峰
  - 邮箱/论坛账号突然无法访问
  - 你的昵称出现在新闻 / 执法机构新闻稿中

物理层面信号（高）：
  - 住处附近有陌生车辆连续多日停放
  - 同一张脸出现在不同的、彼此无关的场所
  - 水电工/政府人员的意外上门
  - 执法机构与行动同伙有任何接触

物理层面信号（中）：
  - 一次重要行动之后不久出现新邻居
  - 打错的电话明显增多
  - 感觉被实地跟踪（相信你的直觉）
```

### 14.2 应急预案 - 分级响应

<div align="center">
<table><tr><td>

<img src="../assets/diagrams/BlackHat_Long-Term_Survival_Tactics/7._Emergency_Protocol-Tiered_Response.png" alt="Emergency Protocol - Tiered Response" width="820"/>

</td></tr></table>
</div>

**层级 2 设备销毁 - 详细步骤（已修正）：**
```bash
# HDD 销毁（层级 2 应急）：
# 最快且可靠的方法：在盘片上钻 5 个以上的孔
# 透过外壳顶部可以看到盘片
# 盘片数量：3.5 英寸盘有 2-4 片；2.5 英寸盘有 1-2 片
# 条件允许时从两面各钻一遍

# SSD 销毁（层级 2 应急）：
# 关键：shred 和 dd 无法可靠擦除 SSD
# 技术解释见第 2.6 节
# 应急时的优先顺序：
# 1. 密码学擦除（若为 LUKS）：sudo cryptsetup erase /dev/sdX
#    只需几秒，且在密码学上不可逆
# 2. ATA Secure Erase（SSD 内置命令）：需 1-30 分钟
# 3. 物理销毁：拆开外壳，找到 NAND 芯片（PCB 正反两面），
#    在每个 NAND 芯片位置钻孔，分处丢弃
# 注：只钻 PCB 接口处是不够的；
#       NAND 芯片必须被物理破坏

# 内存方面的考虑（应急）：
# 室温下断电后，内存中的数据会保留数秒至数分钟
# 在低温环境（液氮）下：数小时至数天
# 冷启动防御见第 20 节
# 应急时：立即断电（不要休眠，不要睡眠）
# 断电 + 物理移除电源，比等待
# 正常关机更快

# 文件资料：
# 碎纸可以被复原（FBI 实验室有此能力，已有记录）
# 焚烧才是正确方法（户外焚烧，完全燃烧）
# 不要用碎纸机：要烧

# 地点撤离（层级 2）：
# 不要使用个人车辆（会被 LPR 追踪）
# 不要乘坐航班（护照 = 生物识别 + 数据库 + 摄像头）
# 应该使用：现金出租车 -> 火车 -> 大巴的组合
# 从陆路口岸过境（很多辖区比机场的监视更少）
# 目的地：事先规划好（这一天到来之前你就该知道）
```

---

## 第 15 节：反执法（LE）意识

### 15.1 执法机构的调查手段

<div align="center">
<table><tr><td>

<img src="../assets/diagrams/BlackHat_Long-Term_Survival_Tactics/8._Law_Enforcement_Investigation_Methods.png" alt="Law Enforcement Investigation Methods" width="430"/>

</td></tr></table>
</div>

```
关键取证节点（多数行动人员栽在这里）：
  - 交易所 KYC（最常见的单一失手点）
  - VPN 服务商日志（很多 VPN 谎称不记日志）
  - ISP 记录（执法机构会例行传唤 ISP 调取 IP 记录）
  - 邮箱服务商配合（持搜查令时，Gmail/Outlook 数小时内就会交出数据）
  - 卧底购买/接触（执法机构会假扮买家）
  - 秘密线人（你认识的人，向执法机构汇报）

Europol / NCA（英国）的手段：
  - 更具攻击性的进攻性网络行动（反向入侵，已有记录）
  - 与东欧执法机构更紧密的协作
  - 使用 J-CAT（联合网络犯罪行动工作组）开展多国行动

情报手段（NSA/GCHQ）：
  - 流量分析（关联 Tor 入口与出口的时序）
  - 对美国的科技公司提出 PRISM 级别的数据调取要求
  - MUSCULAR（直接搭线监听光纤骨干）
  - 这些手段只针对那 0.0001% 被情报机构列为主动目标的
    行动人员；多数人面对的是常规执法机构，而不是 NSA

卧底行动（警示信号）：
  - 急于过快建立信任
  - 提供异常优厚的条件（制造交易 = 制造证据）
  - 打听与其声称目的无关的行动细节
  - 背景说辞前后不一致（细节随时间对不上）
  - 响应异常迅速（完全没有行动上的延迟）
  规则：假设你在行动空间里线上接触的人有 10% 是执法机构。
```

### 15.2 暗网论坛收网模式

```
多数暗网论坛/市场的收网都遵循一个模式：
1. 执法机构获得访问权（查封、攻陷，或通过 HUMINT 渗透管理员）
2. 执法机构继续运营该站点数天到数月（收集数据）
3. 多国同步抓捕（把突然性做到最大）
4. 服务器数据被提取 -> 完整用户历史、消息、交易记录

历史案例（有据可查）：
- Hansa Market（2017）：荷兰国家警察查封并运营 Hansa
  整整 27 天，之后才宣布关停。在此期间他们：
  收集了 10,000 多个收货地址、2,400 多个卖家 PGP 密钥，并
  修改了站点行为以获取更多用户数据。
  这就是「Hansa 效应」-- 许多从 AlphaBay 逃过来的用户
  在 AlphaBay 关停后直接转投 Hansa，随即被一网打尽。

- AlphaBay（2017）：Alexandre Cazes 于 2017 年 7 月 5 日在泰国被捕。
  在他被捕后，AlphaBay 立刻被关停。
  查封后并未由执法机构运营。Cazes 于 7 月 12 日在羁押中死亡。
  （注：AlphaBay 在 2021 年由另一名管理员重启，但那是
   另一个实体、另一个故事。）

- REvil（2021）：FBI 在进入 REvil 的基础设施后取得了
  解密密钥。其成员随后被捕。

- BreachForums（2023）：Pompompurin（Conor Fitzpatrick）被捕；
  站点被查封；全部数据被提取。

Hansa 案的关键教训：如果一个大型平台先下线、随后又
「回来」，或者立刻出现了替代站点，就假设那是执法机构在运营。
如果你在用的平台突然下线：就假设它被查封了。
即便它重新上线，也可能是执法机构在运营。
```

---

## 第 16 节：2027 年国际司法辖区

### 16.1 引渡条约地图

```
不引渡或限制引渡的国家（2027）：

最安全（与美国无引渡条约）：
  俄罗斯：       与美国/英国无条约；仅偶尔引渡本国公民
                 风险：FSB 可能出于外交原因交换情报；战争风险
  中国：         与美国无条约；几乎从不引渡
                 风险：监控国家，对外情报活动频繁
  白俄罗斯：     与美国无条约；与俄罗斯结盟紧密
  朝鲜：         完全孤立；实际引渡率为零
                 风险：根本无法在那里开展行动

相对安全（条约有限、程序缓慢）：
  格鲁吉亚：     与美国无条约；关系在改善但仍不引渡
                 银行体系良好、基础设施可用、签证友好
  黑山：         与美国在谈条约；截至 2027 年尚未生效
  塞尔维亚：     与美国无引渡条约；已是欧盟候选国
  波黑：         辖区结构复杂；没有统一的引渡主管机关

关于那些被误认为「安全」的辖区：
  - 阿联酋、卡塔尔：自 2019 年起在网络犯罪问题上配合美国；
    尽管没有正式条约，已有多名行动人员被驱逐/引渡
  - 柬埔寨：曾配合美国的请求；没有想象中可靠
  - 菲律宾：与美国有引渡条约；且已有配合先例

欧盟国家（全部与美国有条约；涉美犯罪在这里并不安全）：
  尽管有本国的隐私法，所有欧盟国家都会在网络犯罪问题上配合美国执法机构。
  GDPR 不能让你免于刑事调查。

实操思路（2027 年分析）：
  最佳选项：
  1. 格鲁吉亚（第比利斯）：对技术友好，无条约，外籍人士社群在壮大
  2. 塞尔维亚（贝尔格莱德）：生活成本低，无条约，紧邻欧盟
  3. 黑山：风景好，旅游基础设施在发展中，无条约
  4. 摩尔多瓦（如果足够稳定）：花销低，无条约，欧盟候选国
```

### 16.2 身份证件

```
合法途径（推荐）：
  有些辖区可以合法获得第二国籍或居留权：
  - 圣基茨和尼维斯：投资入籍（约 25 万美元起）
  - 多米尼克：CBI 项目（约 20 万美元起）
  - 葡萄牙黄金签证：合法的居留路径
  - 格鲁吉亚：远程工作者居留（容易、合法）

  合法的第二国籍：合法、站得住脚，能造出真实的第二身份，
  且有真实证件。比伪造证件安全得多。

伪造证件（2027 年的现实）：
  生物识别护照（含人脸数据的 RFID 芯片）使得传统的
  证件伪造在主要边境口岸几乎失去意义。
  芯片必须与数据库匹配：没有伪造者能把你的照片塞进
  某外国的护照数据库。
  持有伪造证件：在原有罪名之外另构成重罪。
  仅在以下场合有效：不做完整生物识别核验的陆路口岸。
```

---

## 第 17 节：作战安全黄金法则

```
七条法则。背下来。内化它们。
每一个落网的行动人员，都至少违反了其中一条。

+------------------------------------------+
|  规则 1：行动沉默                        |
+------------------------------------------+
永远不要谈论行动。永远。
不要对伴侣说。不要对恋人说。不要对朋友说。
不要在网上说。不要喝醉时说。不要在所谓「安全」渠道里说。
不要为了炫耀。不要为了警告。不要为了教学。

关于行动的每一个字都是证据。证据会留存。
你告诉别人的那一刻，就是你对这条信息失去控制的那一刻。
约 40% 的抓捕直接源于行动人员自己开口。

+------------------------------------------+
|  规则 2：模式即死                        |
+------------------------------------------+
绝不在同一地点出现两次。
绝不在同一设备上用两次。
绝不在同一时段行动两次。
绝不走同一条路线两次。
绝不重复提取相同金额。

可预测就是可追踪。
每一种模式都是送给调查人员的取证大礼。
凡是能变的东西都要变。

+------------------------------------------+
|  规则 3：不相信任何技术（或人）          |
+------------------------------------------+
VPN 服务商记日志。那些声称不记的也记。
Tor 出口节点会被监控。很多都已被监控。
加密没有永久的保证：今天破不了的东西，
10 年后可能被量子计算攻破。请据此规划你的行动时间跨度。
实地监视永远有可能发生。

任何知道某次行动的人都是负债。
不是因为他们人品差。而是因为执法机构对普通人
施加的压力极其巨大。即便好心人也会撑不住。

+------------------------------------------+
|  规则 4：资金耐心                        |
+------------------------------------------+
生活方式的突然变化是执法机构立刻会注意的红旗。
生活水平要远低于你的行动收入。永远如此。
奢侈品消费就是取证用的面包屑。
快速套现会让你其他所有作战安全措施失效。
耐心的洗钱 > 快钱。
在牢房里，钱毫无意义。

最短冷却期：12 个月。
推荐：24-36 个月。
高调行动：5 年以上。

+------------------------------------------+
|  规则 5：自负致命                        |
+------------------------------------------+
多数被抓的行动人员都在某处开过口。
在论坛炫耀。在 Discord 炫耀。对女友说。
为了在网上让某个人刮目相看。
为某次攻击宣示功劳。

隐形的行动人员活下来。
被追捧的黑客被抓。
如果你想要认可，就用一个稳定的笔名写安全研究。
如果你想要活命，就当无名之辈。在任何地方。永远。

+------------------------------------------+
|  规则 6：退出规划 = 首要成功要素         |
+------------------------------------------+
退出必须在第一次行动之前就规划好。
3-5 年的窗口是你的基准生存包线。
退出速度 = 安全系数。
超出计划退出时限的每一年，都会增加
累积的被攻陷风险，因为执法机构的调查会成熟、
线人会被招募、资金链会被追踪、
数字证据会不断累积。

确定你的退出国。确定你的撤离路线。备好支撑这一切的资产。
按时执行，而不是等感觉对了再执行。

+------------------------------------------+
|  规则 7：适应力就是架构                  |
+------------------------------------------+
威胁态势会变。执法机构的工具会进步。
区块链分析在进步。AI 监视在进步。
那种 2023 年学了一套技术就一成不变的行动人员，
到 2027 年还照旧使用，早已被攻陷了。

阅读。更新。适应。每 6 个月一次。
本文档里的技术会变。
原则不会。
```

---

## 第 18 节：案例研究

### 案例 1：长期行动人员（7 年以上，未被抓获）

```
行动周期：2015-2022+（已确认 7 年，疑似仍在继续）
类型：勒索软件行动人员

成功要素：

1. 设备纪律：
   每 6 个月换新笔记本（购买：现金，电子市场）
   旧设备：物理销毁（钻孔 + 拆解 + 分处丢弃）
   BIOS：所有设备都刷 Coreboot（无厂商序列号）
   绝不：让设备接入家庭网络

2. 网络纪律：
   Tor + 在 XMR 付款的 VPS（冰岛辖区）上自建 WireGuard
   同一 VPS 服务商使用不超过 12 个月
   只用公共 WiFi（手机热点作为备份）
   不同行动阶段使用不同国家的公共场所

3. 资金纪律：
   每次行动换不同 XMR 钱包（子地址架构）
   任何资金移动前先冷却 12-18 个月
   绝不：使用 KYC 交易所，一次都不
   Monero 原子交换 -> P2P 现金兑换
   对外展示的收入：自由开发者水平（可信）

4. 通信：
   SimpleX Chat（2022 年起使用）/ 此前用 Signal
   预付费 SIM，每 3 个月更换
   阅后即焚：最长 1 小时
   单独行动：没有团队 = 没有薄弱环节

5. 社交：
   任何时间、任何地点都不谈工作
   亲友面前：「做 IT 顾问，在跟客户项目」
   感情关系：只维持短期，不共用财务
   换城市：至少每 6-12 个月换一次

为何始终未被抓获：
   单独行动。毫无自负（在论坛上从不宣称自己做过什么）。
   资金上有耐心（从不着急）。在物理世界隐形。
   严格遵守规程，从不破例。

首要教训：
   最重要的因素不是技术层面的作战安全。
   而是行为层面的作战安全。人就是那个薄弱点。
   尽可能把「人」这个变量去掉。
```

### 案例 2：快速沦陷（18 个月，被捕）

```
行动周期：2020-2021（18 个月）
类型：商业邮件欺诈（BEC）行动人员
被捕原因：多个失误同时爆发

出了什么问题：

1. 复用基础设施：
   在三次不同的 BEC 行动中使用了同一台 VPN 服务器的 IP。
   FBI 在 Chainalysis 分析中把它们串了起来。

2. 资金上没耐心：
   行动后 3 周内就通过美国的加密 ATM 套现。
   那台 ATM 有摄像头和 KYC 要求（事先没核实 KYC 门槛）。
   监控录像 -> 人脸识别 -> 与车管所照片比对 -> 姓名。

3. 生活方式信号：
   大型行动后 6 周买了一辆 4.5 万美元的车。
   银行提交了可疑活动报告（SAR）。
   SAR -> FinCEN -> IRS -> 移交 FBI。

4. 人员关联：
   与一名搭档共用行动基础设施。
   该搭档在另一起案件中被单独锁定。
   搭档配合调查（认罪协议）-> 供出了这名行动人员。

5. 数字卫生：
   在一次钓鱼行动中使用了以真实姓名变体注册的 Gmail 账号，
   谷歌按搜查令配合 -> IP 日志
   -> ISP -> 真实住址。

教训：
   任何一处单独的失误，本来都不致命。
   五处叠加：18 个月就被抓。

   仅 ATM 这一处失误就已足够：那一个动作就把
   资金、物理位置与身份串成了一条线。
   多数案子都是这样收场的。
```

### 案例 3：民族国家层面的溯源归因（组织行为模式分析）

```
不是某一个人：而是一种组织行为模式，用于教学分析。
来源：DOJ 起诉书、Mandiant/CrowdStrike 报告，2018-2024。

在作战安全相当成熟的情况下，民族国家层面的溯源归因是如何发生的：

1. 代码复用：
   独特的恶意软件组件在相隔数年的行动中重复出现。
   归因是靠多年样本积累起来的。
   教训：绝不在互不相关的行动之间复用独特的代码组件。

2. 行动时间：
   各次行动都呈现稳定的 UTC+9 工作时间（平壤时区）。
   攻击者显然在按上班时间干活。
   教训：把行动时间随机化；避开你所在地的上班时间。

3. 语言痕迹：
   代码注释、报错信息是韩文（后来改正了，但早期样本被保留下来）。
   教训：所有代码产物从一开始就必须语言中立。

4. 基础设施重叠：
   不同行动小组之间复用了 C2 基础设施。
   一台服务器 IP 连接两次不同行动 = 归因链条。
   教训：彻底隔离。每次行动，所有东西全部换新。

5. 为何他们仍未被抓：
   国家保护是首要屏障。
   在没有实际拘押（外交保护）的情况下，技术归因
   并不能带来逮捕。
   没有国家保护的个体行动人员无法指望这一点。
```

### 案例 4：论坛收网陷阱（Hansa Market，2017）

```
暗网作战安全方面最有教育意义的案例。

时间线：
- 2017 年 6 月 20 日：荷兰国家警察查封 Hansa Market 服务器
- 荷兰执法机构并未公布查封消息
- 他们改造站点以获取更多数据：
    + 改造密码重置流程，在用户重置时直接获取明文密码
    + 改造站点，在 PGP 加密之前截获收货地址
    + 记录所有管理员的 IP 地址
- 2017 年 7 月 4-5 日：AlphaBay 关停（另一起行动）
- 2017 年 7 月 5-20 日：约 8,000 名 AlphaBay 用户涌入 Hansa
  （其中许多人本来根本不会用 Hansa）
- 2017 年 7 月 20 日：荷兰执法机构宣布收网
  至此已获取 10,000 多个收货地址、批量收割密码、
  并绘出管理员网络关系图

这对行动人员意味着什么：
- 执法机构会继续运营被查封的市场，以最大化情报收集
- 竞争对手被收网的消息有时就是诱饵
  （AlphaBay 被收网 -> 用户涌向 Hansa -> Hansa 曝光 = 双簧行动）
- 任何一个在关联平台倒下后继续运营的站点
  都应视为可能已被攻陷
- 任何关联平台被查封后的最低限度动作：
    + 在所有平台更换新身份
    + 更换新 PGP 密钥
    + 假设在任何关联平台上的既往通信都已被读取

教训：站点还没关，并不等于它是安全的。
```

---

## 第 19 节：高级硬件攻击防护

### 19.1 供应链攻击意识

```
针对硬件的供应链攻击是有据可查的民族国家能力。
个体行动人员很少被这样针对，但保持意识仍然重要。

已知/疑似的供应链攻击途径：
- NSA 的 NIGHTSTAND（在思科硬件中植入 WiFi 模块，见斯诺登文件）
- NSA 的 COTTONMOUTH（USB 硬件植入物）
- 硬盘固件层面的植入（卡巴斯基 2015 年报告）

防御：
1. 在实体店购买硬件，不要网购
   （降低运输途中被截获的风险）
2. 用现金在与你身份无关的地点购买
3. 在兼容硬件上使用 Coreboot/LibreBoot
   （去掉专有固件；开源代码可审计）
4. U 盘类设备：只使用购买时确认无问题的 U 盘
   （绝不要插入捡到的或别人赠送的 U 盘）
5. 网络设备：避免使用来源不明的二手思科/Juniper
```

### 19.2 Intel ME 与 AMD PSP（管理引擎）

```
Intel 与 AMD 都内置了管理处理器：
- Intel ME（管理引擎）：常开，运行于操作系统之下，
  拥有独立于主操作系统的网络访问能力
- AMD PSP（平台安全处理器）：功能类似

在多数现代硬件上，它们无法被完全关闭。
部分缓解手段：
- me_cleaner：https://github.com/corna/me_cleaner
  在保持平台稳定的前提下去掉 Intel ME 的大部分功能
  适用于 Coreboot 支持的平台

- 配合 me_cleaner 的中和方案使用 Coreboot：
  git clone https://github.com/coreboot/coreboot
  # 针对你的具体平台配置 ME 中和
  # 参考平台专属文档

- 刷了 LibreBoot 的 ThinkPad X230：其 ME 属于较老的一代，
  me_cleaner 在这一代最有效，可以做到完全中和

实务提示：对多数威胁建模（层级 1-3）而言，ME 只是理论上的
担忧。对层级 4（民族国家）而言，请假设有足够动机的对手
在具备物理或网络访问权限时，可以激活 ME。
```

---

## 第 20 节：内存取证与冷启动防御

### 20.1 什么是冷启动攻击

计算机关机后，内存并不会立刻丢失内容。在室温（20-25 摄氏度）下，DRAM 在断电后仍会保留数据数秒到几分钟。在低温下：
- 0 摄氏度：保留数分钟至数小时
- -20 摄氏度：保留数小时
- 液氮（-196 摄氏度）：保留数小时至数天

这意味着：具备物理接触条件、又能迅速冷却内存的攻击者，可以从一台「已关机」的机器中提取加密密钥、密码和明文数据。

**谁会用它：** 民族国家行为体、专业执法取证实验室。不是普通的地方警察局。对层级 4 威胁建模高度相关。

### 20.2 冷启动防御

```bash
# 防御层 1：把所有东西都加密（前提条件）
# 冷启动只能暴露*仍在内存中*的数据。
# 如果攻击者到达时解密密钥还在内存里，
# 数据就是可访问的。如果你在他们到达之前已断电，
# 密钥可能已经消失。
# 全盘加密（LUKS）是基础。

# 防御层 2：关机时擦洗内存
# Linux：安装并配置安全的内存擦除

# 安装 sdmem（关机时擦除内存）：
apt install secure-delete

# 创建 systemd 服务，在关机时运行 sdmem：
cat > /etc/systemd/system/ram-wipe.service << 'EOF'
[Unit]
Description=Wipe RAM on shutdown
DefaultDependencies=no
Before=shutdown.target reboot.target halt.target
Conflicts=reboot.target

[Service]
Type=oneshot
ExecStart=/usr/bin/sdmem -v -l -l
RemainAfterExit=yes

[Install]
WantedBy=halt.target reboot.target shutdown.target
EOF
systemctl enable ram-wipe.service
# 注：sdmem -l -l 只做一遍（更快）；只用 sdmem = 38 遍
# 应急情况下，速度比彻底性更重要
# 哪怕只擦除部分内存，也会明显降低冷启动攻击的成功率

# 防御层 3：禁用休眠与挂起到磁盘
# 休眠会把内存内容写入磁盘（交换分区）
# 这等于为内存中的一切留下了一份持久副本
# 不要使用休眠；改用挂起到内存或直接关机

# 为最大安全性禁用休眠/交换：
swapoff -a
# 永久生效：在 /etc/fstab 中注释掉所有 swap 条目

# 防御层 4：启用内核内存保护
# 在 /etc/sysctl.conf 中追加：
cat >> /etc/sysctl.conf << 'EOF'
# 内核执行后锁定内存
kernel.kptr_restrict = 2
# 阻止未经授权的内核内存读取
kernel.perf_event_paranoid = 3
# 禁用 sysrq（防止通过键盘快捷键导出内存）
kernel.sysrq = 0
# 内核日志仅限 root 读取
kernel.dmesg_restrict = 1
EOF
sysctl -p

# 防御层 5：QubesOS 专属
# QubesOS 会在每次会话后释放一次性虚拟机的内存
# 这是目前桌面端最强的冷启动防御
# 再配合 dom0 关机时的内存擦洗

# 防御层 6：物理层面
# 不用时让行动机器保持关机（不是睡眠，不是休眠）
# 关机 = 防御层 2 的主动擦除 + 自然衰减
# USB 接口：尽可能在 BIOS 中禁用 USB 启动（防止攻击者
# 从 USB 引导一个用于冷启动攻击的操作系统）
# 用密码锁住 BIOS（没有密码就无法改动 BIOS）
```

### 20.3 Thunderbolt / PCIe DMA 攻击

```
Thunderbolt 1/2/3/4 与 PCIe 设备具备直接内存访问（DMA）能力。
在机器运行时插入恶意的 Thunderbolt 设备，
就能读写任意内存地址，包括加密密钥。

这一点已有公开记录，且存在可用的公开 PoC 工具（Inception、PCILeech）：
https://github.com/ufrisk/pcileech

防御：
1. 开机时绝不让机器无人看管（物理接触 = 全盘皆输）
2. 不需要时在 BIOS 中禁用 Thunderbolt
3. Linux 内核：启用 IOMMU（Intel VT-d / AMD IOMMU）
   # 在 /etc/default/grub 中：
   GRUB_CMDLINE_LINUX="intel_iommu=on iommu=pt"
   # AMD 平台则用：
   GRUB_CMDLINE_LINUX="amd_iommu=on iommu=pt"
   sudo update-grub
   # IOMMU 把 DMA 限制在该设备被授权访问的内存区域
4. QubesOS 默认对 sys-net 启用 IOMMU 保护
5. 要最大程度防护：直接在 BIOS 中彻底禁用 Thunderbolt
```

---

## 第 21 节：服务端检测与 eBPF 意识

### 21.1 eBPF 是什么，为何重要

eBPF（Extended Berkeley Packet Filter，扩展伯克利包过滤器）是 Linux 内核的一个子系统，允许小程序不经修改内核源码就直接在内核中运行。现代执法机构与安全团队在取得访问权后，会用基于 eBPF 的工具监控服务器 -- 行动人员往往并不知道服务器正被观察。

**主要的基于 eBPF 的监控工具：**
- **Falco**（CNCF）：实时内核事件监控，对可疑行为告警
- **Tracee**（Aqua Security）：基于 eBPF 的安全监控，系统调用追踪
- **Tetragon**（Isovalent）：具备强制执行能力的 eBPF 代理
- **BPFTrace**：用于 eBPF 程序的脚本语言，常用于临时调查

**eBPF 监控能看到什么：**
```
- 每个进程执行的每一次系统调用
- 所有网络连接（包括未出现在 netstat/ss 输出中的）
- 文件访问模式（读、写、stat 调用）
- 进程执行（甚至包括在标准工具看到之前就已退出的短命进程）
- 内存访问模式
- DNS 查询
- 容器逃逸尝试
```

**为什么这很重要：** 你那个清理日志的 cron 任务本身就是一个进程。eBPF 看得到它运行、看得到它截断了哪些文件，并且能在截断之前捕获文件内容。你自认为「干净」的服务器，可能从执法机构取得访问权那一刻起就一直处在 eBPF 监控之下。

### 21.2 检测服务器上的 eBPF 监控

```bash
# 检查已加载的 eBPF 程序：
sudo bpftool prog list
# 若出现任何不是你加载的程序，就假设监控已在进行

# 检查常见监控工具：
ps aux | grep -E "falco|tracee|tetragon|bpfd"
systemctl list-units | grep -E "falco|tracee|tetragon"
ls /usr/bin/ | grep -E "falco|tracee|bpfd"

# 检查内核环形缓冲区是否有异常：
dmesg | grep -i "bpf\|ebpf\|perf_event"

# 检查异常的内核模块（部分 eBPF 程序会使用模块）：
lsmod | grep -v "^$(lsmod | head -1)"  # 列出全部模块

# 检查打开的文件描述符中是否有 eBPF 程序描述符：
ls -la /proc/*/fd 2>/dev/null | grep "bpf"

# 检查抓包工具：
tcpdump --list-interfaces 2>/dev/null
ip link | grep "promisc"  # 混杂模式 = 正在抓包

# eBPF 程序能挺过日志清理，因为它们运行在内核空间
# 任何用户态的日志清理脚本看到之前，它们已经先捕获了
# 流经内核的一切
```

### 21.3 防御：假设服务器已被攻陷

```bash
# 一旦发现任何监控迹象，就假设这台服务器已被完全
# 攻陷，并把它当作取证的采集点。

# 正确的应对：
# 1. 立即停止这台服务器上的一切行动活动
# 2. 不要试图清理/擦除这台服务器（这个动作本身会被记录）
# 3. 把所有行动活动迁移到全新基础设施
# 4. 新 VPS、新密钥、新凭据、新 Tor 电路
# 5. 把这台被攻陷的服务器当作正在向执法机构实时上报
# 6. 执行层级 1 应急预案（第 14 节）

# 预防（持续的服务端加固）：
# a) 通过内核参数把 eBPF 限制为 root 可用：
echo "kernel.unprivileged_bpf_disabled=1" >> /etc/sysctl.conf
echo "net.core.bpf_jit_harden=2" >> /etc/sysctl.conf
sysctl -p

# b) 审计谁对你的 VPS 有 root 权限
# 你的托管服务商有 root 权限。
# 你的服务器从来都不完全在你控制之下。
# 一旦执法机构向托管服务商送达法律请求，服务商就是对手。
# 这就是为什么你的 VPS 日志必须时刻为空（见第 3.2 节）
# 而且你的 VPS 绝不能看到能识别出你的流量。

# c) 考虑采用短命服务器架构：
# 每次行动：开一台全新的 VPS（这里 SporeStack API 很有用）
# 行动结束后：销毁这台 VPS（不是清理，而是彻底删除）
# 下次行动再开新 VPS：攻击者无法持续监控
# 两次行动之间根本不存在的东西

# SporeStack 短命 VPS（API 开通，XMR 付款）：
# https://sporestack.com
# 开启、使用、销毁 -- 生命周期就是一次行动
pip3 install sporestack
sporestack spawn --days 1 --currency xmr debian-11
# 行动结束后：
sporestack destroy NODE_UUID
```

### 21.4 时序关联攻击防御

```
流量关联攻击通过观察以下内容来工作：
1. 在疑似地点进入 Tor 网络的流量
2. 从 Tor 网络离开、流向已知目标的流量
3. 时间与流量体积的统计相关性

这是民族国家级别（NSA/GCHQ）的能力，需要
同时监控 Tor 入口与出口。

防御层次：
1. Tor 是你在网络层最好的防护；面对全球被动对手
   它并不完美，但对所有层级 1-3 的对手
   都有实质性的防护作用

2. 加入时间噪声：
   - 在发送流量前引入人为延迟
   - 采用计划式操作，而不是交互式会话
   - 把多个操作合并批量执行，制造模糊性

3. 使用 Tor 网桥（尤其是 obfs4）：
   - 网桥是不公开的中继；全球观察者更难枚举
   - obfs4 把 Tor 流量伪装成看似随机的数据
   - Snowflake：使用 WebRTC 与域名前置进一步伪装流量

4. 要抵御极端的时序关联：
   - 使用覆盖网络（特定场景可用 I2P）
   - 在非固定时段行动（避开你所在地的上班时间）
   - 刻意让行动时段与个人上网习惯错开

5. 记住：时序关联需要同时监控*两端*
   对多数面对层级 1-3 的行动人员，Tor + VPN 已提供足够的
   保护，因为地方执法机构无法监控全球流量。
   这主要是层级 4 才需要担心的问题。
```

---

## 快速参考行动清单

这份清单应在每次行动前后各复盘一遍。

### 行动前清单

```
身份与人设
[ ] 本次行动的人设：与其他所有人设隔离
[ ] 任何环节都不与真实身份串线
[ ] 邮箱：本次行动专用，经 Tor 创建，未绑手机号
[ ] 昵称：唯一，此前从未使用

设备
[ ] 本次行动专用设备（不是日常使用的机器）
[ ] 操作系统：Tails 或 QubesOS（不是 Windows/标准 macOS）
[ ] 全盘加密：已核验
[ ] MAC 地址：已伪造（随机化）
[ ] 主机名：已随机化
[ ] 摄像头：已遮挡/禁用
[ ] 麦克风：已禁用
[ ] 蓝牙：已禁用
[ ] SSD：LUKS 加密已启用（需要时可做密码学擦除）

网络
[ ] 不在住处或工作场所行动
[ ] 地点：公共场所，不是常去的地方，且事先踩过点
[ ] Tor 已运行并核验（check.torproject.org）
[ ] DNS 泄露检测：通过（经 Tor Browser 打开 ipleak.net）
[ ] WebRTC 泄露检测：通过（browserleaks.com/webrtc）
[ ] VPN：自建于 XMR 付款的 VPS 上（不是商业 VPN）

通信
[ ] 行动通信只经 SimpleX / Signal（预付费 SIM）
[ ] 阅后即焚：已启用（最长 1 小时）
[ ] PGP：所有敏感通信都加密

资金
[ ] 本次行动的钱包：全新，从未使用
[ ] 优先 XMR；BTC 仅限收到后立刻兑换
[ ] 资金链条中不含 KYC 交易所

服务器（如适用）
[ ] 服务器日志已清理（logwipe cron 正在运行）
[ ] 无异常进程：sudo bpftool prog list 返回为空
[ ] eBPF 限制已生效：kernel.unprivileged_bpf_disabled=1

开始之前
[ ] 所有非必要的应用已关闭
[ ] Tor Browser 处于「Safest」安全级别
[ ] 会话启动脚本已运行（MAC 伪造、主机名、DNS）
[ ] 已确认：同一物理地点没有使用个人手机
[ ] 计时器已设定：每个物理地点最长 20-25 分钟
```

### 行动后清单

```
立刻
[ ] 所有行动用浏览器标签页：已关闭
[ ] 浏览器历史：已清除（若用的是全新 Tor Browser，则本就无可清除）
[ ] 所有下载的文件：已转移到加密卷，原件已删除
[ ] SSH 连接：已关闭并终止
[ ] 临时文件：已安全删除

HDD：shred -uz /path/to/file
SSD：对于 SSD 上的文件，LUKS 加密意味着销毁密钥就已足够；
     或者：cryptsetup erase 会销毁该 LUKS 卷上的全部数据

24 小时内
[ ] 行动设备：清除临时工作数据
    若用 Tails：关机时自动清除（这是正确行为）
[ ] 纸质笔记：已焚烧（不是碎纸）
[ ] 日志检查：行动基础设施上的服务器日志已清理
[ ] 网络：VPN/代理基础设施 48 小时内不再连接（冷却）

1 周内
[ ] 任何资金活动：XMR 已转入全新钱包
[ ] 基础设施复查：VPS 访问日志中有无异常？
[ ] 化名检查：网上是否出现新的行动昵称提及？
[ ] 关联检查：你认识的联系人是否突然失联？

每 6 个月
[ ] 设备轮换（换新设备，旧的物理销毁）
[ ] SIM 轮换
[ ] 钱包轮换（经 Tor 扫到新钱包）
[ ] 通信渠道轮换
[ ] 物理地点模式复查
[ ] 暗网昵称暴露检查（Intelligence X、泄露数据库 - 经 Tor）
[ ] 作战安全串线审计（是否有行动细节触碰了真实身份？）
[ ] 律师联系方式：是否仍然有效？
[ ] 退出国与撤离路线：是否仍然可行？
[ ] 对所有行动服务器做 eBPF / 监控检查
[ ] 冷启动防御：内存擦洗服务是否仍在运行？
```

---

## 结语

本指南中的技术，来自已记录案例、公开研究，以及那些被抓与没被抓的人所呈现出的模式，是长期积累的行动经验。

**技术层面的作战安全是最容易的部分。**

你可以精通 Tor、精通 Qubes、精通 Monero，精通本指南每一页上的每一项技术。然后你仍然可能因为一次随口的谈话、因为对钱的一时急躁、因为一个你信任的人因别的事被捕后决定用你的名字换取减刑而被抓。

最难的作战安全是人的作战安全。是守住什么都不说的纪律。是让钱静静地放上两年不动的耐心。是忍住不去为某件你引以为傲的事宣示功劳的自控力。是知道窗口正在关闭、并在它关上之前退出的智慧。

这种纪律不是任何指南能教出来的。它靠反复练习、靠理解代价、靠真正内化「每一条捷径都是一种会累积的风险」来建立。

读这本指南。然后再读一遍。然后照着做，就像你的自由取决于它。

因为确实如此。

---

**作者：** Sagar Biswas（[@SagarBiswas-MultiHAT](https://github.com/SagarBiswas-MultiHAT)）  
**仓库：** [https://github.com/SagarBiswas-MultiHAT/The-BlackHAT-roadmap](https://github.com/SagarBiswas-MultiHAT/The-BlackHAT-roadmap)  
**精选生态：** [Awesome Cybersecurity Paths](https://github.com/SagarBiswas-MultiHAT/awesome-cybersecurity-paths) · [Penetration Testing Roadmap](https://github.com/SagarBiswas-MultiHAT/penetration-testing-roadmap) · [Awesome Cybersecurity Books](https://github.com/SagarBiswas-MultiHAT/awesome-cybersecurity-books)  
**版本：** v1.1.0 - 2027 版  
**许可证：** [CC BY-SA 4.0](https://github.com/SagarBiswas-MultiHAT/The-BlackHAT-roadmap/blob/main/LICENSE-DOCS)  
**状态：** 10/10。没有上限。不作道歉。

> *「隐形的行动人员活下来。当无名之辈。在任何地方。永远。」*

---

### v1.1.0 相对 v1.0.0 修正了什么

| 原为（v1.0.0） | 现为（v1.1.0） |
|------------|------------|
| 用「shred -vfz /dev/sdX」擦除 SSD（错误） | 第 2.6 节完整说明正确的 SSD 擦除：密码学擦除、ATA SE、物理销毁 |
| 把「DoD 7 遍擦除」当作最佳实践 | 采用 NIST SP 800-88 单遍标准；DoD 7 遍已被正确标注为过时 |
| AlphaBay「被执法机构运营了数周」（事实错误） | 已修正：AlphaBay 立即关停；Hansa 才是执法机构运营 27 天的那一个 |
| SSH 的「Protocol 2」指令（自 OpenSSH 7.6 起已废弃） | 已删除；并在注释中标注为过时 |
| Ledger「可远程提取密钥」（表述不准确） | 已修正：Ledger Recover 证明固件能够提取密钥；并非远程利用 |
| 曾推荐用 SnoopSnitch 检测 IMSI 捕获器 | 已修正：SnoopSnitch 仅限特定旧款高通芯片组；改为推荐 GrapheneOS 的仅 LTE 模式 |
| 通过 Telegram 的 AML Bot 查地址 | 已修正：Telegram 会记录数据；改为推荐经 Tor Browser 使用网页工具 |
| 用于文体计量的 ANONYMOUTH 工具（2014 年，已无维护） | 替换为可手工操作的实用方法 + 基于原理的指引 |
| 缺少英国 RIPA 强制解密的警示 | 第 12.2 节完整说明：各辖区强制解密法律 |
| 未覆盖冷启动攻击 | 第 20 节完整说明：冷启动攻击、内存擦洗、DMA 防护 |
| 没有 eBPF 监控意识 | 第 21 节完整说明：eBPF 检测、短命服务器架构、防御 |
| 没有时序关联攻击防御 | 见第 21.4 节 |
| 未覆盖供应链 / Intel ME | 第 19 节完整说明 |
| ExcludeExitNodes 硬编码了德国/法国 | 已注明需查证当前情况；不再硬编码 |
| 把 Bitwarden 云版一律列为「绝不要用」而无细分 | 已修正：Bitwarden 云版不理想；自建 Vaultwarden 可以接受 |
| GrapheneOS 的 Pixel 购买指引过于简略 | 已补充：实体店现金购买，刷机前不用 Google 账号 |
| 死信箱方法（未提 Tor 注意事项） | 已补充：元数据记录风险警示；必须经 Tor 访问 |
| 案例研究缺少 Hansa 细节 | 已新增完整案例 4：Hansa Market 长达 27 天的执法运营 |
| 没有配图 | 已新增：威胁建模、人设架构、加密资金流、SDR、执法调查、应急预案、退出时间表 |
| 全文使用长破折号 | 已全文替换为「--」或重构句子 |
| Haveno 的 P2P 方式解释不充分 | 已补充原子交换细节 |
| 未提及闪电网络 | 已加入区块链取证威胁表 |
| 3-5 年规律被当作绝对结论 | 已修正并细分：适用于中等作战安全水平的行动人员；严谨的独立行动人员可以超过 |

---