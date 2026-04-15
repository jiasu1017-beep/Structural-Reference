### 4.4.3. cublasXt<t>symm()

```c++

cublasStatus_t cublasXtSsymm(cublasXtHandle_t handle,
                           cublasSideMode_t side, cublasFillMode_t uplo,
                           size_t m, size_t n,
                           const float           *alpha,
                           const float           *A, size_t lda,
                           const float           *B, size_t ldb,
                           const float           *beta,
                           float           *C, size_t ldc)
cublasStatus_t cublasXtDsymm(cublasXtHandle_t handle,
                           cublasSideMode_t side, cublasFillMode_t uplo,
                           size_t m, size_t n,
                           const double          *alpha,
                           const double          *A, size_t lda,
                           const double          *B, size_t ldb,
                           const double          *beta,
                           double          *C, size_t ldc)
cublasStatus_t cublasXtCsymm(cublasXtHandle_t handle,
                           cublasSideMode_t side, cublasFillMode_t uplo,
                           size_t m, size_t n,
                           const cuComplex       *alpha,
                           const cuComplex       *A, size_t lda,
                           const cuComplex       *B, size_t ldb,
                           const cuComplex       *beta,
                           cuComplex       *C, size_t ldc)
cublasStatus_t cublasXtZsymm(cublasXtHandle_t handle,
                           cublasSideMode_t side, cublasFillMode_t uplo,
                           size_t m, size_t n,
                           const cuDoubleComplex *alpha,
                           const cuDoubleComplex *A, size_t lda,
                           const cuDoubleComplex *B, size_t ldb,
                           const cuDoubleComplex *beta,
                           cuDoubleComplex *C, size_t ldc)


```


此函数执行对称矩阵-矩阵乘法


$C = \left\{ \begin{matrix}
{\alpha AB + \beta C} & {\text{if }\textsf{side == $\mathrm{CUBLAS\_SIDE\_LEFT}$}} \\
{\alpha BA + \beta C} & {\text{if }\textsf{side == $\mathrm{CUBLAS\_SIDE\_RIGHT}$}} \\
\end{matrix} \right.$


其中 A 是以下三角或上三角模式存储的对称矩阵，A 和 B 是 $m \times n$ 矩阵，α 和 β 是标量。


| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | 输入 | cuBLASXt API 上下文的句柄。 |
| side |  | 输入 | 指示矩阵 A 位于 B 的左侧还是右侧。 |
| uplo |  | 输入 | 指示存储矩阵 A 的下三角还是上三角部分，另一对称部分未被引用，而是从存储的元素推断。 |
| m |  | 输入 | 矩阵 A 和 B 的行数，矩阵 A 相应调整尺寸。 |
| n |  | 输入 | 矩阵 C 和 A 的列数，矩阵 A 相应调整尺寸。 |
| alpha | host | 输入 | 用于乘法的 <type> 标量。 |
| A | host 或 device | 输入 | lda × m 维的 <type> 数组，当 side == CUBLAS_SIDE_LEFT 时 lda >= max(1, m)，否则为 lda × n 维且 lda >= max(1, n)。 |
| lda |  | 输入 | 用于存储矩阵 A 的二维数组的 leading dimension。 |
| B | host 或 device | 输入 | ldb × n 维的 <type> 数组，ldb >= max(1, m)。 |
| ldb |  | 输入 | 用于存储矩阵 B 的二维数组的 leading dimension。 |
| beta | host | 输入 | 用于乘法的 <type> 标量，如果 beta == 0，则 C 不必是有效输入。 |
| C | host 或 device | 输入/输出 | ldc × n 维的 <type> 数组，ldc >= max(1, m)。 |
| ldc |  | 输入 | 用于存储矩阵 C 的二维数组的 leading dimension。 |


此函数返回的可能错误值及其含义如下所列。


| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | 参数 m < 0 或 n < 0 |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数无法在 GPU 上启动 |


相关参考请参阅 NETLIB 文档：


[ssymm()](http://www.netlib.org/blas/ssymm.f), [dsymm()](http://www.netlib.org/blas/dsymm.f), [csymm()](http://www.netlib.org/blas/csymm.f), [zsymm()](http://www.netlib.org/blas/zsymm.f)