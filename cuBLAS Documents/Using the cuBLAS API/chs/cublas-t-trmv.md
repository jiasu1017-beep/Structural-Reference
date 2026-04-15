### 2.6.15. cublas<t>trmv()

```c++
cublasStatus_t cublasStrmv(cublasHandle_t handle, cublasFillMode_t uplo,
                           cublasOperation_t trans, cublasDiagType_t diag,
                           int n, const float           *A, int lda,
                           float           *x, int incx)
cublasStatus_t cublasDtrmv(cublasHandle_t handle, cublasFillMode_t uplo,
                           cublasOperation_t trans, cublasDiagType_t diag,
                           int n, const double          *A, int lda,
                           double          *x, int incx)
cublasStatus_t cublasCtrmv(cublasHandle_t handle, cublasFillMode_t uplo,
                           cublasOperation_t trans, cublasDiagType_t diag,
                           int n, const cuComplex       *A, int lda,
                           cuComplex       *x, int incx)
cublasStatus_t cublasZtrmv(cublasHandle_t handle, cublasFillMode_t uplo,
                           cublasOperation_t trans, cublasDiagType_t diag,
                           int n, const cuDoubleComplex *A, int lda,
                           cuDoubleComplex *x, int incx)
```

此函数支持64位整数接口。

此函数执行三角矩阵与向量的乘法运算

$\textbf{x} = \text{op}(A)\textbf{x}$

其中 $A$ 是以_lower_或_upper_模式存储的三角矩阵，可包含或不包含主对角线，$\mathbf{x}$ 是向量。此外，对于矩阵 $A$

$\text{op}(A) = \left\{ \begin{matrix}
A & {\text{if }\textsf{trans == $\mathrm{CUBLAS\_OP\_N}$}} \\
A^{T} & {\text{if }\textsf{trans == $\mathrm{CUBLAS\_OP\_T}$}} \\
A^{H} & {\text{if }\textsf{trans == $\mathrm{CUBLAS\_OP\_C}$}} \\
\end{matrix} \right.$

| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | 输入 | cuBLAS库上下文的句柄 |
| uplo |  | 输入 | 指示矩阵A的下三角或上三角部分是否被存储，另一部分未被引用，根据已存储的元素进行推断 |
| trans |  | 输入 | 运算op(A)，即非转置或（共轭）转置 |
| diag |  | 输入 | 指示矩阵A主对角线上的元素是否为单位1，以及是否应该被访问 |
| n |  | 输入 | 矩阵A的行数和列数 |
| A | 设备 | 输入 | 维度为lda x n的<type>数组，lda >= max(1, n) |
| lda |  | 输入 | 用于存储矩阵A的二维数组的主导维度 |
| x | 设备 | 输入/输出 | 包含n个元素的<type>向量 |
| incx |  | 输入 | x中连续元素之间的步长 |

此函数返回的可能错误值及其含义如下所列。

| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | 如果n < 0，或incx == 0，或trans不是CUBLAS_OP_N、CUBLAS_OP_T和CUBLAS_OP_C之一，或uplo不是CUBLAS_FILL_MODE_LOWER和CUBLAS_FILL_MODE_UPPER之一，或diag不是CUBLAS_DIAG_UNIT和CUBLAS_DIAG_NON_UNIT之一，或lda < max(1, n) |
| CUBLAS_STATUS_ALLOC_FAILED | 内部临时内存的分配失败 |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数无法在GPU上启动执行 |

参考文献请参阅NETLIB文档：

[strmv()](http://www.netlib.org/blas/strmv.f)、[dtrmv()](http://www.netlib.org/blas/dtrmv.f)、[ctrmv()](http://www.netlib.org/blas/ctrmv.f)、[ztrmv()](http://www.netlib.org/blas/ztrmv.f)