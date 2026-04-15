# 6. 使用 cuBLAS Legacy API

本节不提供每个 Legacy API 数据类型和入口点的完整参考。相反，它描述了如何使用该 API，特别是与常规 cuBLAS API 不同的地方。

请注意，在本节中，所有对"cuBLAS 库"的引用仅指 Legacy cuBLAS API。

> **警告**

警告
legacy cuBLAS API 已弃用，将在未来的版本中移除。

## 6.1. 错误状态

`cublasStatus` 类型用于函数状态返回。cuBLAS 库辅助函数直接返回状态，而核心函数的状态可以使用 `cublasGetError()` 检索。请注意，通过 `cublasGetError()` 读取错误状态会将内部错误状态重置为 `CUBLAS_STATUS_SUCCESS`。目前，定义了以下值：

| 值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_ALLOC_FAILED | 资源分配失败 |
| CUBLAS_STATUS_INVALID_VALUE | 使用了无效的数值作为参数 |
| CUBLAS_STATUS_ARCH_MISMATCH | 需要设备架构功能但不存在 |
| CUBLAS_STATUS_MAPPING_ERROR | 访问 GPU 内存空间失败 |
| CUBLAS_STATUS_EXECUTION_FAILED | GPU 程序执行失败 |
| CUBLAS_STATUS_INTERNAL_ERROR | 内部操作失败 |
| CUBLAS_STATUS_NOT_SUPPORTED | 需要的功能不受支持 |

