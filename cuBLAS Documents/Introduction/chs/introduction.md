# 1. 简介

cuBLAS库是BLAS（Basic Linear Algebra Subprograms，基本线性代数子程序）在NVIDIA®CUDA™运行时之上的实现。它允许用户访问NVIDIA图形处理器（GPU）的计算资源。

cuBLAS库提供四组API：

- cuBLAS API，在本文档中简称为cuBLAS API（从CUDA 6.0开始），
- cuBLASXt API（从CUDA 6.0开始），和
- cuBLASLt API（从CUDA 10.1开始）
- cuBLASDx API（不随CUDA Toolkit一起提供）

要使用cuBLAS API，应用程序必须在GPU内存空间中分配所需的矩阵和向量，用数据填充它们，调用所需的cuBLAS函数序列，然后将结果从GPU内存空间上传回主机。cuBLAS API还提供了用于向GPU写入数据和从GPU检索数据的辅助函数。

要使用cuBLASXt API，应用程序的数据可以在主机上，也可以在参与计算的任何设备上，库将负责根据用户请求将操作分配到一个或多个系统中的GPU，并将数据传输到这些GPU。

cuBLASLt是一个轻量级库，专用于通用矩阵-矩阵乘法（GEMM）操作，并提供新的灵活API。该库增加了矩阵数据布局、输入类型、计算类型以及通过参数可编程性选择算法实现和启发式的灵活性。在用户确定了目标GEMM操作的一组选项后，这些选项可以重复用于不同的输入。这类似于cuFFT和FFTW首先创建计划，然后对不同输入数据重用相同大小和类型的FFT的方式。

## 1.1. 数据布局

为了与现有Fortran环境最大程度兼容，cuBLAS库使用列优先存储和从1开始的索引。由于C和C++使用行优先存储，用这些语言编写的应用程序不能使用二维数组的本机数组语义。相反，应该定义宏或内联函数以在一维数组之上实现矩阵。对于以机械方式移植到C的Fortran代码，可以选择保留从1开始的索引以避免转换循环。在这种情况下，矩阵中第"i"行和第"j"列元素的数组索引可以通过以下宏计算

```c++
// 从1开始的索引宏定义
#define IDX2F(i,j,ld) ((((j)-1)*(ld))+((i)-1))
```

这里，ld指的是矩阵的主维度，在列优先存储的情况下，它是所分配矩阵的行数（即使只使用其中的子矩阵）。对于本机编写的C和C++代码，最可能选择从0开始的索引，在这种情况下，矩阵中第"i"行和第"j"列元素的数组索引可以通过以下宏计算

```c++
// 从0开始的索引宏定义
#define IDX2C(i,j,ld) (((j)*(ld))+(i))
```

## 1.2. 新API和旧版cuBLAS API

从4.0版本开始，cuBLAS库除了现有的旧版API外还提供了新的API。本节讨论为什么提供新API、使用它的优势以及与现有旧版API的差异。

> **警告**

警告
旧版cuBLAS API已弃用，将在未来的版本中删除。

新的cuBLAS库API可以通过包含头文件`cublas_v2.h`来使用。它具有旧版cuBLAS API不具备的以下功能：

- cuBLAS库上下文的句柄使用函数初始化，并明确传递给每个后续的库函数调用。这允许用户在同时使用多个主机线程和多个GPU时更好地控制库设置。这也允许cuBLAS API可重入。
- 标量α和β可以通过引用传递在主机或设备上，而不是仅限于在主机上按值传递。这一更改允许库函数即使在α和β由前一个内核生成时也能使用流异步执行。
- 当库例程返回标量结果时，它可以通过引用返回在主机或设备上，而不是仅限于在主机上按值返回。这一更改允许在标量结果在设备上生成并通过引用返回时异步调用库例程，从而实现最大并行度。
- 错误状态cublasStatus_t由所有cuBLAS库函数调用返回。这一更改便于调试并简化了软件开发。请注意，cublasStatus被重命名为cublasStatus_t，以与cuBLAS库中的其他类型更加一致。
- cublasAlloc()和cublasFree()函数已弃用。这一更改分别删除了围绕cudaMalloc()和cudaFree()的不必要包装器。
- 函数cublasSetKernelStream()被重命名为cublasSetStream()，以与其他CUDA库更加一致。

