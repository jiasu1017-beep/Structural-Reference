### 4.4.6. cublasXt<t>syrkx()

```c++

cublasStatus_t cublasXtSsyrkx(cublasXtHandle_t handle,
                            cublasFillMode_t uplo, cublasOperation_t trans,
                            size_t n, size_t k,
                            const float           *alpha,
                            const float           *A, size_t lda,
                            const float           *B, size_t ldb,
                            const float           *beta,
                            float           *C, size_t ldc)
cublasStatus_t cublasXtDsyrkx(cublasXtHandle_t handle,
                            cublasFillMode_t uplo, cublasOperation_t trans,
                            size_t n, size_t k,
                            const double          *alpha,
                            const double          *A, size_t lda,
                            const double          *B, size_t ldb,
                            const double          *beta,
                            double          *C, size_t ldc)
cublasStatus_t cublasXtCsyrkx(cublasXtHandle_t handle,
                            cublasFillMode_t uplo, cublasOperation_t trans,
                            size_t n, size_t k,
                            const cuComplex       *alpha,
                            const cuComplex       *A, size_t lda,
                            const cuComplex       *B, size_t ldb,
                            const cuComplex       *beta,
                            cuComplex       *C, size_t ldc)
cublasStatus_t cublasXtZsyrkx(cublasXtHandle_t handle,
                            cublasFillMode_t uplo, cublasOperation_t trans,
                            size_t n, size_t k,
                            const cuDoubleComplex *alpha,
                            const cuDoubleComplex *A, size_t lda,
                            const cuDoubleComplex *B, size_t ldb,
                            const cuDoubleComplex *beta,
                            cuDoubleComplex *C, size_t ldc)


```


此函数执行对称秩-k更新的一种变体


$C = \alpha(\text{op}(A)\text{op}(B)^{T} + \beta C$


其中 $\alpha$ 和 $\beta$ 是标量，$C$ 是以下三角或上三角模式存储的对称矩阵，$A$ 和 $B$ 是维度分别为 $\text{op}(A)$ $n \times k$ 和 $\text{op}(B)$ $n \times k$ 的矩阵。此外，对于矩阵 $A$ 和 $B$


$\text{op(}A\text{) and op(}B\text{)} = \left\{ \begin{matrix}
{A\text{ and }B} & {\text{if }\textsf{trans == $\mathrm{CUBLAS\_OP\_N}$}} \\
{A^{T}\text{ and }B^{T}} & {\text{if }\textsf{trans == $\mathrm{CUBLAS\_OP\_T}$}} \\
\end{matrix} \right.$


当矩阵 B 以保证结果对称的方式构造时，可以使用此例程。一个常见的例子是当矩阵 B 是矩阵 A 的缩放形式时：这等价于矩阵 B 是矩阵 A 与对角矩阵的乘积。


| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | 输入 | cuBLASXt API 上下文的句柄。 |
| uplo |  | 输入 | 指示存储矩阵 C 的下半部分还是上半部分，另一种对称部分未被引用，而是从存储的元素推断。 |
| trans |  | 输入 | 操作 op(A)，即非转置或转置。 |
| n |  | 输入 | 矩阵 op(A)、op(B) 和 C 的行数。 |
| k |  | 输入 | 矩阵 op(A) 和 op(B) 的列数。 |
| alpha | 主机 | 输入 | 用于乘法的 <type> 标量。 |
| A | 主机或设备 | 输入 | 维度为 lda x k 的 <type> 数组，当 transa == CUBLAS_OP_N 时 lda >= max(1, n)，否则为 lda x n 且 lda >= max(1, k)。 |
| lda |  | 输入 | 用于存储矩阵 A 的二维数组的leading dimension。 |
| B | 主机或设备 | 输入 | 维度为 ldb x k 的 <type> 数组，当 transb == CUBLAS_OP_N 时 ldb >= max(1, n)，否则为 ldb x n 且 ldb >= max(1, k)。 |
| ldb |  | 输入 | 用于存储矩阵 B 的二维数组的leading dimension。 |
| beta | 主机 | 输入 | 用于乘法的 <type> 标量，如果 beta == 0，则 C 不必是有效输入。 |
| C | 主机或设备 | 输入/输出 | 维度为 ldc x n 的 <type> 数组，ldc >= max(1, n)。 |
| ldc |  | 输入 | 用于存储矩阵 C 的二维数组的leading dimension。 |


此函数返回的可能错误值及其含义如下所列。


| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | 参数 n < 0 或 k < 0 |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数在 GPU 上启动失败 |


有关参考资料，请参阅 NETLIB 文档：


[ssyrk()](http://www.netlib.org/blas/ssyrk.f), [dsyrk()](http://www.netlib.org/blas/dsyrk.f), [csyrk()](http://www.netlib.org/blas/csyrk.f), [zsyrk()](http://www.netlib.org/blas/zsyrk.f) 和


[ssyr2k()](http://www.netlib.org/blas/ssyr2k.f), [dsyr2k()](http://www.netlib.org/blas/dsyr2k.f), [csyr2k()](http://www.netlib.org/blas/csyr2k.f), [zsyr2k()](http://www.netlib.org/blas/zsyr2k.f)