### 1.5.2. 定点数（Fixed-Point）

定点数仿真用于模拟 FP64 算术运算，遵循 [Ozaki Scheme](https://doi.org/10.1177/10943420241239588)。定点数表示通过添加共享的 2 的幂次缩放因子来模拟浮点数，并通过将浮点数的剩余动态范围编码到尾数位中。缩放因子对于 A 矩阵同一行或 B 矩阵同一列中的元素是共享的，用于将所有元素逻辑缩放至 -1 到 1（含）的范围内。

由于 FP64 具有较大的动态范围，因此不存在一种既能保持高性能又能保证对所有浮点输入都精确的单一定点数配置。因此，我们提供了两种定点数仿真方式：动态尾数控制（Dynamic Mantissa Control）和固定尾数控制（Fixed Mantissa Control）。这些配置可以通过 `cublasSetFixedPointEmulationMantissaControl()` 进行设置。

#### 1.5.2.1. 动态尾数控制（Dynamic Mantissa Control）

动态尾数控制表示 cuBLAS 库的默认尾数控制方式。我们的自动动态精度框架会计算保持与 FP64 精度相当或更好精度所需的定点数尾数位数。如果所需的尾数位数超过了库定义的默认值（请参阅默认库配置）或用户提供的最大位数（请参阅 `cublasSetFixedPointEmulationMaxMantissaBitCount()`），则该框架将动态调度至原生 FP64。

#### 1.5.2.2. 固定尾数控制（Fixed Mantissa Control）

固定尾数控制可用于进一步加速定点数仿真。用户可以通过 `cublasSetFixedPointEmulationMaxMantissaBitCount()` 提供定点数表示的尾数位数；但是，由于没有自动动态精度框架，无法保证与 FP64 算术运算精度相当或更好。

#### 1.5.2.3. 表示与映射（Representation and Mappings）

定点数表示由矩阵同一行或同一列元素的共享缩放因子、一个符号位和尾数位组成。我们将符号位和尾数位存储在 8 位整数中。每组 8 位整数矩阵称为一个切片（slice），计算成本随切片数量呈二次增长。将尾数位数转换为切片数量的公式如下：

```

\[\text{sliceCount} = \text{ceildiv}(\text{mantissaBitCount} + 1, 8)\]
```

> **注意**

注意
尾数位数始终会向上取整，以完全占据最低有效切片

#### 1.5.2.4. 定点数工作空间需求（Fixed-Point Workspace Requirements）

使用定点数仿真进行计算时，A 和 B 矩阵会被转换为定点数表示并存储在工作空间内存中。这导致工作空间需求取决于问题大小和仿真参数。以下函数将提供定点数仿真所需工作空间的安全上界（可能会高估）：

```c++
// 获取定点数仿真工作空间大小（以字节为单位）
// 参数：矩阵维度 m, n, k；批次数量；是否为复数；尾数控制模式；最大尾数位数
size_t getFixedPointWorkspaceSizeInBytes(int m, int n, int k, int batchCount, bool isComplex,
                cudaEmulationMantissaControl mantissaControl, int maxMantissaBitCount) {
    constexpr double MULTIPLIER = 1.25;  // 安全系数

    int mult = isComplex ? 2 : 1;  // 复数矩阵需要两倍存储
    int numSlices = ceildiv(maxMantissaBitCount + 1, 8);  // 计算切片数量
    int max_splitk = ceildiv(opts.k, 8192);  // 最大 split-K 因子

    // 对矩阵维度进行对齐填充以优化性能
    int padded_m = ceildiv(m, 1024) * 1024;
    int padded_n = ceildiv(n, 1024) * 1024;
    int padded_k = ceildiv(k, 128) * 128;
    int num_blocks_k = ceildiv(k, 64);

    // 计算 GEMM 工作空间大小
    size_t gemm_workspace = sizeof(int8_t) *
        ((size_t)padded_m * padded_k + (size_t)padded_n * padded_k) * mult * numSlices;
    gemm_workspace += sizeof(int32_t) * ((size_t)padded_m + padded_n) * mult;

    // 计算累加器工作空间大小
    size_t acc_workspace_ver1 = 0;
    if (isComplex) {
        acc_workspace_ver1 += sizeof(double) * (size_t)m * n * mult * mult;
    }
    size_t acc_workspace_ver2 = std::min(sizeof(int32_t) * ((size_t)padded_m * padded_n) * mult * mult * numSlices,
                                         (size_t)(1LL << 32)) *
                                max_splitk;
    gemm_workspace += std::max(acc_workspace_ver1, acc_workspace_ver2);

    // 计算自适应精度工作空间大小
    size_t adp_workspace = 0;
    if (mantissaControl == CUDA_EMULATION_MANTISSA_CONTROL_DYNAMIC) {
        adp_workspace = sizeof(int32_t) * ((size_t)m * num_blocks_k + (size_t)n * num_blocks_k +
                         (size_t)m * n) * mult;
    }

    constexpr size_t CONSTANT_SIZE = 128 * 1024 * 1024;  // 常量缓冲区大小
    // 返回考虑批次数量和安全系数后的总工作空间大小
    return (size_t)(std::max(gemm_workspace, adp_workspace) * batchCount * MULTIPLIER) + CONSTANT_SIZE;
}
```

此函数可用于通过 `cublasSetWorkspace()` 管理您自己的工作空间内存，从而确保结果可重现并提高性能。

#### 1.5.2.5. 定点数性能指南（Fixed-Point Performance Guide）

定点数仿真允许用户在性能和精度之间进行权衡，以实现进一步加速。对于动态尾数控制，用户可以使用 `cublasSetFixedPointEmulationMantissaBitOffset()` 配置自动动态精度框架，使其使用比原生 FP64 精度所需更少或更多的位数。固定尾数控制也可以通过使用 `cublasSetFixedPointEmulationMaxMantissaBitCount()` 增加或减少尾数位数来进行类似的调优。

由于定点数工作空间需求较大，异步分配使用 `cudaMallocAsync()` 完成。在调用次数不足以分摊内存分配成本，或频繁进行 CUDA 流同步的情况下，您可以通过以下方式提高性能：

- 减少 CUDA 流同步的次数
- 管理自己的内存并使用 `cublasSetWorkspace()` 提供工作空间
- 允许默认内存池在同步之间保留内存