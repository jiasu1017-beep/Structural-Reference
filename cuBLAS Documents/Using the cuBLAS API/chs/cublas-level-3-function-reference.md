## 2.7. cuBLAS Level-3 函数参考

在本章中，我们描述执行矩阵-矩阵运算的 Level-3 基本线性代数子程序（BLAS3）函数。

### 2.7.1. cublas<t>gemm()

```c++
// 单精度实数矩阵-矩阵乘法
cublasStatus_t cublasSgemm(cublasHandle_t handle,
                           cublasOperation_t transa, cublasOperation_t transb,
                           int m, int n, int k,
                           const float           *alpha,
                           const float           *A, int lda,
                           const float           *B, int ldb,
                           const float           *beta,
                           float           *C, int ldc)
// 双精度实数矩阵-矩阵乘法
cublasStatus_t cublasDgemm(cublasHandle_t handle,
                           cublasOperation_t transa, cublasOperation_t transb,
                           int m, int n, int k,
                           const double          *alpha,
                           const double          *A, int lda,
                           const double          *B, int ldb,
                           const double          *beta,
                           double          *C, int ldc)
// 单精度复数矩阵-矩阵乘法
cublasStatus_t cublasCgemm(cublasHandle_t handle,
                           cublasOperation_t transa, cublasOperation_t transb,
                           int m, int n, int k,
                           const cuComplex       *alpha,
                           const cuComplex       *A, int lda,
                           const cuComplex       *B, int ldb,
                           const cuComplex       *beta,
                           cuComplex       *C, int ldc)
// 双精度复数矩阵-矩阵乘法
cublasStatus_t cublasZgemm(cublasHandle_t handle,
                           cublasOperation_t transa, cublasOperation_t transb,
                           int m, int n, int k,
                           const cuDoubleComplex *alpha,
                           const cuDoubleComplex *A, int lda,
                           const cuDoubleComplex *B, int ldb,
                           const cuDoubleComplex *beta,
                           cuDoubleComplex *C, int ldc)
// 半精度矩阵-矩阵乘法
cublasStatus_t cublasHgemm(cublasHandle_t handle,
                           cublasOperation_t transa, cublasOperation_t transb,
                           int m, int n, int k,
                           const __half *alpha,
                           const __half *A, int lda,
                           const __half *B, int ldb,
                           const __half *beta,
                           __half *C, int ldc)
```

此函数支持 64 位整数接口。

此函数执行矩阵-矩阵乘法

$C = \alpha\text{op}(A)\text{op}(B) + \beta C$

其中 $\alpha$ 和 $\beta$ 是标量，$A$、$B$ 和 $C$ 是按列主序格式存储的矩阵，维度分别为 $\text{op}(A)$ $m \times k$、$\text{op}(B)$ $k \times n$ 和 $C$ $m \times n$。对于矩阵 $A$

