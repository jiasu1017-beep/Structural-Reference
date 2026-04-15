### 2.8.1. cublas<t>geam()



```c++

cublasStatus_t cublasSgeam(cublasHandle_t handle,
                          cublasOperation_t transa, cublasOperation_t transb,
                          int m, int n,
                          const float           *alpha,
                          const float           *A, int lda,
                          const float           *beta,
                          const float           *B, int ldb,
                          float           *C, int ldc)
cublasStatus_t cublasDgeam(cublasHandle_t handle,
                          cublasOperation_t transa, cublasOperation_t transb,
                          int m, int n,
                          const double          *alpha,
                          const double          *A, int lda,
                          const double          *beta,
                          const double          *B, int ldb,
                          double          *C, int ldc)
cublasStatus_t cublasCgeam(cublasHandle_t handle,
                          cublasOperation_t transa, cublasOperation_t transb,
                          int m, int n,
                          const cuComplex       *alpha,
                          const cuComplex       *A, int lda,
                          const cuComplex       *beta ,
                          const cuComplex       *B, int ldb,
                          cuComplex       *C, int ldc)
cublasStatus_t cublasZgeam(cublasHandle_t handle,
                          cublasOperation_t transa, cublasOperation_t transb,
                          int m, int n,
                          const cuDoubleComplex *alpha,
                          const cuDoubleComplex *A, int lda,
                          const cuDoubleComplex *beta,
                          const cuDoubleComplex *B, int ldb,
                          cuDoubleComplex *C, int ldc)


```


此函数支持64位整数接口。

此函数执行矩阵-矩阵加法/转置操作：

$C = \alpha\text{op}(A) + \beta\text{op}(B)$

其中 $\alpha$ 和 $\beta$ 是标量，$A$、$B$ 和 $C$ 是以列主序格式存储的矩阵，维度分别为 $\text{op}(A)$ $m \times n$、$\text{op}(B)$ $m \times n$ 和 $C$ $m \times n$。同样，对于矩阵 $A$：

$\text{op}(A) = \left\{ \begin{matrix}
A & {\text{if }\textsf{transa == CUBLAS\_OP\_N}} \\
A^{T} & {\text{if }\textsf{transa == CUBLAS\_OP\_T}} \\
A^{H} & {\text{if }\textsf{transa == CUBLAS\_OP\_C}} \\
\end{matrix} \right.$

$\text{op}(B)$ 对于矩阵 $B$ 的定义与此类似。


如果 C 与 A 或 B 不重叠，则该操作是原地外操作。

原地模式支持以下两种操作：

$C = \alpha\text{*}C + \beta\text{op}(B)$

$C = \alpha\text{op}(A) + \beta\text{*}C$

对于原地模式，如果 `C == A`，则 `ldc == lda` 且 `transa == CUBLAS_OP_N`。如果 `C === B`，则 `ldc == ldb` 且 `transb == CUBLAS_OP_N`。如果用户不满足上述要求，将返回 `CUBLAS_STATUS_INVALID_VALUE`。

该操作包含以下特殊情况：

用户可以通过设置 `*alpha = beta = 0` 将矩阵 C 重置为零。

用户可以通过设置 `*alpha = 1 and *beta = 0` 对矩阵 A 进行转置。


| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | input | cuBLAS 库上下文的句柄。 |
| transa |  | input | 操作 op(A)，即非转置或（共轭）转置。 |
| transb |  | input | 操作 op(B)，即非转置或（共轭）转置。 |
| m |  | input | 矩阵 op(A) 和 C 的行数。 |
| n |  | input | 矩阵 op(B) 和 C 的列数。 |
| alpha | host or device | input | 用于乘法的 <type> 标量。如果 *alpha == 0，则 A 不必是有效输入。 |
| A | device | input | 维度为 lda x n 的 <type> 数组，当 transa == CUBLAS_OP_N 时 lda >= max(1, m)，否则为 lda x m 且 lda >= max(1, n)。 |
| lda |  | input | 用于存储矩阵 A 的二维数组的主维度。 |
| B | device | input | 维度为 ldb x n 的 <type> 数组，当 transb == CUBLAS_OP_N 时 ldb >= max(1, m)，否则为 ldb x m 且 ldb >= max(1,n)。 |
| ldb |  | input | 用于存储矩阵 B 的二维数组的主维度。 |
| beta | host or device | input | 用于乘法的 <type> 标量。如果 *beta == 0，则 B 不必是有效输入。 |
| C | device | output | 维度为 ldc x n 的 <type> 数组，ldc >= max(1, m)。 |
| ldc |  | input | 用于存储矩阵 C 的二维数组的主维度。 |


此函数返回的可能错误值及其含义如下所示。


| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | 如果 m < 0 或 n < 0，或<br>如果 transa 不是 CUBLAS_OP_N、CUBLAS_OP_T 和 CUBLAS_OP_C 之一，或<br>如果 transb 不是 CUBLAS_OP_N、CUBLAS_OP_T 和 CUBLAS_OP_C 之一，或<br>如果 transa == CUBLAS_OP_N 时 lda < max(1, m)，否则 lda < max(1, n)，或<br>如果 transb == CUBLAS_OP_N 时 ldb < max(1, m)，否则 ldb < max(1, n)，或<br>如果 ldc < max(1, m)，或<br>如果 A == C 且 (transa != CUBLAS_OP_N) || (lda != ldc)，或<br>如果 B == C 且 (transb != CUBLAS_OP_N) || (ldb != ldc)，或<br>如果 alpha 或 beta 为 NULL |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数在 GPU 上启动失败 |