### 2.6.16. cublas<t>trsv()



```c++
// 64位整数接口支持
cublasStatus_t cublasStrsv(cublasHandle_t handle, cublasFillMode_t uplo,
                           cublasOperation_t trans, cublasDiagType_t diag,
                           int n, const float           *A, int lda,
                           float           *x, int incx)
cublasStatus_t cublasDtrsv(cublasHandle_t handle, cublasFillMode_t uplo,
                           cublasOperation_t trans, cublasDiagType_t diag,
                           int n, const double          *A, int lda,
                           double          *x, int incx)
cublasStatus_t cublasCtrsv(cublasHandle_t handle, cublasFillMode_t uplo,
                           cublasOperation_t trans, cublasDiagType_t diag,
                           int n, const cuComplex       *A, int lda,
                           cuComplex       *x, int incx)
cublasStatus_t cublasZtrsv(cublasHandle_t handle, cublasFillMode_t uplo,
                           cublasOperation_t trans, cublasDiagType_t diag,
                           int n, const cuDoubleComplex *A, int lda,
                           cuDoubleComplex *x, int incx)


```


此函数支持64位整数接口。


此函数求解带有单个右侧向量的三角线性系统


$\text{op}(A)\textbf{x} = \textbf{b}$


其中 $A$ 是以下三角矩阵：按下或上三角模式存储，可带或不带主对角线，$\mathbf{x}$ 和 $\mathbf{b}$ 为向量。此外，对于矩阵 $A$


$\text{op}(A) = \left\{ \begin{matrix}
A & {\text{if }\textsf{transa == CUBLAS\_OP\_N}} \\
A^{T} & {\text{if }\textsf{transa == CUBLAS\_OP\_T}} \\
A^{H} & {\text{if }\textsf{transa == CUBLAS\_OP\_C}} \\
\end{matrix} \right.$


解 $\mathbf{x}$ 在退出时覆盖右侧向量 $\mathbf{b}$。


此函数不包含奇异性或近奇异性测试。


| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | input | cuBLAS 库上下文的句柄。 |
| uplo |  | input | 指示矩阵 A 的下三角或上三角部分是否存储，另一部分未被引用且根据存储的元素推断。 |
| trans |  | input | 操作 op(A)，即非转置或（共轭）转置。 |
| diag |  | input | 指示矩阵 A 主对角线上的元素是否为单位一，且不应被访问。 |
| n |  | input | 矩阵 A 的行数和列数。 |
| A | device | input | 维度为 lda x n 的 <type> 数组，lda >= max(1, n)。 |
| lda |  | input | 用于存储矩阵 A 的二维数组的主维度。 |
| x | device | in/out | 具有 n 个元素的 <type> 向量。 |
| incx |  | input | x 中连续元素之间的步长。 |


此函数可能返回的错误值及其含义如下所列。


| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | 如果 n < 0，或
如果 incx == 0，或
如果 trans 不是 CUBLAS_OP_N、CUBLAS_OP_T 和 CUBLAS_OP_C 之一，或
如果 uplo 不是 CUBLAS_FILL_MODE_LOWER 和 CUBLAS_FILL_MODE_UPPER 之一，或
如果 diag 不是 CUBLAS_DIAG_UNIT 和 CUBLAS_DIAG_NON_UNIT 之一，或
如果 lda < max(1, n) |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数无法在 GPU 上启动 |


相关参考文献请参阅 NETLIB 文档：


[strsv()](http://www.netlib.org/blas/strsv.f), [dtrsv()](http://www.netlib.org/blas/dtrsv.f), [ctrsv()](http://www.netlib.org/blas/ctrsv.f), [ztrsv()](http://www.netlib.org/blas/ztrsv.f)