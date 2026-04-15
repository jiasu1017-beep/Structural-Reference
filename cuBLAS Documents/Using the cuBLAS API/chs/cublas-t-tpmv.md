### 2.6.13. cublas<t>tpmv()

```c++
cublasStatus_t cublasStpmv(cublasHandle_t handle, cublasFillMode_t uplo,
                           cublasOperation_t trans, cublasDiagType_t diag,
                           int n, const float           *AP,
                           float           *x, int incx)
cublasStatus_t cublasDtpmv(cublasHandle_t handle, cublasFillMode_t uplo,
                           cublasOperation_t trans, cublasDiagType_t diag,
                           int n, const double          *AP,
                           double          *x, int incx)
cublasStatus_t cublasCtpmv(cublasHandle_t handle, cublasFillMode_t uplo,
                           cublasOperation_t trans, cublasDiagType_t diag,
                           int n, const cuComplex       *AP,
                           cuComplex       *x, int incx)
cublasStatus_t cublasZtpmv(cublasHandle_t handle, cublasFillMode_t uplo,
                           cublasOperation_t trans, cublasDiagType_t diag,
                           int n, const cuDoubleComplex *AP,
                           cuDoubleComplex *x, int incx)
```

此函数支持64位整数接口。

此函数执行三角压缩矩阵向量乘法

$\textbf{x} = \text{op}(A)\textbf{x}$

其中 $A$ 是以压缩格式存储的三角矩阵，$\mathbf{x}$ 是向量。此外，对于矩阵 $A$

$\text{op}(A) = \left\{ \begin{matrix}
A & {\text{if }\textsf{trans == $\mathrm{CUBLAS\_OP\_N}$}} \\
A^{T} & {\text{if }\textsf{trans == $\mathrm{CUBLAS\_OP\_T}$}} \\
A^{H} & {\text{if }\textsf{trans == $\mathrm{CUBLAS\_OP\_C}$}} \\
\end{matrix} \right.$

如果 `uplo == CUBLAS_FILL_MODE_LOWER`，则三角矩阵 $A$ 下三角部分的元素按列紧凑存储，无间隙，因此元素 $A(i,j)$ 存储在内存位置 `AP[i+((2*n-j+1)*j)/2]` 中，其中 $j = 1,\ldots,n$ 且 $i \geq j$。因此，压缩格式仅需 $\frac{n(n + 1)}{2}$ 个元素进行存储。

如果 `uplo == CUBLAS_FILL_MODE_UPPER`，则三角矩阵 $A$ 上三角部分的元素按列紧凑存储，无间隙，因此元素 $A(i,j)$ 存储在内存位置 `AP[i+(j*(j+1))/2]` 中，适用于 $A(i,j)$ 且 $i \leq j$。因此，压缩格式仅需 $\frac{n(n + 1)}{2}$ 个元素进行存储。


| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | input | cuBLAS 库上下文的句柄。 |
| uplo |  | input | 指示矩阵 A 的下三角或上三角部分是否被存储，另一部分不被引用，并从存储的元素推断。 |
| trans |  | input | 操作 op(A)，即非转置或（共轭）转置。 |
| diag |  | input | 指示矩阵 A 主对角线上的元素是否为单位1，且不应被访问。 |
| n |  | input | 矩阵 A 的行数和列数。 |
| AP | device | input | 以压缩格式存储 $A$ 的 <type> 数组。 |
| x | device | in/out | 具有 n 个元素的 <type> 向量。 |
| incx |  | input | x 中连续元素之间的步长。 |

此函数返回的可能错误值及其含义如下所述。


| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | 如果 n < 0，或 incx == 0，或 trans 不是 CUBLAS_OP_N、CUBLAS_OP_T 和 CUBLAS_OP_C 之一，或 uplo 不是 CUBLAS_FILL_MODE_LOWER 和 CUBLAS_FILL_MODE_UPPER 之一，或 diag 不是 CUBLAS_DIAG_UNIT 和 CUBLAS_DIAG_NON_UNIT 之一 |
| CUBLAS_STATUS_ALLOC_FAILED | 内部临时内存的分配失败 |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数在 GPU 上启动失败 |

有关参考文献，请参阅 NETLIB 文档：

[stpmv()](http://www.netlib.org/blas/stpmv.f), [dtpmv()](http://www.netlib.org/blas/dtpmv.f), [ctpmv()](http://www.netlib.org/blas/ctpmv.f), [ztpmv()](http://www.netlib.org/blas/ztpmv.f)