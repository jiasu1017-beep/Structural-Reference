### 2.7.7. cublas<t>syrk()

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