$\text{op}(A) = \left\{ \begin{matrix}
A & {\text{if }\textsf{transa == CUBLAS\_OP\_N}} \\
A^{T} & {\text{if }\textsf{transa == CUBLAS\_OP\_T}} \\
A^{H} & {\text{if }\textsf{transa == CUBLAS\_OP\_C}} \\
\end{matrix} \right.$

$\text{op}(B)$ 对于矩阵 $B$ 的定义类似。

| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | input | cuBLAS 库上下文的句柄。 |
| transa |  | input | 运算 op(A)，为非转置或（共轭）转置。 |
| transb |  | input | 运算 op(B)，为非转置或（共轭）转置。 |
| m |  | input | 矩阵 op(A) 和 C 的行数。 |
| n |  | input | 矩阵 op(B) 和 C 的列数。 |
| k |  | input | op(A) 的列数和 op(B) 的行数。 |
| alpha | 主机或设备 | input | 用于乘法的 <type> 标量。 |
| A | 设备 | input | <type> 数组，维度为 lda x k，当 transa == CUBLAS_OP_N 时 lda >= max(1, m)，否则为 lda x m，lda >= max(1, k)。 |
| lda |  | input | 用于存储矩阵 A 的二维数组的主维度。 |
| B | 设备 | input | <type> 数组，维度为 ldb x n，当 transb == CUBLAS_OP_N 时 ldb >= max(1, k)，否则为 ldb x k，ldb >= max(1, n)。 |
| ldb |  | input | 用于存储矩阵 B 的二维数组的主维度。 |
| beta | 主机或设备 | input | 用于乘法的 <type> 标量。如果 beta == 0，则 C 不必是有效输入。 |
| C | 设备 | 输入/输出 | <type> 数组，维度为 ldc x n，ldc >= max(1, m)。 |
| ldc |  | input | 用于存储矩阵 C 的二维数组的主维度。 |

此函数可能返回的错误值及其含义如下所列。

| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | 如果 m < 0 或 n < 0 或 k < 0，或如果 transa 和 transb 不是 CUBLAS_OP_N、CUBLAS_OP_C、CUBLAS_OP_T 之一，或如果当 transa == CUBLAS_OP_N 时 lda < max(1, m)，否则 lda < max(1, k)，或如果当 transb == CUBLAS_OP_N 时 ldb < max(1, k)，否则 ldb < max(1, n)，或如果 ldc < max(1, m)，或如果 alpha 或 beta 为 NULL，或如果当 beta 不为零时 C 为 NULL |
| CUBLAS_STATUS_ARCH_MISMATCH | 对于 cublasHgemm()，设备不支持半精度数学运算。 |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数无法在 GPU 上启动 |

有关参考信息，请参阅 NETLIB 文档：

[sgemm()](http://www.netlib.org/blas/sgemm.f)、[dgemm()](http://www.netlib.org/blas/dgemm.f)、[cgemm()](http://www.netlib.org/blas/cgemm.f)、[zgemm()](http://www.netlib.org/blas/zgemm.f)

### 2.7.2. cublas<t>gemm3m()

```c++
// 单精度复数矩阵-矩阵乘法（使用 Gauss 复杂度约简算法）
cublasStatus_t cublasCgemm3m(cublasHandle_t handle,
                           cublasOperation_t transa, cublasOperation_t transb,
                           int m, int n, int k,
                           const cuComplex       *alpha,
                           const cuComplex       *A, int lda,
                           const cuComplex       *B, int ldb,
                           const cuComplex       *beta,
                           cuComplex       *C, int ldc)
// 双精度复数矩阵-矩阵乘法（使用 Gauss 复杂度约简算法）
cublasStatus_t cublasZgemm3m(cublasHandle_t handle,
                           cublasOperation_t transa, cublasOperation_t transb,
                           int m, int n, int k,
                           const cuDoubleComplex *alpha,
                           const cuDoubleComplex *A, int lda,
                           const cuDoubleComplex *B, int ldb,
                           const cuDoubleComplex *beta,
                           cuDoubleComplex *C, int ldc)
```

此函数支持 64 位整数接口。

此函数执行复数矩阵-矩阵乘法，使用 Gauss 复杂度约简算法。这可使性能提升高达 25%

$C = \alpha\text{op}(A)\text{op}(B) + \beta C$

其中 $\alpha$ 和 $\beta$ 是标量，$A$、$B$ 和 $C$ 是按列主序格式存储的矩阵，维度分别为 $\text{op}(A)$ $m \times k$、$\text{op}(B)$ $k \times n$ 和 $C$ $m \times n$。对于矩阵 $A$

$\text{op}(A) = \left\{ \begin{matrix}
A & {\text{if }\textsf{transa == CUBLAS\_OP\_N}} \\
A^{T} & {\text{if }\textsf{transa == CUBLAS\_OP\_T}} \\
A^{H} & {\text{if }\textsf{transa == CUBLAS\_OP\_C}} \\
\end{matrix} \right.$

$\text{op}(B)$ 对于矩阵 $B$ 的定义类似。

> **注意**
>
> 注意
> 这两个例程仅在计算能力等于或大于 5.0 的 GPU 上受支持。

| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | input | cuBLAS 库上下文的句柄。 |
| transa |  | input | 运算 op(A)，为非转置或（共轭）转置。 |
| transb |  | input | 运算 op(B)，为非转置或（共轭）转置。 |
| m |  | input | 矩阵 op(A) 和 C 的行数。 |
| n |  | input | 矩阵 op(B) 和 C 的列数。 |
| k |  | input | op(A) 的列数和 op(B) 的行数。 |
| alpha | 主机或设备 | input | 用于乘法的 <type> 标量。 |
| A | 设备 | input | <type> 数组，维度为 lda x k，当 transa == CUBLAS_OP_N 时 lda >= max(1, m)，否则为 lda x m，lda >= max(1, k)。 |
| lda |  | input | 用于存储矩阵 A 的二维数组的主维度。 |
| B | 设备 | input | <type> 数组，维度为 ldb x n，当 transb == CUBLAS_OP_N 时 ldb >= max(1, k)，否则为 ldb x k，ldb >= max(1, n)。 |
| ldb |  | input | 用于存储矩阵 B 的二维数组的主维度。 |
| beta | 主机或设备 | input | 用于乘法的 <type> 标量。如果 beta == 0，则 C 不必是有效输入。 |
| C | 设备 | 输入/输出 | <type> 数组，维度为 ldc x n，ldc >= max(1, m)。 |
| ldc |  | input | 用于存储矩阵 C 的二维数组的主维度。 |

此函数可能返回的错误值及其含义如下表所列。

| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成。 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化。 |
| CUBLAS_STATUS_INVALID_VALUE | 如果 m < 0 或 n < 0 或 k < 0，或如果 transa 和 transb 不是 CUBLAS_OP_N、CUBLAS_OP_C、CUBLAS_OP_T 之一，或如果当 transa == CUBLAS_OP_N 时 lda < max(1, m)，否则 lda < max(1, k)，或如果当 transb == CUBLAS_OP_N 时 ldb < max(1, k)，否则 ldb < max(1, n)，或如果 ldc < max(1, m)，或如果 alpha 或 beta 为 NULL，或如果当 beta 不为零时 C 为 NULL |
| CUBLAS_STATUS_ARCH_MISMATCH | 设备的计算能力低于 5.0。 |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数无法在 GPU 上启动。 |

有关参考信息，请参阅 NETLIB 文档：

[cgemm()](http://www.netlib.org/blas/cgemm.f)、[zgemm()](http://www.netlib.org/blas/zgemm.f)

### 2.7.3. cublas<t>gemmBatched()

```c++
// 半精度矩阵-矩阵批乘法
cublasStatus_t cublasHgemmBatched(cublasHandle_t handle,
                                  cublasOperation_t transa,
                                  cublasOperation_t transb,
                                  int m, int n, int k,
                                  const __half          *alpha,
                                  const __half          *const Aarray[], int lda,
                                  const __half          *const Barray[], int ldb,
                                  const __half          *beta,
                                  __half          *const Carray[], int ldc,
                                  int batchCount)
// 单精度实数矩阵-矩阵批乘法
cublasStatus_t cublasSgemmBatched(cublasHandle_t handle,
                                  cublasOperation_t transa,
                                  cublasOperation_t transb,
                                  int m, int n, int k,
                                  const float           *alpha,
                                  const float           *const Aarray[], int lda,
                                  const float           *const Barray[], int ldb,
                                  const float           *beta,
                                  float           *const Carray[], int ldc,
                                  int batchCount)
// 双精度实数矩阵-矩阵批乘法
cublasStatus_t cublasDgemmBatched(cublasHandle_t handle,
                                  cublasOperation_t transa,
                                  cublasOperation_t transb,
                                  int m, int n, int k,
                                  const double          *alpha,
                                  const double          *const Aarray[], int lda,
                                  const double          *const Barray[], int ldb,
                                  const double          *beta,
                                  double          *const Carray[], int ldc,
                                  int batchCount)
// 单精度复数矩阵-矩阵批乘法
cublasStatus_t cublasCgemmBatched(cublasHandle_t handle,
                                  cublasOperation_t transa,
                                  cublasOperation_t transb,
                                  int m, int n, int k,
                                  const cuComplex       *alpha,
                                  const cuComplex       *const Aarray[], int lda,
                                  const cuComplex       *const Barray[], int ldb,
                                  const cuComplex       *beta,
                                  cuComplex       *const Carray[], int ldc,
                                  int batchCount)
// 双精度复数矩阵-矩阵批乘法
cublasStatus_t cublasZgemmBatched(cublasHandle_t handle,
                                  cublasOperation_t transa,
                                  cublasOperation_t transb,
                                  int m, int n, int k,
                                  const cuDoubleComplex *alpha,
                                  const cuDoubleComplex *const Aarray[], int lda,
                                  const cuDoubleComplex *const Barray[], int ldb,
                                  const cuDoubleComplex *beta,
                                  cuDoubleComplex *const Carray[], int ldc,
                                  int batchCount)
```

此函数支持 64 位整数接口。

此函数执行一批矩阵的矩阵-矩阵乘法。该批次被认为是"一致的"，即所有实例对于各自的 A、B 和 C 矩阵具有相同的维度 (m, n, k)、主维度 (lda, ldb, ldc) 和转置 (transa, transb)。每个批次实例的输入矩阵和输出矩阵的地址从调用者传递给函数的指针数组中读取。

$C\lbrack i\rbrack = \alpha\text{op}(A\lbrack i\rbrack)\text{op}(B\lbrack i\rbrack) + \beta C\lbrack i\rbrack,\text{ for i } \in \lbrack 0,batchCount - 1\rbrack$

其中 $\alpha$ 和 $\beta$ 是标量，$A$、$B$ 和 $C$ 是指向按列主序格式存储的矩阵的指针数组，维度分别为 $\text{op}(A\lbrack i\rbrack)$ $m \times k$、$\text{op}(B\lbrack i\rbrack)$ $k \times n$ 和 $C\lbrack i\rbrack$ $m \times n$。对于矩阵 $A$

$\text{op}(A) = \left\{ \begin{matrix}
A & {\text{if }\textsf{transa == CUBLAS\_OP\_N}} \\
A^{T} & {\text{if }\textsf{transa == CUBLAS\_OP\_T}} \\
A^{H} & {\text{if }\textsf{transa == CUBLAS\_OP\_C}} \\
\end{matrix} \right.$

$\text{op}(B\lbrack i\rbrack)$ 对于矩阵 $B\lbrack i\rbrack$ 的定义类似。

> **注意**
>
> 注意
> \(C\lbrack i\rbrack\) 矩阵不得重叠，即各个 gemm 操作必须能够独立计算；否则，将导致未定义行为。

在某些问题规模上，在不同的 CUDA 流中多次调用 cublas<t>gemm() 而不是使用此 API 可能更有优势。

| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | input | cuBLAS 库上下文的句柄。 |
| transa |  | input | 运算 op(A[i])，为非转置或（共轭）转置。 |
| transb |  | input | 运算 op(B[i])，为非转置或（共轭）转置。 |
| m |  | input | 矩阵 op(A[i]) 和 C[i] 的行数。 |
| n |  | input | op(B[i]) 和 C[i] 的列数。 |
| k |  | input | op(A[i]) 的列数和 op(B[i]) 的行数。 |
| alpha | 主机或设备 | input | 用于乘法的 <type> 标量。 |
| Aarray | 设备 | input | 指向 <type> 数组的指针数组，每个数组维度为 lda x k，当 transa == CUBLAS_OP_N 时 lda >= max(1, m)，否则为 lda x m，lda >= max(1, k)。所有指针必须满足特定的对齐条件。详情请见下文。 |
| lda |  | input | 用于存储每个矩阵 A[i] 的二维数组的主维度。 |
| Barray | 设备 | input | 指向 <type> 数组的指针数组，每个数组维度为 ldb x n，当 transb == CUBLAS_OP_N 时 ldb >= max(1, k)，否则为 ldb x k，ldb >= max(1, n)。所有指针必须满足特定的对齐条件。详情请见下文。 |
| ldb |  | input | 用于存储每个矩阵 B[i] 的二维数组的主维度。 |
| beta | 主机或设备 | input | 用于乘法的 <type> 标量。如果 beta == 0，则 C 不必是有效输入。 |
| Carray | 设备 | 输入/输出 | 指向 <type> 数组的指针数组。维度为 ldc x n，ldc >= max(1, m)。矩阵 C[i] 不应重叠；否则，将导致未定义行为。所有指针必须满足特定的对齐条件。详情请见下文。 |
| ldc |  | input | 用于存储每个矩阵 C[i] 的二维数组的主维度。 |
| batchCount |  | input | Aarray、Barray 和 Carray 中包含的指针数量。 |

如果数学模式在使用 cublasSgemmBatched() 时启用了快速数学模式，则放置在 GPU 内存中的指针（不是指针数组）必须正确对齐以避免未对齐的内存访问错误。理想情况下，所有指针至少对齐到 16 字节。否则，建议它们满足以下规则：

- 如果 k % 4 == 0，则确保 intptr_t(ptr) % 16 == 0

此函数可能返回的错误值及其含义如下所列。

| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | 如果 m < 0 或 n < 0 或 k < 0，或如果 transa 和 transb 不是 CUBLAS_OP_N、CUBLAS_OP_C、CUBLAS_OP_T 之一，或如果当 transa == CUBLAS_OP_N 时 lda < max(1, m)，否则 lda < max(1, k)，或如果当 transb == CUBLAS_OP_N 时 ldb < max(1, k)，否则 ldb < max(1, n)，或如果 ldc < max(1, m) |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数无法在 GPU 上启动 |
| CUBLAS_STATUS_ARCH_MISMATCH | cublasHgemmBatched() 仅在计算能力等于或大于 5.3 的 GPU 上受支持 |

### 2.7.4. cublas<t>gemmStridedBatched()

```c++
// 半精度矩阵-矩阵跨越式批乘法
cublasStatus_t cublasHgemmStridedBatched(cublasHandle_t handle,
                                  cublasOperation_t transa,
                                  cublasOperation_t transb,
                                  int m, int n, int k,
                                  const __half           *alpha,
                                  const __half           *A, int lda,
                                  long long int          strideA,
                                  const __half           *B, int ldb,
                                  long long int          strideB,
                                  const __half           *beta,
                                  __half                 *C, int ldc,
                                  long long int          strideC,
                                  int batchCount)
// 单精度实数矩阵-矩阵跨越式批乘法
cublasStatus_t cublasSgemmStridedBatched(cublasHandle_t handle,
                                  cublasOperation_t transa,
                                  cublasOperation_t transb,
                                  int m, int n, int k,
                                  const float           *alpha,
                                  const float           *A, int lda,
                                  long long int          strideA,
                                  const float           *B, int ldb,
                                  long long int          strideB,
                                  const float           *beta,
                                  float                 *C, int ldc,
                                  long long int          strideC,
                                  int batchCount)
// 双精度实数矩阵-矩阵跨越式批乘法
cublasStatus_t cublasDgemmStridedBatched(cublasHandle_t handle,
                                  cublasOperation_t transa,
                                  cublasOperation_t transb,
                                  int m, int n, int k,
                                  const double          *alpha,
                                  const double          *A, int lda,
                                  long long int          strideA,
                                  const double          *B, int ldb,
                                  long long int          strideB,
                                  const double          *beta,
                                  double                *C, int ldc,
                                  long long int          strideC,
                                  int batchCount)
// 单精度复数矩阵-矩阵跨越式批乘法
cublasStatus_t cublasCgemmStridedBatched(cublasHandle_t handle,
                                  cublasOperation_t transa,
                                  cublasOperation_t transb,
                                  int m, int n, int k,
                                  const cuComplex       *alpha,
                                  const cuComplex       *A, int lda,
                                  long long int          strideA,
                                  const cuComplex       *B, int ldb,
                                  long long int          strideB,
                                  const cuComplex       *beta,
                                  cuComplex             *C, int ldc,
                                  long long int          strideC,
                                  int batchCount)
// 单精度复数矩阵-矩阵跨越式批乘法（使用 3m 算法）
cublasStatus_t cublasCgemm3mStridedBatched(cublasHandle_t handle,
                                  cublasOperation_t transa,
                                  cublasOperation_t transb,
                                  int m, int n, int k,
                                  const cuComplex       *alpha,
                                  const cuComplex       *A, int lda,
                                  long long int          strideA,
                                  const cuComplex       *B, int ldb,
                                  long long int          strideB,
                                  const cuComplex       *beta,
                                  cuComplex             *C, int ldc,
                                  long long int          strideC,
                                  int batchCount)
// 双精度



```c++

cublasStatus_t cublasSgemm(cublasHandle_t handle,
                           cublasOperation_t transa, cublasOperation_t transb,
                           int m, int n, int k,
                           const float           *alpha,
                           const float           *A, int lda,
                           const float           *B, int ldb,
                           const float           *beta,
                           float           *C, int ldc)
cublasStatus_t cublasDgemm(cublasHandle_t handle,
                           cublasOperation_t transa, cublasOperation_t transb,
                           int m, int n, int k,
                           const double          *alpha,
                           const double          *A, int lda,
                           const double          *B, int ldb,
                           const double          *beta,
                           double          *C, int ldc)
cublasStatus_t cublasCgemm(cublasHandle_t handle,
                           cublasOperation_t transa, cublasOperation_t transb,
                           int m, int n, int k,
                           const cuComplex       *alpha,
                           const cuComplex       *A, int lda,
                           const cuComplex       *B, int ldb,
                           const cuComplex       *beta,
                           cuComplex       *C, int ldc)
cublasStatus_t cublasZgemm(cublasHandle_t handle,
                           cublasOperation_t transa, cublasOperation_t transb,
                           int m, int n, int k,
                           const cuDoubleComplex *alpha,
                           const cuDoubleComplex *A, int lda,
                           const cuDoubleComplex *B, int ldb,
                           const cuDoubleComplex *beta,
                           cuDoubleComplex *C, int ldc)
cublasStatus_t cublasHgemm(cublasHandle_t handle,
                           cublasOperation_t transa, cublasOperation_t transb,
                           int m, int n, int k,
                           const __half *alpha,
                           const __half *A, int lda,
                           const __half *B, int ldb,
                           const __half *beta,
                           __half *C, int ldc)


```


This function supports the 64-bit Integer Interface.


This function performs the matrix-matrix multiplication


$C = \alpha\text{op}(A)\text{op}(B) + \beta C$


where $\alpha$ and $\beta$ are scalars, and $A$ , $B$ and $C$ are matrices stored in column-major format with dimensions $\text{op}(A)$ $m \times k$ , $\text{op}(B)$ $k \times n$ and $C$ $m \times n$ , respectively. Also, for matrix $A$


$\text{op}(A) = \left\{ \begin{matrix}
A & {\text{if }\textsf{transa == CUBLAS\_OP\_N}} \\
A^{T} & {\text{if }\textsf{transa == CUBLAS\_OP\_T}} \\
A^{H} & {\text{if }\textsf{transa == CUBLAS\_OP\_C}} \\
\end{matrix} \right.$


and $\text{op}(B)$ is defined similarly for matrix $B$ .


| Param. | Memory | In/out | Meaning |
| --- | --- | --- | --- |
| handle |  | input | Handle to the cuBLAS library context. |
| transa |  | input | Operation op(A) that is non- or (conj.) transpose. |
| transb |  | input | Operation op(B) that is non- or (conj.) transpose. |
| m |  | input | Number of rows of matrix op(A) and C. |
| n |  | input | Number of columns of matrix op(B) and C. |
| k |  | input | Number of columns of op(A) and rows of op(B). |
| alpha | host or device | input | <type> scalar used for multiplication. |
| A | device | input | <type> array of dimensions lda x k with lda >= max(1, m) if transa == CUBLAS_OP_N and lda x m with lda >= max(1, k) otherwise. |
| lda |  | input | Leading dimension of two-dimensional array used to store the matrix A. |
| B | device | input | <type> array of dimension ldb x n with ldb >= max(1, k) if transb == CUBLAS_OP_N and ldb x k with ldb >= max(1,n) otherwise. |
| ldb |  | input | Leading dimension of two-dimensional array used to store matrix B. |
| beta | host or device | input | <type> scalar used for multiplication. If beta == 0, C does not have to be a valid input. |
| C | device | in/out | <type> array of dimensions ldc x n with ldc >= max(1, m). |
| ldc |  | input | Leading dimension of a two-dimensional array used to store the matrix C. |


The possible error values returned by this function and their meanings are listed below.


| Error Value | Meaning |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | The operation completed successfully |
| CUBLAS_STATUS_NOT_INITIALIZED | The library was not initialized |
| CUBLAS_STATUS_INVALID_VALUE | If m < 0 or n < 0 or k < 0, or
if transa and transb are not one of CUBLAS_OP_N, CUBLAS_OP_C, CUBLAS_OP_T, or
if lda < max(1, m) when transa == CUBLAS_OP_N and lda < max(1, k) otherwise, or
if ldb < max(1, k) when transb == CUBLAS_OP_N and ldb < max(1, n) otherwise, or
if ldc < max(1, m), or
if alpha or beta are NULL, or
if C is NULL when beta is not zero |
| CUBLAS_STATUS_ARCH_MISMATCH | In the case of cublasHgemm() the device does not support math in half precision. |
| CUBLAS_STATUS_EXECUTION_FAILED | The function failed to launch on the GPU |


For references please refer to NETLIB documentation:


[sgemm()](http://www.netlib.org/blas/sgemm.f), [dgemm()](http://www.netlib.org/blas/dgemm.f), [cgemm()](http://www.netlib.org/blas/cgemm.f), [zgemm()](http://www.netlib.org/blas/zgemm.f)






```c++
// 此函数支持64位整数接口

cublasStatus_t cublasCgemm3m(cublasHandle_t handle,
                           cublasOperation_t transa, cublasOperation_t transb,
                           int m, int n, int k,
                           const cuComplex       *alpha,
                           const cuComplex       *A, int lda,
                           const cuComplex       *B, int ldb,
                           const cuComplex       *beta,
                           cuComplex       *C, int ldc)
cublasStatus_t cublasZgemm3m(cublasHandle_t handle,
                           cublasOperation_t transa, cublasOperation_t transb,
                           int m, int n, int k,
                           const cuDoubleComplex *alpha,
                           const cuDoubleComplex *A, int lda,
                           const cuDoubleComplex *B, int ldb,
                           const cuDoubleComplex *beta,
                           cuDoubleComplex *C, int ldc)

```

此函数支持64位整数接口。

该函数使用高斯复杂度归约算法执行复数矩阵-矩阵乘法。这可以将性能提升高达25%。

$C = \alpha\text{op}(A)\text{op}(B) + \beta C$

其中 $\alpha$ 和 $\beta$ 是标量，$A$、$B$ 和 $C$ 是以列优先格式存储的矩阵，维度分别为 $\text{op}(A)$ $m \times k$、$\text{op}(B)$ $k \times n$ 和 $C$ $m \times n$。此外，对于矩阵 $A$：

$\text{op}(A) = \left\{ \begin{matrix}
A & {\text{if }\textsf{transa == CUBLAS\_OP\_N}} \\
A^{T} & {\text{if }\textsf{transa == CUBLAS\_OP\_T}} \\
A^{H} & {\text{if }\textsf{transa == CUBLAS\_OP\_C}} \\
\end{matrix} \right.$

而 $\text{op}(B)$ 对矩阵 $B$ 的定义类似。

> **注意**

注意
这两个例程仅在计算能力大于或等于5.0的GPU上支持。


| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | 输入 | 指向 cuBLAS 库上下文的句柄。 |
| transa |  | 输入 | op(A) 运算，非转置或（共轭）转置。 |
| transb |  | 输入 | op(B) 运算，非转置或（共轭）转置。 |
| m |  | 输入 | 矩阵 op(A) 和 C 的行数。 |
| n |  | 输入 | 矩阵 op(B) 和 C 的列数。 |
| k |  | 输入 | op(A) 的列数和 op(B) 的行数。 |
| alpha | 主机或设备 | 输入 | 用于乘法的 <type> 标量。 |
| A | 设备 | 输入 | <type> 数组，维度为 lda × k（当 transa == CUBLAS_OP_N 时，lda >= max(1, m)）；或者维度为 lda × m（当 transa != CUBLAS_OP_N 时，lda >= max(1, k)）。 |
| lda |  | 输入 | 用于存储矩阵 A 的二维数组的leading维度。 |
| B | 设备 | 输入 | <type> 数组，维度为 ldb × n（当 transb == CUBLAS_OP_N 时，ldb >= max(1, k)）；或者维度为 ldb × k（当 transb != CUBLAS_OP_N 时，ldb >= max(1, n)）。 |
| ldb |  | 输入 | 用于存储矩阵 B 的二维数组的leading维度。 |
| beta | 主机或设备 | 输入 | 用于乘法的 <type> 标量。如果 beta == 0，则 C 不必是有效输入。 |
| C | 设备 | 输入/输出 | <type> 数组，维度为 ldc × n，其中 ldc >= max(1, m)。 |
| ldc |  | 输入 | 用于存储矩阵 C 的二维数组的leading维度。 |


此函数可能返回的错误值及其含义列于下表：


| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成。 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化。 |
| CUBLAS_STATUS_INVALID_VALUE | 如果 m < 0 或 n < 0 或 k < 0，或如果 transa 和 transb 不是 CUBLAS_OP_N、CUBLAS_OP_C、CUBLAS_OP_T 之一，或如果当 transa == CUBLAS_OP_N 时 lda < max(1, m) 且其他情况下 lda < max(1, k)，或如果当 transb == CUBLAS_OP_N 时 ldb < max(1, k) 且其他情况下 ldb < max(1, n)，或如果 ldc < max(1, m)，或如果 alpha 或 beta 为 NULL，或如果 beta 不为零时 C 为 NULL |
| CUBLAS_STATUS_ARCH_MISMATCH | 设备的计算能力低于5.0。 |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数在 GPU 上启动失败。 |


有关参考信息，请参阅 NETLIB 文档：


[cgemm()](http://www.netlib.org/blas/cgemm.f), [zgemm()](http://www.netlib.org/blas/zgemm.f)



```c++

cublasStatus_t cublasHgemmBatched(cublasHandle_t handle,
                                  cublasOperation_t transa,
                                  cublasOperation_t transb,
                                  int m, int n, int k,
                                  const __half          *alpha,
                                  const __half          *const Aarray[], int lda,
                                  const __half          *const Barray[], int ldb,
                                  const __half          *beta,
                                  __half          *const Carray[], int ldc,
                                  int batchCount)
// 半精度浮点型矩阵批次乘法
cublasStatus_t cublasSgemmBatched(cublasHandle_t handle,
                                  cublasOperation_t transa,
                                  cublasOperation_t transb,
                                  int m, int n, int k,
                                  const float           *alpha,
                                  const float           *const Aarray[], int lda,
                                  const float           *const Barray[], int ldb,
                                  const float           *beta,
                                  float           *const Carray[], int ldc,
                                  int batchCount)
// 单精度浮点型矩阵批次乘法
cublasStatus_t cublasDgemmBatched(cublasHandle_t handle,
                                  cublasOperation_t transa,
                                  cublasOperation_t transb,
                                  int m, int n, int k,
                                  const double          *alpha,
                                  const double          *const Aarray[], int lda,
                                  const double          *const Barray[], int ldb,
                                  const double          *beta,
                                  double          *const Carray[], int ldc,
                                  int batchCount)
// 双精度浮点型矩阵批次乘法
cublasStatus_t cublasCgemmBatched(cublasHandle_t handle,
                                  cublasOperation_t transa,
                                  cublasOperation_t transb,
                                  int m, int n, int k,
                                  const cuComplex       *alpha,
                                  const cuComplex       *const Aarray[], int lda,
                                  const cuComplex       *const Barray[], int ldb,
                                  const cuComplex       *beta,
                                  cuComplex       *const Carray[], int ldc,
                                  int batchCount)
// 复数型矩阵批次乘法
cublasStatus_t cublasZgemmBatched(cublasHandle_t handle,
                                  cublasOperation_t transa,
                                  cublasOperation_t transb,
                                  int m, int n, int k,
                                  const cuDoubleComplex *alpha,
                                  const cuDoubleComplex *const Aarray[], int lda,
                                  const cuDoubleComplex *const Barray[], int ldb,
                                  const cuDoubleComplex *beta,
                                  cuDoubleComplex *const Carray[], int ldc,
                                  int batchCount)
// 双精度复数型矩阵批次乘法


```


此函数支持64位整数接口。

此函数执行矩阵批次的矩阵-矩阵乘法。批次被视为"均匀的"，即所有实例具有相同的维度(m, n, k)、前导维度(lda, ldb, ldc)以及各自A、B和C矩阵的转置(transa, transb)。每个批次实例的输入矩阵和输出矩阵的地址从调用者传递给函数的指针数组中读取。


$C\lbrack i\rbrack = \alpha\text{op}(A\lbrack i\rbrack)\text{op}(B\lbrack i\rbrack) + \beta C\lbrack i\rbrack,\text{ for i } \in \lbrack 0,batchCount - 1\rbrack$


其中$\alpha$和$\beta$是标量，$A$、$B$和$C$是指向矩阵的指针数组，这些矩阵以列主序格式存储，维度分别为$\text{op}(A\lbrack i\rbrack)$ $m \times k$、$\text{op}(B\lbrack i\rbrack)$ $k \times n$和$C\lbrack i\rbrack$ $m \times n$。此外，对于矩阵$A$


$\text{op}(A) = \left\{ \begin{matrix}
A & {\text{if }\textsf{transa == CUBLAS\_OP\_N}} \\
A^{T} & {\text{if }\textsf{transa == CUBLAS\_OP\_T}} \\
A^{H} & {\text{if }\textsf{transa == CUBLAS\_OP\_C}} \\
\end{matrix} \right.$


且$\text{op}(B\lbrack i\rbrack)$对矩阵$B\lbrack i\rbrack$的定义类似。


> **注意**

注意
\(C\lbrack i\rbrack\)矩阵不得重叠，即各个gemm操作必须能够独立计算；否则将产生未定义行为。

在某些问题规模下，在不同的CUDA流中多次调用cublas<t>gemm()可能比使用此API更有优势。


| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | 输入 | cuBLAS库上下文的句柄。 |
| transa |  | 输入 | op(A[i])操作，即非转置或(共)转置。 |
| transb |  | 输入 | op(B[i])操作，即非转置或(共)转置。 |
| m |  | 输入 | 矩阵op(A[i])和C[i]的行数。 |
| n |  | 输入 | op(B[i])和C[i]的列数。 |
| k |  | 输入 | op(A[i])的列数和op(B[i])的行数。 |
| alpha | 主机或设备 | 输入 | 用于乘法的<type>标量。 |
| Aarray | 设备 | 输入 | 指向<type>数组的指针数组，每个数组维度为lda x k，当transa == CUBLAS_OP_N时lda >= max(1, m)，否则为lda x m且lda >= max(1, k)。
所有指针必须满足特定的对齐要求。请参阅下文了解更多详情。 |
| lda |  | 输入 | 用于存储每个矩阵A[i]的二维数组的前导维度。 |
| Barray | 设备 | 输入 | 指向<type>数组的指针数组，每个数组维度为ldb x n，当transb == CUBLAS_OP_N时ldb >= max(1, k)，否则为ldb x k且ldb >= max(1,n)。
所有指针必须满足特定的对齐要求。请参阅下文了解更多详情。 |
| ldb |  | 输入 | 用于存储每个矩阵B[i]的二维数组的前导维度。 |
| beta | 主机或设备 | 输入 | 用于乘法的<type>标量。如果beta == 0，C不必是有效的输入。 |
| Carray | 设备 | 输入/输出 | 指向<type>数组的指针数组。维度为ldc x n，ldc >= max(1, m)。矩阵C[i]不应重叠；否则将产生未定义行为。
所有指针必须满足特定的对齐要求。请参阅下文了解更多详情。 |
| ldc |  | 输入 | 用于存储每个矩阵C[i]的二维数组的前导维度。 |
| batchCount |  | 输入 | Aarray、Barray和Carray中包含的指针数量。 |


如果数学模式在使用cublasSgemmBatched()时启用了快速数学模式，则放置在GPU内存中的指针（而非指针数组）必须正确对齐以避免未对齐内存访问错误。理想情况下，所有指针应至少对齐到16字节。否则，建议它们满足以下规则：


- 如果k % 4 == 0，则确保intptr_t(ptr) % 16 == 0，


此函数可能返回的错误值及其含义如下所述。


| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | 如果m < 0或n < 0或k < 0，或
如果transa和transb不是CUBLAS_OP_N、CUBLAS_OP_C、CUBLAS_OP_T之一，或
如果当transa == CUBLAS_OP_N时lda < max(1, m)且否则lda < max(1, k)，或
如果当transb == CUBLAS_OP_N时ldb < max(1, k)且否则ldb < max(1, n)，或
如果ldc < max(1, m) |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数在GPU上启动失败 |
| CUBLAS_STATUS_ARCH_MISMATCH | cublasHgemmBatched()仅支持计算能力等于或大于5.3的GPU |

```c++
cublasStatus_t cublasSgemmGroupedBatched(cublasHandle_t handle,
                                         const cublasOperation_t transa_array[],
                                         const cublasOperation_t transb_array[],
                                         const int m_array[],
                                         const int n_array[],
                                         const int k_array[],
                                         const float  alpha_array[],
                                         const float *const  Aarray[],
                                         const int lda_array[],
                                         const float *const  Barray[],
                                         const int ldb_array[],
                                         const float  beta_array[],
                                         float *const  Carray[],
                                         const int ldc_array[],
                                         int group_count,
                                         const int group_size[])
cublasStatus_t cublasDgemmGroupedBatched(cublasHandle_t handle,
                                         const cublasOperation_t transa_array[],
                                         const cublasOperation_t transb_array[],
                                         const int m_array[],
                                         const int n_array[],
                                         const int k_array[],
                                         const double alpha_array[],
                                         const double *const Aarray[],
                                         const int lda_array[],
                                         const double *const Barray[],
                                         const int ldb_array[],
                                         const double beta_array[],
                                         double *const Carray[],
                                         const int ldc_array[],
                                         int group_count,
                                         const int group_size[])
```

此函数支持64位整数接口。

此函数对矩阵组执行矩阵-矩阵乘法运算。给定的组被认为是"均匀的"，即同一组内的所有实例具有相同的维度(m, n, k)、前置维度(lda, ldb, ldc)和转置操作(transa, transb)，分别对应各自的A、B和C矩阵。然而，维度、前置维度、转置操作和缩放因子(alpha, beta)可能在不同组之间有所不同。批次中每个实例的输入矩阵和输出矩阵的地址从调用者传递给函数的指针数组中读取。这在功能上等同于以下代码：

```c++
idx = 0;
for i = 0:group_count - 1
    for j = 0:group_size[i] - 1
        gemm(transa_array[i], transb_array[i], m_array[i], n_array[i], k_array[i],
             alpha_array[i], Aarray[idx], lda_array[i], Barray[idx], ldb_array[i],
             beta_array[i], Carray[idx], ldc_array[i]);
        idx += 1;
    end
end
```

其中 $\text{alpha\_array}$ 和 $\text{beta\_array}$ 是缩放因子数组，$\text{Aarray}$、$\text{Barray}$ 和 $\text{Carray}$ 是指向以列优先格式存储的矩阵的指针数组。对于属于组 $i$ 的给定索引 $\text{idx}$，维度如下：

> \(\text{op}(\text{Aarray}\lbrack\text{idx}\rbrack)\): \(\text{m\_array}\lbrack i\rbrack \times \text{k\_array}\lbrack i\rbrack\)
\(\text{op}(\text{Barray}\lbrack\text{idx}\rbrack)\): \(\text{k\_array}\lbrack i\rbrack \times \text{n\_array}\lbrack i\rbrack\)
\(\text{Carray}\lbrack\text{idx}\rbrack\): \(\text{m\_array}\lbrack i\rbrack \times \text{n\_array}\lbrack i\rbrack\)

> **注意**

> 此API采用两种不同长度的数组。维度、前置维度、转置操作和缩放因子的数组长度为group_count，而矩阵数组的长度为problem_count，其中 \(\text{problem\_count} = \sum_{i = 0}^{\text{group\_count} - 1} \text{group\_size}\lbrack i\rbrack\)

对于组 $i$ 中的矩阵 $A[\text{idx}]$

$\text{op}(A[\text{idx}]) = \left\{ \begin{matrix}
A[\text{idx}] & {\text{if }\textsf{$\mathrm{transa\_array}\lbrack i\rbrack$ == CUBLAS\_OP\_N}} \\
A[\text{idx}]^{T} & {\text{if }\textsf{$\mathrm{transa\_array}\lbrack i\rbrack$ == CUBLAS\_OP\_T}} \\
A[\text{idx}]^{H} & {\text{if }\textsf{$\mathrm{transa\_array}\lbrack i\rbrack$ == CUBLAS\_OP\_C}} \\
\end{matrix} \right.$

对于组 $i$ 中的矩阵 $B[\text{idx}]$，$\text{op}(B[\text{idx}])$ 的定义类似。

> **注意**

> \(C\lbrack\text{idx}\rbrack\) 矩阵不得重叠，即各个gemm运算必须能够独立计算；否则将导致未定义行为。

在某些问题规模下，在不同的CUDA流中多次调用cublas<t>gemmBatched()可能比使用此API更具优势。

| 参数 | 内存位置 | 输入/输出 | 含义 | 数组长度 |
| --- | --- | --- | --- | --- |
| handle |  | input | cuBLAS库上下文的句柄。 |  |
| transa_array | host | input | 每个组的运算op(A[idx])，即非转置或(共轭)转置。 | group_count |
| transb_array | host | input | 每个组的运算op(B[idx])，即非转置或(共轭)转置。 | group_count |
| m_array | host | input | 包含每个组的矩阵op(A[idx])和C[idx]行数的数组。 | group_count |
| n_array | host | input | 包含每个组的op(B[idx])和C[idx]列数的数组。 | group_count |
| k_array | host | input | 包含每个组的op(A[idx])列数和op(B[idx])行数的数组。 | group_count |
| alpha_array | host | input | 包含每个组用于乘法的<type>标量的数组。 | group_count |
| Aarray | device | input | 指向<type>数组的指针数组，每个数组的维度为lda[i] x k[i]，其中lda[i] >= max(1,m[i])（如果transa[i] == CUBLAS_OP_N），否则为lda[i] x m[i]，其中lda[i] >= max(1,k[i])。
所有指针必须满足特定的对齐条件。具体细节请参见下文。 | problem_count |
| lda_array | host | input | 包含每个组用于存储每个矩阵A[idx]的二维数组的前置维度的数组。 | group_count |
| Barray | device | input | 指向<type>数组的指针数组，每个数组的维度为ldb[i] x n[i]，其中ldb[i] >= max(1,k[i])（如果transb[i] == CUBLAS_OP_N），否则为ldb[i] x k[i]，其中ldb[i] >= max(1,n[i])。
所有指针必须满足特定的对齐条件。具体细节请参见下文。 | problem_count |
| ldb_array | host | input | 包含每个组用于存储每个矩阵B[idx]的二维数组的前置维度的数组。 | group_count |
| beta_array | host | input | 包含每个组用于乘法的<type>标量的数组。 | group_count |
| Carray | device | in/out | 指向<type>数组的指针数组。维度为ldc[i] x n[i]，其中ldc[i] >= max(1,m[i])。矩阵C[idx]不应重叠；否则将导致未定义行为。
所有指针必须满足特定的对齐条件。具体细节请参见下文。 | problem_count |
| ldc_array | host | input | 包含每个组用于存储每个矩阵C[idx]的二维数组的前置维度的数组。 | group_count |
| group_count | host | input | 组数 |  |
| group_size | host | input | 包含每个组在Aarray、Barray和Carray中的指针数量的数组。 | group_count |

如果数学模式在using cublasSgemmGroupedBatched()时启用了快速数学模式，则放置在GPU内存中的指针（不是指针数组本身）必须正确对齐以避免未对齐的内存访问错误。理想情况下，所有指针至少对齐到16字节。否则必须满足以下规则：

- 如果k % 4 == 0，则确保intptr_t(ptr) % 16 == 0

此函数可能返回的错误值及其含义如下所列。

| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | 如果transa_array、transb_array、m_array、n_array、k_array、alpha_array、lda_array、ldb_array、beta_array、ldc_array或group_size为NULL，或
如果group_count < 0，或
如果m_array[i] < 0、n_array[i] < 0、k_array[i] < 0、group_size[i] < 0，或
如果transa_array[i]和transb_array[i]不是CUBLAS_OP_N、CUBLAS_OP_C、CUBLAS_OP_T之一，或
如果transa_array[i] == CUBLAS_OP_N且lda_array[i] < max(1, m_array[i])，否则lda_array[i] < max(1, k_array[i])，或
如果transb_array[i] == CUBLAS_OP_N且ldb_array[i] < max(1, k_array[i])，否则ldb_array[i] < max(1, n_array[i])，或
如果ldc_array[i] < max(1, m_array[i]) |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数在GPU上启动失败 |
| CUBLAS_STATUS_NOT_SUPPORTED | 指针模式设置为CUBLAS_POINTER_MODE_DEVICE |



```c++

cublasStatus_t cublasHgemmStridedBatched(cublasHandle_t handle,
                                  cublasOperation_t transa,
                                  cublasOperation_t transb,
                                  int m, int n, int k,
                                  const __half           *alpha,
                                  const __half           *A, int lda,
                                  long long int          strideA,
                                  const __half           *B, int ldb,
                                  long long int          strideB,
                                  const __half           *beta,
                                  __half                 *C, int ldc,
                                  long long int          strideC,
                                  int batchCount)
cublasStatus_t cublasSgemmStridedBatched(cublasHandle_t handle,
                                  cublasOperation_t transa,
                                  cublasOperation_t transb,
                                  int m, int n, int k,
                                  const float           *alpha,
                                  const float           *A, int lda,
                                  long long int          strideA,
                                  const float           *B, int ldb,
                                  long long int          strideB,
                                  const float           *beta,
                                  float                 *C, int ldc,
                                  long long int          strideC,
                                  int batchCount)
cublasStatus_t cublasDgemmStridedBatched(cublasHandle_t handle,
                                  cublasOperation_t transa,
                                  cublasOperation_t transb,
                                  int m, int n, int k,
                                  const double          *alpha,
                                  const double          *A, int lda,
                                  long long int          strideA,
                                  const double          *B, int ldb,
                                  long long int          strideB,
                                  const double          *beta,
                                  double                *C, int ldc,
                                  long long int          strideC,
                                  int batchCount)
cublasStatus_t cublasCgemmStridedBatched(cublasHandle_t handle,
                                  cublasOperation_t transa,
                                  cublasOperation_t transb,
                                  int m, int n, int k,
                                  const cuComplex       *alpha,
                                  const cuComplex       *A, int lda,
                                  long long int          strideA,
                                  const cuComplex       *B, int ldb,
                                  long long int          strideB,
                                  const cuComplex       *beta,
                                  cuComplex             *C, int ldc,
                                  long long int          strideC,
                                  int batchCount)
cublasStatus_t cublasCgemm3mStridedBatched(cublasHandle_t handle,
                                  cublasOperation_t transa,
                                  cublasOperation_t transb,
                                  int m, int n, int k,
                                  const cuComplex       *alpha,
                                  const cuComplex       *A, int lda,
                                  long long int          strideA,
                                  const cuComplex       *B, int ldb,
                                  long long int          strideB,
                                  const cuComplex       *beta,
                                  cuComplex             *C, int ldc,
                                  long long int          strideC,
                                  int batchCount)
cublasStatus_t cublasZgemmStridedBatched(cublasHandle_t handle,
                                  cublasOperation_t transa,
                                  cublasOperation_t transb,
                                  int m, int n, int k,
                                  const cuDoubleComplex *alpha,
                                  const cuDoubleComplex *A, int lda,
                                  long long int          strideA,
                                  const cuDoubleComplex *B, int ldb,
                                  long long int          strideB,
                                  const cuDoubleComplex *beta,
                                  cuDoubleComplex       *C, int ldc,
                                  long long int          strideC,
                                  int batchCount)


```


This function supports the 64-bit Integer Interface.


This function performs the matrix-matrix multiplication of a batch of matrices. The batch is considered to be “uniform”, i.e. all instances have the same dimensions (m, n, k), leading dimensions (lda, ldb, ldc) and transpositions (transa, transb) for their respective A, B and C matrices. Input matrices A, B and output matrix C for each instance of the batch are located at fixed offsets in number of elements from their locations in the previous instance. Pointers to A, B and C matrices for the first instance are passed to the function by the user along with offsets in number of elements - strideA, strideB and strideC that determine the locations of input and output matrices in future instances.


$C + i*{strideC} = \alpha\text{op}(A + i*{strideA})\text{op}(B + i*{strideB}) + \beta(C + i*{strideC}),\text{ for i } \in \lbrack 0,batchCount - 1\rbrack$


where $\alpha$ and $\beta$ are scalars, and $A$ , $B$ and $C$ are arrays of pointers to matrices stored in column-major format with dimensions $\text{op}(A\lbrack i\rbrack)$ $m \times k$ , $\text{op}(B\lbrack i\rbrack)$ $k \times n$ and $C\lbrack i\rbrack$ $m \times n$ , respectively. Also, for matrix $A$


$\text{op}(A) = \left\{ \begin{matrix}
A & {\text{if }\textsf{transa == CUBLAS\_OP\_N}} \\
A^{T} & {\text{if }\textsf{transa == CUBLAS\_OP\_T}} \\
A^{H} & {\text{if }\textsf{transa == CUBLAS\_OP\_C}} \\
\end{matrix} \right.$


and $\text{op}(B\lbrack i\rbrack)$ is defined similarly for matrix $B\lbrack i\rbrack$ .


> **Note**

Note
\(C\lbrack i\rbrack\) matrices must not overlap, i.e. the individual gemm operations must be computable independently; otherwise, undefined behavior is expected.


On certain problem sizes, it might be advantageous to make multiple calls to cublas<t>gemm() in different CUDA streams, rather than use this API.


> **Note**

Note
In the table below, we use A[i], B[i], C[i] as notation for A, B and C matrices in the ith instance of the batch, implicitly assuming they are respectively offsets in number of elements strideA, strideB, strideC away from A[i-1], B[i-1], C[i-1]. The unit for the offset is number of elements and must not be zero .


| Param. | Memory | In/out | Meaning |
| --- | --- | --- | --- |
| handle |  | input | Handle to the cuBLAS library context. |
| transa |  | input | Operation op(A[i]) that is non- or (conj.) transpose. |
| transb |  | input | Operation op(B[i]) that is non- or (conj.) transpose. |
| m |  | input | Number of rows of matrix op(A[i]) and C[i]. |
| n |  | input | Number of columns of op(B[i]) and C[i]. |
| k |  | input | Number of columns of op(A[i]) and rows of op(B[i]). |
| alpha | host or device | input | <type> scalar used for multiplication. |
| A | device | input | <type>* pointer to the A matrix corresponding to the first instance of the batch, with dimensions lda x k with lda >= max(1, m) if transa == CUBLAS_OP_N and lda x m with lda >= max(1, k) otherwise. |
| lda |  | input | Leading dimension of two-dimensional array used to store each matrix A[i]. |
| strideA |  | input | Value of type long long int that gives the offset in number of elements between A[i] and A[i+1] |
| B | device | input | <type>* pointer to the B matrix corresponding to the first instance of the batch, with dimensions ldb x n with ldb >= max(1, k) if transb == CUBLAS_OP_N and ldb x k with ldb >= max(1,n) otherwise. |
| ldb |  | input | Leading dimension of two-dimensional array used to store each matrix B[i]. |
| strideB |  | input | Value of type long long int that gives the offset in number of elements between B[i] and B[i+1] |
| beta | host or device | input | <type> scalar used for multiplication. If beta == 0, C does not have to be a valid input. |
| C | device | in/out | <type>* pointer to the C matrix corresponding to the first instance of the batch, with dimensions ldc x n with ldc >= max(1, m). Matrices C[i] should not overlap; otherwise, undefined behavior is expected. |
| ldc |  | input | Leading dimension of two-dimensional array used to store each matrix C[i]. |
| strideC |  | input | Value of type long long int that gives the offset in number of elements between C[i] and C[i+1] |
| batchCount |  | input | Number of GEMMs to perform in the batch. |


The possible error values returned by this function and their meanings are listed below.


| Error Value | Meaning |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | The operation completed successfully |
| CUBLAS_STATUS_NOT_INITIALIZED | The library was not initialized |
| CUBLAS_STATUS_INVALID_VALUE | If m < 0 or n < 0 or k < 0, or
if transa and transb are not one of CUBLAS_OP_N, CUBLAS_OP_C, CUBLAS_OP_T, or
if lda < max(1, m) when transa == CUBLAS_OP_N and lda < max(1, k) otherwise, or
if ldb < max(1, k) when transb == CUBLAS_OP_N and ldb < max(1, n) otherwise, or
if ldc < max(1, m) |
| CUBLAS_STATUS_EXECUTION_FAILED | The function failed to launch on the GPU |
| CUBLAS_STATUS_ARCH_MISMATCH | cublasHgemmStridedBatched() is only supported for GPU with architecture capabilities equal or greater than 5.3 |






```c++

cublasStatus_t cublasChemm(cublasHandle_t handle,
                           cublasSideMode_t side, cublasFillMode_t uplo,
                           int m, int n,
                           const cuComplex       *alpha,
                           const cuComplex       *A, int lda,
                           const cuComplex       *B, int ldb,
                           const cuComplex       *beta,
                           cuComplex       *C, int ldc)
cublasStatus_t cublasZhemm(cublasHandle_t handle,
                           cublasSideMode_t side, cublasFillMode_t uplo,
                           int m, int n,
                           const cuDoubleComplex *alpha,
                           const cuDoubleComplex *A, int lda,
                           const cuDoubleComplex *B, int ldb,
                           const cuDoubleComplex *beta,
                           cuDoubleComplex *C, int ldc)


```


This function supports the 64-bit Integer Interface.


This function performs the Hermitian matrix-matrix multiplication


$C = \left\{ \begin{matrix}
{\alpha AB + \beta C} & {\text{if }\textsf{side == CUBLAS\_SIDE\_LEFT}} \\
{\alpha BA + \beta C} & {\text{if }\textsf{side == CUBLAS\_SIDE\_RIGHT}} \\
\end{matrix} \right.$


where $A$ is a Hermitian matrix stored in lower or upper mode, $B$ and $C$ are $m \times n$ matrices, and $\alpha$ and $\beta$ are scalars.


| Param. | Memory | In/out | Meaning |
| --- | --- | --- | --- |
| handle |  | input | Handle to the cuBLAS library context. |
| side |  | input | Indicates if matrix A is on the left or right of B. |
| uplo |  | input | Indicates if matrix A lower or upper part is stored, the other Hermitian part is not referenced and is inferred from the stored elements. |
| m |  | input | Number of rows of matrix C and B, with matrix A sized accordingly. |
| n |  | input | Number of columns of matrix C and B, with matrix A sized accordingly. |
| alpha | host or device | input | <type> scalar used for multiplication. |
| A | device | input | <type> array of dimension lda x m with lda >= max(1, m) if side == CUBLAS_SIDE_LEFT and lda x n with lda >= max(1, n) otherwise. The imaginary parts of the diagonal elements are assumed to be zero. |
| lda |  | input | Leading dimension of two-dimensional array used to store matrix A. |
| B | device | input | <type> array of dimension ldb x n with ldb >= max(1, m). |
| ldb |  | input | Leading dimension of two-dimensional array used to store matrix B. |
| beta |  | input | <type> scalar used for multiplication. If beta == 0 then C does not have to be a valid input. |
| C | device | in/out | <type> array of dimensions ldc x n with ldc >= max(1, m). |
| ldc |  | input | Leading dimension of two-dimensional array used to store matrix C. |


The possible error values returned by this function and their meanings are listed below.


| Error Value | Meaning |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | The operation completed successfully |
| CUBLAS_STATUS_NOT_INITIALIZED | The library was not initialized |
| CUBLAS_STATUS_INVALID_VALUE | If m < 0 or n < 0, or
if side is not one of CUBLAS_SIDE_LEFT and CUBLAS_SIDE_RIGHT, or
if uplo is not one of CUBLAS_FILL_MODE_LOWER and CUBLAS_FILL_MODE_UPPER,  or
if lda < max(1, m) when side == CUBLAS_SIDE_LEFT, and lda < max(1, n) otherwise, or
if ldb < max(1, m), or
if ldc < max(1, m), or
if alpha or beta are NULL, or
if C is NULL when beta is not zero |
| CUBLAS_STATUS_EXECUTION_FAILED | The function failed to launch on the GPU |


For references please refer to NETLIB documentation:


[chemm()](http://www.netlib.org/blas/chemm.f), [zhemm()](http://www.netlib.org/blas/zhemm.f)




```c++

cublasStatus_t cublasCher2k(cublasHandle_t handle,
                            cublasFillMode_t uplo, cublasOperation_t trans,
                            int n, int k,
                            const cuComplex       *alpha,
                            const cuComplex       *A, int lda,
                            const cuComplex       *B, int ldb,
                            const float  *beta,
                            cuComplex       *C, int ldc)
cublasStatus_t cublasZher2k(cublasHandle_t handle,
                            cublasFillMode_t uplo, cublasOperation_t trans,
                            int n, int k,
                            const cuDoubleComplex *alpha,
                            const cuDoubleComplex *A, int lda,
                            const cuDoubleComplex *B, int ldb,
                            const double *beta,
                            cuDoubleComplex *C, int ldc)


```


此函数支持64位整数接口。


此函数执行埃尔米特2k阶更新


$C = \alpha\text{op}(A)\text{op}(B)^{H} + \overset{ˉ}{\alpha}\text{op}(B)\text{op}(A)^{H} + \beta C$


其中 $\alpha$ 和 $\beta$ 是标量，$C$ 是以下三角或上三角模式存储的埃尔米特矩阵，$A$ 和 $B$ 是维度分别为 $\text{op}(A)$ $n \times k$ 和 $\text{op}(B)$ $n \times k$ 的矩阵。同样，对于矩阵 $A$ 和 $B$


$\text{op(}A\text{) and op(}B\text{)} = \left\{ \begin{matrix}
{A\text{ and }B} & {\text{if }\textsf{trans == CUBLAS\_OP\_N}} \\
{A^{H}\text{ and }B^{H}} & {\text{if }\textsf{trans == CUBLAS\_OP\_C}} \\
\end{matrix} \right.$


| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | 输入 | 指向cuBLAS库上下文的句柄。 |
| uplo |  | 输入 | 指定矩阵C的下三角或上三角部分是否存储，另一埃尔米特部分不被引用。 |
| trans |  | 输入 | 运算op(A)，非转置或（共轭）转置。 |
| n |  | 输入 | 矩阵op(A)、op(B)和C的行数。 |
| k |  | 输入 | 矩阵op(A)和op(B)的列数。 |
| alpha | 主机或设备 | 输入 | 用于乘法的<type>标量。 |
| A | 设备 | 输入 | <type>数组，维度为lda x k（当transa == CUBLAS_OP_N且lda >= max(1, n)时），否则为lda x n（lda >= max(1, k)）。 |
| lda |  | 输入 | 用于存储矩阵A的二维数组的主维度。 |
| B | 设备 | 输入 | <type>数组，维度为ldb x k（当transb == CUBLAS_OP_N且ldb >= max(1, n)时），否则为ldb x n（ldb >= max(1, k)）。 |
| ldb |  | 输入 | 用于存储矩阵B的二维数组的主维度。 |
| beta | 主机或设备 | 输入 | 用于乘法的<type>标量。如果beta == 0，则C不必是有效输入。 |
| C | 设备 | 输入/输出 | <type>数组，维度为ldc x n，ldc >= max(1, n)。对角线元素的虚部被假定为零并设置为零。 |
| ldc |  | 输入 | 用于存储矩阵C的二维数组的主维度。 |


此函数可能返回的错误值及其含义如下所述。


| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | 如果n < 0或k < 0，或
如果trans不是CUBLAS_OP_N、CUBLAS_OP_T和CUBLAS_OP_C之一，或
如果uplo不是CUBLAS_FILL_MODE_LOWER和CUBLAS_FILL_MODE_UPPER之一，或
如果trans == CUBLAS_OP_N时lda < max(1, n)，否则lda < max(1, k)，或
如果ldc < max(1, n)，或
如果alpha或beta为NULL，或
如果beta不为零时C为NULL |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数在GPU上启动失败 |


有关参考文献，请参阅NETLIB文档：


[cher2k()](http://www.netlib.org/blas/cher2k.f), [zher2k()](http://www.netlib.org/blas/zher2k.f)

```c++

cublasStatus_t cublasCherk(cublasHandle_t handle,
                           cublasFillMode_t uplo, cublasOperation_t trans,
                           int n, int k,
                           const float  *alpha,
                           const cuComplex       *A, int lda,
                           const float  *beta,
                           cuComplex       *C, int ldc)
//此函数支持64位整数接口
cublasStatus_t cublasZherk(cublasHandle_t handle,
                           cublasFillMode_t uplo, cublasOperation_t trans,
                           int n, int k,
                           const double *alpha,
                           const cuDoubleComplex *A, int lda,
                           const double *beta,
                           cuDoubleComplex *C, int ldc)
//此函数支持64位整数接口
```

此函数执行厄米特（Hermitian）秩-k更新操作。

$C = \alpha\text{op}(A)\text{op}(A)^{H} + \beta C$

其中 $\alpha$ 和 $\beta$ 为标量，$C$ 为以下三角模式存储的厄米特矩阵，$A$ 为维度 $\text{op}(A)$ $n \times k$ 的矩阵。此外，对于矩阵 $A$：

$\text{op}(A) = \left\{ \begin{matrix}
A & {\text{if }\textsf{transa == CUBLAS\_OP\_N}} \\
A^{H} & {\text{if }\textsf{transa == CUBLAS\_OP\_C}} \\
\end{matrix} \right.$

| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | input | cuBLAS库上下文的句柄 |
| uplo |  | input | 指示矩阵C的下三角或上三角部分是否存储，另一半厄米特部分不被引用 |
| trans |  | input | 非转置或（共轭）转置操作 op(A) |
| n |  | input | 矩阵 op(A) 和 C 的行数 |
| k |  | input | 矩阵 op(A) 的列数 |
| alpha | 主机或设备 | input | 用于乘法运算的 <type> 标量 |
| A | 设备 | input | 维度为 lda x k 的 <type> 数组，当 transa == CUBLAS_OP_N 时 lda >= max(1, n)，否则为 lda x n 且 lda >= max(1, k) |
| lda |  | input | 用于存储矩阵A的二维数组的主维度 |
| beta |  | input | 用于乘法运算的 <type> 标量。如果 beta == 0，则C不必是有效输入 |
| C | 设备 | 输入/输出 | 维度为 ldc x n 的 <type> 数组，ldc >= max(1, n)。对角元素的虚部被假定为零并设置为零 |
| ldc |  | input | 用于存储矩阵C的二维数组的主维度 |

此函数返回的可能错误值及其含义如下。

| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | 如果 n < 0 或 k < 0，或如果 trans 不是 CUBLAS_OP_N、CUBLAS_OP_T 和 CUBLAS_OP_C 之一，或如果 uplo 不是 CUBLAS_FILL_MODE_LOWER 和 CUBLAS_FILL_MODE_UPPER 之一，或当 trans == CUBLAS_OP_N 时 lda < max(1, n)，否则 lda < max(1, k)，或 ldc < max(1, n)，或 alpha 或 beta 为 NULL，或当 beta 不为零时 C 为 NULL |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数无法在GPU上启动 |

更多参考信息请参阅NETLIB文档：

[cherk()](http://www.netlib.org/blas/cherk.f), [zherk()](http://www.netlib.org/blas/zherk.f)



```c++

cublasStatus_t cublasCherkx(cublasHandle_t handle,
                            cublasFillMode_t uplo, cublasOperation_t trans,
                            int n, int k,
                            const cuComplex       *alpha,
                            const cuComplex       *A, int lda,
                            const cuComplex       *B, int ldb,
                            const float  *beta,
                            cuComplex       *C, int ldc)
cublasStatus_t cublasZherkx(cublasHandle_t handle,
                            cublasFillMode_t uplo, cublasOperation_t trans,
                            int n, int k,
                            const cuDoubleComplex *alpha,
                            const cuDoubleComplex *A, int lda,
                            const cuDoubleComplex *B, int ldb,
                            const double *beta,
                            cuDoubleComplex *C, int ldc)


```


This function supports the 64-bit Integer Interface.


This function performs a variation of the Hermitian rank- $k$ update


$C = \alpha\text{op}(A)\text{op}(B)^{H} + \beta C$


where $\alpha$ and $\beta$ are scalars, $C$ is a Hermitian matrix stored in lower or upper mode, and $A$ and $B$ are matrices with dimensions $\text{op}(A)$ $n \times k$ and $\text{op}(B)$ $n \times k$ , respectively. Also, for matrix $A$ and $B$


$\text{op(}A\text{) and op(}B\text{)} = \left\{ \begin{matrix}
{A\text{ and }B} & {\text{if }\textsf{trans == CUBLAS\_OP\_N}} \\
{A^{H}\text{ and }B^{H}} & {\text{if }\textsf{trans == CUBLAS\_OP\_C}} \\
\end{matrix} \right.$


This routine can be used when the matrix B is in such way that the result is guaranteed to be hermitian. An usual example is when the matrix B is a scaled form of the matrix A: this is equivalent to B being the product of the matrix A and a diagonal matrix. For an efficient computation of the product of a regular matrix with a diagonal matrix, refer to the routine cublas<t>dgmm().


| Param. | Memory | In/out | Meaning |
| --- | --- | --- | --- |
| handle |  | input | Handle to the cuBLAS library context. |
| uplo |  | input | Indicates if matrix C lower or upper part is stored, the other Hermitian part is not referenced. |
| trans |  | input | Operation op(A) that is non- or (conj.) transpose. |
| n |  | input | Number of rows of matrix op(A), op(B) and C. |
| k |  | input | Number of columns of matrix op(A) and op(B). |
| alpha | host or device | input | <type> scalar used for multiplication. |
| A | device | input | <type> array of dimension lda x k with lda >= max(1, n) if transa == CUBLAS_OP_N and lda x n with lda >= max(1, k) otherwise. |
| lda |  | input | Leading dimension of two-dimensional array used to store matrix A. |
| B | device | input | <type> array of dimension ldb x k with ldb >= max(1, n) if transb == CUBLAS_OP_N and ldb x n with ldb >= max(1,k) otherwise. |
| ldb |  | input | Leading dimension of two-dimensional array used to store matrix B. |
| beta | host or device | input | Real scalar used for multiplication. If beta == 0 then C does not have to be a valid input. |
| C | device | in/out | <type> array of dimension ldc x n, with ldc >= max(1, n). The imaginary parts of the diagonal elements are assumed and set to zero. |
| ldc |  | input | Leading dimension of two-dimensional array used to store matrix C. |


The possible error values returned by this function and their meanings are listed below.


| Error Value | Meaning |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | The operation completed successfully |
| CUBLAS_STATUS_NOT_INITIALIZED | The library was not initialized |
| CUBLAS_STATUS_INVALID_VALUE | If n < 0 or k < 0, or
if trans is not one of CUBLAS_OP_N, CUBLAS_OP_T and CUBLAS_OP_C, or
if uplo is not one of CUBLAS_FILL_MODE_LOWER and CUBLAS_FILL_MODE_UPPER, or
if lda < max(1, n) when trans == CUBLAS_OP_N, and lda < max(1, k) otherwise, or
if ldc < max(1, n), or
if alpha or beta are NULL, or
if C is NULL when beta is not zero |
| CUBLAS_STATUS_EXECUTION_FAILED | The function failed to launch on the GPU |


For references please refer to NETLIB documentation:


[cherk()](http://www.netlib.org/blas/cherk.f), [zherk()](http://www.netlib.org/blas/zherk.f) and


[cher2k()](http://www.netlib.org/blas/cher2k.f), [zher2k()](http://www.netlib.org/blas/zher2k.f)






```c++

cublasStatus_t cublasSsymm(cublasHandle_t handle,
                           cublasSideMode_t side, cublasFillMode_t uplo,
                           int m, int n,
                           const float           *alpha,
                           const float           *A, int lda,
                           const float           *B, int ldb,
                           const float           *beta,
                           float           *C, int ldc)
cublasStatus_t cublasDsymm(cublasHandle_t handle,
                           cublasSideMode_t side, cublasFillMode_t uplo,
                           int m, int n,
                           const double          *alpha,
                           const double          *A, int lda,
                           const double          *B, int ldb,
                           const double          *beta,
                           double          *C, int ldc)
cublasStatus_t cublasCsymm(cublasHandle_t handle,
                           cublasSideMode_t side, cublasFillMode_t uplo,
                           int m, int n,
                           const cuComplex       *alpha,
                           const cuComplex       *A, int lda,
                           const cuComplex       *B, int ldb,
                           const cuComplex       *beta,
                           cuComplex       *C, int ldc)
cublasStatus_t cublasZsymm(cublasHandle_t handle,
                           cublasSideMode_t side, cublasFillMode_t uplo,
                           int m, int n,
                           const cuDoubleComplex *alpha,
                           const cuDoubleComplex *A, int lda,
                           const cuDoubleComplex *B, int ldb,
                           const cuDoubleComplex *beta,
                           cuDoubleComplex *C, int ldc)


```


This function supports the 64-bit Integer Interface.


This function performs the symmetric matrix-matrix multiplication


$C = \left\{ \begin{matrix}
{\alpha AB + \beta C} & {\text{if }\textsf{side == CUBLAS\_SIDE\_LEFT}} \\
{\alpha BA + \beta C} & {\text{if }\textsf{side == CUBLAS\_SIDE\_RIGHT}} \\
\end{matrix} \right.$


where $A$ is a symmetric matrix stored in lower or upper mode, $B$ and $C$ are $m \times n$ matrices, and $\alpha$ and $\beta$ are scalars.


| Param. | Memory | In/out | Meaning |
| --- | --- | --- | --- |
| handle |  | input | Handle to the cuBLAS library context. |
| side |  | input | Indicates if matrix A is on the left or right of B. |
| uplo |  | input | Indicates if matrix A lower or upper part is stored, the other symmetric part is not referenced and is inferred from the stored elements. |
| m |  | input | Number of rows of matrix C and B, with matrix A sized accordingly. |
| n |  | input | Number of columns of matrix C and B, with matrix A sized accordingly. |
| alpha | host or device | input | <type> scalar used for multiplication. |
| A | device | input | <type> array of dimension lda x m with lda >= max(1, m) if side == CUBLAS_SIDE_LEFT and lda x n with lda >= max(1, n) otherwise. |
| lda |  | input | Leading dimension of two-dimensional array used to store matrix A. |
| B | device | input | <type> array of dimension ldb x n with ldb >= max(1, m). |
| ldb |  | input | Leading dimension of two-dimensional array used to store matrix B. |
| beta | host or device | input | <type> scalar used for multiplication. If beta == 0 then C does not have to be a valid input. |
| C | device | in/out | <type> array of dimension ldc x n with ldc >= max(1, m). |
| ldc |  | input | Leading dimension of two-dimensional array used to store matrix C. |


The possible error values returned by this function and their meanings are listed below.


| Error Value | Meaning |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | The operation completed successfully |
| CUBLAS_STATUS_NOT_INITIALIZED | The library was not initialized |
| CUBLAS_STATUS_INVALID_VALUE | If m < 0 or n < 0, or
if side is not one of CUBLAS_SIDE_LEFT and CUBLAS_SIDE_RIGHT, or
if uplo is not one of CUBLAS_FILL_MODE_LOWER and CUBLAS_FILL_MODE_UPPER,  or
if lda < max(1, m) when side == CUBLAS_SIDE_LEFT, and lda < max(1, n) otherwise, or
if ldb < max(1, m), or
if ldc < max(1, m), or
if alpha or beta are NULL, or
if C is NULL when beta is not zero |
| CUBLAS_STATUS_EXECUTION_FAILED | The function failed to launch on the GPU |


For references please refer to NETLIB documentation:


[ssymm()](http://www.netlib.org/blas/ssymm.f), [dsymm()](http://www.netlib.org/blas/dsymm.f), [csymm()](http://www.netlib.org/blas/csymm.f), [zsymm()](http://www.netlib.org/blas/zsymm.f)






```c++

cublasStatus_t cublasSsyr2k(cublasHandle_t handle,
                            cublasFillMode_t uplo, cublasOperation_t trans,
                            int n, int k,
                            const float           *alpha,
                            const float           *A, int lda,
                            const float           *B, int ldb,
                            const float           *beta,
                            float           *C, int ldc)
cublasStatus_t cublasDsyr2k(cublasHandle_t handle,
                            cublasFillMode_t uplo, cublasOperation_t trans,
                            int n, int k,
                            const double          *alpha,
                            const double          *A, int lda,
                            const double          *B, int ldb,
                            const double          *beta,
                            double          *C, int ldc)
cublasStatus_t cublasCsyr2k(cublasHandle_t handle,
                            cublasFillMode_t uplo, cublasOperation_t trans,
                            int n, int k,
                            const cuComplex       *alpha,
                            const cuComplex       *A, int lda,
                            const cuComplex       *B, int ldb,
                            const cuComplex       *beta,
                            cuComplex       *C, int ldc)
cublasStatus_t cublasZsyr2k(cublasHandle_t handle,
                            cublasFillMode_t uplo, cublasOperation_t trans,
                            int n, int k,
                            const cuDoubleComplex *alpha,
                            const cuDoubleComplex *A, int lda,
                            const cuDoubleComplex *B, int ldb,
                            const cuDoubleComplex *beta,
                            cuDoubleComplex *C, int ldc)


```


This function supports the 64-bit Integer Interface.


This function performs the symmetric rank- $2k$ update


$C = \alpha(\text{op}(A)\text{op}(B)^{T} + \text{op}(B)\text{op}(A)^{T}) + \beta C$


where $\alpha$ and $\beta$ are scalars, $C$ is a symmetric matrix stored in lower or upper mode, and $A$ and $B$ are matrices with dimensions $\text{op}(A)$ $n \times k$ and $\text{op}(B)$ $n \times k$ , respectively. Also, for matrix $A$ and $B$


$\text{op(}A\text{) and op(}B\text{)} = \left\{ \begin{matrix}
{A\text{ and }B} & {\text{if }\textsf{trans == CUBLAS\_OP\_N}} \\
{A^{T}\text{ and }B^{T}} & {\text{if }\textsf{trans == CUBLAS\_OP\_T}} \\
\end{matrix} \right.$


| Param. | Memory | In/out | Meaning |
| --- | --- | --- | --- |
| handle |  | input | Handle to the cuBLAS library context. |
| uplo |  | input | Indicates if matrix C lower or upper part, is stored, the other symmetric part is not referenced and is inferred from the stored elements. |
| trans |  | input | Operation op(A) that is non- or transpose. |
| n |  | input | Number of rows of matrix op(A), op(B) and C. |
| k |  | input | Number of columns of matrix op(A) and op(B). |
| alpha | host or device | input | <type> scalar used for multiplication. |
| A | device | input | <type> array of dimension lda x k with lda >= max(1, n) if transa == CUBLAS_OP_N and lda x n with lda >= max(1, k) otherwise. |
| lda |  | input | Leading dimension of two-dimensional array used to store matrix A. |
| B | device | input | <type> array of dimensions ldb x k with ldb >= max(1, n) if transb == CUBLAS_OP_N and ldb x n with ldb >= max(1,k) otherwise. |
| ldb |  | input | Leading dimension of two-dimensional array used to store matrix B. |
| beta | host or device | input | <type> scalar used for multiplication. If beta == 0, then C does not have to be a valid input. |
| C | device | in/out | <type> array of dimensions ldc x n with ldc >= max(1, n). |
| ldc |  | input | Leading dimension of two-dimensional array used to store matrix C. |


The possible error values returned by this function and their meanings are listed below.


| Error Value | Meaning |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | The operation completed successfully |
| CUBLAS_STATUS_NOT_INITIALIZED | The library was not initialized |
| CUBLAS_STATUS_INVALID_VALUE | If n < 0 or k < 0, or
if trans is not one of CUBLAS_OP_N, CUBLAS_OP_T and CUBLAS_OP_C, or
if uplo is not one of CUBLAS_FILL_MODE_LOWER and CUBLAS_FILL_MODE_UPPER, or
if lda < max(1, n) when trans == CUBLAS_OP_N, and lda < max(1, k) otherwise, or
if ldb < max(1, n) when trans == CUBLAS_OP_N, and ldb < max(1, k) otherwise, or
if ldc < max(1, n), or
if alpha or beta are NULL, or
if C is NULL when beta is not zero |
| CUBLAS_STATUS_EXECUTION_FAILED | The function failed to launch on the GPU |


For references please refer to NETLIB documentation:


[ssyr2k()](http://www.netlib.org/blas/ssyr2k.f), [dsyr2k()](http://www.netlib.org/blas/dsyr2k.f), [csyr2k()](http://www.netlib.org/blas/csyr2k.f), [zsyr2k()](http://www.netlib.org/blas/zsyr2k.f)




```c++

cublasStatus_t cublasSsyrk(cublasHandle_t handle,
                           cublasFillMode_t uplo, cublasOperation_t trans,
                           int n, int k,
                           const float           *alpha,
                           const float           *A, int lda,
                           const float           *beta,
                           float           *C, int ldc)
cublasStatus_t cublasDsyrk(cublasHandle_t handle,
                           cublasFillMode_t uplo, cublasOperation_t trans,
                           int n, int k,
                           const double          *alpha,
                           const double          *A, int lda,
                           const double          *beta,
                           double          *C, int ldc)
cublasStatus_t cublasCsyrk(cublasHandle_t handle,
                           cublasFillMode_t uplo, cublasOperation_t trans,
                           int n, int k,
                           const cuComplex       *alpha,
                           const cuComplex       *A, int lda,
                           const cuComplex       *beta,
                           cuComplex       *C, int ldc)
cublasStatus_t cublasZsyrk(cublasHandle_t handle,
                           cublasFillMode_t uplo, cublasOperation_t trans,
                           int n, int k,
                           const cuDoubleComplex *alpha,
                           const cuDoubleComplex *A, int lda,
                           const cuDoubleComplex *beta,
                           cuDoubleComplex *C, int ldc)


```

此函数支持64位整数接口。

此函数执行对称秩-$k$更新

$C = \alpha\text{op}(A)\text{op}(A)^{T} + \beta C$

其中 $\alpha$ 和 $\beta$ 是标量，$C$ 是以下三角模式存储的对称矩阵，$A$ 是维度为 $\text{op}(A)$ $n \times k$ 的矩阵。另外，对于矩阵 $A$

$\text{op}(A) = \left\{ \begin{matrix}
A & {\text{if }\textsf{transa == CUBLAS\_OP\_N}} \\
A^{T} & {\text{if }\textsf{transa == CUBLAS\_OP\_T}} \\
\end{matrix} \right.$

| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | 输入 | cuBLAS 库上下文的句柄。 |
| uplo |  | 输入 | 指示矩阵 C 的下三角或上三角部分是否被存储，另一对称部分未被引用，且从存储的元素中推断。 |
| trans |  | 输入 | 操作 op(A)，即非转置或转置。 |
| n |  | 输入 | 矩阵 op(A) 和 C 的行数。 |
| k |  | 输入 | 矩阵 op(A) 的列数。 |
| alpha | 主机或设备 | 输入 | 用于乘法的 <type> 标量。 |
| A | 设备 | 输入 | 维度为 lda x k 的 <type> 数组，当 trans == CUBLAS_OP_N 时 lda >= max(1, n)，否则为 lda x n 且 lda >= max(1, k)。 |
| lda |  | 输入 | 用于存储矩阵 A 的二维数组的主维度。 |
| beta | 主机或设备 | 输入 | 用于乘法的 <type> 标量。如果 beta == 0，则 C 不必是有效输入。 |
| C | 设备 | 输入/输出 | 维度为 ldc x n 的 <type> 数组，ldc >= max(1, n)。 |
| ldc |  | 输入 | 用于存储矩阵 C 的二维数组的主维度。 |

此函数返回的可能错误值及其含义如下所列。

| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | 如果 n < 0 或 k < 0，或
如果 trans 不是 CUBLAS_OP_N、CUBLAS_OP_T 和 CUBLAS_OP_C 之一，或
如果 uplo 不是 CUBLAS_FILL_MODE_LOWER 和 CUBLAS_FILL_MODE_UPPER 之一，或
如果 trans == CUBLAS_OP_N 时 lda < max(1, n)，否则 lda < max(1, k)，或
如果 ldc < max(1, n)，或
如果 alpha 或 beta 为 NULL，或
如果 beta 不为零时 C 为 NULL |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数在 GPU 上启动失败 |

参考文献请参阅 NETLIB 文档：

[ssyrk()](http://www.netlib.org/blas/ssyrk.f), [dsyrk()](http://www.netlib.org/blas/dsyrk.f), [csyrk()](http://www.netlib.org/blas/csyrk.f), [zsyrk()](http://www.netlib.org/blas/zsyrk.f)

```c++

cublasStatus_t cublasSsyrkx(cublasHandle_t handle,
                            cublasFillMode_t uplo, cublasOperation_t trans,
                            int n, int k,
                            const float           *alpha,
                            const float           *A, int lda,
                            const float           *B, int ldb,
                            const float           *beta,
                            float           *C, int ldc)
cublasStatus_t cublasDsyrkx(cublasHandle_t handle,
                            cublasFillMode_t uplo, cublasOperation_t trans,
                            int n, int k,
                            const double          *alpha,
                            const double          *A, int lda,
                            const double          *B, int ldb,
                            const double          *beta,
                            double          *C, int ldc)
cublasStatus_t cublasCsyrkx(cublasHandle_t handle,
                            cublasFillMode_t uplo, cublasOperation_t trans,
                            int n, int k,
                            const cuComplex       *alpha,
                            const cuComplex       *A, int lda,
                            const cuComplex       *B, int ldb,
                            const cuComplex       *beta,
                            cuComplex       *C, int ldc)
cublasStatus_t cublasZsyrkx(cublasHandle_t handle,
                            cublasFillMode_t uplo, cublasOperation_t trans,
                            int n, int k,
                            const cuDoubleComplex *alpha,
                            const cuDoubleComplex *A, int lda,
                            const cuDoubleComplex *B, int ldb,
                            const cuDoubleComplex *beta,
                            cuDoubleComplex *C, int ldc)


```

此函数支持64位整数接口。

此函数执行对称秩k更新的一种变体

$C = \alpha\text{op}(A)\text{op}(B)^{T} + \beta C$

其中 $\alpha$ 和 $\beta$ 是标量，$C$ 是以下三角或上三角模式存储的对称矩阵，$A$ 和 $B$ 是维度分别为 $\text{op}(A)$ $n \times k$ 和 $\text{op}(B)$ $n \times k$ 的矩阵。同样，对于矩阵 $A$ 和 $B$

$\text{op(}A\text{) and op(}B\text{)} = \left\{ \begin{matrix}
{A\text{ and }B} & {\text{if }\textsf{trans == CUBLAS\_OP\_N}} \\
{A^{T}\text{ and }B^{T}} & {\text{if }\textsf{trans == CUBLAS\_OP\_T}} \\
\end{matrix} \right.$

当B以保证结果对称的方式给出时，可以使用此例程。一个常见的例子是矩阵B是矩阵A的缩放形式：这等价于矩阵B是矩阵A与对角矩阵的乘积。有关矩阵与对角矩阵乘积的高效计算，请参阅 `cublas<t>dgmm()` 例程。

| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | input | cuBLAS库上下文的句柄。 |
| uplo |  | input | 指示是否存储矩阵C的下三角或上三角部分，另一对称部分未被引用，且从存储的元素中推断。 |
| trans |  | input | op(A)运算，非转置或转置。 |
| n |  | input | 矩阵op(A)、op(B)和C的行数。 |
| k |  | input | 矩阵op(A)和op(B)的列数。 |
| alpha | 主机或设备 | input | 用于乘法的<type>标量。 |
| A | 设备 | input | 维度为lda x k的<type>数组，当transa == CUBLAS_OP_N时lda >= max(1, n)，否则为lda x n且lda >= max(1, k)。 |
| lda |  | input | 用于存储矩阵A的二维数组的主维度。 |
| B | 设备 | input | 当transb == CUBLAS_OP_N时维度为ldb x k的<type>数组，ldb >= max(1, n)，否则为ldb x n且ldb >= max(1,k)。 |
| ldb |  | input | 用于存储矩阵B的二维数组的主维度。 |
| beta | 主机或设备 | input | 用于乘法的<type>标量。如果beta == 0，则C不必是有效输入。 |
| C | 设备 | 输入/输出 | 维度为ldc x n的<type>数组，ldc >= max(1, n)。 |
| ldc |  | input | 用于存储矩阵C的二维数组的主维度。 |

此函数返回的可能错误值及其含义如下表所示。

| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | 如果n < 0或k < 0，或
如果trans不是CUBLAS_OP_N、CUBLAS_OP_T和CUBLAS_OP_C之一，或
如果uplo不是CUBLAS_FILL_MODE_LOWER和CUBLAS_FILL_MODE_UPPER之一，或
如果当trans == CUBLAS_OP_N时lda < max(1, n)，否则lda < max(1, k)，或
如果当trans == CUBLAS_OP_N时ldb < max(1, n)，否则ldb < max(1, k)，或
如果ldc < max(1, n)，或
如果alpha或beta为NULL，或
如果beta不为零时C为NULL |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数无法在GPU上启动 |

有关参考文献，请参阅NETLIB文档：

[ssyrk()](http://www.netlib.org/blas/ssyrk.f)、[dsyrk()](http://www.netlib.org/blas/dsyrk.f)、[csyrk()](http://www.netlib.org/blas/csyrk.f)、[zsyrk()](http://www.netlib.org/blas/zsyrk.f)和

[ssyr2k()](http://www.netlib.org/blas/ssyr2k.f)、[dsyr2k()](http://www.netlib.org/blas/dsyr2k.f)、[csyr2k()](http://www.netlib.org/blas/csyr2k.f)、[zsyr2k()](http://www.netlib.org/blas/zsyr2k.f)



```c++

cublasStatus_t cublasStrmm(cublasHandle_t handle,
                           cublasSideMode_t side, cublasFillMode_t uplo,
                           cublasOperation_t trans, cublasDiagType_t diag,
                           int m, int n,
                           const float           *alpha,
                           const float           *A, int lda,
                           const float           *B, int ldb,
                           float                 *C, int ldc)
cublasStatus_t cublasDtrmm(cublasHandle_t handle,
                           cublasSideMode_t side, cublasFillMode_t uplo,
                           cublasOperation_t trans, cublasDiagType_t diag,
                           int m, int n,
                           const double          *alpha,
                           const double          *A, int lda,
                           const double          *B, int ldb,
                           double                *C, int ldc)
cublasStatus_t cublasCtrmm(cublasHandle_t handle,
                           cublasSideMode_t side, cublasFillMode_t uplo,
                           cublasOperation_t trans, cublasDiagType_t diag,
                           int m, int n,
                           const cuComplex       *alpha,
                           const cuComplex       *A, int lda,
                           const cuComplex       *B, int ldb,
                           cuComplex             *C, int ldc)
cublasStatus_t cublasZtrmm(cublasHandle_t handle,
                           cublasSideMode_t side, cublasFillMode_t uplo,
                           cublasOperation_t trans, cublasDiagType_t diag,
                           int m, int n,
                           const cuDoubleComplex *alpha,
                           const cuDoubleComplex *A, int lda,
                           const cuDoubleComplex *B, int ldb,
                           cuDoubleComplex       *C, int ldc)


```


This function supports the 64-bit Integer Interface.


This function performs the triangular matrix-matrix multiplication


$C = \left\{ \begin{matrix}
{\alpha\text{op}(A)B} & {\text{if }\textsf{side == CUBLAS\_SIDE\_LEFT}} \\
{\alpha B\text{op}(A)} & {\text{if }\textsf{side == CUBLAS\_SIDE\_RIGHT}} \\
\end{matrix} \right.$


where $A$ is a triangular matrix stored in lower or upper mode with or without the main diagonal, $B$ and $C$ are $m \times n$ matrix, and $\alpha$ is a scalar. Also, for matrix $A$


$\text{op}(A) = \left\{ \begin{matrix}
A & {\text{if }\textsf{transa == CUBLAS\_OP\_N}} \\
A^{T} & {\text{if }\textsf{transa == CUBLAS\_OP\_T}} \\
A^{H} & {\text{if }\textsf{transa == CUBLAS\_OP\_C}} \\
\end{matrix} \right.$


Notice that in order to achieve better parallelism cuBLAS differs from the BLAS API only for this routine. The BLAS API assumes an in-place implementation (with results written back to B), while the cuBLAS API assumes an out-of-place implementation (with results written into C). The application can obtain the in-place functionality of BLAS in the cuBLAS API by passing the address of the matrix B in place of the matrix C. No other overlapping in the input parameters is supported.


| Param. | Memory | In/out | Meaning |
| --- | --- | --- | --- |
| handle |  | input | Handle to the cuBLAS library context. |
| side |  | input | Indicates if matrix A is on the left or right of B. |
| uplo |  | input | Indicates if matrix A lower or upper part is stored, the other part is not referenced and is inferred from the stored elements. |
| trans |  | input | Operation op(A) that is non- or (conj.) transpose. |
| diag |  | input | Indicates if the elements on the main diagonal of matrix A are unity and should not be accessed. |
| m |  | input | Number of rows of matrix B, with matrix A sized accordingly. |
| n |  | input | Number of columns of matrix B, with matrix A sized accordingly. |
| alpha | host or device | input | <type> scalar used for multiplication, if alpha == 0 then A is not referenced and B does not have to be a valid input. |
| A | device | input | <type> array of dimension lda x m with lda >= max(1, m) if side == CUBLAS_SIDE_LEFT and lda x n with lda >= max(1, n) otherwise. |
| lda |  | input | Leading dimension of two-dimensional array used to store matrix A. |
| B | device | input | <type> array of dimension ldb x n with ldb >= max(1, m). |
| ldb |  | input | Leading dimension of two-dimensional array used to store matrix B. |
| C | device | in/out | <type> array of dimension ldc x n with ldc >= max(1, m). |
| ldc |  | input | Leading dimension of two-dimensional array used to store matrix C. |


The possible error values returned by this function and their meanings are listed below.


| Error Value | Meaning |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | The operation completed successfully |
| CUBLAS_STATUS_NOT_INITIALIZED | The library was not initialized |
| CUBLAS_STATUS_INVALID_VALUE | If m < 0, n < 0, or
if trans is not one of CUBLAS_OP_N, CUBLAS_OP_T and CUBLAS_OP_C, or
if uplo is not one of CUBLAS_FILL_MODE_LOWER and CUBLAS_FILL_MODE_UPPER, or
if side is not one of CUBLAS_SIDE_LEFT and CUBLAS_SIDE_RIGHT, or
if lda < max(1, m) if side == CUBLAS_SIDE_LEFT, and lda < max(1, n) otherwise, or
if ldb < max(1, m), or
if ldc < max(1, m), or
if alpha is NULL |
| CUBLAS_STATUS_EXECUTION_FAILED | The function failed to launch on the GPU |


For references please refer to NETLIB documentation:


[strmm()](http://www.netlib.org/blas/strmm.f), [dtrmm()](http://www.netlib.org/blas/dtrmm.f), [ctrmm()](http://www.netlib.org/blas/ctrmm.f), [ztrmm()](http://www.netlib.org/blas/ztrmm.f)




```c++
// 此函数支持64位整数接口

cublasStatus_t cublasStrsm(cublasHandle_t handle,
                           cublasSideMode_t side, cublasFillMode_t uplo,
                           cublasOperation_t trans, cublasDiagType_t diag,
                           int m, int n,
                           const float           *alpha,
                           const float           *A, int lda,
                           float           *B, int ldb)
cublasStatus_t cublasDtrsm(cublasHandle_t handle,
                           cublasSideMode_t side, cublasFillMode_t uplo,
                           cublasOperation_t trans, cublasDiagType_t diag,
                           int m, int n,
                           const double          *alpha,
                           const double          *A, int lda,
                           double          *B, int ldb)
cublasStatus_t cublasCtrsm(cublasHandle_t handle,
                           cublasSideMode_t side, cublasFillMode_t uplo,
                           cublasOperation_t trans, cublasDiagType_t diag,
                           int m, int n,
                           const cuComplex       *alpha,
                           const cuComplex       *A, int lda,
                           cuComplex       *B, int ldb)
cublasStatus_t cublasZtrsm(cublasHandle_t handle,
                           cublasSideMode_t side, cublasFillMode_t uplo,
                           cublasOperation_t trans, cublasDiagType_t diag,
                           int m, int n,
                           const cuDoubleComplex *alpha,
                           const cuDoubleComplex *A, int lda,
                           cuDoubleComplex *B, int ldb)


```

此函数支持64位整数接口。

此函数求解带有多个右侧项的三角线性系统

$\left\{ \begin{matrix}
{\text{op}(A)X = \alpha B} & {\text{if }\textsf{side == CUBLAS\_SIDE\_LEFT}} \\
{X\text{op}(A) = \alpha B} & {\text{if }\textsf{side == CUBLAS\_SIDE\_RIGHT}} \\
\end{matrix} \right.$

其中 $A$ 是一个三角矩阵，以低模式或高模式存储，可能包含或不包含主对角线，$X$ 和 $B$ 是 $m \times n$ 矩阵，$\alpha$ 是标量。同样，对于矩阵 $A$

$\text{op}(A) = \left\{ \begin{matrix}
A & {\text{if }\textsf{transa == CUBLAS\_OP\_N}} \\
A^{T} & {\text{if }\textsf{transa == CUBLAS\_OP\_T}} \\
A^{H} & {\text{if }\textsf{transa == CUBLAS\_OP\_C}} \\
\end{matrix} \right.$

解 $X$ 在输出时覆盖右侧项 $B$。

此函数不包含奇异性或近奇异性的检测。

| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | input | cuBLAS 库上下文的句柄。 |
| side |  | input | 指示矩阵 A 位于 X 的左侧还是右侧。 |
| uplo |  | input | 指示矩阵 A 的低三角部分还是高三角部分被存储，另一部分未被引用且从存储的元素中推断。 |
| trans |  | input | 操作 op(A)，即非转置或（共轭）转置。 |
| diag |  | input | 指示矩阵 A 主对角线上的元素是否为单位元素，且不应被访问。 |
| m |  | input | 矩阵 B 的行数，矩阵 A 相应调整大小。 |
| n |  | input | 矩阵 B 的列数，矩阵 A 相应调整大小。 |
| alpha | 主机或设备 | input | 用于乘法运算的 <type> 标量，如果 alpha == 0，则不引用 A，且 B 不必是有效输入。 |
| A | 设备 | input | 维度为 lda x m 的 <type> 数组，当 side == CUBLAS_SIDE_LEFT 时 lda >= max(1, m)，否则为 lda x n 且 lda >= max(1, n)。 |
| lda |  | input | 用于存储矩阵 A 的二维数组的主维度。 |
| B | 设备 | 输入/输出 | <type> 数组，维度为 ldb x n，其中 ldb >= max(1, m)。 |
| ldb |  | input | 用于存储矩阵 B 的二维数组的主维度。 |

此函数返回的可能错误值及其含义如下所列。

| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | 如果 m < 0, n < 0，或<br>如果 trans 不是 CUBLAS_OP_N、CUBLAS_OP_T 和 CUBLAS_OP_C 之一，或<br>如果 uplo 不是 CUBLAS_FILL_MODE_LOWER 和 CUBLAS_FILL_MODE_UPPER 之一，或<br>如果 side 不是 CUBLAS_SIDE_LEFT 和 CUBLAS_SIDE_RIGHT 之一，或<br>如果 diag 不是 CUBLAS_DIAG_UNIT 和 CUBLAS_DIAG_NON_UNIT 之一，或<br>如果 side == CUBLAS_SIDE_LEFT 时 lda < max(1, m)，否则 lda < max(1, n)，或<br>如果 ldb < max(1, m)，或<br>如果 alpha 为 NULL |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数在 GPU 上启动失败 |

有关参考文献，请参阅 NETLIB 文档：

[strsm()](http://www.netlib.org/blas/strsm.f), [dtrsm()](http://www.netlib.org/blas/dtrsm.f), [ctrsm()](http://www.netlib.org/blas/ctrsm.f), [ztrsm()](http://www.netlib.org/blas/ztrsm.f)



```c++

cublasStatus_t cublasStrsmBatched( cublasHandle_t    handle,
                                   cublasSideMode_t  side,
                                   cublasFillMode_t  uplo,
                                   cublasOperation_t trans,
                                   cublasDiagType_t  diag,
                                   int m,
                                   int n,
                                   const float *alpha,
                                   const float *const A[],
                                   int lda,
                                   float *const B[],
                                   int ldb,
                                   int batchCount);
cublasStatus_t cublasDtrsmBatched( cublasHandle_t    handle,
                                   cublasSideMode_t  side,
                                   cublasFillMode_t  uplo,
                                   cublasOperation_t trans,
                                   cublasDiagType_t  diag,
                                   int m,
                                   int n,
                                   const double *alpha,
                                   const double *const A[],
                                   int lda,
                                   double *const B[],
                                   int ldb,
                                   int batchCount);
cublasStatus_t cublasCtrsmBatched( cublasHandle_t    handle,
                                   cublasSideMode_t  side,
                                   cublasFillMode_t  uplo,
                                   cublasOperation_t trans,
                                   cublasDiagType_t  diag,
                                   int m,
                                   int n,
                                   const cuComplex *alpha,
                                   const cuComplex *const A[],
                                   int lda,
                                   cuComplex *const B[],
                                   int ldb,
                                   int batchCount);
cublasStatus_t cublasZtrsmBatched( cublasHandle_t    handle,
                                   cublasSideMode_t  side,
                                   cublasFillMode_t  uplo,
                                   cublasOperation_t trans,
                                   cublasDiagType_t  diag,
                                   int m,
                                   int n,
                                   const cuDoubleComplex *alpha,
                                   const cuDoubleComplex *const A[],
                                   int lda,
                                   cuDoubleComplex *const B[],
                                   int ldb,
                                   int batchCount);


```


This function supports the 64-bit Integer Interface.


This function solves an array of triangular linear systems with multiple right-hand-sides


$\left\{ \begin{matrix}
{\text{op}(A\lbrack i\rbrack)X\lbrack i\rbrack = \alpha B\lbrack i\rbrack} & {\text{if }\textsf{side == CUBLAS\_SIDE\_LEFT}} \\
{X\lbrack i\rbrack\text{op}(A\lbrack i\rbrack) = \alpha B\lbrack i\rbrack} & {\text{if }\textsf{side == CUBLAS\_SIDE\_RIGHT}} \\
\end{matrix} \right.$


where $A\lbrack i\rbrack$ is a triangular matrix stored in lower or upper mode with or without the main diagonal, $X\lbrack i\rbrack$ and $B\lbrack i\rbrack$ are $m \times n$ matrices, and $\alpha$ is a scalar. Also, for matrix $A$


$\text{op}(A\lbrack i\rbrack) = \left\{ \begin{matrix}
{A\lbrack i\rbrack} & {\text{if }\textsf{transa == CUBLAS\_OP\_N}} \\
{A^{T}\lbrack i\rbrack} & {\text{if }\textsf{transa == CUBLAS\_OP\_T}} \\
{A^{H}\lbrack i\rbrack} & {\text{if }\textsf{transa == CUBLAS\_OP\_C}} \\
\end{matrix} \right.$


The solution $X\lbrack i\rbrack$ overwrites the right-hand-sides $B\lbrack i\rbrack$ on exit.


No test for singularity or near-singularity is included in this function.


This function works for any sizes but is intended to be used for matrices of small sizes where the launch overhead is a significant factor. For bigger sizes, it might be advantageous to call `batchCount` times the regular cublas<t>trsm() within a set of CUDA streams.


The current implementation is limited to devices with compute capability above or equal 2.0.


| Param. | Memory | In/out | Meaning |
| --- | --- | --- | --- |
| handle |  | input | Handle to the cuBLAS library context. |
| side |  | input | Indicates if matrix A[i] is on the left or right of X[i]. |
| uplo |  | input | Indicates if matrix A[i] lower or upper part is stored, the other part is not referenced and is inferred from the stored elements. |
| trans |  | input | Operation op(A[i]) that is non- or (conj.) transpose. |
| diag |  | input | Indicates if the elements on the main diagonal of matrix A[i] are unity and should not be accessed. |
| m |  | input | Number of rows of matrix B[i], with matrix A[i] sized accordingly. |
| n |  | input | Number of columns of matrix B[i], with matrix A[i] is sized accordingly. |
| alpha | host or device | input | <type> scalar used for multiplication, if alpha == 0 then A[i] is not referenced and B[i] does not have to be a valid input. |
| A | device | input | Array of pointers to <type> array, with each array of dim. lda x m with lda >= max(1, m) if side == CUBLAS_SIDE_LEFT and lda x n with lda >= max(1, n) otherwise. |
| lda |  | input | Leading dimension of two-dimensional array used to store matrix A[i]. |
| B | device | in/out | Array of pointers to <type> array, with each array of dim. ldb x n with ldb >= max(1, m). Matrices B[i] should not overlap; otherwise, undefined behavior is expected. |
| ldb |  | input | Leading dimension of two-dimensional array used to store matrix B[i]. |
| batchCount |  | input | Number of pointers contained in A and B. |


The possible error values returned by this function and their meanings are listed below.


| Error Value | Meaning |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | The operation completed successfully |
| CUBLAS_STATUS_NOT_INITIALIZED | The library was not initialized |
| CUBLAS_STATUS_INVALID_VALUE | If m < 0, n < 0, or
if trans is not one of CUBLAS_OP_N, CUBLAS_OP_T and CUBLAS_OP_C, or
if uplo is not one of CUBLAS_FILL_MODE_LOWER and CUBLAS_FILL_MODE_UPPER, or
if side is not one of CUBLAS_SIDE_LEFT and CUBLAS_SIDE_RIGHT, or
if diag is not one of CUBLAS_DIAG_UNIT and CUBLAS_DIAG_NON_UNIT, or
if lda < max(1, m) if side == CUBLAS_SIDE_LEFT, and lda < max(1, n) otherwise, or
if ldb < max(1, m) |
| CUBLAS_STATUS_EXECUTION_FAILED | The function failed to launch on the GPU |


For references please refer to NETLIB documentation:


[strsm()](http://www.netlib.org/blas/strsm.f), [dtrsm()](http://www.netlib.org/blas/dtrsm.f), [ctrsm()](http://www.netlib.org/blas/ctrsm.f), [ztrsm()](http://www.netlib.org/blas/ztrsm.f)


