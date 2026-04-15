### 2.8.4. cublas<t>getrsBatched()

```c++

cublasStatus_t cublasSgetrsBatched(cublasHandle_t handle,
                                   cublasOperation_t trans,
                                   int n,
                                   int nrhs,
                                   const float *const Aarray[],
                                   int lda,
                                   const int *devIpiv,
                                   float *const Barray[],
                                   int ldb,
                                   int *info,
                                   int batchSize);

cublasStatus_t cublasDgetrsBatched(cublasHandle_t handle,
                                   cublasOperation_t trans,
                                   int n,
                                   int nrhs,
                                   const double *const Aarray[],
                                   int lda,
                                   const int *devIpiv,
                                   double *const Barray[],
                                   int ldb,
                                   int *info,
                                   int batchSize);

cublasStatus_t cublasCgetrsBatched(cublasHandle_t handle,
                                   cublasOperation_t trans,
                                   int n,
                                   int nrhs,
                                   const cuComplex *const Aarray[],
                                   int lda,
                                   const int *devIpiv,
                                   cuComplex *const Barray[],
                                   int ldb,
                                   int *info,
                                   int batchSize);

cublasStatus_t cublasZgetrsBatched(cublasHandle_t handle,
                                   cublasOperation_t trans,
                                   int n,
                                   int nrhs,
                                   const cuDoubleComplex *const Aarray[],
                                   int lda,
                                   const int *devIpiv,
                                   cuDoubleComplex *const Barray[],
                                   int ldb,
                                   int *info,
                                   int batchSize);


```

此函数用于求解一系列线性方程组，形式如下：

$\text{op}(A\lbrack i \rbrack) X\lbrack i\rbrack = B\lbrack i\rbrack$

其中，$A\lbrack i\rbrack$ 是经过带部分主元的 LU 分解的矩阵，$X\lbrack i\rbrack$ 和 $B\lbrack i\rbrack$ 是 $n \times {nrhs}$ 矩阵。同样，对于矩阵 $A$：

$\text{op}(A\lbrack i\rbrack) = \left\{ \begin{matrix}
{A\lbrack i\rbrack} & {\text{if }\textsf{trans == $\mathrm{CUBLAS\_OP\_N}$}} \\
{A^{T}\lbrack i\rbrack} & {\text{if }\textsf{trans == $\mathrm{CUBLAS\_OP\_T}$}} \\
{A^{H}\lbrack i\rbrack} & {\text{if }\textsf{trans == $\mathrm{CUBLAS\_OP\_C}$}} \\
\end{matrix} \right.$

此函数适用于矩阵规模较小、启动开销占比较高的场景。

`cublas<t>getrsBatched()` 支持不带主元选择的 LU 分解（当 `devIpiv` 为 `NULL` 时）。

`cublas<t>getrsBatched()` 支持任意维度。

`cublas<t>getrsBatched()` 仅支持计算能力 2.0 及以上的设备。

| 参数 | 内存位置 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | 输入 | cuBLAS 库上下文的句柄。 |
| trans |  | 输入 | 运算 op(A)，可以是未转置或（共轭）转置。 |
| n |  | 输入 | Aarray[i] 的行数和列数。 |
| nrhs |  | 输入 | Barray[i] 的列数。 |
| Aarray | 设备端 | 输入 | 指向 <type> 类型数组的指针数组，每个数组维度为 n x n，且 lda >= max(1, n)。 |
| lda |  | 输入 | 用于存储每个矩阵 Aarray[i] 的二维数组的主导维度。 |
| devIpiv | 设备端 | 输入 | 大小为 n x batchSize 的数组，其中包含以线性方式存储的每个 Aarray[i] 分解的旋转序列。如果 devIpiv 为 NULL，则忽略所有 Aarray[i] 的旋转操作。 |
| Barray | 设备端 | 输入/输出 | 指向 <type> 类型数组的指针数组，每个数组维度为 n x nrhs，且 ldb >= max(1, n)。矩阵 Barray[i] 之间不应重叠，否则将导致未定义行为。 |
| ldb |  | 输入 | 用于存储每个解矩阵 Barray[i] 的二维数组的主导维度。 |
| info | 主机端 | 输出 | 如果 info == 0，表示执行成功。
如果 info = -j，表示第 j 个参数具有非法值。 |
| batchSize |  | 输入 | Aarray 中包含的指针数量。 |

此函数可能返回的错误值及其含义如下表所列。

| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | 如果 n < 0 或 nrhs < 0，或
如果 trans 不是 CUBLAS_OP_N、CUBLAS_OP_T 和 CUBLAS_OP_C 之一，或
如果 lda < max(1, n)，或
如果 ldb < max(1, n) |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数未能在 GPU 上启动执行 |

相关参考文献请参阅 NETLIB 文档：

[sgeqrs()](http://www.netlib.org/lapack/single/sgetrs.f)、[dgeqrs()](http://www.netlib.org/lapack/double/dgetrs.f)、[cgeqrs()](http://www.netlib.org/lapack/complex/cgetrs.f)、[zgeqrs()](http://www.netlib.org/lapack/complex16/zgetrs.f)