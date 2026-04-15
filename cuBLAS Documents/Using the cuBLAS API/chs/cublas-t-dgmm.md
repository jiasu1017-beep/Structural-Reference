### 2.8.2. cublas<t>dgmm()

```c++

cublasStatus_t cublasSdgmm(cublasHandle_t handle, cublasSideMode_t mode,
                          int m, int n,
                          const float           *A, int lda,
                          const float           *x, int incx,
                          float           *C, int ldc)
cublasStatus_t cublasDdgmm(cublasHandle_t handle, cublasSideMode_t mode,
                          int m, int n,
                          const double          *A, int lda,
                          const double          *x, int incx,
                          double          *C, int ldc)
cublasStatus_t cublasCdgmm(cublasHandle_t handle, cublasSideMode_t mode,
                          int m, int n,
                          const cuComplex       *A, int lda,
                          const cuComplex       *x, int incx,
                          cuComplex       *C, int ldc)
cublasStatus_t cublasZdgmm(cublasHandle_t handle, cublasSideMode_t mode,
                          int m, int n,
                          const cuDoubleComplex *A, int lda,
                          const cuDoubleComplex *x, int incx,
                          cuDoubleComplex *C, int ldc)


```


此函数支持64位整数接口。


此函数执行矩阵-矩阵乘法


$C = \left\{ \begin{matrix}
{A \times diag(X)} & {\text{if }\textsf{mode == CUBLAS\_SIDE\_RIGHT}} \\
{diag(X) \times A} & {\text{if }\textsf{mode == CUBLAS\_SIDE\_LEFT}} \\
\end{matrix} \right.$


其中 $A$ 和 $C$ 是以列优先格式存储的矩阵，维度为 $m \times n$。当 `mode == CUBLAS_SIDE_RIGHT` 时，$X$ 是大小为 $n$ 的向量；当 `mode == CUBLAS_SIDE_LEFT` 时，$X$ 是大小为 $m$ 的向量。$X$ 从一维数组 x 中以步长 `incx` 进行聚集。`incx` 的绝对值是步长，`incx` 的符号是步长的方向。如果 `incx` 为正，则从第一个元素开始正向遍历 x。否则，从最后一个元素开始反向遍历 x。$X$ 的公式为


$X\lbrack j\rbrack = \left\{ \begin{matrix}
{x\lbrack j \times incx\rbrack} & {\text{if }incx \geq 0} \\
{x\lbrack(\chi - 1) \times |incx| - j \times |incx|\rbrack} & {\text{if }incx < 0} \\
\end{matrix} \right.$


其中，当 `mode == CUBLAS_SIDE_LEFT` 时 $\chi = m$，当 `mode == CUBLAS_SIDE_RIGHT` 时 $\chi = n$。


示例 1：如果用户想要执行 $diag(diag(B)) \times A$，则 $incx = ldb + 1$，其中 ldb 是矩阵 `B` 的主维度，无论是行优先还是列优先格式。


示例 2：如果用户想要执行 $\alpha \times A$，有两种选择：要么使用 `*beta == 0` 和 `transa == CUBLAS_OP_N` 的 cublas<t>geam()，要么使用 `incx == 0` 和 `x[0] == alpha` 的 cublas<t>dgmm()。


该操作是原地（out-of-place）操作。仅当 `lda == ldc` 时原地（in-place）操作才有效。


| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | input | cuBLAS 库上下文的句柄。 |
| mode |  | input | 如果 mode == CUBLAS_SIDE_LEFT 则左乘，如果 mode == CUBLAS_SIDE_RIGHT 则右乘 |
| m |  | input | 矩阵 A 和 C 的行数。 |
| n |  | input | 矩阵 A 和 C 的列数。 |
| A | device | input | 维度为 lda x n 的 <type> 数组，其中 lda >= max(1, m) |
| lda |  | input | 用于存储矩阵 A 的二维数组的主维度。 |
| x | device | input | 一维 <type> 数组，当 mode == CUBLAS_SIDE_LEFT 时大小为 abs(incx) x m，当 mode == CUBLAS_SIDE_RIGHT 时大小为 abs(incx) x n |
| incx |  | input | 一维数组 x 的步长。 |
| C | device | in/out | 维度为 ldc x n 的 <type> 数组，其中 ldc >= max(1, m)。 |
| ldc |  | input | 用于存储矩阵 C 的二维数组的主维度。 |


此函数返回的可能错误值及其含义如下所列。


| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | 如果 m < 0 或 n < 0，或<br>如果 mode 不是 CUBLAS_SIDE_LEFT 和 CUBLAS_SIDE_RIGHT 之一，或<br>如果 lda < max(1, m)，或<br>如果 ldc < max(1, m) |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数在 GPU 上启动失败 |