旧版cuBLAS API（在"使用cuBLAS旧版API"中有更详细的说明）可以通过包含头文件`cublas.h`来使用。由于旧版API与先前发布的cuBLAS库API完全相同，现有应用程序可以开箱即用，并自动使用此旧版API，无需任何源代码更改。

当前API和旧版cuBLAS API不能在同一翻译单元中同时使用：包含`cublas.h`和`cublas_v2.h`两个头文件将导致编译错误，因为符号重新声明不兼容。

一般来说，新应用程序不应使用旧版cuBLAS API，现有应用程序如果需要复杂和最佳的流并行性，或者从多个线程并发调用cuBLAS例程，应该转换为使用新API。

对于本文档的其余部分，新的cuBLAS库API将简称为cuBLAS库API。

如前所述，旧版API和cuBLAS库API的接口分别是头文件`cublas.h`和`cublas_v2.h`。此外，使用cuBLAS库的应用

程序需要链接到：

- Linux上的动态库cublas.so，
- Windows上的动态库cublas.dll，或
- Mac OS X上的动态库cublas.dylib。

> **注意**

注意
相同的动态库实现了新的和旧版的cuBLAS API。

## 1.3. 示例代码

有关示例代码参考，请参见下面的两个示例。它们展示了一个使用cuBLAS库API用C编写的应用程序，具有两种索引样式（示例1. "使用C和cuBLAS的应用程序：从1开始的索引"和示例2. "使用C和cuBLAS的应用程序：从0开始的索引"）。

```c++
//示例1. 使用C和cuBLAS的应用程序：从1开始的索引
//-----------------------------------------------------------
#include <stdio.h>
#include <stdlib.h>
#include <math.h>
#include <cuda_runtime.h>
#include "cublas_v2.h"
#define M 6
#define N 5
#define IDX2F(i,j,ld) ((((j)-1)*(ld))+((i)-1))

static __inline__ void modify (cublasHandle_t handle, float *m, int ldm, int n, int p, int q, float alpha, float beta){
    // 对从(p,q)开始的列向量进行缩放
    cublasSscal (handle, n-q+1, &alpha, &m[IDX2F(p,q,ldm)], ldm);
    // 对从(p,q)开始的行向量进行缩放
    cublasSscal (handle, ldm-p+1, &beta, &m[IDX2F(p,q,ldm)], 1);
}

int main (void){
    cudaError_t cudaStat;
    cublasStatus_t stat;
    cublasHandle_t handle;
    int i, j;
    float* devPtrA;
    float* a = 0;
    // 在主机上分配内存
    a = (float *)malloc (M * N * sizeof (*a));
    if (!a) {
        printf ("主机内存分配失败");
        return EXIT_FAILURE;
    }
    // 初始化矩阵数据
    for (j = 1; j <= N; j++) {
        for (i = 1; i <= M; i++) {
            a[IDX2F(i,j,M)] = (float)((i-1) * N + j);
        }
    }
    // 在设备上分配内存
    cudaStat = cudaMalloc ((void**)&devPtrA, M*N*sizeof(*a));
    if (cudaStat != cudaSuccess) {
        printf ("设备内存分配失败");
        free (a);
        return EXIT_FAILURE;
    }
    // 创建cuBLAS句柄
    stat = cublasCreate(&handle);
    if (stat != CUBLAS_STATUS_SUCCESS) {
        printf ("CUBLAS初始化失败\n");
        free (a);
        cudaFree (devPtrA);
        return EXIT_FAILURE;
    }
    // 将数据从主机复制到设备
    stat = cublasSetMatrix (M, N, sizeof(*a), a, M, devPtrA, M);
    if (stat != CUBLAS_STATUS_SUCCESS) {
        printf ("数据下载失败");
        free (a);
        cudaFree (devPtrA);
        cublasDestroy(handle);
        return EXIT_FAILURE;
    }
    // 执行矩阵修改操作
    modify (handle, devPtrA, M, N, 2, 3, 16.0f, 12.0f);
    // 将结果从设备复制回主机
    stat = cublasGetMatrix (M, N, sizeof(*a), devPtrA, M, a, M);
    if (stat != CUBLAS_STATUS_SUCCESS) {
        printf ("数据上传失败");
        free (a);
        cudaFree (devPtrA);
        cublasDestroy(handle);
        return EXIT_FAILURE;
    }
    // 释放设备内存和cuBLAS句柄
    cudaFree (devPtrA);
    cublasDestroy(handle);
    // 打印结果矩阵
    for (j = 1; j <= N; j++) {
        for (i = 1; i <= M; i++) {
            printf ("%7.0f", a[IDX2F(i,j,M)]);
        }
        printf ("\n");
    }
    free(a);
    return EXIT_SUCCESS;
}
```