此 legacy 类型对应于 cuBLAS 库 API 中的类型 [cublasStatus_t](#cublasstatus-t)。

## 6.2. 初始化和关闭

函数 `cublasInit()` 和 `cublasShutdown()` 用于初始化和关闭 cuBLAS 库。建议在任何其他函数调用之前调用 `cublasInit()`。它会为调用该函数的当前主机线程所绑定的 GPU 设备分配硬件资源。

legacy 初始化和关闭函数与 cuBLAS 库 API 例程 [cublasCreate()](#cublascreate) 和 [cublasDestroy()](#cublasdestroy) 类似。

## 6.3. 线程安全

legacy API 在与多个主机线程和设备一起使用时不是线程安全的。建议仅在需要与 Fortran 高度兼容且使用单个主机线程来设置库并调用所有函数时才使用它。

## 6.4. 内存管理

 legacy cuBLAS 库 API 使用的内存分别使用函数 `cublasAlloc()` 和 `cublasFree()` 进行分配和释放。这些函数在 GPU 内存空间中创建和销毁一个对象，该对象能够容纳包含 `n` 个元素的数组，其中每个元素需要 `elemSize` 字节的存储空间。请参阅 legacy cuBLAS API 头文件"cublas.h"以获取这些函数的原型。

函数 `cublasAlloc()` 是函数 `cudaMalloc()` 的包装器，因此 `cublasAlloc()` 返回的设备指针可以传递给任何 CUDA™ 设备内核函数。但是，这些设备指针不能在主机代码中被解引用。函数 `cublasFree()` 是函数 `cudaFree()` 的包装器。

## 6.5. 标量参数

在 legacy cuBLAS API 中，标量参数通过值从主机传递。此外，少数返回标量结果的函数（如 dot() 和 nrm2()）会在主机上返回结果值，因此这些例程在返回之前会等待设备上的内核执行完成，这使得与流的并行变得不切实际。然而，大多数函数不返回任何值，以便与 Fortran 和现有的 BLAS 库更好地兼容。

## 6.6. 辅助函数

在本节中，我们列出了 legacy cuBLAS API 提供的辅助函数及其功能。关于这些函数的确切原型，请参阅 legacy cuBLAS API 头文件"cublas.h"。

| 辅助函数 | 含义 |
| --- | --- |
| cublasInit() | 初始化库 |
| cublasShutdown() | 关闭库 |
| cublasGetError() | 检索库的 error 状态 |
| cublasSetKernelStream() | 设置库使用的流 |
| cublasAlloc() | 为库分配设备内存 |
| cublasFree() | 释放为库分配的设备内存 |
| cublasSetVector() | 将主机上的向量 x 复制到 GPU 上的向量 |
| cublasGetVector() | 将 GPU 上的向量 x 复制到主机上的向量 |
| cublasSetMatrix() | 将主机上矩阵的 \(m \times n\) 区块复制到 GPU |
| cublasGetMatrix() | 将 GPU 上矩阵的 \(m \times n\) 区块复制到主机 |
| cublasSetVectorAsync() | 类似于 cublasSetVector()，但复制是异步的 |
| cublasGetVectorAsync() | 类似于 cublasGetVector()，但复制是异步的 |
| cublasSetMatrixAsync() | 类似于 cublasSetMatrix()，但复制是异步的 |
| cublasGetMatrixAsync() | 类似于 cublasGetMatrix()，但复制是异步的 |

## 6.7. Level-1、2、3 函数

Level-1、2、3 cuBLAS 函数（也称为核心函数）与本文档第 3、4 和 5 章中列出的函数具有相同的名称和行为。关于它们的确切原型，请参阅 legacy cuBLAS API 头文件"cublas.h"。此外，下一节将更详细地讨论 legacy API 和 cuBLAS API 原型之间的差异，特别是如何将函数调用从一个 API 转换到另一个 API。

## 6.8. 从 Legacy 转换到 cuBLAS API

有一些通用规则可用于从 legacy 转换到 cuBLAS API：

- 将头文件"cublas.h"替换为"cublas_v2.h"。
- 将类型 cublasStatus 替换为 cublasStatus_t。
- 将函数 cublasSetKernelStream() 替换为 cublasSetStream()。
- 分别将函数 cublasAlloc() 和 cublasFree() 替换为 cudaMalloc() 和 cudaFree()。请注意，cudaMalloc() 期望以字节为单位提供所分配内存的大小（通常只需提供 n × elemSize 来分配 n 个元素，每个元素大小为 elemSize 字节）。
- 声明 cublasHandle_t cuBLAS 库句柄。
- 使用 cublasCreate() 初始化句柄。使用完后再使用 cublasDestroy() 释放句柄。
- 将句柄作为第一个参数添加到所有 cuBLAS 库函数调用中。
- 将标量参数更改为通过引用传递，而不是通过值传递（通常在 C/C++ 中只需添加"&"符号即可，因为参数默认在主机上通过引用传递）。但是，请注意，如果例程异步运行，则保存标量参数的变量在例程分派的内核完成之前不能更改。请参阅 CUDA C++ 编程指南以获取关于如何使用流的详细讨论。
- 将参数字符 N 或 n（非转置操作）、T 或 t（转置操作）以及 C 或 c（共轭转置操作）分别更改为 CUBLAS_OP_N、CUBLAS_OP_T 和 CUBLAS_OP_C。
- 将参数字符 L 或 l（填充下半部分）和 U 或 u（填充上半部分）分别更改为 CUBLAS_FILL_MODE_LOWER 和 CUBLAS_FILL_MODE_UPPER。
- 将参数字符 N 或 n（非单位对角线）和 U 或 u（单位对角线）分别更改为 CUBLAS_DIAG_NON_UNIT 和 CUBLAS_DIAG_UNIT。
- 将参数字符 L 或 l（左侧）和 R 或 r（右侧）分别更改为 CUBLAS_SIDE_LEFT 和 CUBLAS_SIDE_RIGHT。
- 如果 legacy API 函数返回标量值，请添加一个相同类型的额外标量参数作为引用传递，作为同一函数的最后一个参数。
- 不使用 cublasGetError()，而是使用函数本身的返回值来检查错误。
- 最后，请使用头文件 cublas.h 和 cublas_v2.h 中的函数原型来检查代码的正确性。

## 6.9. 示例

有关使用 legacy cuBLAS API 的示例代码参考，请参阅下面的两个示例。它们展示了一个使用 legacy cuBLAS 库 API 用 C 编写的应用程序，具有两种索引样式（示例 A.1. "使用 C 和 cuBLAS 的应用程序：基于 1 的索引"和示例 A.2. "使用 C 和 cuBLAS 的应用程序：基于 0 的索引"）。此应用程序与引言章节中所示的使用 cuBLAS 库 API 的应用程序类似。

示例 A.1. 使用 C 和 cuBLAS 的应用程序：基于 1 的索引

```c++
//-----------------------------------------------------------
// 包含头文件
#include <stdio.h>
#include <stdlib.h>
#include <math.h>
#include "cublas.h"
#define M 6
#define N 5
#define IDX2F(i,j,ld) ((((j)-1)*(ld))+((i)-1))

// 修改矩阵元素的函数
static __inline__ void modify (float *m, int ldm, int n, int p, int q, float alpha, float beta){
    cublasSscal (n-q+1, alpha, &m[IDX2F(p,q,ldm)], ldm);
    cublasSscal (ldm-p+1, beta, &m[IDX2F(p,q,ldm)], 1);
}

int main (void){
    int i, j;
    cublasStatus stat;
    float* devPtrA;
    float* a = 0;
    // 为主机分配内存
    a = (float *)malloc (M * N * sizeof (*a));
    if (!a) {
        printf ("主机内存分配失败");
        return EXIT_FAILURE;
    }
    // 初始化矩阵数据
    for (j = 1; j <= N; j++) {
        for (i = 1; i <= M; i++) {
            a[IDX2F(i,j,M)] = (float)((i-1) * M + j);
        }
    }
    // 初始化 cuBLAS 库
    cublasInit();
    // 为设备分配内存
    stat = cublasAlloc (M*N, sizeof(*a), (void**)&devPtrA);
    if (stat != CUBLAS_STATUS_SUCCESS) {
        printf ("设备内存分配失败");
        cublasShutdown();
        return EXIT_FAILURE;
    }
    // 将数据从主机复制到设备
    stat = cublasSetMatrix (M, N, sizeof(*a), a, M, devPtrA, M);
    if (stat != CUBLAS_STATUS_SUCCESS) {
        printf ("数据下载失败");
        cublasFree (devPtrA);
        cublasShutdown();
        return EXIT_FAILURE;
    }
    // 执行矩阵修改操作
    modify (devPtrA, M, N, 2, 3, 16.0f, 12.0f);
    // 将数据从设备复制回主机
    stat = cublasGetMatrix (M, N, sizeof(*a), devPtrA, M, a, M);
    if (stat != CUBLAS_STATUS_SUCCESS) {
        printf ("数据上传失败");
        cublasFree (devPtrA);
        cublasShutdown();
        return EXIT_FAILURE;
    }
    // 释放设备内存并关闭库
    cublasFree (devPtrA);
    cublasShutdown();
    // 打印结果
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

示例 A.2. 使用 C 和 cuBLAS 的应用程序：基于 0 的索引

```c++
//-----------------------------------------------------------
// 包含头文件
#include <stdio.h>
#include <stdlib.h>
#include <math.h>
#include "cublas.h"
#define M 6
#define N 5
#define IDX2C(i,j,ld) (((j)*(ld))+(i))

// 修改矩阵元素的函数
static __inline__ void modify (float *m, int ldm, int n, int p, int q, float alpha, float beta){
    cublasSscal (n-q, alpha, &m[IDX2C(p,q,ldm)], ldm);
    cublasSscal (ldm-p, beta, &m[IDX2C(p,q,ldm)], 1);
}

int main (void){
    int i, j;
    cublasStatus stat;
    float* devPtrA;
    float* a = 0;
    // 为主机分配内存
    a = (float *)malloc (M * N * sizeof (*a));
    if (!a) {
        printf ("主机内存分配失败");
        return EXIT_FAILURE;
    }
    // 初始化矩阵数据
    for (j = 0; j < N; j++) {
        for (i = 0; i < M; i++) {
            a[IDX2C(i,j,M)] = (float)(i * M + j + 1);
        }
    }
    // 初始化 cuBLAS 库
    cublasInit();
    // 为设备分配内存
    stat = cublasAlloc (M*N, sizeof(*a), (void**)&devPtrA);
    if (stat != CUBLAS_STATUS_SUCCESS) {
        printf ("设备内存分配失败");
        cublasShutdown();
        return EXIT_FAILURE;
    }
    // 将数据从主机复制到设备
    stat = cublasSetMatrix (M, N, sizeof(*a), a, M, devPtrA, M);
    if (stat != CUBLAS_STATUS_SUCCESS) {
        printf ("数据下载失败");
        cublasFree (devPtrA);
        cublasShutdown();
        return EXIT_FAILURE;
    }
    // 执行矩阵修改操作
    modify (devPtrA, M, N, 1, 2, 16.0f, 12.0f);
    // 将数据从设备复制回主机
    stat = cublasGetMatrix (M, N, sizeof(*a), devPtrA, M, a, M);
    if (stat != CUBLAS_STATUS_SUCCESS) {
        printf ("数据上传失败");
        cublasFree (devPtrA);
        cublasShutdown();
        return EXIT_FAILURE;
    }
    // 释放设备内存并关闭库
    cublasFree (devPtrA);
    cublasShutdown();
    // 打印结果
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