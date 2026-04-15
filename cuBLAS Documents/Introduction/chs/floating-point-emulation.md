## 1.5. 浮点模拟

浮点模拟首次引入于CUDA 12.9，用于进一步加速高精度的矩阵乘法。浮点模拟的工作原理是：首先将输入转换为多个低精度值，然后利用低精度硬件单元计算部分结果，最后将结果重新组合为完整精度。这些算法可以在保持相同或更好精度的同时，提供比原生精度运算显著的性能优势；然而，结果不符合IEEE-754标准。

| 浮点模拟算法 | 模拟精度 | 支持的计算能力 | CUDA版本 |
| --- | --- | --- | --- |
| BF16x9 | FP32 | 10.0, 10.3 | 12.9+ |
| Fixed-Point | FP64 | 8.x, 9.0, 10.0, 11.0, 12.x | 13.0u2+ |

无需任何代码更改即可启用浮点模拟，可以使用以下环境变量。

| 环境变量 | 描述 |
| --- | --- |
| CUBLAS_EMULATION_STRATEGY | 用于覆盖默认模拟策略的环境变量。有效值为performant和eager；更多详情请参见cublasEmulationStrategy_t。 |
| CUBLAS_EMULATION_SPECIAL_VALUES_SUPPORT_MASK | 用于覆盖模拟中默认特殊值支持掩码的环境变量。该值是一个位掩码，其中位0表示无穷大支持，位1表示NaN支持；更多详情请参见cudaEmulationSpecialValuesSupport_t。这相当于使用指定的掩码调用cublasSetEmulationSpecialValuesSupport()。 |
| CUBLAS_EMULATE_SINGLE_PRECISION | 用于启用和禁用单精度浮点模拟的环境变量，分别使用值1和0。 |
| CUBLAS_EMULATE_DOUBLE_PRECISION | 用于启用和禁用双精度浮点模拟的环境变量，分别使用值1和0。 |
| CUBLAS_FIXEDPOINT_EMULATION_MANTISSA_BIT_COUNT | 用于定点模拟的尾数位数。当设置时，模拟算法将使用指定的尾数位数。这相当于使用CUDA_EMULATION_MANTISSA_CONTROL_FIXED（参见cudaEmulationMantissaControl_t）调用cublasSetFixedPointEmulationMantissaControl()，并使用用户提供的值调用cublasSetFixedPointEmulationMaxMantissaBitCount()。 |



### 1.5.1. BF16x9

BF16x9算法用于模拟FP32运算。FP32值可以精确表示为三个BF16值，如下所示：



```

\[\begin{split}a & = a_0 + 2^{-8} a_1 + 2^{-16} a_2 \\\end{split}\]
```


我们可以通过BF16值完整重建FP32值，不会造成任何精度损失。基于此，我们定义FMA运算（d = ab + c）如下：



```

\[\begin{split}d & = ab + c \\
  & = (a_0 + 2^{-8} a_1 + 2^{-16} a_2) \cdot (b_0 + 2^{-8} b_1 + 2^{-16} b_2) + c \\
  & = a_0b_0 + 2^{-8}a_0b_1 + 2^{-16}a_0b_2 \\
  & \quad + 2^{-8}a_1b_0 + 2^{-16}a_1b_1 + 2^{-24}a_1b_2 \\
  & \quad + 2^{-16}a_2b_0 + 2^{-24}a_2b_1 + 2^{-32}a_2b_2 + c \\\end{split}\]
```


在实践中，使用BF16张量核心而非FMA单元，并且这个思想自然地扩展到复数运算。

虽然BF16x9可以在所有硬件上支持，但只有当峰值BF16吞吐量超过峰值FP32吞吐量的9倍以上时，才能提供性能优势。它还需要特殊的硬件特性来以高性能的方式应用额外的缩放因子。因此，BF16x9仅在特定架构上受支持。更多详情请参见浮点模拟支持概述表。




