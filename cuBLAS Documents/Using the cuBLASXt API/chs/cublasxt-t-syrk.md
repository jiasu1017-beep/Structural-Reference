### 4.4.4. cublasXt<t>syrk()



```c++

cublasStatus_t cublasXtSsyrk(cublasXtHandle_t handle,
                           cublasFillMode_t uplo, cublasOperation_t trans,
                           int n, int k,
                           const float           *alpha,
                           const float           *A, int lda,
                           const float           *beta,
                           float           *C, int ldc)
cublasStatus_t cublasXtDsyrk(cublasXtHandle_t handle,
                           cublasFillMode_t uplo, cublasOperation_t trans,
                           int n, int k,
                           const double          *alpha,
                           const double          *A, int lda,
                           const double          *beta,
                           double          *C, int ldc)
cublasStatus_t cublasXtCsyrk(cublasXtHandle_t handle,
                           cublasFillMode_t uplo, cublasOperation_t trans,
                           int n, int k,
                           const cuComplex       *alpha,
                           const cuComplex       *A, int lda,
                           const cuComplex       *beta,
                           cuComplex       *C, int ldc)
cublasStatus_t cublasXtZsyrk(cublasXtHandle_t handle,
                           cublasFillMode_t uplo, cublasOperation_t trans,
                           int n, int k,
                           const cuDoubleComplex *alpha,
                           const cuDoubleComplex *A, int lda,
                           const cuDoubleComplex *beta,
                           cuDoubleComplex *C, int ldc)


```


此函数执行对称 rank-$k$ 更新


$C = \alpha\text{op}(A)\text{op}(A)^{T} + \beta C$


其中 $\alpha$ 和 $\beta$ 为标量，$C$ 为以下三角模式存储的对称矩阵，$A$ 为维度 $\text{op}(A)$ $n \times k$ 的矩阵。同样，对于矩阵 $A$


$\text{op}(A) = \left\{ \begin{matrix}
A & {\text{if }\textsf{transa == CUBLAS\_OP\_N}} \\
A^{T} & {\text{if }\textsf{transa == CUBLAS\_OP\_T}} \\
\end{matrix} \right.$


| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | input | cuBLASXt API 上下文的句柄。 |
| uplo |  | input | 指示矩阵 C 的下三角或上三角部分是否存储，另一对称部分未被引用，且从存储的元素中推断。 |
| trans |  | input | 非转置或转置操作 op(A)。 |
| n |  | input | 矩阵 op(A) 和 C 的行数。 |
| k |  | input | 矩阵 op(A) 的列数。 |
| alpha | host | input | 用于乘法运算的 <type> 标量。 |
| A | host or device | input | 维度为 lda x k 的 <type> 数组，当 trans == CUBLAS_OP_N 时 lda >= max(1, n)，否则为 lda x n 且 lda >= max(1, k)。 |
| lda |  | input | 用于存储矩阵 A 的二维数组的主维度。 |
| beta | host | input | 用于乘法运算的 <type> 标量，若 beta == 0 则 C 不必为有效输入。 |
| C | host or device | in/out | 维度为 ldc x n 的 <type> 数组，ldc >= max(1, n)。 |
| ldc |  | input | 用于存储矩阵 C 的二维数组的主维度。 |


此函数可能返回的错误值及其含义如下所列。


| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | 参数 n < 0 或 k < 0 |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数无法在 GPU 上启动执行 |

有关参考信息，请参阅 NETLIB 文档：


[ssyrk()](http://www.netlib.org/blas/ssyrk.f), [dsyrk()](http://www.netlib.org/blas/dsyrk.f), [csyrk()](http://www.netlib.org/blas/csyrk.f), [zsyrk()](http://www.netlib.org/blas/zsyrk.f)