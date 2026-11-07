# 阶段 0：基础

**作者：** Sagar Biswas ([@SagarBiswas-MultiHAT](https://github.com/SagarBiswas-MultiHAT))<br/>
**规范仓库：** [The BlackHAT Roadmap](https://github.com/SagarBiswas-MultiHAT/The-BlackHAT-roadmap)<br/>
**许可证：** [CC BY-SA 4.0](https://github.com/SagarBiswas-MultiHAT/The-BlackHAT-roadmap/blob/main/LICENSE-DOCS)<br/>
**版本：** v1.0.0 · 2027 版<br/>

<div align="right">

**你无法攻破自己不理解的系统。**

</div>

**时长：** 5-8 个月（无基础）| 3-5 个月（计算机/开发背景）| **难度：** 入门到中级 | **每周小时数：** 20-25 | **前置要求：** 阶段 -1（OPSEC 与基础设施）| **完成率：** 70% —— 而那 30% 退出的人，是在第 3-6 周退出的。开始之前先读失败点一节。

---

> **这是整个路线图中最重要的阶段。**
>
> 从阶段 1 开始的一切都假设你已完全掌握这些材料。不是“理解它”。**是掌握它。** 用它构建。凭记忆调试。在它意外出问题时改造它。
>
> 赶着做这一阶段，就是操作者在现实压力下崩溃的原因。地基决定上限。把功课做完。全部做完。

---

## 目录

1. [目标与理念](#1-目标与理念)
2. [如何使用这一阶段](#2-如何使用这一阶段)
3. [前置要求](#3-前置要求)
4. [检查点：结束时你必须掌握的内容](#4-检查点结束时你必须掌握的内容)
5. [时间线与并行轨道架构](#5-时间线与并行轨道架构)
6. [第1节：操作系统基础](#6-第1节操作系统基础)
7. [第1B节：Bash 脚本基础](#7-第1b节bash-脚本基础)
8. [第2节：C 编程](#8-第2节c-编程)
9. [第3节：Python 脚本](#9-第3节python-脚本)
10. [第4节：网络基础](#10-第4节网络基础)
11. [第5节：x86-64 汇编](#11-第5节x86-64-汇编)
12. [第6节：逆向工程基础](#12-第6节逆向工程基础)
13. [第7节：密码学入门](#13-第7节密码学入门)
14. [第8节：ARM64 架构认知](#14-第8节arm64-架构认知)
15. [第9节：glibc 内部机制入门](#15-第9节glibc-内部机制入门)
16. [里程碑项目：完整规格卡](#16-里程碑项目完整规格卡)
17. [实验室搭建](#17-实验室搭建)
18. [GDB 设置与命令参考](#18-gdb-设置与命令参考)
19. [CTF 平台指南](#19-ctf-平台指南)
20. [常见失败点与修复](#20-常见失败点与修复)
21. [阶段 0 总清单](#21-阶段-0-总清单)
22. [接下来是什么](#22-接下来是什么)
23. [资源汇总](#23-资源汇总)

---

## 1. 目标与理念

**目标：** 在操作系统、编程、网络、汇编、逆向工程和密码学上打下不可动摇的基础。你无法攻破自己不理解的系统。这里的捷径会积累成日后灾难性的缺口 —— 当漏洞利用在内存中表现异常时、当二进制不符合你的心智模型时、当网络抓包完全说不通时，这些缺口就会显现。

### 这一阶段真正建立的是什么

你学的不是使用工具。你在建立让每一个工具都说得通的**心智模型**。

走完阶段 0 之后，你打开调试器时已经知道各寄存器是什么意思。你看到网络抓包时已经知道那些字节代表什么。你读到 shellcode 时能在脑中跟踪它。你在反编译器中看到一个 XOR 循环时，清楚它在做什么、为什么这么做。工具只是一扇窗户，窗外是你已经理解的东西。

### 是什么把能坚持下来的操作者区分开

不是智力。不是速度。不是先前经验。

**是在困惑中坐得足够久、直到它自行解开的能力。**

这一阶段的每个概念，在变得显而易见之前都会显得不可能。从不可能到显而易见之间的窗口，通常是 48-72 小时的持续接触。多数人就在那个窗口里退出。他们把困惑解读为自己不适合做这件事。他们错了。困惑正是学习过程在正常运转。你并没有在学习的信号，是你什么都感觉不到 —— 当你只是在被动阅读而没有动手构建、只是点头而没有真正理解时。

不要在困惑的窗口里退出。穿过它去构建。

### 为什么 2027 年比往年要求更高

攻击格局已经变了。x86-64 不再是唯一重要的架构：

- Apple Silicon（arm64）主导 macOS 开发机 —— 你的目标会落在这些机器上
- AWS Graviton 与 Ampere Altra 支撑着越来越多的云基础设施
- Android（arm64）按用户数算是世界上最常见的操作系统
- IoT 与嵌入式目标绝大多数是 ARM Cortex-M 和 Cortex-A
- RISC-V 正在嵌入式和服务器场景中出现

阶段 0 以 x86-64 作为主要架构来教，因为那里的工具链、资源和漏洞利用技术最成熟。但它也会现在就种下 ARM64 的种子，这样你在阶段 2 遇到它时不是从零开始。

---

## 2. 如何使用这一阶段

### 从第一天起就建立知识库

安装 **Obsidian**（免费、本地优先、Markdown）：https://obsidian.md

建立一个名为 `hacking-kb` 的库。这一阶段里你每学到一样东西，就写一条笔记。不是复制粘贴 —— 而是用你自己的话重述。一个概念一条笔记。写作这个动作会强制理解发生。

建议的结构：
```
hacking-kb/
├── os/
│   ├── virtual-memory.md
│   ├── syscalls.md
│   └── process-model.md
├── c/
│   ├── pointers.md
│   └── memory-layout.md
├── assembly/
│   ├── x86-64-registers.md
│   ├── arm64-registers.md
│   └── calling-convention.md
├── networking/
│   ├── tcp-handshake.md
│   └── dns-resolution.md
├── re/
│   └── elf-format.md
├── crypto/
│   ├── xor-basics.md
│   └── pki-tls.md
└── gdb-cheatsheet.md   -- 你个人的 GDB 参考，边学边建
```

之后的每一个阶段，你都会查阅这个知识库。在阶段 0 就把它建起来的操作者，在阶段 3 和阶段 4 里快 2 倍。没建的人，会在阶段 3 花时间重新研究他们早已见过一次又忘掉的概念。

### 构建法则

**只读不建就是观光。** 每学完一个子节，关掉文档，打开终端，动手建点东西。哪怕很小。哪怕它会坏。尤其是它会坏的时候。坏掉的构建教给你的比能跑的示例更多。

### 每周自我评估

每周结束时，花 15 分钟在你的 Obsidian 库里回答三个问题：

1. 今天我能建出什么、而上周还建不出来？
2. 哪个概念仍然不牢？(这是你下周第一个回头补的东西。)
3. 这周我达到 CTF 最低量了吗？(每天至少一道题。)

这些不是绩效考核。它们是校准仪器。目标是诚实的数据，不是好看的分数。

### 每周“我是否在轨道上”检查点

把这些当作健康检查。如果你做不出本周对应的事项，你并没有落后 —— 你在困惑窗口里。继续构建。

| 周次 | 你应当能够…… |
|------|--------------------------|
| 2 | 写并编译一个使用 malloc、free 和指向结构体的指针的 C 程序 |
| 4 | 凭记忆解释 fork/exec；浏览 /proc/[pid]/maps 并说出每个区域是什么 |
| 6 | 写一个 Bash 脚本，读取文件并用管道把输出经 awk 和 grep 过滤 |
| 8 | 写一个不依赖 libc、直接发起 write() 系统调用的 C 程序 |
| 10 | 写一个 Python TCP 客户端，能连接、发送数据，并用 struct 解析二进制响应 |
| 12 | 双向追踪一个数据包从应用到网线，并说出每一个头部字段 |
| 14 | 写一个可从 C 调用的 NASM 函数；用 GDB 在指令级单步跟踪它 |
| 18 | 在 Ghidra 中打开一个未知 ELF，找到 main()，重命名所有变量，理清控制流 |
| 20 | 用 Python 实现 XOR 加解密，并用频率分析破解单字节 XOR |
| 22 | 不查任何资料，说出 x86-64 与 ARM64 调用约定的区别 |

### 卡住的时候

1. **读错误信息。** 完整地读。不是第一行 —— 全部。
2. **重读相关概念。** 你心智模型里有东西是错的。
3. **精确地搜索。** “C segfault dereferencing null pointer”比“C program crash”有效。
4. **用 GDB。** 在崩溃前设断点。看寄存器。看内存。答案总在里面。
5. **两小时毫无进展之后：** 去看一份参考实现。理解它为什么能工作。然后关掉它，凭记忆重建。

跳过第 4 步是初学者最常犯的错误。GDB 不是高级工具。它是第一个工具。在第一周就要把它用熟。

---

## 3. 前置要求

开始阶段 0 之前，你需要：

- 阶段 -1 已完成（OPSEC 与基础设施）
- 一个可用的 Linux 安装（推荐 Ubuntu 22.04 LTS）：真机安装或虚拟机
- 按阶段 -1 搭好的匿名研究环境
- 基本的终端熟练度：会切换目录、创建文件、运行命令
- 一个文本编辑器 —— 推荐 **vim**（你到哪都会用到它，现在就学基础）

**第一周需要的 Vim 基础**（练 15 分钟就能覆盖）：
```
i          --> 插入模式（开始输入）
Esc        --> 普通模式（停止输入）
:w         --> 保存
:q         --> 退出
:wq        --> 保存并退出
:q!        --> 不保存退出
dd         --> 删除一行
yy         --> 复制一行
p          --> 粘贴
/word      --> 搜索“word”
n          --> 下一个匹配
G          --> 文件末尾
gg         --> 文件开头
```

**完全没有编程经验？** 这一阶段能接住你。第 2 节（C）从零开始。不要让“我从没写过代码”拦住你起步。

**有计算机/开发背景？** 把操作系统和 Python 两节砍掉 40-50%。但**不要**跳过汇编或逆向工程 —— 几乎没有哪个学位项目会教到这里的深度。

**Windows 用户：** WSL2（Windows Subsystem for Linux 2）是阶段 0 学习时替代完整虚拟机的可行方案。从 Microsoft Store 安装 Ubuntu 22.04。WSL2 运行真正的 Linux 内核，性能接近原生。限制：原始套接字操作（AF_PACKET）在项目 3 中需要虚拟机或裸机。阶段 0 的其他内容在 WSL2 下都能正常工作。

---

## 4. 检查点：结束时你必须掌握的内容

在进入阶段 1 之前，你必须**不查任何资料**就能做到下面每一条。这些不是可选项。它们是阶段 1 的入场条件。

### 操作系统
- [ ] 解释从 `execve()` 到一个运行中的进程发生了什么：fork、exec、地址空间布局
- [ ] 解释虚拟内存：页、页表、TLB、物理地址与虚拟地址
- [ ] 解释中断处理：硬件中断 -> 内核入口 -> 处理程序 -> 返回用户空间
- [ ] 解释进程调度：上下文切换、调度器、进程状态
- [ ] 浏览 `/proc/[pid]/` 并提取：maps、fd、status、cmdline、mem

### Bash 脚本
- [ ] 写一个 Bash 脚本，接受文件名作为参数，逐行读取，并只打印匹配某个模式的行
- [ ] 用管道串联三个工具，从命令输出中提取特定字段
- [ ] 写一个 Makefile，编译多文件 C 程序，并带有 `clean` 目标
- [ ] 用 `awk` 从空格分隔的输出中提取第 3 个字段
- [ ] 写一个 `for` 循环，对文件中一组 IP 逐个运行 nmap

### C 编程
- [ ] 写一个正确使用指针、指针算术和 void 指针的程序
- [ ] 解释栈分配与堆分配的区别；两种都实现
- [ ] 用 C 写一个可用的链表，含插入、删除、遍历
- [ ] 写一个用内联汇编直接发起系统调用的程序（不用 libc 封装）
- [ ] 故意制造一次内存泄漏，然后用 Valgrind 和 AddressSanitizer 分别检出
- [ ] 写一个 Makefile，编译含多个源文件的 C 程序

### Python 脚本
- [ ] 用原生 Python socket 写一个 TCP 客户端和服务端
- [ ] 用 `struct` 模块解析一种二进制文件格式
- [ ] 写一个脚本，运行子进程、捕获 stdout 并处理输出
- [ ] 用 Scapy 构造并发送一个原始 ARP 请求；解析响应

### 网络
- [ ] 追踪一个数据包从应用层到物理层再返回：每一层、每一个头部字段
- [ ] 逐字节解释 TCP 三次握手
- [ ] 解释 DNS 解析从查询到应答：每一步
- [ ] 读一份 Wireshark 抓包，识别出一个 TCP 连接、一次 DNS 查询和一个 HTTP 请求
- [ ] 解释 IPv4 与 IPv6 寻址的区别；一眼认出 IPv6 地址

### 汇编与调试
- [ ] 读懂 C 函数生成的 x86-64 汇编，并跟踪其控制流
- [ ] 凭记忆解释 x86-64 System V AMD64 调用约定
- [ ] 用 NASM 汇编写一个接受两个参数并返回值的函数
- [ ] 使用带 GEF 的 GDB：设断点、单步执行指令、检查寄存器和内存
- [ ] 用两句话说明 ARM64 调用约定与 x86-64 有何不同

### 逆向工程
- [ ] 用 `readelf` 判断一个 ELF 二进制的架构、入口点和各节
- [ ] 从二进制中提取可打印字符串，并找出其中有意思的
- [ ] 在 Ghidra 中打开一个二进制，定位到 `main()`，读反编译输出
- [ ] 用 `ltrace` 跟踪库调用，用 `strace` 跟踪系统调用
- [ ] 描述 ELF（Linux）与 PE（Windows）两种格式的结构差异

### 密码学
- [ ] 用 Python 从零实现 XOR 加密/解密
- [ ] 解释 XOR 为什么可逆（一行数学证明）
- [ ] 实现凯撒密码，并用频率分析破解它
- [ ] 解释对称加密与非对称加密的区别（一段话，不查笔记）
- [ ] 计算文件的 MD5 与 SHA-256 哈希，并解释它们为什么是单向的
- [ ] 解释 TLS 证书是什么，以及信任链意味着什么

### ARM64 认知
- [ ] 说出 ARM64 用于传参（x0-x7）和返回值（x0）的通用寄存器
- [ ] 说出 ARM64 与 x86-64 指令设计上的一处结构差异
- [ ] 用 `file` 或 `readelf` 识别出一个 ARM64 ELF 二进制

---

## 5. 时间线与并行轨道架构

对完全没有背景的初学者，诚实的时间线是**每周 20-25 小时、持续 5-8 个月。** 如果你已有开发经验，3-5 个月是现实的。

**关于并行的关键认识：** 你不是做完一节再开始下一节。有好几条轨道同时跑，因为它们互相强化。一边读操作系统的内存管理，一边写会分配内存的 C 程序，两者都会更快打通。一边学汇编，一边读 C 编译器的输出，两者都会更锐利。

### 阶段 0 学习路径总览

<div align="center">
<table><tr><td>

<img src="../assets/diagrams/PHASE_0/1._Phase_0_Learning_Path_Overview.png" alt="Phase 0 Learning Path Overview" width="450"/>

</td></tr></table>
</div>

### 里程碑项目日程

| 项目 | 主攻小节 | 目标周 | 小时数 |
|---------|----------------|-------------|-------|
| 1. C 语言简易 shell | C + 操作系统 | 6-8 | 15-25 |
| 2. 内存分配器 | C + 操作系统 | 10-12 | 20-30 |
| 3. 网络数据包分析器 | 网络 + C | 14-16 | 15-20 |
| 4. 汇编函数库 | 汇编 | 17-19 | 10-15 |
| 5. 首个二进制逆向 | 逆向基础 | 22-24 | 10-15 |

**CTF（picoCTF）：** 第 4 周开始。此后永远并行进行。细节见第 19 节。

---

## 6. 第1节：操作系统基础

**时长：** 6-8 周（第 1-8 周）| **并行于：** C 编程、Bash 脚本

### 为什么这排在第一位

每一个漏洞利用针对的都是操作系统的抽象。缓冲区溢出破坏栈 —— 而栈是由操作系统和调用约定定义的结构。进程注入写入另一个进程的地址空间 —— 而那个地址空间只因为操作系统创建了它才存在。提权滥用操作系统的权限模型。理解你在破坏什么不是可选的背景知识：它是每一种技术所立足的地基。

---

### 1.1 进程与线程

**进程**是一个正在运行的程序。它不是程序本身 —— 程序是磁盘上的字节。当操作系统执行一个程序时，它创建一个进程：一个独立的执行上下文，拥有自己的地址空间、文件描述符表和状态。

**一个进程由什么组成：**
- **地址空间：** 进程看到的虚拟内存（代码、数据、栈、堆、映射的文件）
- **线程：** 真正的执行流 —— 一个进程至少有一条
- **文件描述符表：** 以整数索引的打开文件、套接字、管道（0=stdin，1=stdout，2=stderr）
- **进程状态：** 运行、睡眠（可中断/不可中断）、僵尸、停止
- **PID：** 进程标识符，由操作系统在创建时分配

**线程**是进程内的一个执行上下文。线程共享进程的地址空间，但各自拥有自己的栈和寄存器。这就是为什么线程比进程创建成本更低（不需要新地址空间），也是为什么它们会引入竞态条件（共享内存 + 并发访问 = 没有同步就是未定义行为）。

**进程如何创建 —— fork/exec 模型：**

```c
// 在 Linux 上，新进程来自 fork() + exec()
// 你的 shell 就是这样运行你输入的每条命令的。

#include <unistd.h>
#include <sys/wait.h>
#include <stdio.h>

int main() {
    pid_t pid = fork();    // 创建当前进程的一份精确副本
                           // 子进程中返回 0，父进程中返回子进程的 PID，出错返回 -1

    if (pid == 0) {
        // 我们在子进程中（pid == 0 意思是“我是子进程”）
        char *argv[] = {"/bin/ls", "-la", NULL};
        char *envp[] = {NULL};
        execve("/bin/ls", argv, envp);  // 用 ls 替换子进程的整个内存映像
        // 如果 execve() 返回了，说明它失败了。成功时 execve 永不返回。
        perror("execve failed");
        return 1;

    } else if (pid > 0) {
        // 我们在父进程中
        int status;
        waitpid(pid, &status, 0);  // 等待子进程结束；避免产生僵尸进程
        printf("Child exited with status: %d\n", WEXITSTATUS(status));

    } else {
        // pid == -1：fork 失败（内存不足、触及进程数上限）
        perror("fork failed");
        return 1;
    }
    return 0;
}
```

**进程相关的关键系统调用：**

| 系统调用 | 编号（x86-64） | 作用 |
|---------|-----------------|--------------|
| `fork()` | 57 | 创建子进程（父进程的副本） |
| `execve()` | 59 | 用新程序替换进程映像 |
| `exit()` | 60 | 终止进程，把状态返回给父进程 |
| `waitpid()` | 61 | 等待子进程状态变化；收集退出状态 |
| `getpid()` | 39 | 获取当前进程 ID |
| `getppid()` | 110 | 获取父进程 ID |
| `clone()` | 56 | 创建线程（fork，但对共享资源有细粒度控制） |
| `kill()` | 62 | 向进程发送信号 |

**查看活动进程：**
```bash
# 列出所有进程及完整详情
ps aux

# 进程树（显示父子关系）
pstree -p

# 动态进程查看器
top
htop   # 更好用；安装：apt install htop

# 某个特定进程的一切信息
ls -la /proc/[pid]/
cat /proc/[pid]/status     # 状态、PID、PPID、内存统计
cat /proc/[pid]/cmdline    # 启动它的命令行（以 null 分隔）
cat /proc/[pid]/maps       # 虚拟内存映射（极其重要 —— 要研究它）
ls -la /proc/[pid]/fd/     # 打开的文件描述符
```

---

### 1.2 虚拟内存：阶段 0 最重要的概念

这是每一种内存破坏型漏洞利用的地基。继续往下之前先把它彻底搞懂。

**虚拟内存**让每个进程都产生一种错觉：它拥有整个地址空间。在 64 位 Linux 上，每个进程看到一个 48 位的虚拟地址空间（约 128 TB）。物理内存可能只有 16 GB。这个不匹配并不重要，因为操作系统透明地处理地址转换。

**为什么存在虚拟内存：**
1. **隔离：** 进程 A 默认无法读取进程 B 的内存。(这正是进程注入所打破的东西。)
2. **过量提交：** 进程可以申请比物理内存更多的内存；操作系统把冷内存换页到磁盘。
3. **共享库：** `libc.so` 在运行时装进每个进程，但物理内存中只存在一份。

**进程的地址空间布局：**

<div align="center">
<table><tr><td>

<img src="../assets/diagrams/PHASE_0/2._Address_Space_Layout_of_a_Process.png" alt="Address Space Layout of a Process" width="350"/>

</td></tr></table>
</div>

**ASLR（地址空间布局随机化）：** 在现代 Linux 上，栈、堆和库的基地址在加载时被随机化。PIE（位置无关可执行文件）的代码段也被随机化。这就是硬编码地址会失败的原因 —— 也是击败 ASLR 之所以成为阶段 3 核心技术的原因。

**页与页表：**

内存被划分为**页**（默认 4096 字节 = 4 KB）。CPU 的内存管理单元（MMU）用内核维护的页表把虚拟地址翻译成物理地址。

```
虚拟地址（64 位 x86-64）：
  [未用：位 63-48][PML4 索引：9 位][PDPT 索引：9 位]
  [PD 索引：9 位][PT 索引：9 位][页内偏移：12 位]
                                                   |
                                      页表遍历（4 级）
                                                   |
物理地址：[物理帧号][页内偏移：12 位]
```

每一页都有硬件强制执行的**权限位**：
- **R**（可读）：可以读取这一页
- **W**（可写）：可以写入这一页
- **X**（可执行）：可以从这一页执行代码

`.text` 节是 **R+X，不是 W**。栈是 **R+W，不是 X**（在启用 NX/DEP 时）。写入只读页会触发缺页，内核随即向进程发送 SIGSEGV。

**转译后备缓冲器（TLB）：** 页表遍历很昂贵（4 次内存访问）。TLB 缓存最近的虚拟地址到物理地址的翻译。上下文切换会冲刷 TLB —— 这是一笔重大的性能开销。

**读取一个活动进程的内存映射：**
```bash
# 你自己的进程
cat /proc/self/maps

# 另一个进程（需要相同 UID 或 root）
cat /proc/[pid]/maps

# 示例输出，以及每个字段的含义：
# 55f0a3e00000-55f0a3e01000 r--p 00000000 08:01 1234567  /usr/bin/cat
# 地址范围                   权限  偏移   设备  inode    路径
#
# 权限：r=读, w=写, x=执行, p=私有(CoW), s=共享
```

**实践练习：** 打开一个终端。运行 `cat /proc/self/maps`。找出：代码段、栈、堆、libc 的映射。判断每个区域的权限。注意是否有任何段是可执行的。这就是你在阶段 3 将要利用的那张地图。

---

### 1.3 系统调用：内核接口

系统调用是用户空间代码请求内核执行特权操作时的受控机制：打开文件、分配内存、创建进程、通过网络发送数据。CPU 有两种运行模式：**用户模式**（ring 3）和**内核模式**（ring 0）。用户空间代码无法直接碰硬件。系统调用是那座桥。

**x86-64 Linux 上的系统调用机制：**

```nasm
; 第 1 步：把系统调用号装入 rax
; 第 2 步：把参数依次装入 rdi、rsi、rdx、r10、r8、r9
; 第 3 步：执行 `syscall` 指令 -> CPU 切换到 ring 0
; 第 4 步：内核校验参数、执行、再切回 ring 3
; 第 5 步：返回值在 rax 中（出错时为负值，即 -errno）

; 示例：write(1, "hello\n", 6) —— 写入 stdout
section .data
    msg db "hello", 0x0a    ; "hello\n"

section .text
    global _start
_start:
    mov rax, 1          ; 系统调用号 1 = write
    mov rdi, 1          ; 参数1: fd = 1 (stdout)
    mov rsi, msg        ; 参数2: 缓冲区指针
    mov rdx, 6          ; 参数3: 字节数
    syscall             ; 调用内核

    mov rax, 60         ; 系统调用号 60 = exit
    xor rdi, rdi        ; 参数1: 退出码 = 0
    syscall
```

**必需的系统调用参考（x86-64 Linux）：**

| 系统调用 | 编号 | 签名 |
|---------|--------|-----------|
| `read` | 0 | `read(fd, buf, count)` |
| `write` | 1 | `write(fd, buf, count)` |
| `open` | 2 | `open(filename, flags, mode)` |
| `close` | 3 | `close(fd)` |
| `stat` | 4 | `stat(filename, statbuf)` |
| `mmap` | 9 | `mmap(addr, len, prot, flags, fd, offset)` |
| `mprotect` | 10 | `mprotect(addr, len, prot)` |
| `munmap` | 11 | `munmap(addr, len)` |
| `brk` | 12 | `brk(addr)` —— 堆增长 |
| `fork` | 57 | `fork()` |
| `execve` | 59 | `execve(filename, argv, envp)` |
| `exit` | 60 | `exit(error_code)` |
| `socket` | 41 | `socket(family, type, protocol)` |
| `connect` | 42 | `connect(fd, addr, addrlen)` |
| `accept` | 43 | `accept(fd, addr, addrlen)` |

完整参考：https://syscall.sh —— 把它加进书签。你会一直用到它。

**跟踪任何程序的系统调用：**
```bash
# 打印一个程序发起的每一次系统调用，含参数与返回值
strace /bin/ls

# 按 PID 附加到运行中的进程
strace -p [pid]

# 只过滤特定系统调用
strace -e trace=open,read,write /bin/cat /etc/passwd

# 显示在每个系统调用中花费的时间
strace -c /bin/ls
```

---

### 1.4 文件系统

**在 Linux 里一切都是文件。** 设备、套接字、管道、进程（/proc）、硬件（/dev）—— 全都通过文件接口（open/read/write/close）暴露出来。

**文件系统层次结构（这些路径要熟记）：**
```
/               根
/bin            基本二进制文件（ls、cat、sh）
/sbin           系统二进制文件（fdisk、ifconfig）
/etc            配置文件（/etc/passwd、/etc/shadow、/etc/hosts）
/home/username  用户主目录
/root           root 用户主目录
/tmp            临时文件（全局可写；经典攻击面）
/var            可变数据（日志在 /var/log/、邮件、假脱机）
/proc           虚拟文件系统：实时的内核/进程数据（不落盘）
/sys            虚拟文件系统：硬件/驱动信息
/dev            设备文件（disk、null、random、urandom、tty）
/lib            共享库
/usr/lib        更多共享库
/opt            可选的第三方软件
```

**进攻工作涉及的关键文件（背下来）：**
```bash
/etc/passwd        # 用户账户（用户名、UID、GID、主目录、shell）
/etc/shadow        # 口令哈希（只有 root 可读）
/etc/hosts         # 静态主机名/IP 映射
/etc/crontab       # 系统级 cron 任务（提权目标）
/etc/sudoers       # 谁能以 root 身份执行什么（sudo 配置）
/etc/ssh/          # SSH 服务配置与主机密钥
~/.ssh/            # 用户 SSH 密钥（authorized_keys、id_rsa）
~/.bash_history    # 命令历史（含口令、路径、线索）
/var/log/auth.log  # 认证日志（Ubuntu）/ /var/log/secure（RHEL）
/var/log/syslog    # 系统日志
/tmp/              # 全局可写；用来投放工具
```

**文件权限 —— 一眼读懂：**
```bash
# ls -la 的输出：
# -rwxr-xr-- 1 root staff 4096 Jan 1 00:00 filename
#  rwx r-x r--
#  属主 属组 其他

# 用数字读权限：
# r=4, w=2, x=1
# rwxr-xr-- = 754
# rw-r--r-- = 644（典型文件）
# rwx------ = 700（只有属主能做任何事）
# rwxr-xr-x = 755（典型可执行文件）

# SUID 位：设置在一个可执行文件上时，它以文件属主的身份运行，而不是调用者
# ls -la 在属主位上显示 's' 而不是 'x'：
# -rwsr-xr-x  （设置了 SUID —— 若属主是 root，则无论谁调用都以 root 运行）

# 找出系统上所有 SUID 二进制：
find / -perm -4000 -type f 2>/dev/null
```

---

### 1.5 /proc 文件系统

`/proc` 是一个虚拟文件系统 —— 它不存在于磁盘上。内核动态生成它的内容。它是 Linux 上最有用的调试与侦察接口。

```bash
# 针对你自己的 shell 进程（$$ = 当前 shell 的 PID）
cat /proc/$$/maps         # shell 进程的虚拟内存映射
cat /proc/$$/status       # 名称、状态、PID、PPID、UID、GID、内存占用
ls -la /proc/$$/fd/       # 打开的文件描述符
cat /proc/$$/cmdline      # 命令行（以 null 字节分隔）
cat /proc/$$/environ      # 环境变量

# 系统级信息
cat /proc/cpuinfo         # CPU 详情（架构、特性、标志）
cat /proc/meminfo         # 内存统计
cat /proc/net/tcp         # 活动 TCP 连接（十六进制地址与端口）
cat /proc/net/udp         # 活动 UDP 连接
cat /proc/loadavg         # 系统平均负载
cat /proc/version         # 内核版本字符串
cat /proc/sys/kernel/randomize_va_space  # ASLR 设置（0=关, 1=部分, 2=全开）
```

**练习：** 打开一个文本编辑器（gedit、nano）。用 `ps aux | grep gedit` 找到它的 PID。读它的 `/proc/[pid]/maps`。指出：编辑器的代码在哪？libc 在哪？栈在哪？堆在哪？

---

### 第1节 资源

| 资源 | 类型 | 费用 | 说明 |
|----------|------|------|-------|
| [Operating Systems: Three Easy Pieces (OSTEP)](https://pages.cs.wisc.edu/~remzi/OSTEP/) | 免费书 | 免费 | 最好的操作系统教科书。对话式笔调。读进程、虚拟内存、并发这几章。 |
| [Linux Kernel Labs](https://linux-kernel-labs.github.io/) | 教程 | 免费 | 讲得很深。想要更多时就把它当参考。 |
| `man 2 syscall` | 手册页 | 免费 | 读它。然后读 `man 2 fork`、`man 2 execve`、`man 2 mmap`。手册页是完整的。 |
| [The Linux Programming Interface (Kerrisk)](https://man7.org/tlpi/) | 书 | 约 70 美元 | Linux 系统编程的权威参考。阶段 0 可选，最终必备。 |

---

## 7. 第1B节：Bash 脚本基础

**时长：** 5-6 周（第 1-6 周）| **并行于：** 操作系统基础、C 编程

> **从第 1 周就开始。让它与其他一切并行。这不是可选项。**
>
> Bash 在进攻工作中每天都会用到：封装工具、解析输出、自动化侦察、处理日志文件、编写投递脚本。不会 Bash 就像一个不会用卷尺的木匠 —— 如果你不能高效工作，其他技能都无从谈起。

---

### 1B.1 最基础的部分

```bash
#!/bin/bash

# 变量：= 两边不能有空格
name="Sagar Biswas"
port=4444
echo "Name: $name"
echo "Port: ${port}"
echo "Port+1: $((port + 1))"

# 字符串
greeting="Hello, $name"      # 双引号：变量会展开
literal='No $expansion here'  # 单引号：不展开

# 命令替换：把命令的输出捕获到变量里
current_user=$(whoami)
current_dir=$(pwd)
file_count=$(ls /etc | wc -l)

echo "User: $current_user, Dir: $current_dir, /etc files: $file_count"
```

---

### 1B.2 管道与重定向：最重要的 Bash 概念

```bash
# 重定向
command > file.txt        # 把 stdout 重定向到文件（覆盖）
command >> file.txt       # 把 stdout 重定向到文件（追加）
command 2> errors.txt     # 把 stderr 重定向到文件
command 2>&1              # 把 stderr 重定向到 stdout
command > out.txt 2>&1    # 把 stdout 和 stderr 都重定向到文件
command < input.txt       # 从文件读取 stdin

# 管道：左边的 stdout 成为右边的 stdin
cat /etc/passwd | grep bash
ps aux | grep python | awk '{print $2}' | head -5
cat access.log | sort | uniq -c | sort -rn | head -20

# /dev/null：丢弃你不需要的输出
command 2>/dev/null       # 抑制错误消息
command > /dev/null 2>&1  # 抑制全部输出

# tee：把输出同时送到文件 AND stdout
nmap 192.168.1.0/24 | tee scan.txt
```

---

### 1B.3 文本处理三件套：grep、awk、sed

掌握这三个工具。进攻工作中 90% 的文本处理任务都由它们完成。

#### grep —— 查找匹配某个模式的行

```bash
grep "pattern" file.txt           # 打印匹配模式的行
grep -i "pattern" file.txt        # 忽略大小写
grep -r "pattern" /directory/     # 递归
grep -n "pattern" file.txt        # 显示行号
grep -v "pattern" file.txt        # 反转：打印不匹配的行
grep -E "error|warning|critical" /var/log/syslog  # OR 匹配

# 实战中的进攻用法
grep -r "password" /var/www/ 2>/dev/null
grep -r "api_key\|secret\|token" . 2>/dev/null
grep -E "[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}" file.txt
cat /etc/passwd | grep -v "nologin\|false"
```

#### awk —— 字段提取与模式处理

```bash
# 默认字段分隔符：空白
awk '{print $1}' file.txt         # 每行的第一个字段
awk '{print $1, $3}' file.txt     # 第 1 和第 3 个字段
awk '{print $NF}' file.txt        # 最后一个字段

# 用 -F 指定字段分隔符
awk -F: '{print $1}' /etc/passwd           # 打印用户名
awk -F: '{print $1, $3}' /etc/passwd       # 用户名和 UID
awk -F: '$3 == 0' /etc/passwd              # 等同于 root 的账户
awk -F: '$3 >= 1000 {print $1}' /etc/passwd  # 普通用户账户

# 算术
awk '{sum += $1} END {print sum}' numbers.txt    # 对一列求和
awk '{count[$1]++} END {for(k in count) print count[k], k}' access.log

# 实战中的进攻用法
ps aux | awk '{print $2, $11}'
ss -tnp | awk 'NR>1 {print $4, $6}'
cat /etc/passwd | awk -F: '{print $1":"$3":"$6}'
```

#### sed —— 流编辑器

```bash
sed 's/old/new/' file.txt          # 每行替换第一处
sed 's/old/new/g' file.txt         # 每行替换全部
sed -i 's/old/new/g' file.txt      # 原地编辑
sed '/^#/d' file.txt               # 删除注释行
sed '/^$/d' file.txt               # 删除空行
sed -n '5,10p' file.txt            # 打印第 5-10 行

# 实战
cat /etc/hosts | sed '/^#/d' | sed '/^$/d'
sed 's/\r//' windows_file.txt      # 去掉 Windows 回车符
```

---

### 1B.4 控制流

```bash
#!/bin/bash

# if/elif/else
if [ -f "/etc/passwd" ]; then
    echo "File exists"
elif [ -d "/etc/shadow" ]; then
    echo "It is a directory"
else
    echo "Neither"
fi

# 常用测试运算符：
# [ -f file ]       文件存在且是普通文件
# [ -d dir ]        目录存在
# [ -r file ]       文件可读
# [ -x file ]       文件可执行
# [ -z "$var" ]     字符串为空
# [ "$a" = "$b" ]   字符串相等
# [ "$n" -gt 5 ]    整数大于

# for 循环
for i in 1 2 3 4 5; do
    echo "Number: $i"
done

# 遍历文件中的行
while IFS= read -r line; do
    echo "Line: $line"
done < hosts.txt

# 遍历命令输出
for pid in $(pgrep python); do
    echo "Python process: $pid"
    cat /proc/$pid/cmdline | tr '\0' ' '
    echo
done
```

---

### 1B.5 函数与脚本结构

```bash
#!/bin/bash
# 最佳实践的脚本结构

set -euo pipefail
# -e：命令失败时立即退出
# -u：把未定义变量当作错误
# -o pipefail：管道中任一命令失败则整条管道失败
# 每一个严肃的 Bash 脚本都应该以这三行开头。

check_root() {
    if [ "$EUID" -ne 0 ]; then
        echo "[-] Must run as root" >&2
        exit 1
    fi
    echo "[+] Running as root"
}

scan_host() {
    local host="$1"
    local port="$2"
    echo "[*] Scanning $host:$port"
    nc -z -w 2 "$host" "$port" && echo "[+] Open" || echo "[-] Closed"
}

main() {
    check_root
    local target="${1:-192.168.1.1}"
    for port in 22 80 443 445 3389; do
        scan_host "$target" "$port"
    done
}

main "$@"
```

---

### 1B.6 数组与实用模式

```bash
#!/bin/bash

# 数组
targets=("192.168.1.1" "192.168.1.2" "10.0.0.5")
echo "First: ${targets[0]}"
echo "All: ${targets[@]}"
echo "Count: ${#targets[@]}"
targets+=("10.0.0.10")

# 遍历数组
for ip in "${targets[@]}"; do
    ping -c 1 -W 1 "$ip" &>/dev/null && echo "[+] $ip is up" || echo "[-] $ip down"
done

# 从文件读取数组
mapfile -t hosts < hosts.txt

# 字符串操作
filename="/path/to/file.txt"
echo "${filename##*/}"    # Filename only: file.txt
echo "${filename%.*}"     # Without extension: /path/to/file
echo "${filename##*.}"    # Extension only: txt

# 并行执行
for ip in "${targets[@]}"; do
    nmap -sn "$ip" &
done
wait
echo "Scan complete"
```

---

### 1B.7 Makefile 基础

```makefile
# 关键：缩进必须是 TAB 字符，不能用空格。

CC = gcc
CFLAGS = -Wall -Wextra -g -O0
TARGET = shell
SRCS = main.c utils.c syscalls.c
OBJS = $(SRCS:.c=.o)

all: $(TARGET)

$(TARGET): $(OBJS)
	$(CC) $(CFLAGS) -o $(TARGET) $(OBJS)
	@echo "[+] Built $(TARGET)"

%.o: %.c
	$(CC) $(CFLAGS) -c -o $@ $<

.PHONY: all clean debug install

clean:
	rm -f $(TARGET) $(OBJS)
	@echo "[*] Cleaned"

debug: CFLAGS += -DDEBUG -fsanitize=address,undefined
debug: $(TARGET)
```

### 1B.8 要动手做什么（第1B节）

**练习 1：** 写 `port_check.sh`：从文件读取 IP，用 `nc` 检查 22 和 80 端口，把结果写入 `results.txt`。

**练习 2：** 解析 `/var/log/auth.log`，提取失败的 SSH 登录尝试，按来源 IP 计数，按次数降序排序，打印前 10 名。

**练习 3：** 为一个两文件的 C 项目写 Makefile，包含目标：`all`、`clean`、`debug` 和 `install`。

**练习 4：** 递归找出某个目录下所有 `.c` 文件，统计每个文件的行数，按行数排序打印（从大到小）。

**练习 5：** 用 `tail -f` 实时监控一个日志文件，只要有匹配 "FAILED" 或 "ERROR" 的行出现，就向 stderr 报警。

### 第1B节 资源

| 资源 | 类型 | 费用 | 说明 |
|----------|------|------|-------|
| [Bash scripting cheatsheet](https://devhints.io/bash) | 参考 | 免费 | 最好的速查表。收藏它。 |
| [Shell Scripting Tutorial](https://www.shellscript.sh/) | 教程 | 免费 | 对初学者友好。把它过一遍。 |
| `man bash` | 手册页 | 免费 | 权威参考。很长，但完整。 |
| [CommandLineFu](https://www.commandlinefu.com/) | 示例 | 免费 | 用来找灵感的单行命令。每天读。 |
| [The Art of Command Line](https://github.com/jlevy/the-art-of-command-line) | 指南 | 免费 | 中级水平。阶段 1 期间回头再看。 |

---

## 8. 第2节：C 编程

**时长：** 10-12 周（第 1-12 周）| **并行于：** 操作系统基础、Bash

### 为什么 C 不可绕过

Linux 内核用 C 写。Windows 内核用 C 写。每一种漏洞利用原语 —— 缓冲区溢出、use-after-free、格式化字符串 —— 都是 C 概念。shellcode 与 C 运行时约定打交道。每一个值得理解的安全工具（glibc、OpenSSL、内核本身）都是 C。不会 C，就意味着对这一切的理解都停留在表面。

---

### 2.1 基础：数据、变量、类型

```c
#include <stdio.h>    // Standard I/O: printf, scanf, fgets, fopen
#include <stdlib.h>   // malloc、free、exit、atoi
#include <string.h>   // memcpy、memset、strlen、strcpy（危险 —— 要知道为什么）
#include <stdint.h>   // 定宽整数：uint8_t、uint32_t、uint64_t

// 基本类型及其大小（x86-64 Linux）：
// 类型             大小    范围
// char             1 字节  -128 到 127（unsigned 则为 0-255）
// short            2 字节
// int              4 字节  -2,147,483,648 到 2,147,483,647
// long             8 字节（64 位 Linux 上；Windows 64 位上却是 4 字节！）
// long long        8 字节
// float            4 字节
// double           8 字节
// 指针             8 字节（64 位上 —— 这一点至关重要）

// 当大小重要时用定宽类型（在安全工作中，它总是重要）：
uint8_t  byte_val  = 0xFF;
uint16_t word_val  = 0xDEAD;
uint32_t dword_val = 0xDEADBEEF;
uint64_t qword_val = 0xDEADBEEFCAFEBABE;

// 整数溢出 —— 经典 bug，也是经典利用原语：
uint8_t a = 255;
a++;                    // a = 0（无符号溢出：回绕 —— 定义良好的行为）
printf("%u\n", a);      // prints 0

int8_t b = 127;
b++;                    // b = -128（有符号溢出：C 标准中属未定义行为）
printf("%d\n", b);      // prints -128 on most compilers but the optimizer can remove this
```

---

### 2.2 指针：一切的核心

在 C 里如果你只懂一样东西，就懂这一节。每一种内存破坏型漏洞利用归根结底都是指针操作。

```c
#include <stdio.h>
#include <stdint.h>

int main() {
    int x = 42;
    int *p = &x;     // p 是指向 int 的指针；&x 给出 x 的地址

    printf("Value of x: %d\n", x);
    printf("Address of x: %p\n", (void*)&x);
    printf("*p (dereferenced): %d\n", *p);  // 42

    *p = 100;   // 通过指针写入：改变 x 的值
    printf("x is now: %d\n", x);  // 100

    // 指针算术：按所指类型的大小前进
    int arr[5] = {10, 20, 30, 40, 50};
    int *ap = arr;       // 指向 arr[0]

    printf("%d\n", *(ap + 1)); // 20 -- advances by sizeof(int) = 4 bytes
    printf("%d\n", arr[3]);    // 40
    printf("%d\n", *(arr + 3));// 40 -- same thing: array indexing IS pointer arithmetic

    // 指向指针的指针
    int **pp = &p;
    printf("%d\n", **pp);  // 42 (double dereference)

    // void 指针：可指向任何类型；解引用前必须强转
    void *vp = &x;
    printf("%d\n", *(int*)vp);

    // NULL 指针：绝对不要解引用它
    int *null_p = NULL;
    if (null_p == NULL) {
        printf("Null pointer -- do not dereference\n");
    }

    // 64 位上的指针大小：
    printf("sizeof(int): %zu\n", sizeof(int));       // 4
    printf("sizeof(int*): %zu\n", sizeof(int*));     // 8 on 64-bit
    printf("sizeof(void*): %zu\n", sizeof(void*));   // 8 on 64-bit
    // 在 64 位系统上，所有指针都是 8 字节，无论它们指向什么。

    return 0;
}
```

**把这个画出来。真笔真纸。每次你对指针感到困惑的时候。** 为变量画方框，为指针画箭头。箭头就是指针。它指向的方框就是数据。一直画到你能不用画就把它想象出来。

---

### 2.3 栈内存与堆内存

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

// 栈：自动、有限（默认约 8MB）、快速、自动清理
void stack_example() {
    int x = 10;              // 在栈上
    char buf[256];           // 栈上的 256 字节
    // 这个函数返回时，栈内存就不存在了。
    // 绝不要返回指向栈内存的指针 —— 那是未定义行为。
}

// 堆：动态、容量大（受内存限制）、必须手动管理
void heap_example() {
    int *p = (int*)malloc(sizeof(int));
    if (p == NULL) {
        fprintf(stderr, "malloc failed\n");
        exit(1);
    }
    *p = 42;
    printf("Heap value: %d\n", *p);
    free(p);
    p = NULL;  // 释放后置空 —— 防止 use-after-free

    int *arr = (int*)calloc(100, sizeof(int));  // 分配并清零
    if (!arr) { exit(1); }
    free(arr);

    char *buf = (char*)malloc(64);
    if (!buf) { exit(1); }
    strcpy(buf, "hello");
    buf = (char*)realloc(buf, 256);
    if (!buf) { exit(1); }
    strcat(buf, " world");
    free(buf);
}

// 你在阶段 3 一定会用到的内存错误：
void memory_errors_demo() {
    // 1. 缓冲区溢出：写到分配范围之外
    char *buf = (char*)malloc(10);
    strcpy(buf, "this is more than 10 characters");  // 溢出

    // 2. use-after-free：释放之后继续使用内存
    char *p = (char*)malloc(32);
    free(p);
    p[0] = 'A';  // USE-AFTER-FREE —— 可利用

    // 3. double free：同一指针释放两次
    char *q = (char*)malloc(32);
    free(q);
    free(q);     // DOUBLE FREE —— 可利用的堆破坏

    // 4. 内存泄漏：分配后不释放
    for (int i = 0; i < 1000; i++) {
        char *leak = (char*)malloc(1024);
        // 从不释放
    }
}

int main() {
    heap_example();
    return 0;
}
```

### 2.4 内存错误检测：Valgrind 与 AddressSanitizer

**两个工具都要用。它们捕获不同类别的 bug。**

**Valgrind** 很彻底，能用于已有的二进制，但很慢（约 20 倍）：
```bash
gcc -g -O0 program.c -o program
valgrind --leak-check=full --show-leak-kinds=all --track-origins=yes ./program
```

**AddressSanitizer（ASan）** 很快（约 2 倍开销），能捕获栈破坏，并且对许多类别的 bug 给出更好的错误信息。**开发期间用这个：**

```bash
# 用 ASan 和 UBSan 编译（UBSan 捕获未定义行为）
gcc -fsanitize=address,undefined -g -O0 program.c -o program_asan
./program_asan

# 堆缓冲区溢出的 ASan 输出示例：
# ==12345==ERROR: AddressSanitizer: heap-buffer-overflow on address 0x...
# WRITE of size 1 at 0x... thread T0
#     #0 0x... in vulnerable_function /home/user/program.c:42
# 它告诉你：哪个文件、哪一行、什么类型的破坏。非常精确。
```

**什么时候用哪个：**

| 工具 | 何时使用 |
|------|----------|
| ASan + UBSan | 开发期间始终启用（加进 CFLAGS） |
| Valgrind | 查找泄漏；审计已有的已编译二进制 |
| 两者都用 | 在把任何项目标记为“完成”之前 |

**带 sanitizer 的默认 Makefile：**
```makefile
CC = gcc
CFLAGS_BASE = -Wall -Wextra -g -O0
CFLAGS = $(CFLAGS_BASE) -fsanitize=address,undefined

all: $(TARGET)

# 不带 sanitizer 构建（用于性能测试）：
release: CFLAGS = $(CFLAGS_BASE) -O2
release: $(TARGET)
```

---

### 2.5 C 中的字符串

```c
#include <stdio.h>
#include <string.h>
#include <stdlib.h>

int main() {
    // 栈上分配的字符串（可写、大小固定）
    char buf[32] = "hello";
    buf[0] = 'H';           // 可以：可写
    printf("%s\n", buf);    // "Hello"

    // 安全的字符串函数
    strncpy(buf, "a very long string...", sizeof(buf) - 1);
    buf[sizeof(buf) - 1] = '\0';  // strncpy 可能不补 null 结尾；手动补上

    snprintf(buf, sizeof(buf), "Value: %d", 42);  // 带长度限制的格式化

    // 内存函数（作用于原始字节 —— 不会在 null 字节处停下）
    memset(buf, 0, sizeof(buf));
    memset(buf, 0x41, 16);      // 用 'A'（0x41）填满前 16 字节
    memcpy(buf, "hello", 5);    // 复制 5 字节

    return 0;
}
```

**为什么 strcpy/gets/sprintf 危险（对阶段 3 至关重要）：**
```c
// 这是教科书式的缓冲区溢出：
void vulnerable(char *input) {
    char buf[64];
    strcpy(buf, input);  // 如果 input 超过 64 字节就溢出：覆盖栈
}
// 在阶段 3，你控制用什么覆盖栈。
// 保存的返回地址就紧挨在缓冲区之后。
// 用一个你控制的地址覆盖它 = 代码执行。
// 这是基于栈的缓冲区溢出利用的地基。
```

---

### 2.6 函数、结构体与文件 I/O

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <stdint.h>

typedef struct {
    char username[32];
    uint32_t uid;
    uint32_t gid;
    char home[128];
    char shell[64];
} User;

// 函数指针：函数就是地址；你可以把它们存进指针
typedef int (*CompareFunc)(const void*, const void*);

int compare_ints(const void *a, const void *b) {
    return *(int*)a - *(int*)b;
}

void file_operations() {
    FILE *f = fopen("output.txt", "w");
    if (!f) { perror("fopen"); exit(1); }
    fprintf(f, "Line %d: %s\n", 1, "hello");
    fclose(f);

    // 读取整个二进制文件
    FILE *bf = fopen("/bin/ls", "rb");
    if (!bf) { perror("fopen"); exit(1); }

    fseek(bf, 0, SEEK_END);
    long size = ftell(bf);
    fseek(bf, 0, SEEK_SET);

    uint8_t *data = (uint8_t*)malloc(size);
    fread(data, 1, size, bf);
    printf("Magic: %02X %02X %02X %02X\n",
           data[0], data[1], data[2], data[3]);
    // ELF：7F 45 4C 46
    free(data);
    fclose(bf);
}

int main() {
    User u = {
        .username = "root",
        .uid = 0,
        .gid = 0,
        .home = "/root",
        .shell = "/bin/bash"
    };
    printf("User: %s (uid=%u)\n", u.username, u.uid);

    int arr[] = {5, 2, 8, 1, 9, 3};
    qsort(arr, 6, sizeof(int), compare_ints);

    file_operations();
    return 0;
}
```

---

### 2.7 C 中直接发起系统调用

```c
#include <sys/syscall.h>
#include <unistd.h>
#include <stdio.h>

// 方法 1：libc 里的 syscall() 封装
int main() {
    syscall(SYS_write, 1, "hello via syscall\n", 18);
    syscall(SYS_exit, 0);
    return 0;
}
```

```c
// 方法 2：内联汇编（直接系统调用，完全不用 libc）
#include <stdint.h>

static long raw_write(int fd, const void *buf, size_t count) {
    long ret;
    __asm__ volatile (
        "syscall"
        : "=a" (ret)
        : "0" (1),
          "D" ((long)fd),
          "S" (buf),
          "d" ((long)count)
        : "rcx", "r11", "memory"
    );
    return ret;
}

void raw_exit(int code) {
    __asm__ volatile (
        "syscall"
        :
        : "a" (60), "D" ((long)code)
        :
    );
}

int main() {
    raw_write(1, "direct syscall\n", 15);
    raw_exit(0);
    return 0;
}
```

---

### 第2节 资源

| 资源 | 类型 | 费用 | 说明 |
|----------|------|------|-------|
| [The C Programming Language (K&R)](https://en.wikipedia.org/wiki/The_C_Programming_Language) | 书 | 约 40 美元 | 整本读完。经典。必备。 |
| [Beej's Guide to C Programming](https://beej.us/guide/bgc/) | 免费书 | 免费 | 比 K&R 更好上手。如果 K&R 太密，先读这本。 |
| [CS50](https://cs50.harvard.edu/x/) | 课程 | 免费 | 哈佛的计算机入门课。扎实的 C 基础。 |
| [Learn C the Hard Way](https://learncodethehardway.org/c/) | 书/课程 | 约 30 美元 | 以练习为中心。适合动手构建而不只是阅读。 |

### 要动手做什么（第2节）

1. **链表：** 插入、删除、查找、反转 —— 完整实现
2. **栈与队列：** 都用 C 和动态分配实现
3. **直接系统调用程序：** 不引入任何 libc 头文件，完成 write、open、read、close
4. **字符串解析器：** 不用 strtok 按分隔符拆分字符串（自己实现一个）
5. **二进制文件检查器：** 读一个文件，用十六进制 + ASCII 打印前 16 字节（像 xxd 那样）

---

## 9. 第3节：Python 脚本

**时长：** 8-10 周（第 9-18 周）| **并行于：** 网络、汇编

### 为什么在 C 之外还要学 Python

C 教你看清机器实际在做什么。Python 让你能快速地把那份理解付诸行动。漏洞利用投递、模糊测试框架、网络扫描器、二进制解析器、自动化脚本 —— Python 都能用少得多的代码完成。两样都要：C 负责深度，Python 负责覆盖广度。

---

### 3.1 Python 基础

```python
# Python 3.10+（Ubuntu 22.04 自带 3.10 或 3.11）

# 类型
x: int = 42
pi: float = 3.14159
msg: str = "hello"
data: bytes = b"\x41\x42\x43"
data_hex: bytes = bytes.fromhex("414243")

# f-string
addr = 0xdeadbeef
print(f"Address: {addr:#010x}")
print(f"Hex bytes: {data.hex()}")
print(f"Decimal: {int.from_bytes(b'\x02\x01', 'little')}")

# 列表
targets = ["192.168.1.1", "10.0.0.5"]
targets.append("172.16.0.1")
filtered = [t for t in targets if t.startswith("192")]

# 字典
findings = {"host": "192.168.1.1", "port": 22, "service": "ssh"}
findings["version"] = "OpenSSH_8.9"
for key, value in findings.items():
    print(f"  {key}: {value}")

# 集合
seen_ips = set()
seen_ips.add("10.0.0.1")
seen_ips.add("10.0.0.1")  # 重复项 —— 静默忽略
print(len(seen_ips))        # 1
```

---

### 3.2 二进制处理：struct 模块

struct 是解析二进制协议、文件格式和网络数据包的基础。

```python
import struct

# 格式字符串：
# B = uint8， b = int8
# H = uint16， h = int16
# I = uint32， i = int32
# Q = uint64， q = int64
# < = 小端（x86 原生）
# > = 大端（网络字节序）

# 打包一个结构体
payload = struct.pack("<IHH", 0xdeadbeef, 0x0001, 0x0002)
print(payload.hex())  # efbeadde01000200

# 解包
magic, version, flags = struct.unpack("<IHH", payload)
print(f"magic={magic:#010x}, version={version}, flags={flags}")

# 解析 ELF 头（前 64 字节）
with open("/bin/ls", "rb") as f:
    elf_header = f.read(64)

ei_class = elf_header[4]   # 1=32 位，2=64 位
ei_data  = elf_header[5]   # 1=小端，2=大端

print(f"Class: {'64-bit' if ei_class == 2 else '32-bit'}")
print(f"Endian: {'little' if ei_data == 1 else 'big'}")

e_type, e_machine, e_version, e_entry = struct.unpack_from("<HHIQ", elf_header, 16)
print(f"Machine: {e_machine:#06x}, Entry: {e_entry:#018x}")
```

---

### 3.3 套接字：TCP 客户端与服务端

```python
import socket

# TCP 客户端
def tcp_client(host: str, port: int, data: bytes) -> bytes:
    with socket.socket(socket.AF_INET, socket.SOCK_STREAM) as s:
        s.settimeout(5.0)
        s.connect((host, port))
        s.sendall(data)
        response = b""
        while True:
            chunk = s.recv(4096)
            if not chunk:
                break
            response += chunk
    return response

# TCP 服务端
def tcp_server(host: str, port: int):
    with socket.socket(socket.AF_INET, socket.SOCK_STREAM) as srv:
        srv.setsockopt(socket.SOL_SOCKET, socket.SO_REUSEADDR, 1)
        srv.bind((host, port))
        srv.listen(5)
        print(f"[*] Listening on {host}:{port}")
        while True:
            conn, addr = srv.accept()
            print(f"[+] Connection from {addr[0]}:{addr[1]}")
            with conn:
                data = conn.recv(4096)
                print(f"[<] {len(data)} bytes: {data[:64]}")
                conn.sendall(b"ACK\n")

# 端口扫描器
def scan_port(host: str, port: int, timeout: float = 0.5) -> bool:
    try:
        with socket.socket(socket.AF_INET, socket.SOCK_STREAM) as s:
            s.settimeout(timeout)
            return s.connect_ex((host, port)) == 0
    except Exception:
        return False

def port_scan(host: str, ports):
    print(f"[*] Scanning {host}")
    for port in ports:
        if scan_port(host, port):
            print(f"[+] {port}/tcp OPEN")
```

---

### 3.4 子进程与操作系统交互

```python
import subprocess
import shlex

def run_cmd(cmd: str):
    result = subprocess.run(
        shlex.split(cmd),
        capture_output=True,
        text=True,
        timeout=30
    )
    return result.returncode, result.stdout, result.stderr

rc, out, err = run_cmd("nmap -sV --open -p 22,80,443 192.168.1.1")
if rc == 0:
    for line in out.splitlines():
        if "open" in line.lower():
            print(f"[+] {line.strip()}")

# 流式输出（长时间运行的命令）
proc = subprocess.Popen(
    ["nmap", "-sn", "192.168.1.0/24"],
    stdout=subprocess.PIPE,
    stderr=subprocess.PIPE,
    text=True
)
for line in proc.stdout:
    print(line, end="")
proc.wait()
```

---

### 3.5 Scapy：数据包构造与分析

Scapy 是用来构造、发送和解析原始网络数据包的 Python 库。它是进攻性 Python 工作中操作数据包的黄金标准。

```bash
pip3 install scapy --break-system-packages
```

```python
from scapy.all import *

# 1. ICMP ping（需要 root）
def ping(target: str):
    pkt = IP(dst=target) / ICMP()
    reply = sr1(pkt, timeout=2, verbose=False)
    if reply:
        print(f"[+] {target} up -- TTL={reply.ttl}")
    else:
        print(f"[-] {target} no response")

# 2. ARP 扫描（发现本地子网内的存活主机）
def arp_scan(network: str):
    answered, _ = srp(
        Ether(dst="ff:ff:ff:ff:ff:ff") / ARP(pdst=network),
        timeout=2, verbose=False
    )
    for sent, received in answered:
        print(f"[+] {received.psrc:15s}  {received.hwsrc}")

# 3. TCP SYN 扫描（半开 —— 不完成握手）
def syn_scan(target: str, ports: list) -> list:
    open_ports = []
    for port in ports:
        pkt = IP(dst=target) / TCP(dport=port, flags="S")
        reply = sr1(pkt, timeout=1, verbose=False)
        if reply and reply.haslayer(TCP):
            if reply[TCP].flags & 0x12:     # SYN+ACK = 开放
                open_ports.append(port)
                send(IP(dst=target) / TCP(dport=port, flags="R"), verbose=False)
    return open_ports

# 4. 数据包嗅探
def packet_callback(pkt):
    if pkt.haslayer(IP):
        src, dst = pkt[IP].src, pkt[IP].dst
        print(f"{src:15s} -> {dst:15s}", end="")
        if pkt.haslayer(TCP):
            print(f"  TCP {pkt[TCP].sport} -> {pkt[TCP].dport}", end="")
        elif pkt.haslayer(UDP):
            print(f"  UDP {pkt[UDP].sport} -> {pkt[UDP].dport}", end="")
        print()

# sniff(iface="eth0", prn=packet_callback, count=50)

# 5. 读取 pcap 文件
def analyze_pcap(pcap_file: str):
    packets = rdpcap(pcap_file)
    print(f"[*] {len(packets)} packets from {pcap_file}")
    for i, pkt in enumerate(packets[:10]):
        print(f"  [{i}] {pkt.summary()}")
```

**Scapy 的层分隔符：** 用 `/` 堆叠各层：`IP() / TCP() / Raw(b"data")`

| 任务 | 调用 |
|------|------|
| 发送 L3（IP）数据包 | `send(pkt)` |
| 发送 L2（以太网）数据包 | `sendp(pkt)` |
| 发送并接收一个响应 | `sr1(pkt)` |
| 发送 L2 并接收 | `srp(pkt)` |
| 嗅探实时流量 | `sniff(iface, prn, count)` |
| 读取 pcap 文件 | `rdpcap(file)` |
| 写入 pcap 文件 | `wrpcap(file, packets)` |

---

### 3.6 文件与数据处理

```python
import json, re, hashlib

def parse_auth_log(logfile: str) -> dict:
    failed: dict = {}
    pattern = re.compile(r"Failed password for .+ from (\d+\.\d+\.\d+\.\d+)")
    with open(logfile, "r", errors="replace") as f:
        for line in f:
            m = pattern.search(line)
            if m:
                ip = m.group(1)
                failed[ip] = failed.get(ip, 0) + 1
    return dict(sorted(failed.items(), key=lambda x: -x[1]))

def hash_file(path: str) -> dict:
    h256 = hashlib.sha256()
    with open(path, "rb") as f:
        for chunk in iter(lambda: f.read(65536), b""):
            h256.update(chunk)
    return {"sha256": h256.hexdigest()}
```

### 第3节 资源

| 资源 | 类型 | 费用 |
|----------|------|------|
| [Automate the Boring Stuff with Python](https://automatetheboringstuff.com/) | 免费书 | 免费 |
| [Black Hat Python (Seitz/Arnold)](https://nostarch.com/black-hat-python2E) | 书 | 约 30 美元 |
| [Violent Python (TJ O'Connor)](https://www.amazon.com/dp/1597499579) | 书 | 约 30 美元 |
| [Scapy Documentation](https://scapy.readthedocs.io/) | 文档 | 免费 |
| [Python Docs: struct](https://docs.python.org/3/library/struct.html) | 文档 | 免费 |

---

## 10. 第4节：网络基础

**时长：** 8-10 周（第 9-18 周）| **并行于：** Python、汇编

### 为什么学网络

每一个网络服务都是一个从套接字读取数据的程序。每一个 Web 应用、API 和 VPN 都建立在需要你在字节层面掌握的那些协议之上。这一节结束时，Wireshark 对你应该像文本编辑器一样顺手。

---

### 4.1 OSI 模型与 TCP/IP 协议栈

<div align="center">
<table><tr><td>

<img src="../assets/diagrams/PHASE_0/3._The_OSI_Model_and_TCP-IP_Stack.png" alt="The OSI Model and TCP/IP Stack" width="400"/>

</td></tr></table>
</div>

发送 TCP 载荷时的帧结构：
```
[ 以太网头 | IP 头 | TCP 头 | 应用数据 ]
  14 字节     20 字节  20 字节   可变
```

---

### 4.2 IP 寻址：IPv4 与 IPv6

#### IPv4

```
192.168.1.100 = 11000000.10101000.00000001.01100100

CIDR： 192.168.1.0/24  = 主机 .1 到 .254，广播 .255

私有地址段：
  10.0.0.0/8       A 类私有
  172.16.0.0/12    B 类私有
  192.168.0.0/16   C 类私有
  127.0.0.0/8      回环
  169.254.0.0/16   链路本地（APIPA）
```

#### IPv6 —— 现在需要掌握的部分

IPv6 是 128 位，写成 8 组 4 位十六进制数字，以冒号分隔。

```
完整：       2001:0db8:85a3:0000:0000:8a2e:0370:7334
压缩：       2001:db8:85a3::8a2e:370:7334
             （:: = 一个或多个全零组；每个地址中只能使用一次）

关键地址：
  ::1              回环（= 127.0.0.1）
  fe80::/10        链路本地（在每个接口上自动配置）
  ff02::1          所有节点组播（本地链路）

命令：
  ip -6 addr show
  ping6 ::1
  ping6 -I eth0 fe80::...    # 链路本地必须指定接口
  ss -6 -tnp
  nmap -6 [target_ipv6]
```

**进攻相关性：** 双栈主机的 IPv6 防火墙规则往往更弱。邻居发现协议（NDP）取代 ARP，并带来新的攻击面（阶段 2）。许多组织对 IPv6 流量的监控不如 IPv4 那么严密。

---

### 4.3 TCP：三次握手

<div align="center">
<table><tr><td>

<img src="../assets/diagrams/PHASE_0/4._The_Three-Way_Handshake.png" alt="The TCP Three-Way Handshake" width="370"/>

</td></tr></table>
</div>

**TCP 标志位：**

| 标志 | 含义 |
|------|---------|
| SYN | 发起连接 |
| ACK | 确认已收到的数据 |
| FIN | 本方没有更多数据 |
| RST | 立即中止连接 |
| PSH | 立即把数据推给应用 |
| URG | 存在紧急数据 |

**SYN 扫描中的端口状态：**
- SYN -> SYN-ACK = **开放**
- SYN -> RST = **关闭**
- SYN -> 无响应 = **被过滤**

---

### 4.4 DNS：从查询到应答

<div align="center">
<table><tr><td>

<img src="../assets/diagrams/PHASE_0/5._From_Query_to_Answer.png" alt="DNS: From Query to Answer" width="750"/>

</td></tr></table>
</div>

**DNS 记录类型：**

| 类型 | 用途 |
|------|---------|
| A | IPv4 地址 |
| AAAA | IPv6 地址 |
| CNAME | 指向另一个名字的别名 |
| MX | 邮件服务器 |
| NS | 权威名称服务器 |
| TXT | 任意文本（SPF、DKIM、验证） |
| PTR | 反向 DNS（IP 到名字） |

```bash
dig example.com
dig example.com MX
dig @8.8.8.8 example.com
dig -x 93.184.216.34          # 反向 DNS
dig axfr example.com @ns1.example.com  # 尝试区域传送
dig +trace example.com        # 完整解析链
```

---

### 4.5 HTTP 基础

```bash
# 原始 HTTP/1.1 请求格式：
# GET /index.html HTTP/1.1\r\n
# Host: example.com\r\n
# User-Agent: Custom/1.0\r\n
# \r\n

echo -e "GET / HTTP/1.1\r\nHost: example.com\r\nConnection: close\r\n\r\n" \
    | nc example.com 80

curl -v http://example.com/
curl -v https://target.com/ --insecure
curl -H "X-Custom: value" -X POST -d '{"key":"val"}' http://target.com/api
```

**HTTP 方法：** GET、POST、PUT、DELETE、HEAD、OPTIONS、PATCH

**要掌握的状态码：**
- 200 OK | 301/302 重定向 | 400 错误请求 | 401 未授权
- 403 禁止访问 | 404 未找到 | 500 内部错误 | 503 不可用

---

### 4.6 Wireshark

```bash
sudo apt install wireshark tshark

# 抓包
sudo tcpdump -i eth0 -w capture.pcap

# 命令行分析
tshark -r capture.pcap
tshark -r capture.pcap -Y "http"
tshark -r capture.pcap -Y "dns" -T fields -e dns.qry.name
```

**关键显示过滤器：**

| 过滤器 | 显示内容 |
|--------|-------|
| `tcp` | 所有 TCP 流量 |
| `http` | 只有 HTTP |
| `dns` | 只有 DNS |
| `ip.addr == 10.0.0.1` | 指定 IP |
| `tcp.flags.syn == 1 and tcp.flags.ack == 0` | SYN 数据包 |
| `http contains "password"` | 载荷中包含 password 的 HTTP |
| `ipv6` | IPv6 流量 |
| `!arp and !dns` | 排除 ARP 与 DNS 噪声 |

---

### 第4节 资源

| 资源 | 类型 | 费用 |
|----------|------|------|
| [Beej's Guide to Network Programming](https://beej.us/guide/bgnet/) | 免费书 | 免费 |
| [Computer Networking: Top-Down Approach (Kurose/Ross)](https://gaia.cs.umass.edu/kurose_ross/) | 书 | 约 60 美元 |
| [Julia Evans -- DNS deep dives](https://jvns.ca/) | 博客 | 免费 |
| [Wireshark Documentation](https://www.wireshark.org/docs/) | 文档 | 免费 |
| [Practical Packet Analysis (Beale)](https://nostarch.com/packetanalysis3) | 书 | 约 30 美元 |

---

## 11. 第5节：x86-64 汇编

**时长：** 6-8 周（第 13-19 周）| **并行于：** Python、逆向基础

### 为什么汇编不可跳过

汇编是机器的母语。shellcode 就是汇编。缓冲区溢出利用操作的是栈 —— 一个汇编层面的概念。ROP 链是一串汇编 gadget。恶意软件在被理解之前都要被反编译回汇编。当 Ghidra 无法干净地反编译时，你去读汇编。这一节不能跳过。

---

### 5.1 寄存器：CPU 的工作记忆

CPU 在计算过程中无法访问内存。所有工作都在寄存器里完成。寄存器是 CPU 内部有名字的存储位置 —— 极快，但数量极少。

**x86-64 通用寄存器：**

```
64 位    32 位    16 位    8 位（高）  8 位（低）  惯常用途
rax      eax      ax       ah            al            返回值；累加器
rbx      ebx      bx       bh            bl            被调用者保存（跨调用保持）
rcx      ecx      cx       ch            cl            第 4 个参数；循环计数器
rdx      edx      dx       dh            dl            第 3 个参数；I/O 端口
rsi      esi      si                     sil           第 2 个参数；源字符串指针
rdi      edi      di                     dil           第 1 个参数；目的指针
rsp      esp      sp                     spl           栈指针（不要破坏）
rbp      ebp      bp                     bpl           基址指针（栈帧）
r8       r8d      r8w                    r8b           第 5 个参数
r9       r9d      r9w                    r9b           第 6 个参数
r10      r10d     r10w                   r10b          调用者保存；系统调用参数 4
r11      r11d     r11w                   r11b          调用者保存；系统调用返回值
r12-r15  ...                                           被调用者保存
rip                                                    指令指针（PC）
rflags                                                 标志位（ZF、CF、SF、OF、DF）
```

**关键标志位（RFLAGS）：**

| 标志 | 位 | 何时置位 |
|------|-----|----------|
| ZF（零标志） | 6 | 结果为 0 |
| CF（进位） | 0 | 无符号溢出或借位 |
| SF（符号） | 7 | 结果为负 |
| OF（溢出） | 11 | 有符号溢出 |
| DF（方向） | 10 | 字符串操作沿内存向低地址方向进行 |

---

### 5.2 必需指令

```nasm
section .text
    global _start

; 数据移动
mov  rax, 42          ; rax = 42  （立即数）
mov  rax, rbx         ; rax = rbx（寄存器到寄存器）
mov  rax, [rbx]       ; rax = *rbx（从内存加载）
mov  [rbx], rax       ; *rbx = rax（存入内存）
mov  [rbx + 8], rax   ; *(rbx+8) = rax（基址+偏移寻址）
lea  rax, [rbx + rcx*4 + 8]  ; rax = rbx + rcx*4 + 8 的地址（不访问内存）
xchg rax, rbx         ; 交换 rax 和 rbx
movzx rax, byte [rbx] ; 从内存取一个字节并零扩展到 rax
movsx rax, dword [rbx]; 从内存取一个双字并符号扩展到 rax

; 算术
add  rax, rbx         ; rax += rbx
sub  rax, rbx         ; rax -= rbx
imul rax, rbx         ; rax *= rbx（有符号）
idiv rbx              ; rdx:rax / rbx -> rax=商，rdx=余数
inc  rax              ; rax++（不设置 CF）
dec  rax              ; rax--
neg  rax              ; rax = -rax（二补码）

; 位运算
and  rax, rbx         ; rax &= rbx
or   rax, rbx         ; rax |= rbx
xor  rax, rbx         ; rax ^= rbx
xor  rax, rax         ; rax = 0（惯用法：清零寄存器最快的方式）
not  rax              ; rax = ~rax
shl  rax, 3           ; rax <<= 3（乘以 8）
shr  rax, 3           ; rax >>= 3（除以 8，无符号）
sar  rax, 3           ; rax >>= 3（除以 8，有符号 —— 保留符号位）

; 比较与跳转
cmp  rax, 10          ; 依据 (rax - 10) 设置标志位，不保存结果
test rax, rax         ; 若 rax==0 则设置 ZF（比 cmp rax, 0 代价更低）
je   label            ; 若 ZF=1 则跳转（相等/为零）
jne  label            ; 若 ZF=0 则跳转（不相等/非零）
jl   label            ; 小于则跳转（有符号：SF != OF）
jg   label            ; 大于则跳转（有符号）
jb   label            ; 低于则跳转（无符号）
ja   label            ; 高于则跳转（无符号）
jmp  label            ; 无条件跳转
jmp  rax              ; 间接跳转：跳到 rax 中的地址

; 栈操作（push 前 rsp 先减，pop 后 rsp 再加）
push rax              ; rsp -= 8; mem[rsp] = rax
pop  rbx              ; rbx = mem[rsp]; rsp += 8
push 0x1234           ; 压入立即数

; 函数调用
call function         ; push rip+5; jmp function
ret                   ; pop rip（返回调用者）
```

---

### 5.3 x86-64 System V AMD64 调用约定

**把它背下来。它决定了 Linux 上每一个函数如何工作。**

```
函数参数（整数/指针，按顺序）：
  参数1 -> rdi
  参数2 -> rsi
  参数3 -> rdx
  参数4 -> rcx
  参数5 -> r8
  参数6 -> r9
  参数7 及之后 -> 压入栈（从右到左）

返回值：rax（64 位），rdx:rax（128 位）

调用者保存的寄存器（若调用后还需要，调用者必须自己保存）：
  rax, rcx, rdx, rsi, rdi, r8, r9, r10, r11

被调用者保存的寄存器（被调用的函数必须在返回前恢复）：
  rbx, rbp, r12, r13, r14, r15

栈对齐：在 CALL 指令处 rsp 必须是 16 字节对齐。
  这意味着在执行 call 之前 rsp % 16 == 8（因为 call 会压入 8 字节）。
  SIMD 指令（SSE/AVX）在栈未对齐时会触发段错误。
```

**完整的函数示例 —— 可从 C 调用的 NASM 函数：**

```nasm
; 文件：add_numbers.asm
; int64_t add_numbers(int64_t a, int64_t b);
; a 在 rdi 中，b 在 rsi 中。返回值放在 rax 中。
section .text
    global add_numbers

add_numbers:
    push rbp              ; 保存调用者的基址指针（被调用者保存）
    mov  rbp, rsp         ; 建立栈帧

    mov  rax, rdi         ; rax = a
    add  rax, rsi         ; rax += b  （结果 = a + b）

    pop  rbp              ; 恢复调用者的基址指针
    ret                   ; 返回：rax 中保存结果
```

```c
// main.c
#include <stdio.h>
#include <stdint.h>

extern int64_t add_numbers(int64_t a, int64_t b);

int main() {
    int64_t result = add_numbers(10, 32);
    printf("Result: %ld\n", result);  // 42
    return 0;
}
```

```makefile
# 把汇编、编译、链接串起来的 Makefile
CC     = gcc
NASM   = nasm
TARGET = main

all:
	$(NASM) -f elf64 -o add_numbers.o add_numbers.asm
	$(CC) -o $(TARGET) main.c add_numbers.o
	@echo "[+] Built $(TARGET)"

clean:
	rm -f *.o $(TARGET)
```

---

### 5.4 阅读编译器输出

```bash
# 从 C 代码生成汇编
gcc -S -O0 -o output.asm source.c        # AT&T 语法（GAS）
gcc -S -O0 -masm=intel -o output.asm source.c  # Intel 语法（推荐）

# 或者在线用 Godbolt：https://godbolt.org
# 粘贴你的 C 代码，选择 GCC x86-64，加上 -O0 -masm=intel 标志
```

**示例：在汇编中跟踪一个 C 函数：**

```c
// C 源码
int add(int a, int b) {
    return a + b;
}
```

```nasm
; 编译器输出（GCC -O0 -masm=intel）
add:
    push    rbp           ; 保存调用者的 rbp
    mov     rbp, rsp      ; 建立新栈帧
    mov     DWORD PTR [rbp-4], edi   ; 把参数 a 存到栈上
    mov     DWORD PTR [rbp-8], esi   ; 把参数 b 存到栈上
    mov     edx, DWORD PTR [rbp-4]   ; 加载 a
    mov     eax, DWORD PTR [rbp-8]   ; 加载 b
    add     eax, edx                  ; a + b
    pop     rbp           ; 恢复调用者的 rbp
    ret                   ; 返回（结果在 eax -> 零扩展到 rax）
```

---

### 5.5 汇编中的系统调用

```nasm
; 系统调用约定（Linux x86-64）：
; rax = 系统调用号
; rdi = 参数1，rsi = 参数2，rdx = 参数3，r10 = 参数4，r8 = 参数5，r9 = 参数6
; 返回值在 rax 中；负值 = -errno

section .data
    msg  db "hello, world", 0x0a
    msglen equ $ - msg

section .text
    global _start

_start:
    ; write(1, msg, msglen)
    mov  rax, 1           ; SYS_write = 1
    mov  rdi, 1           ; fd = 1（stdout）
    mov  rsi, msg         ; buf = msg 的地址
    mov  rdx, msglen      ; count = 长度
    syscall

    ; exit(0)
    mov  rax, 60          ; SYS_exit = 60
    xor  rdi, rdi         ; status = 0
    syscall
```

```bash
# 汇编并链接（不用 libc）
nasm -f elf64 -o hello.o hello.asm
ld -o hello hello.o
./hello
```

---

### 5.6 检查二进制

```bash
# 看看编译器实际生成了什么
objdump -d -M intel binary     # 反汇编所有节，Intel 语法
objdump -d -M intel -j .text binary  # 只反汇编 .text 节
readelf -h binary              # ELF 头
readelf -S binary              # 节表
readelf -l binary              # 程序头（段）
nm binary                      # 符号表（函数名、全局变量）
strings binary                 # 提取可打印字符串（最少 4 个字符）
strings -n 8 binary            # 最少 8 个字符的字符串
xxd binary | head -4           # 前 4 行的十六进制转储（检查魔数字节）
strace ./binary                # 在运行时跟踪系统调用
ltrace ./binary                # 在运行时跟踪库调用
```

---

### 5.7 Godbolt：你的汇编实验室

Godbolt Compiler Explorer（https://godbolt.org）是理解 C 如何映射到汇编的最快方式：

1. 把 C 代码粘贴到左边
2. 选择“x86-64 gcc”和版本（用 13.x 或 14.x —— 用 `gcc --version` 对齐你的 Ubuntu 版本）
3. 添加标志：`-O0 -masm=intel`（不优化，Intel 语法）
4. 右边会实时更新汇编
5. 把鼠标悬停在汇编行上，会高亮生成它的那一行 C

可以试试：
- 加上/去掉 `volatile`，看有什么变化
- 对比 `-O0`、`-O2`、`-O3`（优化会改变一切）
- 有符号与无符号类型的整数溢出
- 结构体访问，以及 `->` 和 `.` 如何变成 `[rbp-N]` 加载

---

### 第5节 资源

| 资源 | 类型 | 费用 |
|----------|------|------|
| [x86-64 Reference (Félix Cloutier)](https://www.felixcloutier.com/x86/) | 参考 | 免费 |
| [NASM Documentation](https://www.nasm.us/doc/) | 文档 | 免费 |
| [Godbolt Compiler Explorer](https://godbolt.org) | 工具 | 免费 |
| [CS 61C (Berkeley) -- Machine Structures](https://cs61c.org/) | 课程 | 免费 |
| [Computer Organization and Design (Patterson/Hennessy)](https://www.elsevier.com/books/computer-organization-and-design-x86-edition) | 书 | 约 60 美元 |
| [Linux Syscall Table](https://syscall.sh) | 参考 | 免费 |

---

## 12. 第6节：逆向工程基础

**时长：** 6-8 周（第 18-26 周）| **并行于：** 汇编、密码学

### 为什么在利用之前先学逆向

漏洞利用是应用化的逆向工程。你通过理解一个二进制在做什么来发现漏洞。你通过观察二进制行为的变化来验证利用是否有效。没有逆向技能，你是在猜。有了它，你是在阅读。

---

### 6.1 ELF 与 PE：两个世界

<div align="center">
<table><tr><td>

<img src="../assets/diagrams/PHASE_0/6._ELF_vs_PE.png" alt="ELF vs PE" width="650"/>

</td></tr></table>
</div>

---

**关键结构差异：**

| 特性 | ELF（Linux） | PE（Windows） |
|---------|-------------|--------------|
| 魔数字节 | `7F 45 4C 46`（`\x7fELF`） | `4D 5A`（`MZ`） |
| 导入表 | PLT + GOT | 导入地址表（IAT） |
| 导出表 | 动态符号表 | 导出目录 |
| 加载器 | `ld-linux.so` | `ntdll.dll` |
| 分析工具 | readelf、objdump | PE-bear、CFF Explorer |

---

### 6.2 ELF 深入

```bash
# 识别任意二进制
file /bin/ls
# /bin/ls: ELF 64-bit LSB pie executable, x86-64, version 1 (SYSV),
#   dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2,
#   BuildID[sha1]=..., stripped

# 完整的 ELF 头
readelf -h /bin/ls

# 节表（名称、类型、地址、偏移、大小、标志）
readelf -S /bin/ls
# 标志：A=分配, W=写, X=执行
# .text：AX（分配 + 执行 —— 代码就在这里）
# .data：AW（分配 + 写 —— 已初始化的全局变量）
# .bss： AW（分配 + 写 —— 零初始化的全局变量）
# .got： AW（分配 + 写 —— 覆盖它就是劫持函数指针）

# 动态链接信息（需要哪些 .so 文件）
readelf -d /bin/ls | grep NEEDED
ldd /bin/ls          # 显示所有共享库依赖

# 反汇编这个二进制
objdump -d -M intel /bin/ls | less

# 找到入口点
readelf -h /bin/ls | grep "Entry"
objdump -d -M intel /bin/ls | grep -A 20 "<_start>"
```

---

### 6.3 静态分析：Ghidra

**Ghidra** 是 NSA 的免费开源逆向工程框架。它的反编译器能把汇编转回可读的类 C 伪代码。你大部分逆向时间都会花在这里。

```bash
# 安装（需要 Java 17+）
sudo apt install openjdk-17-jdk
wget https://github.com/NationalSecurityAgency/ghidra/releases/download/Ghidra_11.2_build/ghidra_11.2_PUBLIC_20241127.zip
unzip ghidra_11.2_PUBLIC_20241127.zip
cd ghidra_11.2_PUBLIC
./ghidraRun
```

**工作流程：**
1. File -> New Project -> Non-Shared Project -> 起个名字
2. File -> Import File -> 选择二进制
3. 自动分析：接受默认值，点 Analyze（等一会儿 —— 对大二进制要好几分钟）
4. Window -> Functions -> 找到 `main`
5. 反编译器窗口（右侧）：读伪代码
6. 汇编窗口（中间）：读实际指令
7. 点击反编译器里的任何变量 -> 汇编中对应的名字也会高亮

**Ghidra 必备操作：**

| 操作 | 如何做 |
|--------|-----|
| 重命名变量 | 悬停在上面时按 L |
| 重命名函数 | 右键 -> Edit Function |
| 跳转到地址 | 按 G 然后输入地址 |
| 查找字符串引用 | Window -> Defined Strings -> 双击 |
| 按名字查找函数 | Window -> Functions -> 搜索 |
| 交叉引用 | 右键符号 -> References |
| 导出反编译输出 | File -> Export Program -> C/C++ |

**替代工具（知道它们存在，按任务选择）：**
- **Binary Ninja**（https://binary.ninja）：快、可脚本化、API 优秀。有免费版。更适合自动化。
- **IDA Free**（https://hex-rays.com/ida-free）：行业标准。免费版限于 x86/x86-64/ARM。值得拥有。
- **radare2**（免费，命令行）：学习曲线陡，但强大、可脚本化。把 Ghidra 用熟之后很合适。
- **Cutter**（免费）：radare2 的图形界面。进入 radare2 更容易的入口。

---

### 6.4 动态分析：strace、ltrace、GDB

```bash
# 跟踪二进制发起的每一次系统调用
strace ./binary
strace -e trace=open,read,write,connect ./binary   # 只跟踪指定调用
strace -f ./binary                                  # 跟随 fork
strace -o trace.log ./binary                        # 把跟踪结果写入文件

# Trace library calls (printf, malloc, strcmp, etc.)
ltrace ./binary
ltrace -e strcmp ./binary   # 只观察 strcmp 调用 —— 对 crackme 很有用

# 两者一起用
strace -e trace=all -f -o strace.out ./binary &
ltrace -f -o ltrace.out ./binary &
```

---

### 6.5 第一个 crackme 完整走查（方法论）

**crackme** 是一个专门用来被逆向的程序。目标通常是找出一个有效的口令、序列号或密钥。

**标准做法：**

```bash
# 第 1 步：识别文件
file crackme
readelf -h crackme     # 如果是 ELF

# 第 2 步：提取字符串（找：硬编码口令、提示信息、线索）
strings crackme
strings -n 8 crackme   # 最小长度更长 —— 误报更少

# 第 3 步：先做一次动态观察
strace ./crackme <<< "test_input"   # 喂 stdin
ltrace ./crackme <<< "test_input"   # 观察库调用
# 找：strcmp、strncmp、memcmp —— 往往就是你需要绕过的那次比较

# 第 4 步：在 Ghidra 中找到校验逻辑
# 加载二进制，自动分析
# 找：调用那次比较的函数
# 追踪：程序把你的输入和什么比较？

# 第 5 步：GDB 动态分析
gdb ./crackme
(gdb) info functions    # 列出所有函数名
(gdb) break strcmp      # 在调用 strcmp 时中断
(gdb) run <<< "test"
(gdb) x/s $rdi          # 打印第一个参数（被比较的字符串）
(gdb) x/s $rsi          # 打印第二个参数（它拿来比较的对象）
```

---

### 第6节 资源

| 资源 | 类型 | 费用 |
|----------|------|------|
| [Ghidra Book (NSA/Buchanan/Eagle)](https://nostarch.com/GhidraBook) | 书 | 约 50 美元 |
| [Practical Malware Analysis (Sikorski/Honig)](https://nostarch.com/malware) | 书 | 约 50 美元 |
| [Binary Exploitation (pwn.college)](https://pwn.college/) | 免费课程 | 免费 |
| [crackmes.one](https://crackmes.one/) | 练习 | 免费 |
| [Reverse Engineering for Beginners (Dennis Yurichev)](https://beginners.re/) | 免费书 | 免费 |
| [LiveOverflow -- Binary Exploitation series](https://www.youtube.com/@LiveOverflow) | YouTube | 免费 |

---

## 13. 第7节：密码学入门

**时长：** 4-6 周（第 15-20 周）| **并行于：** 汇编、逆向

### 为什么密码学属于进攻知识

恶意软件用 XOR 混淆载荷。C2 通道使用自制的或实现拙劣的密码。CTF 题目把 flag 藏在弱密码之后。TLS 出现在每一个 Web 目标上。如果你不能读懂、实现并攻破基础密码学，那么二进制和协议所做的一半事情你都看不见。

---

### 7.1 XOR：漏洞利用开发者的最好朋友

XOR 是漏洞利用开发中最重要的操作。shellcode 混淆、自制 C2 加密，以及你会见到的一半 CTF 题目，都建立在 XOR 之上。

**数学基础：**
```
XOR 真值表：         0 XOR 0 = 0
                     0 XOR 1 = 1
                     1 XOR 0 = 1
                     1 XOR 1 = 0   （输入相同 = 0）

为什么它是自逆的：
  若 C = M XOR K  （加密：明文 XOR 密钥 = 密文）
  则 M = C XOR K  （解密：密文 XOR 密钥 = 明文）

证明：
  C XOR K = (M XOR K) XOR K = M XOR (K XOR K) = M XOR 0 = M
```

**对进攻有意义的性质：**
- `x XOR x = 0` —— 任何值与自身 XOR 都为零（用于清零寄存器：`xor rax, rax`）
- `x XOR 0 = x` —— 与零 XOR 是恒等（不改变）
- `x XOR 0xFF = ~x` —— 与全 1 XOR 翻转所有位（按位取反）
- 可交换：`A XOR B = B XOR A`
- 可结合：`(A XOR B) XOR C = A XOR (B XOR C)`

```python
def xor_crypt(data: bytes, key: bytes) -> bytes:
    return bytes(b ^ key[i % len(key)] for i, b in enumerate(data))

plaintext = b"Hello, World!"
key = b"\xAA\xBB\xCC"

ciphertext = xor_crypt(plaintext, key)
recovered  = xor_crypt(ciphertext, key)

print(f"Encrypted: {ciphertext.hex()}")
print(f"Decrypted: {recovered}")
assert recovered == plaintext
```

---

### 7.2 用频率分析破解单字节 XOR

单字节 XOR 密钥很容易破解。下面这个技巧用于在你不知道密钥的情况下把它找出来。

```python
def score_english(text: bytes) -> float:
    freq = {
        ord('e'): 12.7, ord('t'): 9.1,  ord('a'): 8.2,  ord('o'): 7.5,
        ord('i'): 7.0,  ord('n'): 6.7,  ord('s'): 6.3,  ord('h'): 6.1,
        ord('r'): 6.0,  ord('d'): 4.3,  ord('l'): 4.0,  ord(' '): 13.0,
    }
    return sum(freq.get(b, 0) for b in text.lower())

def break_single_byte_xor(ciphertext: bytes) -> tuple:
    best_score = -1
    best_key = 0
    best_plain = b""

    for key_byte in range(256):
        candidate = bytes(b ^ key_byte for b in ciphertext)
        score = score_english(candidate)
        if score > best_score:
            best_score = score
            best_key = key_byte
            best_plain = candidate

    return best_key, best_plain, best_score

ciphertext = bytes.fromhex("1b37373331363f78151b7f2b783431333d78397828372d363c7837373c")
key, plaintext, score = break_single_byte_xor(ciphertext)
print(f"Key: {key:#04x} ({key})")
print(f"Plaintext: {plaintext}")
```

---

### 7.3 哈希：单向函数

**哈希函数**接受任意输入，产生固定长度的摘要。它是单向的：你无法从输出恢复输入（理论上）。它是确定性的：相同输入永远产生相同输出。

```python
import hashlib

data = b"hello, world"
print(hashlib.md5(data).hexdigest())       # 128 位（32 个十六进制字符）—— 已被破解，不要用于安全
print(hashlib.sha1(data).hexdigest())      # 160 位（40 个十六进制字符）—— 已被破解
print(hashlib.sha256(data).hexdigest())    # 256 位（64 个十六进制字符）—— 当前标准
print(hashlib.sha512(data).hexdigest())    # 512 位（128 个十六进制字符）
print(hashlib.sha3_256(data).hexdigest())  # SHA-3（Keccak）—— SHA-2 之后的标准

# 文件哈希
with open("/bin/ls", "rb") as f:
    h = hashlib.sha256()
    for chunk in iter(lambda: f.read(65536), b""):
        h.update(chunk)
print(h.hexdigest())
```

**哈希为什么对进攻重要：**
- 口令数据库存的是哈希，不是明文。破解 = 找出能产生相同哈希的输入。
- MD5/SHA-1 的哈希碰撞已可实用化 —— 文件伪造攻击。
- HMAC（基于哈希的 MAC）用于请求签名 —— 如果密钥弱，就可攻击。

---

### 7.4 对称加密

对称加密用同一把密钥加密和解密。速度快。用于批量数据。

```python
from cryptography.hazmat.primitives.ciphers.aead import AESGCM
import os

# AES-256-GCM：带认证加密的现代正确选择
# “带认证” = 在一次操作中同时完成加密与完整性校验
key = os.urandom(32)   # 256 位密钥（必须保密）
nonce = os.urandom(12) # 96 位 nonce（绝不要与同一密钥重复使用）

aesgcm = AESGCM(key)
plaintext = b"SECRET: password=hunter2"
aad = b"authenticated but not encrypted header"

ciphertext = aesgcm.encrypt(nonce, plaintext, aad)
decrypted  = aesgcm.decrypt(nonce, ciphertext, aad)

assert decrypted == plaintext
print(f"Ciphertext ({len(ciphertext)} bytes): {ciphertext.hex()[:32]}...")
```

**为什么用 AES-GCM 而不是 AES-ECB/CBC：**
- ECB 独立加密每个 16 字节块 —— 相同的块产生相同的密文。ECB 企鹅图就展示了这个弱点。绝不要用 ECB。
- CBC 比 ECB 好，但存在填充预言漏洞（POODLE、BEAST）。只有在你理解风险时才用它。
- GCM 同时提供机密性与完整性（认证标签）。对密文的篡改会被检测到。这才是你要的。

```bash
pip3 install cryptography --break-system-packages
```

---

### 7.5 非对称加密与数字签名

非对称密码学使用一对密钥：**公钥**（可自由分发）和**私钥**（绝不外传）。公钥加密的东西只有私钥能解密。私钥签名过的东西，公钥可以验证。

```python
from cryptography.hazmat.primitives.asymmetric import rsa, padding
from cryptography.hazmat.primitives import hashes, serialization

# 生成 RSA 密钥对
private_key = rsa.generate_private_key(
    public_exponent=65537,
    key_size=2048
)
public_key = private_key.public_key()

# 用公钥加密（只有私钥能解密）
ciphertext = public_key.encrypt(
    b"secret message",
    padding.OAEP(
        mgf=padding.MGF1(algorithm=hashes.SHA256()),
        algorithm=hashes.SHA256(),
        label=None
    )
)

# 用私钥解密
plaintext = private_key.decrypt(
    ciphertext,
    padding.OAEP(
        mgf=padding.MGF1(algorithm=hashes.SHA256()),
        algorithm=hashes.SHA256(),
        label=None
    )
)
print(plaintext)  # b'secret message'

# 用私钥签名（证明真实性）
signature = private_key.sign(
    b"message to sign",
    padding.PSS(mgf=padding.MGF1(hashes.SHA256()), salt_length=padding.PSS.MAX_LENGTH),
    hashes.SHA256()
)

# 用公钥验证（任何人都能验证）
public_key.verify(
    signature,
    b"message to sign",
    padding.PSS(mgf=padding.MGF1(hashes.SHA256()), salt_length=padding.PSS.MAX_LENGTH),
    hashes.SHA256()
)
print("Signature valid")
```

---

### 7.6 PKI 与 TLS：证书究竟是什么

你攻击的每一条 HTTPS 连接都涉及证书。你需要理解信任链。

**TLS 证书是什么：**
TLS 证书是一个数据结构，包含：
- 服务器的**公钥**
- 服务器的**域名**（Common Name / Subject Alternative Name）
- **签发者**（谁签署了这份证书）
- **有效期**（不早于 / 不晚于的日期）
- 来自签发者的**数字签名**

**信任链：**

```
根 CA（根证书颁发机构）
  —— 自签名。预装在浏览器/操作系统中。
  —— 例如：DigiCert Global Root G2、ISRG Root X1（Let's Encrypt）

中间 CA（由根 CA 签发）
  —— 根 CA 很少直接签发终端实体证书。
  —— 多一层安全（中间 CA 被攻破 != 根被攻破）

终端实体证书（由中间 CA 签发）
  —— 你的浏览器连接 example.com 时验证的那份证书
  —— 包含服务器的公钥和域名
```

**浏览器连接 https://example.com 时会做什么：**
1. 服务器发送它的证书（以及中间 CA 证书）
2. 浏览器用中间 CA 的公钥验证终端实体证书上的签名
3. 浏览器用根 CA 的公钥验证中间证书上的签名
4. 浏览器检查根 CA 是否在它的受信任存储里（由操作系统/浏览器厂商预装）
5. 浏览器检查证书里的域名与 example.com 匹配
6. 浏览器检查证书未过期
7. 若所有检查都通过：浏览器用服务器公钥建立 TLS 会话
8. 若任何检查失败：浏览器显示警告

**自签名证书**是签发者与主体相同的那种证书 —— 证书由自己签署。浏览器默认不信任自签名证书，因为没有通向可信根的链条。

```bash
# 查看某个网站的证书
openssl s_client -connect example.com:443 -showcerts < /dev/null 2>/dev/null | \
    openssl x509 -text -noout | head -40

# 创建自签名证书（供实验环境使用）
openssl req -x509 -newkey rsa:4096 -keyout server.key -out server.crt \
    -days 365 -nodes -subj "/CN=localhost"

# 查看本地证书
openssl x509 -in server.crt -text -noout
```

**这对进攻为什么重要：**
- MITM 攻击：你需要呈现一份受害者浏览器信任的证书。这意味着要么窃取一份合法证书，要么用受害者被骗去信任的某个 CA 生成一份，要么利用某个 MITM 工具（要用 Burp Suite 的 CA 证书做 HTTPS 拦截，必须把它装进受害者浏览器）。
- 证书校验缺陷（CWE-295）：没有正确校验信任链的软件，即使不动浏览器也能被 MITM。
- 客户端证书：有些应用用客户端证书做认证。找到这些证书是后渗透阶段的目标。

---

### 7.7 Cryptopals 挑战

去做。这不是建议。

https://cryptopals.com

第 1、2 组用 Python 从零覆盖了本节的全部内容以及更多。如果你能在进入阶段 1 之前完成第 1-2 组，你的密码学直觉就是正确的。第 1 组的练习包括：
- 十六进制转 base64
- 固定 XOR
- 破解单字符 XOR
- 在文件中检测单字符 XOR
- 重复密钥 XOR（维吉尼亚式）
- 用汉明距离和频率分析破解重复密钥 XOR
- ECB 模式下的 AES
- 检测 ECB 模式

---

### 第7节 资源

| 资源 | 类型 | 费用 |
|----------|------|------|
| [Cryptopals Challenges](https://cryptopals.com) | 练习 | 免费 |
| [Serious Cryptography (Aumasson)](https://nostarch.com/seriouscrypto) | 书 | 约 40 美元 |
| [Crypto 101 (Laurens Van Houtven)](https://www.crypto101.io/) | 免费书 | 免费 |
| [Dan Boneh -- Cryptography I (Coursera)](https://www.coursera.org/learn/crypto) | 课程 | 免费（旁听） |
| [openssl s_client documentation](https://www.openssl.org/docs/man3.0/man1/openssl-s_client.html) | 文档 | 免费 |

---

## 14. 第8节：ARM64 架构认知

**时长：** 2-3 周（第 20-22 周）| **并行于：** 逆向基础、密码学

> 这一节不在本路线图的早期版本中。现在它在这里，因为 2027 年需要它。

### 为什么在阶段 0 讲 ARM64

在你走完这份路线图之前就会遇到 ARM64 目标：
- Apple Silicon 上的 macOS（M 系列 Mac）：每个安全研究员的笔记本，也是许多开发目标
- AWS Graviton 实例：ARM64 每计算单元便宜 20-40%；采用速度在加快
- Android：所有现代 Android 手机都是 ARM64
- IoT 与嵌入式设备：树莓派 4/5、路由器、摄像头、工业控制器

ARM64 汇编的寄存器不同、指令名不同、调用约定也与 x86-64 不同。**概念**（寄存器、栈、调用约定、系统调用）完全一样。**具体细节**不同。现在学它们，意味着你在阶段 2 第一次碰到 ARM64 目标时不是从零开始。

---

### 8.1 ARM64 寄存器

```
通用寄存器：x0-x30
  x0-x7    函数参数与返回值
              x0 = 参数1（同时也是返回值）
              x1 = 参数2
              x2 = 参数3
              x3 = 参数4
              x4 = 参数5
              x5 = 参数6
              x6 = 参数7
              x7 = 参数8
  x8       系统调用号（在 Linux ARM64 上 —— 与 x86-64 的 rax 不同）
           在 ABI 中也用作间接结果位置寄存器（XR）
  x9-x15   临时寄存器（调用者保存）
  x16-x17  过程调用内暂存（IP0、IP1）—— 链接器桩会用到
  x18      平台寄存器（不要使用；操作系统可能占用）
  x19-x28  被调用者保存（函数若使用必须在返回前恢复）
  x29      帧指针（FP）—— 相当于 x86-64 的 rbp
  x30      链接寄存器（LR）—— 保存返回地址（默认不在栈上）
  xzr      零寄存器：读总是 0，写入被丢弃（x86-64 中没有对应物）

特殊寄存器：
  sp       栈指针（某些语境下写作 x31）
  pc       程序计数器（指令指针 —— 不能像 rip 那样直接访问）
  pstate   处理器状态标志（N、Z、C、V —— 相当于 SF、ZF、CF、OF）
```

**与 x86-64 的对比：**

| 概念 | x86-64 | ARM64 |
|---------|--------|-------|
| 返回值 | rax | x0 |
| 参数 1 | rdi | x0 |
| 参数 2 | rsi | x1 |
| 参数 3 | rdx | x2 |
| 参数 4 | rcx | x3 |
| 参数 5 | r8 | x4 |
| 参数 6 | r9 | x5 |
| 参数 7 及之后 | 栈 | x6、x7，然后栈 |
| 栈指针 | rsp | sp |
| 帧指针 | rbp | x29 |
| 返回地址 | 在栈上（由 call 压入） | 在 x30（链接寄存器）中 |
| 系统调用号 | rax | x8 |
| 零寄存器 | 无（xor rax, rax） | xzr |

**命名约定：**
- `x0` = 64 位寄存器
- `w0` = x0 的低 32 位（写 w0 会零扩展到 x0）
- `h0` / `b0` = 16 位 / 8 位（在 AArch64 通用代码中较少见）

---

### 8.2 ARM64 指令集基础

ARM64 是 **RISC**（精简指令集计算机）架构。与 x86-64（CISC）的关键设计差异：

1. **定宽指令：** 每条 ARM64 指令恰好 4 字节（32 位）。x86-64 指令是 1-15 字节。
2. **加载/存储架构：** 不能直接对内存做运算。必须先从内存加载到寄存器，在寄存器上运算，再存回去。x86-64 可以直接写 `add rax, [rbx]`；ARM64 需要 `ldr x1, [x0]; add x0, x0, x1`。
3. **三操作数指令：** `add x0, x1, x2` 意思是 `x0 = x1 + x2`。x86-64 用两操作数：`add rax, rbx` 意思是 `rax = rax + rbx`。
4. **大多数指令带条件码：** 多数 ARM64 指令都有条件变体。

```asm
// ARM64 汇编（使用 GNU as 语法）

// 数据移动
mov  x0, #42           // x0 = 42（立即数，须符合 movz/movk 的 16 位限制）
mov  x1, x0            // x1 = x0
ldr  x0, [x1]          // x0 = *x1（从 x1 中的地址加载 64 位）
str  x0, [x1]          // *x1 = x0（把 64 位存到 x1 中的地址）
ldr  x0, [x1, #8]      // x0 = *(x1 + 8)
ldr  x0, [x1, x2]      // x0 = *(x1 + x2)
ldr  w0, [x1]          // 加载 32 位并零扩展到 x0

// 算术（三操作数）
add  x0, x1, x2        // x0 = x1 + x2
sub  x0, x1, x2        // x0 = x1 - x2
mul  x0, x1, x2        // x0 = x1 * x2
add  x0, x1, #8        // x0 = x1 + 8（立即数）

// 位运算
and  x0, x1, x2        // x0 = x1 & x2
orr  x0, x1, x2        // x0 = x1 | x2（注意：是 'orr' 不是 'or'）
eor  x0, x1, x2        // x0 = x1 ^ x2（XOR —— 注意：是 'eor' 不是 'xor'）
mvn  x0, x1            // x0 = ~x1（按位取反）
lsl  x0, x1, #3        // x0 = x1 << 3
lsr  x0, x1, #3        // x0 = x1 >> 3（逻辑右移，高位补零）
asr  x0, x1, #3        // x0 = x1 >> 3（算术右移，高位补符号）

// 比较与分支
cmp  x0, #10           // 依据 x0 - 10 设置标志位
cmp  x0, x1            // 依据 x0 - x1 设置标志位
b    label             // 无条件分支（= jmp）
beq  label             // 相等则分支（ZF=1）
bne  label             // 不相等则分支（ZF=0）
blt  label             // 小于则分支（有符号）
bgt  label             // 大于则分支（有符号）
cbz  x0, label         // x0 == 0 则分支（比较并分支 —— 不设置标志位）
cbnz x0, label         // x0 != 0 则分支

// 栈（满递减：push 前 sp 先减，pop 后 sp 再加）
// ARM64 没有 push/pop 指令 —— 用前索引的存储/加载
str  x30, [sp, #-16]!  // 压入 x30（链接寄存器）：sp -= 16；*(sp) = x30
ldr  x30, [sp], #16    // 弹出 x30：x30 = *(sp)；sp += 16

stp  x29, x30, [sp, #-16]!  // 压入一对：同时保存帧指针和链接寄存器（常见写法）
ldp  x29, x30, [sp], #16    // 弹出一对：同时恢复两者

// 函数调用与返回
bl   function          // Branch-and-Link：x30 = pc+4，然后跳转（= call）
blr  x0               // Branch-with-Link to Register：调用 x0 中的地址
ret                    // 返回：跳转到 x30（链接寄存器）中的地址
ret  x30              // 显式形式（x30 是默认值）
```

---

### 8.3 ARM64 Linux 系统调用约定

```asm
// Linux ARM64 系统调用约定：
// x8  = 系统调用号
// x0  = 参数1
// x1  = 参数2
// x2  = 参数3
// x3  = 参数4
// x4  = 参数5
// x5  = 参数6
// svc #0 = supervisor call（触发内核入口）
// 返回值在 x0 中；负值 = -errno

// 示例：write(1, "hello\n", 6)
.section .data
msg:    .ascii "hello\n"

.section .text
.global _start
_start:
    mov  x8, #64          // SYS_write = 64（ARM64 Linux）
    mov  x0, #1           // fd = 1（stdout）
    ldr  x1, =msg         // buf = msg 的地址
    mov  x2, #6           // count = 6
    svc  #0               // 系统调用

    mov  x8, #93          // SYS_exit = 93（ARM64 Linux）
    mov  x0, #0           // status = 0
    svc  #0
```

**ARM64 Linux 的系统调用号与 x86-64 不同：**

| 系统调用 | x86-64 | ARM64 |
|---------|--------|-------|
| read | 0 | 63 |
| write | 1 | 64 |
| open | 2 | 不适用（用 openat=56） |
| close | 3 | 57 |
| mmap | 9 | 222 |
| execve | 59 | 221 |
| exit | 60 | 93 |
| socket | 41 | 198 |

完整的 ARM64 系统调用表：https://arm64.syscall.sh

---

### 8.4 识别 ARM64 二进制

```bash
# 开始之前先识别架构
file /usr/bin/python3
# 在 x86-64 系统上：
# ELF 64-bit LSB pie executable, x86-64, ...
# 在 ARM64 系统上（或交叉编译出来的二进制）：
# ELF 64-bit LSB pie executable, ARM aarch64, ...

readelf -h binary | grep Machine
# Machine: AArch64     <- ARM64
# Machine: Advanced Micro Devices X86-64   <- x86-64

# 反汇编 ARM64 二进制（需要 aarch64 binutils）
sudo apt install binutils-aarch64-linux-gnu
aarch64-linux-gnu-objdump -d binary
aarch64-linux-gnu-readelf -h binary

# 用 GDB 调试 ARM64 二进制（在 ARM64 主机上或通过 QEMU）
# Ghidra 原生支持 ARM64 —— 直接打开二进制即可
```

---

### 8.5 搭建 ARM64 实验环境

阶段 0 的认知层面不需要 ARM64 硬件。你可以用模拟：

```bash
# QEMU 用户模式：在 x86-64 上运行单个 ARM64 二进制
sudo apt install qemu-user-static gcc-aarch64-linux-gnu

# 为 ARM64 交叉编译一个 C 程序
aarch64-linux-gnu-gcc -o hello_arm64 hello.c

# 用 QEMU 用户模式模拟运行它
qemu-aarch64-static ./hello_arm64

# 完整 ARM64 系统：用 QEMU 系统模式跑 Ubuntu 22.04 ARM64
# （下载：ubuntu.com/download/server/arm）
# 运行：qemu-system-aarch64，加上合适的 -M virt -cpu cortex-a53 标志
```

---

### 8.6 ARM64 资源

| 资源 | 类型 | 费用 |
|----------|------|------|
| [Azeria Labs ARM Assembly](https://azeria-labs.com/writing-arm-assembly-part-1/) | 教程 | 免费 |
| [ARM Architecture Reference Manual (AArch64)](https://developer.arm.com/documentation/ddi0487/latest) | 手册 | 免费 |
| [ARM64 Syscall Table](https://arm64.syscall.sh) | 参考 | 免费 |
| [ARM Developer Documentation](https://developer.arm.com/documentation) | 文档 | 免费 |
| [Code with Engineering Playbook -- ARM64](https://microsoft.github.io/code-with-engineering-playbook/) | 指南 | 免费 |

---

## 15. 第9节：glibc 内部机制入门

**时长：** 1 周（第 22-23 周）| **面向阶段 3 的认知准备**

> 这一节存在的意义是插一面旗。你不会在阶段 0 掌握堆利用。但你会知道得足够多，以致阶段 3 的堆内容不会打得你措手不及。

### 为什么 glibc 版本重要

glibc（GNU C Library）是 Linux 上的标准 C 库。每一个用到 `malloc`、`free`、`printf` 或大多数标准函数的 C 程序都会链接它。

glibc 内部的堆分配器叫 **ptmalloc2**。它的内部结构 —— bins、chunks、tcache —— 正是堆利用攻击的对象。这个结构在各版本之间变化很大：

- **glibc 2.26（2017）：** 引入 tcache（线程本地缓存）。新的利用目标。
- **glibc 2.29（2019）：** tcache 加固（加入计数检查）。
- **glibc 2.32（2020）：** 对单链表指针（fastbin、tcache）引入 safe-linking。
- **glibc 2.34（2021）：** 移除 `__malloc_hook`、`__free_hook`、`__realloc_hook`。2019 年代的大量技术失效。
- **glibc 2.35（2022 —— Ubuntu 22.04）：** 进一步加固。
- **glibc 2.39+（2024+）：** 更新的发行版中已有。

**Ubuntu 版本与 glibc 版本对照：**

| Ubuntu | glibc | 关键变化 |
|--------|-------|-------------|
| 18.04 LTS | 2.27 | 有 tcache，有 hooks |
| 20.04 LTS | 2.31 | 无 safe-linking，有 hooks |
| 22.04 LTS | 2.35 | 有 safe-linking，hooks 已移除 |
| 24.04 LTS | 2.39 | 进一步加固 |

**这对你意味着什么：** 2019-2021 年间那些使用 `__free_hook` 或 `__malloc_hook` 的 CTF 题解和利用教程，在 Ubuntu 22.04 上**不**成立。照着旧题解做却失败时，先查 glibc 版本。

```bash
# 查看你的 glibc 版本
ldd --version
# 或者
/lib/x86_64-linux-gnu/libc.so.6 --version

# 查看某个二进制链接的 glibc
ldd binary | grep libc

# 针对 CTF 题目：把二进制打补丁，改用指定版本的 glibc
# 工具：patchelf
sudo apt install patchelf
patchelf --set-interpreter ./ld-2.31.so --set-rpath . ./binary
```

### 堆块结构（只需有概念）

```
内存里的一个 malloc 块长这样：
  （prev_size 字段：只有前一个块空闲时才会用到）
  size 字段：块的字节大小，低 3 位是指标位
              第 0 位（P）：前一个块正在使用
              第 1 位（M）：这是 mmap 出来的块
              第 2 位（A）：属于非主 arena
  用户数据：malloc() 返回给调用者的那些字节
  （下一个块紧接在它后面）

释放一个块时（简化版）：
  它按自身大小进入某个 bin：
    tcache：每线程单链表，0-1032 字节（glibc 2.26+）
    fastbin：小块，单链表
    smallbin：双链表，按大小有序
    largebin：双链表，先无序存放
    unsorted bin：刚释放、等待被排序的块
```

阶段 0 里你不需要利用其中任何一点。你只需要知道它存在，这样当阶段 3 提到 “tcache poisoning” 或 “fastbin dup” 时，你有一个心智模型可以把技术挂上去。

**现在唯一要动手做的一件实事：**

```c
// 编译它，在 gdb 里运行。
// 在 malloc() 处设断点。单步跟进去。
// 用 `x/32gx ptr` 查看堆内存。
// 看看块头（ptr 之前的 8 个字节）。

#include <stdlib.h>
int main() {
    void *a = malloc(64);
    void *b = malloc(64);
    free(a);
    void *c = malloc(64);  // 很可能返回和 a 相同的地址（tcache）
    return 0;
}
```

### 第9节 资源

| 资源 | 类型 | 费用 |
|----------|------|------|
| [Heap Exploitation (Shellphish how2heap)](https://github.com/shellphish/how2heap) | 指南 + 代码 | 免费 |
| [glibc malloc source (2.35)](https://sourceware.org/git/?p=glibc.git;a=blob;f=malloc/malloc.c;hb=glibc-2.35) | 源码 | 免费 |
| [heap-exploitation book (dhavalkapil)](https://heap-exploitation.dhavalkapil.com/) | 免费书 | 免费 |

---

## 16. 里程碑项目：完整规格卡

> 项目是这一阶段的证明。阅读建立认知，构建建立能力。这里每个项目都有通过/不通过的标准。达不到标准，就是没做完。

---

### 项目 1：C 语言简易 shell

**目标周：** 6-8  
**预计小时：** 15-25  
**主要技能：** C、操作系统、Bash

#### 规格

构建一个 Unix shell，它：

1. 显示提示符（`>>> `）
2. 读取一行输入
3. 解析命令与参数（能处理带引号的字符串：`echo "hello world"` 算一个参数）
4. fork 一个子进程，`execve` 该命令
5. 等待子进程并显示退出码
6. 处理内建命令：`cd`、`exit`、`pwd`、`export`
7. 处理管道：`ls -la | grep .c | wc -l`（至少两条管道的链）
8. 处理 I/O 重定向：`cat file.txt > output.txt` 和 `sort < input.txt`
9. 处理后台作业：`sleep 60 &`
10. 处理 SIGINT（Ctrl+C）：不要杀死 shell 本身

#### 通过标准

```bash
# 在你的 shell 里，这些必须正确工作：
ls -la | grep .c | wc -l
echo "hello world" > /tmp/test.txt && cat /tmp/test.txt
cd /tmp && pwd && cd - && pwd
./your_shell <<< "ls /etc | head -5"
```

#### 实现说明

- 不要用 `system()`。直接用 `fork() + execve()`。
- 先写词法分析器（处理空格和引号），在写其余部分之前单独测它。
- 等基本的 fork/exec 循环能跑之后，再加内建命令。
- 管道：串联 `pipe()` 调用。用 `dup2()` 把进程 N 的 stdout 接到进程 N+1 的 stdin。
- 编译命令：`gcc -Wall -Wextra -g -fsanitize=address,undefined -o shell shell.c`

---

### 项目 2：内存分配器

**目标周：** 10-12  
**预计小时：** 20-30  
**主要技能：** C、操作系统、系统编程

#### 规格

用 `sbrk()`（已废弃，但有教学价值）或 `mmap()` 实现 `my_malloc()`、`my_free()` 和 `my_realloc()`。你的分配器必须：

1. 满足任意大小的分配请求
2. 使用空闲链表（首次适配或最佳适配）
3. 合并相邻的空闲块
4. 通过测试套件（下面给出）
5. 在 Valgrind 与 AddressSanitizer 下都零错误
6. 有一个 `my_heap_dump()` 函数，打印所有块的地址、大小和空闲/占用状态

#### 通过标准

```bash
# 下面每一条都必须零错误：
valgrind --leak-check=full ./allocator_test
gcc -fsanitize=address,undefined -o allocator_test_asan allocator.c test.c && ./allocator_test_asan

# 正确性测试：
void test_allocator() {
    void *a = my_malloc(64);
    void *b = my_malloc(128);
    my_free(a);
    void *c = my_malloc(32);   // 应当复用 a 的块
    assert(c == a || c < a + 64);  // 复用或在旧块范围内
    my_free(b);
    my_free(c);
    // 全部释放之后：堆应当是一个大的空闲块（已合并）
    my_heap_dump();  // 应当显示一个空闲块
}
```

#### 为什么做这个项目

你会深入理解 `malloc()`。日后学堆利用时，你不会被块头、空闲链表和合并搞混 —— 这些东西全是你自己造过的。

---

### 项目 3：网络数据包分析器

**目标周：** 14-16  
**预计小时：** 15-20  
**主要技能：** C、网络、套接字

#### 规格

用 C 构建一个原始数据包嗅探器，它：

1. 打开原始套接字（`AF_PACKET, SOCK_RAW, htons(ETH_P_ALL)`）—— 需要 root
2. 从某个网络接口抓包
3. 解析并显示：以太网头、IP 头（IPv4 与 IPv6 都要）、TCP/UDP 头
4. 显示源与目的地址、端口、协议和载荷大小
5. 有一个 BPF 风格的过滤选项：`--proto tcp`、`--proto udp`、`--port 80`
6. 把抓到的包写入 `.pcap` 文件（按 pcap 文件格式规范自行实现）

#### 通过标准

```bash
# 运行你的嗅探器，同时另开一处运行 curl：
sudo ./sniffer --proto tcp --port 80 -o capture.pcap &
curl http://neverssl.com/ > /dev/null
sleep 2 && kill %1

# 你的 capture.pcap 必须能被 Wireshark 无错打开
# 并且能看到 HTTP GET 请求和 200 响应。
wireshark capture.pcap
```

#### 关于 WSL2 的说明

WSL2 中无法使用原始 `AF_PACKET` 套接字。这个项目请用虚拟机或裸机。阶段 0 的其他内容在 WSL2 下都能正常工作。

---

### 项目 4：汇编函数库

**目标周：** 17-19  
**预计小时：** 10-15  
**主要技能：** 汇编、C、ABI

#### 规格

写一个 NASM 汇编库（`asm_lib.asm`），把它链到一个 C 测试台上。用纯 x86-64 汇编实现：

1. `int64_t asm_strlen(const char *s)` —— 不依赖 libc 求字符串长度
2. `void asm_memcpy(void *dst, const void *src, size_t n)` —— 不依赖 libc 的内存复制
3. `int64_t asm_atoi(const char *s)` —— ASCII 字符串转整数（能处理负数）
4. `void asm_reverse(char *buf, size_t len)` —— 原地反转字节
5. `int64_t asm_strcmp(const char *a, const char *b)` —— 不依赖 libc 的字符串比较
6. 一个直接系统调用函数：`int64_t raw_write(int fd, const void *buf, size_t count)` —— 不调用 libc

#### 通过标准

```c
// test.c —— 必须让所有断言通过，且没有任何 sanitizer 报错
#include <assert.h>
#include <string.h>
int main() {
    assert(asm_strlen("hello") == 5);
    assert(asm_strlen("") == 0);
    assert(asm_atoi("42") == 42);
    assert(asm_atoi("-100") == -100);
    assert(asm_strcmp("abc", "abc") == 0);
    assert(asm_strcmp("abc", "abd") < 0);
    // 等等
    raw_write(1, "all tests passed\n", 17);
    return 0;
}
```

---

### 项目 5：首个二进制逆向

**目标周：** 22-24  
**预计小时：** 10-15  
**主要技能：** 逆向、GDB、Ghidra

#### 规格

从 https://crackmes.one 下载一个 crackme 二进制（推荐难度：Easy）。交付物是写在你 Obsidian 库里的一份分析文档，包含：

1. 二进制元数据：架构、文件类型、是否 stripped、链接的库
2. 有意思的字符串，以及它们暗示了程序的什么逻辑
3. 校验算法（伪代码或重建的 C）
4. 能通过校验的正确输入
5. GDB 会话笔记：设了哪些断点、观察到的寄存器值、检查过的内存
6. 关键校验函数的 Ghidra 反编译输出（重命名变量后整理干净）

#### 通过标准

用你找出的输入运行 crackme，得到“正确”的输出（通常是 “Correct!” 之类），并且没有对二进制打过任何补丁。你是通过分析解决的，不是靠暴力猜。

---

## 17. 实验室搭建

### Linux：主环境

**Ubuntu 22.04 LTS** 是推荐的基线系统。它自带 glibc 2.35、GCC 11、Python 3.10，软件包覆盖也非常好。

```bash
# 阶段 0 的完整软件包安装
sudo apt update && sudo apt upgrade -y

# 构建必备
sudo apt install -y \
    build-essential gcc g++ gdb git vim tmux \
    nasm yasm binutils binutils-aarch64-linux-gnu \
    make cmake ninja-build \
    strace ltrace gdb-peda python3-pip python3-venv

# 网络工具
sudo apt install -y \
    net-tools iproute2 iputils-ping \
    wireshark tshark tcpdump \
    nmap netcat-openbsd curl wget \
    dnsutils whois traceroute

# 安全与分析工具
sudo apt install -y \
    pwndbg binwalk \
    patchelf upx-ucl \
    checksec

# 逆向工具
sudo apt install -y \
    radare2 ltrace strings file xxd hexdump

# 模拟环境（用于 ARM64 工作）
sudo apt install -y \
    qemu-user-static qemu-system-aarch64 \
    gcc-aarch64-linux-gnu

# Python 包
pip3 install --break-system-packages \
    pwntools scapy cryptography \
    requests beautifulsoup4 \
    z3-solver ropgadget

# 安装 GEF（GDB Enhanced Features）
bash -c "$(curl -fsSL https://gef.blah.cat/sh)"

# 验证 glibc 版本（重要 —— 记下来）
ldd --version | head -1

# 安装 Ghidra（需要 Java 17）
sudo apt install -y openjdk-17-jdk
# 从以下地址下载最新的 Ghidra：https://github.com/NationalSecurityAgency/ghidra/releases
# 解压并运行 ./ghidraRun
```

---

### Windows 虚拟机：备用环境

现在就搭一个 Windows 10 或 11 虚拟机。你会需要它来做：
- PE 二进制分析
- Windows 专有的漏洞利用开发（阶段 3）
- 在 Windows Defender 下测试载荷
- SMB/Active Directory 实验（阶段 2）

**推荐的虚拟机（免费）：**
- Windows 10 评估版：https://www.microsoft.com/en-us/evalcenter/evaluate-windows-10-enterprise（90 天试用）
- Windows 11 开发虚拟机：https://developer.microsoft.com/en-us/windows/downloads/virtual-machines/（预装好，90 天）

**要在 Windows 虚拟机里装的工具：**
```
x64dbg        -- https://x64dbg.com（Windows 调试器）
PE-bear       -- https://github.com/hasherezade/pe-bear（PE 分析）
CFF Explorer  -- https://ntcore.com/?page_id=388（PE 编辑器）
Process Monitor (ProcMon) -- 来自 Sysinternals Suite
Process Hacker 2 -- https://processhacker.sourceforge.io
Wireshark     -- https://www.wireshark.org
```

---

### WSL2 替代方案（Windows 宿主机用户）

WSL2（Windows Subsystem for Linux 2）运行真正的 Linux 内核，对阶段 0 的大部分工作都够用：

```powershell
# 在 Windows PowerShell 中（管理员身份）
wsl --install -d Ubuntu-22.04
wsl --set-default-version 2

# 安装完成后，从开始菜单打开 Ubuntu 22.04
# 运行与上面相同的 apt install 命令
```

**WSL2 在阶段 0 的限制：**
- 原始 `AF_PACKET` 套接字（项目 3 需要）需要虚拟机或裸机
- 部分 QEMU 系统模拟能力受限
- 其余一切都能正常工作

---

### pwntools 速查

pwntools 是用于漏洞利用开发的 Python 框架。现在就装，边用边学。

```python
from pwn import *

# 上下文设置（在每个利用脚本顶部设置这些）
context.arch = 'amd64'      # 也可以是 'i386'、'arm'、'aarch64'
context.os = 'linux'
context.log_level = 'info'  # 或 'debug' 输出详细日志

# 进程交互（本地二进制）
p = process('./vulnerable_binary')
p.sendline(b"input data")
output = p.recvline()
p.interactive()

# 网络交互
r = remote('target.com', 1337)
r.sendline(b"payload")
r.recvuntil(b"$ ")

# 构造载荷
payload = b"A" * 64             # 64 个 'A' 字节
payload += p64(0xdeadbeef)      # 追加 8 字节小端地址
payload += p64(0xcafebabe)

# 有用的转换函数
p64(0x400080)           # 打包成 64 位小端
p32(0xdeadbeef)         # 打包成 32 位小端
u64(b"\x80\x00\x40\x00\x00\x00\x00\x00")  # 解包
hex(u64(p64(0x400080))) # 转换并验证

# ELF 交互
elf = ELF('./binary')
elf.symbols['main']     # main() 的地址
elf.got['printf']       # GOT entry for printf
elf.plt['printf']       # PLT entry for printf
elf.bss()              # .bss 节的起始地址
```

---

### 关键环境检查

```bash
# 运行这些来验证你的环境
echo "=== GCC ==="
gcc --version

echo "=== Python ==="
python3 --version
python3 -c "import pwn; print('pwntools ok')"
python3 -c "from scapy.all import IP; print('scapy ok')"

echo "=== GDB + GEF ==="
gdb --version
gdb -batch -ex "gef version" 2>/dev/null | head -1

echo "=== NASM ==="
nasm --version

echo "=== glibc ==="
ldd --version | head -1

echo "=== ASLR ==="
cat /proc/sys/kernel/randomize_va_space  # 应当是 2

echo "=== Java for Ghidra ==="
java --version
```

---

## 18. GDB 设置与命令参考

GDB 是你主要的动态分析工具。从你写第一行 C 代码那天起就用它。它不是高级工具 —— 它是第一个工具。

### 安装与 GEF 配置

```bash
# 安装 GEF（GDB Enhanced Features）
bash -c "$(curl -fsSL https://gef.blah.cat/sh)"

# 验证
gdb --quiet
# GEF 提示符应当带颜色和上下文显示出现

# 替代方案：pwndbg（外观不同，同样优秀）
git clone https://github.com/pwndbg/pwndbg && cd pwndbg && ./setup.sh
```

### 必备的 GDB 会话工作流

```bash
# 开始调试一个二进制
gdb ./binary
gdb -q ./binary                 # 安静模式（不显示横幅）
gdb --args ./binary arg1 arg2   # 带参数启动

# 附加到运行中的进程
gdb -p 1234
```

```gdb
# === 环境设置 ===
set disassembly-flavor intel     # Intel 语法（可读性好）
set follow-fork-mode child       # fork 时跟随子进程
set detach-on-fork off          # 父子进程都保持附加

# === 断点 ===
break main                      # 在函数名处下断
break *0x401234                 # 在指定地址下断
break file.c:42                 # 在源码行下断
break *main+30                  # 在函数内偏移处下断
info breakpoints                # 列出所有断点
delete 1                        # 删除断点 1
disable 2                       # 禁用断点 2（保留它）
enable 2                        # 重新启用

# === 执行 ===
run                             # 从头运行程序
run arg1 arg2                   # 带参数运行
run < /tmp/input.txt            # 从文件提供 stdin
continue                        # 继续到下一个断点（c）
next                            # 单步跳过（不进函数）（n）
step                            # 单步进入（进函数）（s）
nexti                           # 单步跳过一条指令（ni）
stepi                           # 单步进入一条指令（si）
finish                          # 执行到当前函数返回
until 42                        # 执行到第 42 行
jump *0x401234                  # 跳转到地址（谨慎使用）

# === 寄存器 ===
info registers                  # 显示所有寄存器
info registers rax rbx rsp      # 显示指定寄存器
print $rax                      # 打印 rax 的值
print/x $rax                    # 以十六进制打印 rax
set $rax = 0x42                 # 设置 rax 的值（打补丁）
# GEF 在每次中断时自动显示寄存器 —— 用 'regs' 命令

# === 内存检查 ===
x/10gx $rsp                    # 查看 rsp 处 10 个 8 字节十六进制值
x/20wx 0x401000                # 查看该地址处 20 个 4 字节十六进制值
x/s $rdi                       # 把 rdi 处的内存按字符串查看
x/i $rip                       # 显示 rip 处的指令
x/10i main                     # 显示 main 起的 10 条指令
x/20bx 0x602000                # 以十六进制查看 20 个字节

# 格式字母：x=十六进制, d=十进制, u=无符号, s=字符串, i=指令, c=字符
# 大小字母：b=字节(1), h=半字(2), w=字(4), g=巨字(8)

# GEF 专属的内存命令
heap bins                       # 显示堆 bin 状态（GEF）
heap chunks                     # 显示所有堆块（GEF）
vmmap                           # 虚拟内存映射（类似 /proc/pid/maps）
search-pattern "password"       # 在内存中搜索字符串
search-pattern 0xdeadbeef       # 在内存中搜索数值

# === 栈 ===
info stack                      # 回溯（调用链）
backtrace                       # 同 info stack（bt）
frame 2                         # 切换到栈帧 2
info frame                      # 当前栈帧的详情
info locals                     # 当前栈帧的局部变量
info args                       # 当前函数的参数

# === 反汇编 ===
disassemble main                # 反汇编 main 函数
disassemble /r main             # 带原始字节
disassemble 0x401000,0x401050   # 指定地址范围
layout asm                      # 分屏：源码 + 汇编
layout regs                     # 分屏：寄存器 + 汇编

# === 进程信息 ===
info proc maps                  # 虚拟内存映射
info files                      # 文件与节
info sharedlibrary              # 已加载的共享库
shell cat /proc/self/maps        # 另一种方式：在 gdb 里执行 shell 命令

# === 观察点 ===
watch $rax                      # rax 的值变化时中断
watch *0x602000                 # 该地址的内存变化时中断
rwatch *0x602000                # 该内存被读取时中断
awatch *0x602000                # 读或写时中断

# === 便捷设置 ===
define hook-stop                # 每次停下时自动执行命令
  x/5i $rip
  info registers rax rbx rcx rdx rsi rdi rsp rbp
end

# 把 GDB 命令保存到文件
echo "break main\nrun\ninfo registers" > gdb_script.txt
gdb -x gdb_script.txt ./binary

# 或者在 GDB 里用 Python
python print(gdb.parse_and_eval('$rax'))
```

### GDB 工作流：调试段错误

```bash
gdb ./segfaulting_program
(gdb) run arg1
# 程序收到 SIGSEGV
(gdb) backtrace             # 是哪些函数调用到这里来的？
(gdb) frame 0               # 切到出错的那个栈帧
(gdb) info registers        # 寄存器里当时是什么？
(gdb) x/20i $rip-20         # 我们刚才在执行哪些指令？
# rip = 0x00000000 表示我们经由空指针跳转了
# rip = 0x41414141 表示我们经由被破坏的指针（'AAAA'）跳转了
# rip = （栈地址）表示我们跳到了栈上 —— 缓冲区溢出
(gdb) x/32gx $rsp           # 看看栈
(gdb) x/s $rdi              # 某个字符串参数被破坏了吗？
```

---

## 19. CTF 平台指南

CTF（Capture The Flag）竞赛提供安全、合法的环境，让你针对故意留有漏洞的系统练习进攻技术。它们是理论与真实技能之间的桥。

### 在哪里练习

| 平台 | 类型 | 最适合 |
|----------|------|---------|
| [picoCTF](https://picoctf.org) | 对初学者友好 | 第一批题 —— 第 4 周从这里开始 |
| [pwn.college](https://pwn.college) | 专注二进制利用 | 汇编与利用题 |
| [Hack The Box](https://www.hackthebox.com) | 完整靶机 | Web、Linux 提权、逆向 |
| [TryHackMe](https://tryhackme.com) | 引导式路径 | 结构化学习，适合初学者 |
| [CTFtime](https://ctftime.org) | 赛事聚合 | 进行中的比赛与存档 |
| [crackmes.one](https://crackmes.one) | 只有逆向 | crackme 二进制 |
| [CryptoHack](https://cryptohack.org) | 只有密码学 | 密码学题目 |
| [OverTheWire Bandit](https://overthewire.org/wargames/bandit/) | Linux 基础 | 命令行与基础 |

### 阶段 0 的 CTF 日程

**第 4 周 —— 开始 picoCTF：**
- 类别：General Skills（先把所有 “Easy” 题做完）
- 目标：每周至少 5 道题

**第 6 周 —— 加上 picoCTF 取证：**
- strings、hexdump、文件类型识别

**第 8 周 —— 加上 picoCTF 密码学：**
- 与第 7 节对应；ROT13、凯撒、base64、XOR

**第 12 周 —— 加上 picoCTF 逆向工程：**
- 简单的 crackme、入门逆向

**第 14 周 —— 加上 pwn.college 汇编：**
- 与第 5 节直接对应

**第 18 周 —— 加上 OverTheWire Bandit：**
- 应用 Bash 与 Linux 基础

**第 22 周 —— 试试你的第一台 Hack The Box Easy 靶机：**
- 侦察、枚举、Web 漏洞基础

### 两小时规则

卡在一道 CTF 题上时：
1. 在看提示之前，至少认真尝试 2 小时
2. 2 小时之后：去看提示或题解
3. **读题解，然后关掉它，用你学到的东西自己把题解出来**
4. 在你的 Obsidian 库里写一条笔记：技术点是什么？你原来不知道什么？

读题解不是作弊。不理解就抄答案是作弊（坑的是你自己）。

---

## 20. 常见失败点与修复

> 那 30% 退出的人，是在第 3-6 周退出的。下面就是具体的失败模式。现在就读，趁它们还没发生。

---

**失败：“我读了这一章，但还是不懂指针。”**

修复：合上书。打开终端。写下这个程序，编译它，运行它：
```c
int x = 5;
int *p = &x;
printf("x=%d addr=%p *p=%d\n", x, (void*)p, *p);
*p = 99;
printf("x=%d\n", x);
```
现在把它画在纸上。给 x 画个方框。从 p 画一支箭头。箭头指着什么？当你顺着箭头写入时发生了什么？概念是通过构建打通的，不是通过阅读。

---

**失败：“程序能编译，但一运行就崩，错误信息没有任何用。”**

修复：始终带 sanitizer 编译：`gcc -fsanitize=address,undefined -g -O0`。如果 ASan 没显示出错误，就在 Valgrind 下运行。如果 Valgrind 也没显示，就在 GDB 下运行：`gdb ./program`、`run`，崩溃时执行 `backtrace`。错误总是能被找到。总是。

---

**失败：“我不知道自己是否准备好进入下一节。”**

修复：翻到第 4 节（检查点），动手做你当前这一节对应的条目。不要只在脑子里过 —— 在终端里做。如果不查资料就做不出来，你就还没准备好。那不是失败 —— 那是诚实的校准。再多花一周构建。

---

**失败：“汇编完全讲不通。就是一堆乱码字符。”**

修复：用 Godbolt。写最简单的 C 函数 —— `int add(int a, int b) { return a + b; }` —— 看汇编输出。每一行汇编都对应你 C 里的某样东西。当你能并排看到两者时，这个对应关系就显而易见了。

---

**失败：“我在这一阶段待了 4 个月，感觉毫无进展。”**

修复：打开你的 Obsidian 库。看看你第 1 周写的东西，对比你现在能写的东西。进展是真实的 —— 你离得太近所以看不见。具体的诊断方法：回到第 2 周的练习，看你现在多快能做完。进展是拿过去的自己比，不是拿某个想象出来的标准比。

---

**失败：“一道 CTF 题卡了 3 天，然后我放弃了。”**

修复：套用两小时规则（第 19 节）。然后正确地使用题解：理解技术点，关掉它，从头重解一遍。一道没解出来的题，不代表你做不到。它代表你摸到了当前知识的边界。那条边界正是你成长的地方。

---

**失败：“网络那一节太抽象了。我看不出它和进攻有什么关系。”**

修复：运行 `wireshark`，随便浏览一个 HTTP 网站。实时看你的 TCP 握手。看你的 DNS 查询。看那些数据包字节。当你看到真实流量时，抽象就塌了。第 4 节的每个概念都能在任何一次抓包里看见。

---

**失败：“我全都装好了，可 GDB 只显示 'No symbol table loaded'。”**

修复：带 `-g` 标志编译：`gcc -g -O0 -o program program.c`。`-g` 标志会嵌入调试信息（DWARF 格式），GDB 需要它才能显示源码行、变量名和函数名。没有它，GDB 也能用，但只显示地址。

---

**失败：“我不知道 ARM64 是什么。新加的第 8 节让人望而生畏。”**

修复：第 8 节不要求你在阶段 0 为 ARM64 构建任何东西。它只要求你读寄存器表、能用两句话讲清调用约定的差异、并且能用 `file` 识别出 ARM64 二进制。仅此而已。完整的 ARM64 利用工作是阶段 3。现在种下种子，日后收获。

---

**失败：“我连着两周只读文档，什么也没动手做。”**

修复：关掉文档。打开文本编辑器。做点东西 —— 任何东西 —— 跟刚读的内容相关。哪怕它是错的。哪怕它会崩。构建会强迫你面对自己真正理解的东西与自以为理解的东西之间的差距。只读不建，就是操作者长出危险盲区的方式。

---

## 21. 阶段 0 总清单

在这一节每一项都被勾上之前，不要进入阶段 1。这些是入场条件。

### 操作系统
- [ ] 凭记忆讲清 fork/exec 及其正确的系统调用
- [ ] 浏览 `/proc/[pid]/` 并识别其中每一个主要文件
- [ ] 凭记忆画出虚拟地址空间布局（text、data、bss、堆、mmap、栈）
- [ ] 用两段话解释虚拟内存与页表
- [ ] 解释系统调用机制：`syscall` 指令执行时发生了什么
- [ ] 掌握 x86-64 Linux 上最重要的 15 个系统调用号

### Bash 脚本
- [ ] 写一个函数，在管道里用 grep + awk + sed 处理日志文件
- [ ] 为一个多文件 C 项目写 Makefile
- [ ] 写一个脚本，从文件读取 IP，并对每个 IP 做点什么
- [ ] 正确使用 `set -euo pipefail`，并解释每个标志的作用
- [ ] 知道如何把 stdout、stderr 以及两者分别重定向到文件或彼此

### C 编程
- [ ] 用一个具体例子解释指针算术
- [ ] 写一个可用的动态数据结构（链表、栈或队列）
- [ ] 写一个完全不引入 libc 头文件、直接发起系统调用的程序
- [ ] 对自己的代码跑 Valgrind 与 AddressSanitizer，并看懂输出
- [ ] 写一个带 `all`、`clean`、`debug`、`release` 目标的可用的 Makefile

### Python 脚本
- [ ] 从零写一个 TCP 客户端与服务端
- [ ] 用 `struct.pack` 和 `struct.unpack` 解析一种二进制文件格式
- [ ] 用 Scapy 发送 ARP 请求并解析响应
- [ ] 用原始套接字写一个端口扫描器

### 网络
- [ ] 追踪一个数据包从应用层到物理层再返回
- [ ] 逐字节解释 TCP 三次握手
- [ ] 解释 DNS 解析从查询到应答（每一步）
- [ ] 读一份 Wireshark 抓包，识别出 TCP、DNS 和 HTTP 流量
- [ ] 一眼认出 IPv6 地址；解释 `::1` 和 `fe80::/10`
- [ ] 掌握最重要的 6 种 DNS 记录类型

### 汇编与调试
- [ ] 说出所有 x86-64 通用寄存器及其在调用约定中的角色
- [ ] 写一个可从 C 调用的 NASM 函数
- [ ] 用带 GEF 的 GDB 单步跟踪汇编，并检查寄存器与内存
- [ ] 解释 x86-64 调用约定：参数寄存器、返回寄存器、被调用者/调用者保存
- [ ] 用两句话说明 ARM64 调用约定与 x86-64 的差异
- [ ] 用 `objdump -d -M intel` 反汇编一个二进制并读懂输出

### 逆向工程
- [ ] 在 Ghidra 中打开一个二进制，分析它，定位到 main()，读反编译输出
- [ ] 用 `readelf -S` 和 `readelf -h` 提取二进制元数据
- [ ] 用 `strace` 跟踪程序的系统调用
- [ ] 用 `ltrace` 跟踪程序的库调用
- [ ] 不打补丁解出一个入门级 crackme
- [ ] 解释 ELF（Linux）与 PE（Windows）格式结构的差异

### 密码学
- [ ] 从零实现 XOR 加密与解密
- [ ] 用频率分析破解单字节 XOR（要写出实现，不只是理解）
- [ ] 解释为什么优先选 AES-GCM 而不是 AES-ECB
- [ ] 解释 TLS 证书是什么，以及信任链意味着什么
- [ ] 用 Python 的 hashlib 计算一个文件的 SHA-256

### ARM64 与 glibc
- [ ] 说出 ARM64 用于函数参数的寄存器
- [ ] 用 `file` 识别一个 ARM64 二进制
- [ ] 知道自己所用 Ubuntu 版本的 glibc 版本号
- [ ] 用一句话解释 glibc 版本为什么对堆利用重要

### 项目
- [ ] 项目 1：shell 能正确处理管道与 I/O 重定向
- [ ] 项目 2：分配器在 Valgrind 和 ASan 下零错误通过
- [ ] 项目 3：数据包嗅探器写出合法的 pcap（在 Wireshark 中确认）
- [ ] 项目 4：所有汇编函数都通过测试台
- [ ] 项目 5：crackme 已解出，分析文档已写进 Obsidian

### 知识库
- [ ] Obsidian 库已建好，结构有条理
- [ ] 至少写了 20 条笔记（每个概念一条）
- [ ] 个人的 GDB 速查表已根据真实会话经验整理出来
- [ ] CTF 题解笔记：至少记录了 10 道题，并附技术点说明

---

## 22. 接下来是什么

**阶段 1：Web 应用安全**

你会把网络知识用到 Web 目标上。主题包括：

- 深入 HTTP：cookie、会话、认证、CORS
- OWASP Top 10：SQL 注入、XSS、CSRF、XXE、SSRF、IDOR、认证失效
- Web 侦察：子域名枚举、目录爆破、技术栈指纹识别
- Burp Suite：拦截、修改、重放、模糊测试 HTTP 请求
- API 安全：REST、GraphQL、JWT 攻击
- 文件上传漏洞与 webshell

你的阶段 0 基础之所以能支撑这些，是因为你理解：TCP（HTTP 连接为什么能工作）、DNS（侦察如何映射到 IP）、Python 套接字（curl 和 HTTP 为什么只是套接字操作）、以及 C 字符串（SQL 注入与 XSS 本质上是输入处理缺陷）。

---

## 23. 资源汇总

### 操作系统

| 资源 | URL |
|----------|-----|
| Operating Systems: Three Easy Pieces | https://pages.cs.wisc.edu/~remzi/OSTEP/ |
| Linux Kernel Labs | https://linux-kernel-labs.github.io/ |
| Linux Programming Interface | https://man7.org/tlpi/ |
| Linux Syscall Table (x86-64) | https://syscall.sh |
| Linux Syscall Table (ARM64) | https://arm64.syscall.sh |

### Bash 与工具

| 资源 | URL |
|----------|-----|
| Bash Scripting Cheatsheet | https://devhints.io/bash |
| Shell Scripting Tutorial | https://www.shellscript.sh/ |
| Art of Command Line | https://github.com/jlevy/the-art-of-command-line |
| CommandLineFu | https://www.commandlinefu.com/ |

### C 编程

| 资源 | URL |
|----------|-----|
| The C Programming Language (K&R) | ISBN 978-0131103627 |
| Beej's Guide to C | https://beej.us/guide/bgc/ |
| Learn C the Hard Way | https://learncodethehardway.org/c/ |
| CS50 (Harvard) | https://cs50.harvard.edu/x/ |

### Python

| 资源 | URL |
|----------|-----|
| Automate the Boring Stuff | https://automatetheboringstuff.com/ |
| Black Hat Python | https://nostarch.com/black-hat-python2E |
| Scapy Documentation | https://scapy.readthedocs.io/ |
| pwntools Documentation | https://docs.pwntools.com/ |

### 网络

| 资源 | URL |
|----------|-----|
| Beej's Guide to Network Programming | https://beej.us/guide/bgnet/ |
| Julia Evans (networking deep dives) | https://jvns.ca/ |
| Wireshark Sample Captures | https://wiki.wireshark.org/SampleCaptures |
| Practical Packet Analysis | https://nostarch.com/packetanalysis3 |

### 汇编

| 资源 | URL |
|----------|-----|
| x86-64 Instruction Reference | https://www.felixcloutier.com/x86/ |
| Godbolt Compiler Explorer | https://godbolt.org |
| NASM Documentation | https://www.nasm.us/doc/ |
| Azeria Labs ARM Assembly | https://azeria-labs.com/writing-arm-assembly-part-1/ |
| ARM Architecture Reference Manual | https://developer.arm.com/documentation/ddi0487/latest |

### 逆向工程

| 资源 | URL |
|----------|-----|
| Ghidra Releases | https://github.com/NationalSecurityAgency/ghidra/releases |
| Ghidra Book | https://nostarch.com/GhidraBook |
| Binary Ninja | https://binary.ninja |
| IDA Free | https://hex-rays.com/ida-free |
| Practical Malware Analysis | https://nostarch.com/malware |
| Reverse Engineering for Beginners | https://beginners.re/ |
| LiveOverflow (YouTube) | https://www.youtube.com/@LiveOverflow |

### 密码学

| 资源 | URL |
|----------|-----|
| Cryptopals Challenges | https://cryptopals.com |
| CryptoHack | https://cryptohack.org |
| Serious Cryptography | https://nostarch.com/seriouscrypto |
| Crypto 101 | https://www.crypto101.io/ |
| Dan Boneh Cryptography I | https://www.coursera.org/learn/crypto |

### CTF 平台

| 平台 | URL |
|----------|-----|
| picoCTF | https://picoctf.org |
| pwn.college | https://pwn.college |
| Hack The Box | https://www.hackthebox.com |
| TryHackMe | https://tryhackme.com |
| CTFtime | https://ctftime.org |
| crackmes.one | https://crackmes.one |
| OverTheWire | https://overthewire.org/wargames/ |

### 堆与 glibc

| 资源 | URL |
|----------|-----|
| how2heap | https://github.com/shellphish/how2heap |
| heap-exploitation book | https://heap-exploitation.dhavalkapil.com/ |
| glibc source (2.35) | https://sourceware.org/git/?p=glibc.git |

---

<div align="right">

*阶段 0 完成。地基已经稳了。阶段 1 开始。*<br/>
*The BlackHAT Roadmap | 维护者 Sagar Biswas ([@SagarBiswas-MultiHAT](https://github.com/SagarBiswas-MultiHAT))*<br/>
*精选生态：[Awesome Cybersecurity Paths](https://github.com/SagarBiswas-MultiHAT/awesome-cybersecurity-paths) · [Penetration Testing Roadmap](https://github.com/SagarBiswas-MultiHAT/penetration-testing-roadmap) · [Awesome Cybersecurity Books](https://github.com/SagarBiswas-MultiHAT/awesome-cybersecurity-books)*<br/>
*按 Creative Commons Attribution-ShareAlike 4.0 International（CC BY-SA 4.0）许可发布*

</div>

---