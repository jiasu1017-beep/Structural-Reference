### 4.4.10. cublasXt<t>trsm()



```c++

cublasStatus_t cublasXtStrsm(cublasXtHandle_t handle,
                           cublasSideMode_t side, cublasFillMode_t uplo,
                           cublasOperation_t trans, cublasXtDiagType_t diag,
                           size_t m, size_t n,
                           const float           *alpha,
                           const float           *A, size_t lda,
                           float           *B, size_t ldb)
// 此函数求解带有多个右侧向量的三角线性系统组
cublasStatus_t cublasXtDtrsm(cublasXtHandle_t handle,
                           cublasSideMode_t side, cublasFillMode_t uplo,
                           cublasOperation_t trans, cublasXtDiagType_t diag,
                           size_t m, size_t n,
                           const double          *alpha,
                           const double          *A, size_t lda,
                           double          *B, size_t ldb)
// 此函数求解带有多个右侧向量的三角线性系统组
cublasStatus_t cublasXtCtrsm(cublasXtHandle_t handle,
                           cublasSideMode_t side, cublasFillMode_t uplo,
                           cublasOperation_t trans, cublasXtDiagType_t diag,
                           size_t m, size_t n,
                           const cuComplex       *alpha,
                           const cuComplex       *A, size_t lda,
                           cuComplex       *B, size_t ldb)
// 此函数求解带有多个右侧向量的三角线性系统组
cublasStatus_t cublasXtZtrsm(cublasXtHandle_t handle,
                           cublasSideMode_t side, cublasFillMode_t uplo,
                           cublasOperation_t trans, cublasXtDiagType_t diag,
                           size_t m, size_t n,
                           const cuDoubleComplex *alpha,
                           const cuDoubleComplex *A, size_t lda,
                           cuDoubleComplex *B, size_t ldb)
// 此函数求解带有多个右侧向量的三角线性系统组


```


此函数求解带有多个右侧向量的三角线性系统组


$\left\{ \begin{matrix}
{\text{op}(A)X = \alpha B} & {\text{if }\textsf{side == $\mathrm{CUBLAS\_SIDE\_LEFT}$}} \\
{X\text{op}(A) = \alpha B} & {\text{if }\textsf{side == $\mathrm{CUBLAS\_SIDE\_RIGHT}$}} \\
\end{matrix} \right.$


其中 $A$ 是一个以低位模式或高位模式存储的三角矩阵（是否包含主对角线均可），$X$ 和 $B$ 是 $m \times n$ 矩阵，$\alpha$ 是标量。此外，对于矩阵 $A$


$\text{op}(A) = \left\{ \begin{matrix}
A & {\text{if }\textsf{transa == $\mathrm{CUBLAS\_OP\_N}$}} \\
A^{T} & {\text{if }\textsf{transa == $\mathrm{CUBLAS\_OP\_T}$}} \\
A^{H} & {\text{if }\textsf{transa == $\mathrm{CUBLAS\_OP\_C}$}} \\
\end{matrix} \right.$


求解结果 $X$ 在退出时覆盖右侧向量 $B$。


此函数不包含奇异性或近似奇异性的检测。


| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | input | cuBLASXt API上下文的句柄。 |
| side |  | input | 指明矩阵A位于X的左侧还是右侧。 |
| uplo |  | input | 指明矩阵A的下三角或上三角部分是否被存储，另一部分不引用并从存储的元素推断。 |
| trans |  | input | 操作 op(A)，即非转置或（共轭）转置。 |
| diag |  | input | 指明矩阵A主对角线上的元素是否为单位元素且不应被访问。 |
| m |  | input | 矩阵B的行数，矩阵A的尺寸相应调整。 |
| n |  | input | 矩阵B的列数，矩阵A的尺寸相应调整。 |
| alpha | host | input | 用于乘法的 <type> 标量，如果 alpha == 0，则不引用 A，且 B 不必是有效输入。 |
| A | host or device | input | <type> 数组，维度为 lda x m（当 side == CUBLAS_SIDE_LEFT 时 lda >= max(1, m)），否则为 lda x n 且 lda >= max(1, n)。 |
| lda |  | input | 用于存储矩阵A的二维数组的主维。 |
| B | host or device | in/out | <type> 数组，维度为 ldb x n，ldb >= max(1, m)。 |
| ldb |  | input | 用于存储矩阵B的二维数组的主维。 |


此函数返回的可能错误值及其含义如下所列。


| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | 参数 m < 0 或 n < 0 |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数在GPU上启动失败 |


参考文献请参阅 NETLIB 文档：


[strsm()](http://www.netlib.org/blas/strsm.f), [dtrsm()](http://www.netlib.org/blas/dtrsm.f), [ctrsm()](http://www.netlib.org/blas/ctrsm.f), [ztrsm()](http://www.netlib.org/blas/ztrsm.f)