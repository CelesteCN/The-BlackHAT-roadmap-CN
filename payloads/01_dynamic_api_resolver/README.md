# 实验 01：通过 PEB 遍历与导出哈希实现动态 API 解析

## 架构概览

标准 Windows 可执行文件在导入地址表（IAT）中声明依赖。安全软件、静态特征引擎与 EDR 代理会在文件入库时检查 IAT，以评估可疑能力指标（例如是否导入 `VirtualAlloc`、`WriteProcessMemory`、`CreateRemoteThread`）。

本实验演示操作员如何把能力执行与静态 IAT 解耦：

1. **遍历进程环境块（PEB）**：直接访问 `GS:[0x60]`（x64 上），以定位已加载模块链表（`InLoadOrderModuleList` / `InMemoryOrderModuleList`），而不调用 `GetModuleHandle`。
2. **解析导出地址表（EAT）**：直接解析目标 DLL 的 DOS 头、NT 头与可选头数据目录，以检查导出符号的 RVA。
3. **DJB2 哈希比对**：用预计算的哈希值与函数名比对，而不是在 `.rdata` 节中保存明文函数名。

## 编译

在 Linux 或 Windows 上使用 MinGW-w64：

```bash
x86_64-w64-mingw32-gcc -Wall -O2 -s -o resolver.exe main.c
```

或使用 Microsoft Visual C++（`cl.exe`）：

```cmd
cl.exe /O2 /W3 main.c
```