---

```c++
//示例2. 使用C和cuBLAS的应用程序：从0开始的索引
//-----------------------------------------------------------
#include <stdio.h>
#include <stdlib.h>
#include <math.h>
#include <cuda_runtime.h>
#include "cublas_v2.h"
#define M 6
#define N 5
#define IDX2C(i,j,ld) (((j)*(ld))+(i))

static __inline__ void modify (cublasHandle_t handle, float *m, int ldm, int n, int p, int q, float alpha, float beta){
    // 对从(p,q)开始的列向量进行缩放
    cublasSscal (handle, n-q, &alpha, &m[IDX2C(p,q,ldm)], ldm);
    // 对从(p,q)开始的行向量进行缩放
    cublasSscal (handle, ldm-p, &beta, &m[IDX2C(p,q,ldm)], 1);
}

int main (void){
    cudaError_t cudaStat;
    cublasStatus_t stat;
    cublasHandle_t handle;
    int i, j;
    float* devPtrA;
    float* a = 0;
    // 在主机上分配内存
    a = (float *)malloc (M * N * sizeof (*a));
    if (!a) {
        printf ("主机内存分配失败");
        return EXIT_FAILURE;
    }
    // 初始化矩阵数据
    for (j = 0; j < N; j++) {
        for (i = 0; i < M; i++) {
            a[IDX2C(i,j,M)] = (float)(i * N + j + 1);
        }
    }
    // 在设备上分配内存
    cudaStat = cudaMalloc ((void**)&devPtrA, M*N*sizeof(*a));
    if (cudaStat != cudaSuccess) {
        printf ("设备内存分配失败");
        free (a);
        return EXIT_FAILURE;
    }
    // 创建cuBLAS句柄
    stat = cublasCreate(&handle);
    if (stat != CUBLAS_STATUS_SUCCESS) {
        printf ("CUBLAS初始化失败\n");
        free (a);
        cudaFree (devPtrA);
        return EXIT_FAILURE;
    }
    // 将数据从主机复制到设备
    stat = cublasSetMatrix (M, N, sizeof(*a), a, M, devPtrA, M);
    if (stat != CUBLAS_STATUS_SUCCESS) {
        printf ("数据下载失败");
        free (a);
        cudaFree (devPtrA);
        cublasDestroy(handle);
        return EXIT_FAILURE;
    }
    // 执行矩阵修改操作
    modify (handle, devPtrA, M, N, 1, 2, 16.0f, 12.0f);
    // 将结果从设备复制回主机
    stat = cublasGetMatrix (M, N, sizeof(*a), devPtrA, M, a, M);
    if (stat != CUBLAS_STATUS_SUCCESS) {
        printf ("数据上传失败");
        free (a);
        cudaFree (devPtrA);
        cublasDestroy(handle);
        return EXIT_FAILURE;
    }
    // 释放设备内存和cuBLAS句柄
    cudaFree (devPtrA);
    cublasDestroy(handle);
    // 打印结果矩阵
    for (j = 0; j < N; j++) {
        for (i = 0; i < M; i++) {
            printf ("%7.0f", a[IDX2C(i,j,M)]);
        }
        printf ("\n");
    }
    free(a);
    return EXIT_SUCCESS;
}
```

