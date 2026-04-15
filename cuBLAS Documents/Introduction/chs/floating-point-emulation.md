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



##### 1.5.1. BF16x9
##### 1.5.2. Fixed-Point
###### 1.5.2.1. Dynamic Mantissa Control
###### 1.5.2.2. Fixed Mantissa Control
###### 1.5.2.3. Representation and Mappings
###### 1.5.2.4. Fixed-Point Workspace Requirements
###### 1.5.2.5. Fixed-Point Performance Guide
##### 1.5.3. Default Library Configurations
##### 1.5.4. Support For Floating Point Special Values
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

BF16x9 算法用于模拟 FP32 运算。一个 FP32 值可以精确地表示为三个 BF16 值，如下所示：

```

\[\begin{split}a & = a_0 + 2^{-8} a_1 + 2^{-16} a_2 \\\end{split}\]
```

我们可以从 BF16 值完整地重建 FP32 值，而不会有任何精度损失。利用这一点，我们定义 FMA 运算（d = ab + c）如下：

```

\[\begin{split}d & = ab + c \\
  & = (a_0 + 2^{-8} a_1 + 2^{-16} a_2) \cdot (b_0 + 2^{-8} b_1 + 2^{-16} b_2) + c \\
  & = a_0b_0 + 2^{-8}a_0b_1 + 2^{-16}a_0b_2 \\
  & \quad + 2^{-8}a_1b_0 + 2^{-16}a_1b_1 + 2^{-24}a_1b_2 \\
  & \quad + 2^{-16}a_2b_0 + 2^{-24}a_2b_1 + 2^{-32}a_2b_2 + c \\\end{split}\]
```

在实践中，使用 BF16 张量核心而不是 FMA 单元，并且这个概念也可以自然地扩展到复数运算。

虽然 BF16x9 可以在所有硬件上支持，但只有当峰值 BF16 吞吐量超过峰值 FP32 吞吐量的九倍时，它才能提供性能优势。它还需要特殊的硬件功能来以高性能的方式应用额外的缩放因子。因此，BF16x9 仅在特定架构上支持。有关更多详细信息，请参阅浮点模拟支持概述表。

仿真模式的库默认值可能会发生变化。

| API | 尾数控制 | 默认行为 |
| --- | --- | --- |
| `cublasGetEmulationStrategy()` | 不适用 | `CUBLAS_EMULATION_STRATEGY_DEFAULT` |
| `cublasGetEmulationSpecialValuesSupport()` | 不适用 | `CUBLAS_EMULATION_SPECIAL_VALUES_SUPPORT_DEFAULT` |
| `cublasGetFixedPointEmulationMantissaControl()` | 不适用 | `CUDA_EMULATION_MANTISSA_CONTROL_DYNAMIC` |
| `cublasGetFixedPointEmulationMaxMantissaBitCount()` | `CUDA_EMULATION_MANTISSA_CONTROL_DYNAMIC` | 79 |
| `cublasGetFixedPointEmulationMaxMantissaBitCount()` | `CUDA_EMULATION_MANTISSA_CONTROL_FIXED` | 55 |
| `cublasGetFixedPointEmulationMantissaBitOffset()` | 不适用 | 0 |
| `cublasGetFixedPointEmulationMantissaBitCountPointer()` | 不适用 | `NULL` |

动态尾数控制代表 cuBLAS 库的默认尾数控制方式。我们的自动动态精度框架会计算维持与 FP64 相同或更高精度所需的适当定点尾数位数。如果所需尾数位数超过了库定义的默认值（参见默认库配置），或超过了用户提供的最大位数（参见 `cublasSetFixedPointEmulationMaxMantissaBitCount()`），该框架将动态调度到原生 FP64。

固定尾数控制可用于进一步加速定点模拟。用户可以通过 `cublasSetFixedPointEmulationMaxMantissaBitCount()` 为定点表示提供尾数位数；然而，如果没有自动动态精度框架，则无法保证达到或优于FP64算术的精度。

定点仿真允许用户在性能和精度之间进行权衡，以实现进一步的加速。对于动态尾数控制，用户能够配置自动动态精度框架，使用比原生FP64精度要求更少或更多的位数，通过 `cublasSetFixedPointEmulationMantissaBitOffset()` 实现。定点尾数控制可以通过增加或减少尾数位数来类似地调整，通过 `cublasSetFixedPointEmulationMaxMantissaBitCount()` 实现。

由于定点工作区需求量大，异步分配使用 `cudaMallocAsync()` 完成。在GEMM调用次数不足以分摊内存分配成本的情况下，或者在CUDA流同步非常频繁的情况下，您可以通过以下方式提高性能：

- 减少CUDA流同步次数
- 管理自己的内存并通过 `cublasSetWorkspace()` 提供工作区
- 允许默认内存池在同步之间保留内存

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


The fixed-point representation consists of a shared scaling factor for elements in the same row or column of a matrix, a sign bit, and mantissa bits.  We store the sign bit and mantissa bits within 8-bit integers.  Each matrix of 8-bit integers are referred to as a slice and the computational cost grows quadratically with the number of slices.  The formula to convert mantissa bit count to slice count is as follows:



```

\[\text{sliceCount} = \text{ceildiv}(\text{mantissaBitCount} + 1, 8)\]
```


> **Note**

Note
The number of mantissa bits will always be rounded up to fully occupy the least significant slice





The implementations of floating point emulation algorithms maintain the accuracy of the emulated precision for both normal and denormalized values but may not adhere to the IEEE-754 standard with respect to $\text{Inf}$, $\text{NaN}$, or signed zeros.  If the underlying emulated algorithm cannot implicitly support a given special value, and the library is configured to support it (see cublasSetEmulationSpecialValuesSupport()), then extra steps are taken to support it.  The following table shows which special values are implicitly supported for each emulation algorithm.


| Floating Point Emulation Algorithm | Implicitly Supported Special Values |
| --- | --- |
| BF16x9 | \(\text{NaN}\) |
| Fixed-Point | None |


