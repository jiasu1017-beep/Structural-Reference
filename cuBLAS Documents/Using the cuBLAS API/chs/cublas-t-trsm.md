### 2.7.11. cublas<t>trsm()

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