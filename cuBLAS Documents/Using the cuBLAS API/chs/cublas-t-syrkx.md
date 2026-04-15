### 2.7.9. cublas<t>syrkx()

```c++

cublasStatus_t cublasSsyrkx(cublasHandle_t handle,
                            cublasFillMode_t uplo, cublasOperation_t trans,
                            int n, int k,
                            const float           *alpha,
                            const float           *A, int lda,
                            const float           *B, int ldb,
                            const float           *beta,
                            float           *C, int ldc)
cublasStatus_t cublasDsyrkx(cublasHandle_t handle,
                            cublasFillMode_t uplo, cublasOperation_t trans,
                            int n, int k,
                            const double          *alpha,
                            const double          *A, int lda,
                            const double          *B, int ldb,
                            const double          *beta,
                            double          *C, int ldc)
cublasStatus_t cublasCsyrkx(cublasHandle_t handle,
                            cublasFillMode_t uplo, cublasOperation_t trans,
                            int n, int k,
                            const cuComplex       *alpha,
                            const cuComplex       *A, int lda,
                            const cuComplex       *B, int ldb,
                            const cuComplex       *beta,
                            cuComplex       *C, int ldc)
cublasStatus_t cublasZsyrkx(cublasHandle_t handle,
                            cublasFillMode_t uplo, cublasOperation_t trans,
                            int n, int k,
                            const cuDoubleComplex *alpha,
                            const cuDoubleComplex *A, int lda,
                            const cuDoubleComplex *B, int ldb,
                            const cuDoubleComplex *beta,
                            cuDoubleComplex *C, int ldc)


```

此函数支持64位整数接口。

此函数执行对称秩k更新的一种变体

$C = \alpha\text{op}(A)\text{op}(B)^{T} + \beta C$

其中 $\alpha$ 和 $\beta$ 是标量，$C$ 是以下三角或上三角模式存储的对称矩阵，$A$ 和 $B$ 是维度分别为 $\text{op}(A)$ $n \times k$ 和 $\text{op}(B)$ $n \times k$ 的矩阵。同样，对于矩阵 $A$ 和 $B$

$\text{op(}A\text{) and op(}B\text{)} = \left\{ \begin{matrix}
{A\text{ and }B} & {\text{if }\textsf{trans == CUBLAS\_OP\_N}} \\
{A^{T}\text{ and }B^{T}} & {\text{if }\textsf{trans == CUBLAS\_OP\_T}} \\
\end{matrix} \right.$

当B以保证结果对称的方式给出时，可以使用此例程。一个常见的例子是矩阵B是矩阵A的缩放形式：这等价于矩阵B是矩阵A与对角矩阵的乘积。有关矩阵与对角矩阵乘积的高效计算，请参阅 `cublas<t>dgmm()` 例程。

| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | input | cuBLAS库上下文的句柄。 |
| uplo |  | input | 指示是否存储矩阵C的下三角或上三角部分，另一对称部分未被引用，且从存储的元素中推断。 |
| trans |  | input | op(A)运算，非转置或转置。 |
| n |  | input | 矩阵op(A)、op(B)和C的行数。 |
| k |  | input | 矩阵op(A)和op(B)的列数。 |
| alpha | 主机或设备 | input | 用于乘法的<type>标量。 |
| A | 设备 | input | 维度为lda x k的<type>数组，当transa == CUBLAS_OP_N时lda >= max(1, n)，否则为lda x n且lda >= max(1, k)。 |
| lda |  | input | 用于存储矩阵A的二维数组的主维度。 |
| B | 设备 | input | 当transb == CUBLAS_OP_N时维度为ldb x k的<type>数组，ldb >= max(1, n)，否则为ldb x n且ldb >= max(1,k)。 |
| ldb |  | input | 用于存储矩阵B的二维数组的主维度。 |
| beta | 主机或设备 | input | 用于乘法的<type>标量。如果beta == 0，则C不必是有效输入。 |
| C | 设备 | 输入/输出 | 维度为ldc x n的<type>数组，ldc >= max(1, n)。 |
| ldc |  | input | 用于存储矩阵C的二维数组的主维度。 |

此函数返回的可能错误值及其含义如下表所示。

| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | 如果n < 0或k < 0，或
如果trans不是CUBLAS_OP_N、CUBLAS_OP_T和CUBLAS_OP_C之一，或
如果uplo不是CUBLAS_FILL_MODE_LOWER和CUBLAS_FILL_MODE_UPPER之一，或
如果当trans == CUBLAS_OP_N时lda < max(1, n)，否则lda < max(1, k)，或
如果当trans == CUBLAS_OP_N时ldb < max(1, n)，否则ldb < max(1, k)，或
如果ldc < max(1, n)，或
如果alpha或beta为NULL，或
如果beta不为零时C为NULL |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数无法在GPU上启动 |

有关参考文献，请参阅NETLIB文档：

[ssyrk()](http://www.netlib.org/blas/ssyrk.f)、[dsyrk()](http://www.netlib.org/blas/dsyrk.f)、[csyrk()](http://www.netlib.org/blas/csyrk.f)、[zsyrk()](http://www.netlib.org/blas/zsyrk.f)和

[ssyr2k()](http://www.netlib.org/blas/ssyr2k.f)、[dsyr2k()](http://www.netlib.org/blas/dsyr2k.f)、[csyr2k()](http://www.netlib.org/blas/csyr2k.f)、[zsyr2k()](http://www.netlib.org/blas/zsyr2k.f)