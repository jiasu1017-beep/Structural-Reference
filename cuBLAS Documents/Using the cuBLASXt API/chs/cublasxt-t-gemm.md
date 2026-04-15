### 4.4.1. cublasXt<t>gemm()

```c++
// 单精度实数矩阵乘法
cublasStatus_t cublasXtSgemm(cublasXtHandle_t handle,
                           cublasOperation_t transa, cublasOperation_t transb,
                           size_t m, size_t n, size_t k,
                           const float           *alpha,
                           const float           *A, int lda,
                           const float           *B, int ldb,
                           const float           *beta,
                           float           *C, int ldc)
// 双精度实数矩阵乘法
cublasStatus_t cublasXtDgemm(cublasXtHandle_t handle,
                           cublasOperation_t transa, cublasOperation_t transb,
                           int m, int n, int k,
                           const double          *alpha,
                           const double          *A, int lda,
                           const double          *B, int ldb,
                           const double          *beta,
                           double          *C, int ldc)
// 单精度复数矩阵乘法
cublasStatus_t cublasXtCgemm(cublasXtHandle_t handle,
                           cublasOperation_t transa, cublasOperation_t transb,
                           int m, int n, int k,
                           const cuComplex       *alpha,
                           const cuComplex       *A, int lda,
                           const cuComplex       *B, int ldb,
                           const cuComplex       *beta,
                           cuComplex       *C, int ldc)
// 双精度复数矩阵乘法
cublasStatus_t cublasXtZgemm(cublasXtHandle_t handle,
                           cublasOperation_t transa, cublasOperation_t transb,
                           int m, int n, int k,
                           const cuDoubleComplex *alpha,
                           const cuDoubleComplex *A, int lda,
                           const cuDoubleComplex *B, int ldb,
                           const cuDoubleComplex *beta,
                           cuDoubleComplex *C, int ldc)
```

此函数执行矩阵-矩阵乘法

$C = \alpha\text{op}(A)\text{op}(B) + \beta C$

其中 $\alpha$ 和 $\beta$ 为标量，$A$、$B$ 和 $C$ 为以列优先格式存储的矩阵，维度分别为 $\text{op}(A)$ $m \times k$、$\text{op}(B)$ $k \times n$ 和 $C$ $m \times n$。此外，对于矩阵 $A$

$\text{op}(A) = \left\{ \begin{matrix}
A & {\text{if }\textsf{transa == $\mathrm{CUBLAS\_OP\_N}$}} \\
A^{T} & {\text{if }\textsf{transa == $\mathrm{CUBLAS\_OP\_T}$}} \\
A^{H} & {\text{if }\textsf{transa == $\mathrm{CUBLAS\_OP\_C}$}} \\
\end{matrix} \right.$

对于矩阵 $B$，$\text{op}(B)$ 的定义类似。

| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | 输入 | cuBLASXt API 上下文的句柄。 |
| transa |  | 输入 | 运算 op(A)，即非转置或（共轭）转置。 |
| transb |  | 输入 | 运算 op(B)，即非转置或（共轭）转置。 |
| m |  | 输入 | 矩阵 op(A) 和 C 的行数。 |
| n |  | 输入 | 矩阵 op(B) 和 C 的列数。 |
| k |  | 输入 | op(A) 的列数和 op(B) 的行数。 |
| alpha | 主机端 | 输入 | 用于乘法的 <type> 标量。 |
| A | 主机端或设备端 | 输入 | 维度为 lda x k 的 <type> 数组，当 transa == CUBLAS_OP_N 时 lda >= max(1, m)，否则为 lda x m 且 lda >= max(1, k)。 |
| lda |  | 输入 | 用于存储矩阵 A 的二维数组的主维度。 |
| B | 主机端或设备端 | 输入 | 维度为 ldb x n 的 <type> 数组，当 transb == CUBLAS_OP_N 时 ldb >= max(1, k)，否则为 ldb x k 且 ldb >= max(1, n)。 |
| ldb |  | 输入 | 用于存储矩阵 B 的二维数组的主维度。 |
| beta | 主机端 | 输入 | 用于乘法的 <type> 标量。如果 beta == 0，则 C 不必是有效输入。 |
| C | 主机端或设备端 | 输入/输出 | 维度为 ldc x n 的 <type> 数组，ldc >= max(1, m)。 |
| ldc |  | 输入 | 用于存储矩阵 C 的二维数组的主维度。 |

此函数返回的可能错误值及其含义如下所列。

| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | 参数 m,n,k<0 |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数在 GPU 上启动失败 |

相关参考请参阅 NETLIB 文档：

[sgemm()](http://www.netlib.org/blas/sgemm.f)、[dgemm()](http://www.netlib.org/blas/dgemm.f)、[cgemm()](http://www.netlib.org/blas/cgemm.f)、[zgemm()](http://www.netlib.org/blas/zgemm.f)