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
A & {\text{if }\textsf{transa == $\mathrm{CUBLAS\_OP\_N}$}} \\
A^{T} & {\text{if }\textsf{transa == $\mathrm{CUBLAS\_OP\_T}$}} \\
A^{H} & {\text{if }\textsf{transa == $\mathrm{CUBLAS\_OP\_C}$}} \\
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
A & {\text{if }\textsf{transa == $\mathrm{CUBLAS\_OP\_N}$}} \\
A^{T} & {\text{if }\textsf{transa == $\mathrm{CUBLAS\_OP\_T}$}} \\
A^{H} & {\text{if }\textsf{transa == $\mathrm{CUBLAS\_OP\_C}$}} \\
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
A & {\text{if }\textsf{transa == $\mathrm{CUBLAS\_OP\_N}$}} \\
A^{T} & {\text{if }\textsf{transa == $\mathrm{CUBLAS\_OP\_T}$}} \\
A^{H} & {\text{if }\textsf{transa == $\mathrm{CUBLAS\_OP\_C}$}} \\
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