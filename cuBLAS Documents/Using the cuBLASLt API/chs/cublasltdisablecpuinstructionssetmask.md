### 3.4.3. cublasLtDisableCpuInstructionsSetMask()

```c++

unsigned cublasLtDisableCpuInstructionsSetMask(unsigned mask);


```

指示 cuBLASLt 库不要使用 `mask` 中标志所指定的 CPU 指令。此函数的优先级高于 `CUBLASLT_DISABLE_CPU_INSTRUCTIONS_MASK` 环境变量。

**参数：** `mask` – 通过按位 OR(|) 运算符合并的标志，用于指定不应使用的 CPU 指令。

支持的标志：

| 值 | 描述 |
| --- | --- |
| 0x1 | x86-64 AVX512 ISA。 |

**返回值：** `mask` 的前一个值。