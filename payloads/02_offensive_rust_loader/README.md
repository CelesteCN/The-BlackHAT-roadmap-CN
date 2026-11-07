# 实验 02：进攻性 Rust 内存加载器

## 架构概览

现代端点检测与响应（EDR）代理会主动检查以 `PAGE_EXECUTE_READWRITE`（RWX）分配的内存区域。创建 RWX 分配会立刻触发内存扫描器与行为启发式规则。

本实验演示 Rust 中的现代载荷执行机制：

1. **状态翻转（RW -> RX）**：以 `PAGE_READWRITE` 分配、写入载荷字节，并在派发执行前把保护属性切换为 `PAGE_EXECUTE_READ`。
2. **二进制加固**：利用 `Cargo.toml` 中的 profile 配置（`opt-level = "z"`、`lto = true`、`panic = "abort"`、`strip = true`）剥离编译产物与符号表，并减小载荷体积。

## 编译

使用 MSVC 工具链以 release 模式构建：

```bash
cargo build --release --target x86_64-pc-windows-msvc
```

构建输出路径：
`target/x86_64-pc-windows-msvc/release/offensive-rust-loader.exe`