## 1.4. 前向兼容性

由于PTX JIT，cuBLAS库在大多数情况下可以在未来的GPU上工作。但是，存在某些限制：

- 没有性能保证：在新硬件上运行可能会更慢，尽管理论峰值更好。
- 对窄精度（FP4和FP8）以及平铺8位整数布局的前向兼容性有限。

## 1.5. 浮点模拟

浮点模拟首次在CUDA 12.9中引入，用于进一步加速更高精度数据类型的矩阵乘法。浮点模拟的工作方式是首先将输入转换为多个低精度值，然后利用低精度硬件单元计算部分结果，最后将结果重新组合为全精度。这些算法可以比原生精度算术提供显著的性能优势，同时保持相同或更好的精度；但是，结果不符合IEEE-754标准。

| 浮点模拟算法 | 模拟精度 | 支持的计算能力 | CUDA版本 |
| --- | --- | --- | --- |
| BF16x9 | FP32 | 10.0, 10.3 | 12.9+ |
| 定点 | FP64 | 8.x, 9.0, 10.0, 11.0, 12.x | 13.0u2+ |

要启用浮点模拟而无需任何代码更改，可以使用以下环境变量。

| 环境变量 | 描述 |
| --- | --- |
| CUBLAS_EMULATION_STRATEGY | 用于覆盖默认模拟策略的环境变量。有效值为performant和eager；有关更多详细信息，请参见cublasEmulationStrategy_t。 |
| CUBLAS_EMULATION_SPECIAL_VALUES_SUPPORT_MASK | 用于覆盖模拟中默认特殊值支持掩码的环境变量。该值是一个位掩码，其中位0表示无穷大支持，位1表示NaN支持；请参见cudaEmulationSpecialValuesSupport_t。这相当于使用指定掩码调用cublasSetEmulationSpecialValuesSupport()。 |
| CUBLAS_EMULATE_SINGLE_PRECISION | 用于启用和禁用单精度浮点模拟的环境变量，分别使用值1和0。 |
| CUBLAS_EMULATE_DOUBLE_PRECISION | 用于启用和禁用双精度浮点模拟的环境变量，分别使用值1和0。 |
| CUBLAS_FIXEDPOINT_EMULATION_MANTISSA_BIT_COUNT | 用于定点模拟的尾数字位数。当设置时，模拟算法将使用指定的尾数字位数。这相当于使用CUDA_EMULATION_MANTISSA_CONTROL_FIXED（请参见cudaEmulationMantissaControl_t）调用cublasSetFixedPointEmulationMantissaControl()，并将cublasSetFixedPointEmulationMaxMantissaBitCount()设置为用户提供的值。 |

### 1.5.1. BF16x9

BF16x9算法用于模拟FP32算术。一个FP32值可以精确表示为三个BF16值，如下所示：

```

\[\begin{split}a & = a_0 + 2^{-8} a_1 + 2^{-16} a_2 \\\end{split}\]
```

我们可以从BF16值完全重建FP32值而不损失精度。利用这一点，我们定义FMA操作（d = ab + c）如下：

```

\[\begin{split}d & = ab + c \\
  & = (a_0 + 2^{-8} a_1 + 2^{-16} a_2) \cdot (b_0 + 2^{-8} b_1 + 2^{-16} b_2) + c \\
  & = a_0b_0 + 2^{-8}a_0b_1 + 2^{-16}a_0b_2 \\
  & \quad + 2^{-8}a_1b_0 + 2^{-16}a_1b_1 + 2^{-24}a_1b_2 \\
  & \quad + 2^{-16}a_2b_0 + 2^{-24}a_2b_1 + 2^{-32}a_2b_2 + c \\\end{split}\]
```