### 1.5.2. Fixed-Point

定点模拟用于模拟FP64运算，遵循[Ozaki Scheme](https://doi.org/10.1177/10943420241239588)。定点表示通过添加共享的二进制缩放因子来模拟浮点数，并通过在尾数位中编码浮点数的剩余动态范围。缩放因子在矩阵A同一行的元素或矩阵B同一列的元素之间共享，用于将所有元素逻辑缩放到-1到1之间（包括边界）。

由于FP64的动态范围很大，没有单一的定点配置能够同时满足所有浮点数输入的性能和精度要求。因此，我们启用了两种定点模拟变体：动态尾数控制和固定尾数控制。这些配置可以通过cublasSetFixedPointEmulationMantissaControl()设置。




#### 1.5.2.1. Dynamic Mantissa Control

动态尾数控制代表cuBLAS库的默认尾数控制。我们的自动动态精度框架计算维持与FP64相同或更好精度所需的固定点尾数位数。如果所需尾数位数超过库定义的默认值（参见默认库配置）或用户提供的最大位数（参见cublasSetFixedPointEmulationMaxMantissaBitCount()），该框架将动态调度到原生FP64。




#### 1.5.2.2. Fixed Mantissa Control

固定尾数控制可用于进一步加速定点模拟。用户可以通过cublasSetFixedPointEmulationMaxMantissaBitCount()提供定点表示的尾数位数；但是，如果没有自动动态精度框架，则无法保证与FP64运算相同或更好的精度。




#### 1.5.2.3. Representation and Mappings

定点表示由矩阵同一行或列元素的共享缩放因子、一个符号位和尾数位组成。我们将符号位和尾数位存储在8位整数中。每组8位整数矩阵称为一个切片，计算成本随切片数量呈二次增长。尾数位数转换为切片数量的公式如下：



```

\[\text{sliceCount} = \text{ceildiv}(\text{mantissaBitCount} + 1, 8)\]
```


> **注意**

尾数位数将始终向上取整，以完全占用最低有效切片。





#### 1.5.2.4. Fixed-Point Workspace Requirements

为了使用定点模拟进行计算，A和B矩阵在工作区内存中被转换为定点表示。这导致工作区需求取决于问题大小和模拟参数。以下函数将提供定点模拟所需工作区的安全上限（可能高估）：



```c++
// 获取定点工作区大小（以字节为单位）的函数
// 参数：m, n, k - 矩阵维度，batchCount - 批次数量
// isComplex - 是否为复数，mantissaControl - 尾数控制模式
// maxMantissaBitCount - 最大尾数位数
size_t getFixedPointWorkspaceSizeInBytes(int m, int n, int k, int batchCount, bool isComplex,
                cudaEmulationMantissaControl mantissaControl, int maxMantissaBitCount) {
    constexpr double MULTIPLIER = 1.25;  // 安全系数乘数

    int mult = isComplex ? 2 : 1;  // 复数倍数
    int numSlices = ceildiv(maxMantissaBitCount + 1, 8);  // 计算切片数量
    int max_splitk = ceildiv(opts.k, 8192);  // 最大split-k值

    // 对矩阵维度进行填充以优化内存访问
    int padded_m = ceildiv(m, 1024) * 1024;
    int padded_n = ceildiv(n, 1024) * 1024;
    int padded_k = ceildiv(k, 128) * 128;
    int num_blocks_k = ceildiv(k, 64);

    // 计算GEMM工作区大小
    size_t gemm_workspace = sizeof(int8_t) *
        ((size_t)padded_m * padded_k + (size_t)padded_n * padded_k) * mult * numSlices;
    gemm_workspace += sizeof(int32_t) * ((size_t)padded_m + padded_n) * mult;

    // 计算累加器工作区大小 - 版本1
    size_t acc_workspace_ver1 = 0;
    if (isComplex) {
        acc_workspace_ver1 += sizeof(double) * (size_t)m * n * mult * mult;
    }
    // 计算累加器工作区大小 - 版本2
    size_t acc_workspace_ver2 = std::min(sizeof(int32_t) * ((size_t)padded_m * padded_n) * mult * mult * numSlices,
                                         (size_t)(1LL << 32)) *
                                max_splitk;
    gemm_workspace += std::max(acc_workspace_ver1, acc_workspace_ver2);

    // 计算自适应工作区大小
    size_t adp_workspace = 0;
    if (mantissaControl == CUDA_EMULATION_MANTISSA_CONTROL_DYNAMIC) {
        adp_workspace = sizeof(int32_t) * ((size_t)m * num_blocks_k + (size_t)n * num_blocks_k +
                         (size_t)m * n) * mult;
    }

    constexpr size_t CONSTANT_SIZE = 128 * 1024 * 1024;  // 常量大小
    // 返回最大工作区大小并应用乘数和批次数量
    return (size_t)(std::max(gemm_workspace, adp_workspace) * batchCount * MULTIPLIER) + CONSTANT_SIZE;
}
```

此函数可用于管理您自己的工作区内存，并与cublasSetWorkspace()配合使用，这可用于保证结果的可重现性并提高性能。




#### 1.5.2.5. Fixed-Point Performance Guide

定点模拟允许用户进行性能和精度的权衡以实现进一步加速。对于动态尾数控制，用户可以使用cublasSetFixedPointEmulationMantissaBitOffset()配置自动动态精度框架，以使用比原生FP64所需精度更少或更多的位数。固定尾数控制可以通过使用cublasSetFixedPointEmulationMaxMantissaBitCount()增加或减少尾数位数来进行类似的调整。

由于定点工作区需求较大，异步分配使用cudaMallocAsync()完成。在GEMM调用不足以分摊内存分配成本的情况下，或者当频繁发生CUDA流同步时，您可以通过以下方式提高性能：


- 减少CUDA流同步次数
- 管理您自己的内存并使用cublasSetWorkspace()提供工作区
- 允许默认内存池在同步之间保留内存




### 1.5.3. Default Library Configurations

模拟的库默认值可能会发生变化。

| API | 尾数控制 | 默认行为 |
| --- | --- | --- |
| cublasGetEmulationStrategy() | 不适用 | CUBLAS_EMULATION_STRATEGY_DEFAULT |
| cublasGetEmulationSpecialValuesSupport() | 不适用 | CUBLAS_EMULATION_SPECIAL_VALUES_SUPPORT_DEFAULT |
| cublasGetFixedPointEmulationMantissaControl() | 不适用 | CUDA_EMULATION_MANTISSA_CONTROL_DYNAMIC |
| cublasGetFixedPointEmulationMaxMantissaBitCount() | CUDA_EMULATION_MANTISSA_CONTROL_DYNAMIC | 79 |
| cublasGetFixedPointEmulationMaxMantissaBitCount() | CUDA_EMULATION_MANTISSA_CONTROL_FIXED | 55 |
| cublasGetFixedPointEmulationMantissaBitOffset() | 不适用 | 0 |
| cublasGetFixedPointEmulationMantissaBitCountPointer() | 不适用 | NULL |




### 1.5.4. Support For Floating Point Special Values

浮点模拟算法的实现对于正规化和非正规化值都保持了模拟精度的准确性，但可能不会在$\text{Inf}$、$\text{NaN}$或带符号零方面遵守IEEE-754标准。如果底层模拟算法不能隐式支持给定的特殊值，且库配置为支持它（参见cublasSetEmulationSpecialValuesSupport()），则会采取额外步骤来支持它。下表显示了每种模拟算法隐式支持哪些特殊值。


| 浮点模拟算法 | 隐式支持的特殊值 |
| --- | --- |
| BF16x9 | \(\text{NaN}\) |
| Fixed-Point | 无 |