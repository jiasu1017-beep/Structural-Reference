#### 1.5.2.4. 定点工作空间需求

为了使用定点模拟进行计算，A 和 B 矩阵被转换为工作空间内存中的定点表示。这导致工作空间需求依赖于问题大小和模拟参数。以下函数将提供定点模拟所需工作空间的安全界限（可能高估）：

```c++
size_t getFixedPointWorkspaceSizeInBytes(int m, int n, int k, int batchCount, bool isComplex,
                cudaEmulationMantissaControl mantissaControl, int maxMantissaBitCount) {
    // 倍数因子，用于安全估算
    constexpr double MULTIPLIER = 1.25;

    int mult = isComplex ? 2 : 1;  // 复数情况下系数翻倍
    int numSlices = ceildiv(maxMantissaBitCount + 1, 8);  // 计算切片数量
    int max_splitk = ceildiv(opts.k, 8192);  // 最大split-k值

    // 对输入维度进行对齐填充以优化内存访问
    int padded_m = ceildiv(m, 1024) * 1024;
    int padded_n = ceildiv(n, 1024) * 1024;
    int padded_k = ceildiv(k, 128) * 128;
    int num_blocks_k = ceildiv(k, 64);  // k方向上的块数

    // 计算GEMM操作所需的工作空间
    size_t gemm_workspace = sizeof(int8_t) *
        ((size_t)padded_m * padded_k + (size_t)padded_n * padded_k) * mult * numSlices;
    gemm_workspace += sizeof(int32_t) * ((size_t)padded_m + padded_n) * mult;

    // 版本1累加器工作空间（用于复数矩阵）
    size_t acc_workspace_ver1 = 0;
    if (isComplex) {
        acc_workspace_ver1 += sizeof(double) * (size_t)m * n * mult * mult;
    }
    // 版本2累加器工作空间（基于分块和最大split-k）
    size_t acc_workspace_ver2 = std::min(sizeof(int32_t) * ((size_t)padded_m * padded_n) * mult * mult * numSlices,
                                         (size_t)(1LL << 32)) *
                                max_splitk;
    gemm_workspace += std::max(acc_workspace_ver1, acc_workspace_ver2);

    // 自适应工作空间（用于动态尾数控制）
    size_t adp_workspace = 0;
    if (mantissaControl == CUDA_EMULATION_MANTISSA_CONTROL_DYNAMIC) {
        adp_workspace = sizeof(int32_t) * ((size_t)m * num_blocks_k + (size_t)n * num_blocks_k +
                         (size_t)m * n) * mult;
    }

    // 常量开销（固定开销）
    constexpr size_t CONSTANT_SIZE = 128 * 1024 * 1024;
    // 返回考虑批次和倍数的最大工作空间需求，并加上常量开销
    return (size_t)(std::max(gemm_workspace, adp_workspace) * batchCount * MULTIPLIER) + CONSTANT_SIZE;
}
```

此函数可用于通过 `cublasSetWorkspace()` 管理您自己的工作空间内存，这可用于保证可重现的结果并提高性能。