在实践中，利用的是BF16张量核心而不是FMA单元，这个想法也很自然地扩展到复数算术。

虽然BF16x9可以在所有硬件上支持，但只有当峰值BF16吞吐量超过峰值FP32吞吐量的九倍时，它才能提供性能优势。它还需要特殊的硬件功能才能以高性能方式应用额外的缩放因子。因此，BF16x9仅在特定架构上支持。有关更多详细信息，请参见浮点模拟支持概述表。

### 1.5.2. 定点

定点模拟用于模拟FP64算术，并遵循[Ozaki方案](https://doi.org/10.1177/10943420241239588)。定点表示通过添加共享的2的幂缩放因子，并通过尾数字位编码浮点的剩余动态范围来模拟浮点。缩放因子对矩阵A同一行或矩阵B同一列中的元素共享，用于将所有元素逻辑缩放到-1和1之间（含）。

由于FP64的动态范围很大，没有单一的定点配置既能高性能又能对所有浮点输入保持准确。因此，我们启用两种风格的定点模拟：动态尾数字控制固定尾数字控制。这些配置可以通过cublasSetFixedPointEmulationMantissaControl()设置。

#### 1.5.2.1. 动态尾数字控制

动态尾数字控制代表cuBLAS库的默认尾数字控制。我们的自动动态精度框架计算维持等于或优于FP64精度所需的定点尾数字位数。如果所需尾数字位数超过库定义的默认值（请参见默认库配置）或用户提供的最大位数（请参见cublasSetFixedPointEmulationMaxMantissaBitCount()），框架将动态分派到原生FP64。

#### 1.5.2.2. 固定尾数字控制

固定尾数字控制可用于进一步加速定点模拟。用户可以通过cublasSetFixedPointEmulationMaxMantissaBitCount()提供定点表示的尾数字位数；但是，没有自动动态精度框架，无法保证等于或优于FP64算术的精度。

#### 1.5.2.3. 表示和映射

定点表示由对矩阵同一行或列中元素共享的缩放因子、一个符号位和尾数字位组成。我们将符号位和尾数字位存储在8位整数中。每个8位整数矩阵称为一个切片，计算成本随切片数量呈二次方增长。将尾数字位数转换为切片数量的公式如下：

```

\[\text{sliceCount} = \text{ceildiv}(\text{mantissaBitCount} + 1, 8)\]
```

> **注意**

注意
尾数字位数将始终向上舍入以完全占用最低有效切片

#### 1.5.2.4. 定点工作空间需求

为了使用定点模拟进行计算，A和B矩阵在工作站内存中被转换为定点表示。这导致工作空间需求依赖于问题大小和模拟参数。以下函数将提供定点模拟所需工作空间的安全上限（可能高估）：

```c++
// 计算定点模拟所需工作空间大小的函数
size_t getFixedPointWorkspaceSizeInBytes(int m, int n, int k, int batchCount, bool isComplex,
                cudaEmulationMantissaControl mantissaControl, int maxMantissaBitCount) {
    // 工作空间安全系数
    constexpr double MULTIPLIER = 1.25;

    // 复数需要两倍的元素
    int mult = isComplex ? 2 : 1;
    // 计算所需的切片数量
    int numSlices = ceildiv(maxMantissaBitCount + 1, 8);
    // 计算最大splitk值
    int max_splitk = ceildiv(opts.k, 8192);

    // 对矩阵维度进行填充以优化性能
    int padded_m = ceildiv(m, 1024) * 1024;
    int padded_n = ceildiv(n, 1024) * 1024;
    int padded_k = ceildiv(k, 128) * 128;
    int num_blocks_k = ceildiv(k, 64);

    // 计算GEMM工作空间大小
    size_t gemm_workspace = sizeof(int8_t) *
        ((size_t)padded_m * padded_k + (size_t)padded_n * padded_k) * mult * numSlices;
    gemm_workspace += sizeof(int32_t) * ((size_t)padded_m + padded_n) * mult;

    // 计算累加器工作空间版本1
    size_t acc_workspace_ver1 = 0;
    if (isComplex) {
        acc_workspace_ver1 += sizeof(double) * (size_t)m * n * mult * mult;
    }
    // 计算累加器工作空间版本2
    size_t acc_workspace_ver2 = std::min(sizeof(int32_t) * ((size_t)padded_m * padded_n) * mult * mult * numSlices,
                                         (size_t)(1LL << 32)) *
                                max_splitk;
    gemm_workspace += std::max(acc_workspace_ver1, acc_workspace_ver2);

    // 计算自适应精度工作空间
    size_t adp_workspace = 0;
    if (mantissaControl == CUDA_EMULATION_MANTISSA_CONTROL_DYNAMIC) {
        adp_workspace = sizeof(int32_t) * ((size_t)m * num_blocks_k + (size_t)n * num_blocks_k +
                         (size_t)m * n) * mult;
    }

    // 常量大小（128MB）
    constexpr size_t CONSTANT_SIZE = 128 * 1024 * 1024;
    return (size_t)(std::max(gemm_workspace, adp_workspace) * batchCount * MULTIPLIER) + CONSTANT_SIZE;
}
```

此函数可用于使用cublasSetWorkspace()管理您自己的工作空间内存，这可用于保证可重现的结果并提高性能。

#### 1.5.2.5. 定点性能指南

定点模拟允许用户进行性能和精度权衡以进一步加速。对于动态尾数字控制，用户能够使用cublasSetFixedPointEmulationMantissaBitOffset()配置自动动态精度框架以使用比原生FP64所需精度更少或更多的位数。固定尾数字控制可以通过使用cublasSetFixedPointEmulationMaxMantissaBitCount()增加或减少尾数字位数进行类似的调整。

由于定点工作空间需求很大，异步分配使用cudaMallocAsync()完成。在GEMM调用不足以摊销内存分配成本的情况下，或在非常频繁的CUDA流同步发生时，您可以通过以下方式提高性能：

- 减少CUDA流同步次数
- 管理自己的内存并使用cublasSetWorkspace()提供工作空间
- 允许默认内存池在同步之间保留内存

### 1.5.3. 默认库配置

模拟的库默认值可能会更改。

| API | 尾数字控制 | 默认行为 |
| --- | --- | --- |
| cublasGetEmulationStrategy() | 不适用 | CUBLAS_EMULATION_STRATEGY_DEFAULT |
| cublasGetEmulationSpecialValuesSupport() | 不适用 | CUBLAS_EMULATION_SPECIAL_VALUES_SUPPORT_DEFAULT |
| cublasGetFixedPointEmulationMantissaControl() | 不适用 | CUDA_EMULATION_MANTISSA_CONTROL_DYNAMIC |
| cublasGetFixedPointEmulationMaxMantissaBitCount() | CUDA_EMULATION_MANTISSA_CONTROL_DYNAMIC | 79 |
| cublasGetFixedPointEmulationMaxMantissaBitCount() | CUDA_EMULATION_MANTISSA_CONTROL_FIXED | 55 |
| cublasGetFixedPointEmulationMantissaBitOffset() | 不适用 | 0 |
| cublasGetFixedPointEmulationMantissaBitCountPointer() | 不适用 | NULL |

### 1.5.4. 对浮点特殊值的支持

浮点模拟算法的实现对正常值和反规范化值都保持模拟精度的准确性，但可能不会遵守IEEE-754标准关于$\text{Inf}$、$\text{NaN}$或带符号零的规定。如果底层模拟算法不能隐式支持给定的特殊值，并且库配置为支持它（请参见cublasSetEmulationSpecialValuesSupport()），则会采取额外步骤来支持它。下表显示了每个模拟算法隐式支持哪些特殊值。

| 浮点模拟算法 | 隐式支持的特殊值 |
| --- | --- |
| BF16x9 | $\text{NaN}$ |
| 定点 | 无 |