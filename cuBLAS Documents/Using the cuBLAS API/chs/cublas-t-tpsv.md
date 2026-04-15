### 2.6.14. cublas<t>tpsv()

```c++

cublasStatus_t cublasStpsv(cublasHandle_t handle, cublasFillMode_t uplo,
                           cublasOperation_t trans, cublasDiagType_t diag,
                           int n, const float           *AP,
                           float           *x, int incx)
cublasStatus_t cublasDtpsv(cublasHandle_t handle, cublasFillMode_t uplo,
                           cublasOperation_t trans, cublasDiagType_t diag,
                           int n, const double          *AP,
                           double          *x, int incx)
cublasStatus_t cublasCtpsv(cublasHandle_t handle, cublasFillMode_t uplo,
                           cublasOperation_t trans, cublasDiagType_t diag,
                           int n, const cuComplex       *AP,
                           cuComplex       *x, int incx)
cublasStatus_t cublasZtpsv(cublasHandle_t handle, cublasFillMode_t uplo,
                           cublasOperation_t trans, cublasDiagType_t diag,
                           int n, const cuDoubleComplex *AP,
                           cuDoubleComplex *x, int incx)


```

此函数支持 64 位整数接口。

此函数求解压缩格式三角线性方程组（包含单个右端项）

$\text{op}(A)\textbf{x} = \textbf{b}$

其中 $A$ 是以压缩格式存储的三角矩阵，$\mathbf{x}$ 和 $\mathbf{b}$ 是向量。此外，对于矩阵 $A$

$\text{op}(A) = \left\{ \begin{matrix}
A & {\text{if }\textsf{trans == CUBLAS\_OP\_N}} \\
A^{T} & {\text{if }\textsf{trans == CUBLAS\_OP\_T}} \\
A^{H} & {\text{if }\textsf{trans == CUBLAS\_OP\_C}} \\
\end{matrix} \right.$

解 $\mathbf{x}$ 会在退出时覆盖右端项 $\mathbf{b}$。

此函数不包含奇异性或近似奇异性的检测。

如果 `uplo == CUBLAS_FILL_MODE_LOWER`，则三角矩阵 $A$ 下三角部分的元素按列紧凑存储（无间隙），使得元素 $A(i,j)$ 存储在内存位置 `AP[i+((2*n-j+1)*j)/2]` 中，其中 $j = 1,\ldots,n$ 且 $i \geq j$。因此，压缩格式仅需要 $\frac{n(n + 1)}{2}$ 个元素进行存储。

如果 `uplo == CUBLAS_FILL_MODE_UPPER`，则三角矩阵 $A$ 上三角部分的元素按列紧凑存储（无间隙），使得元素 $A(i,j)$ 存储在内存位置 `AP[i+(j*(j+1))/2]` 中，其中 $j = 1,\ldots,n$ 且 $i \leq j$。因此，压缩格式仅需要 $\frac{n(n + 1)}{2}$ 个元素进行存储。

| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | 输入 | cuBLAS 库上下文的句柄。 |
| uplo |  | 输入 | 指示矩阵 A 的下三角或上三角部分是否被存储，另一部分未被引用且从存储的元素中推断。 |
| trans |  | 输入 | 操作 op(A)，可为非转置或（共）转置。 |
| diag |  | 输入 | 指示矩阵主对角线上的元素是否为单元（1），且不应被访问。 |
| n |  | 输入 | 矩阵 A 的行数和列数。 |
| AP | 设备端 | 输入 | 以压缩格式存储 $A$ 的 `<type>` 数组。 |
| x | 设备端 | 输入/输出 | 包含 n 个元素的 `<type>` 向量。 |
| incx |  | 输入 | x 中连续元素之间的步长。 |

此函数可能返回的错误值及其含义如下所述。

| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | 如果 n < 0，或
如果 incx == 0，或
如果 trans 不是 CUBLAS_OP_N、CUBLAS_OP_T 和 CUBLAS_OP_C 之一，或
如果 uplo 不是 CUBLAS_FILL_MODE_LOWER 和 CUBLAS_FILL_MODE_UPPER 之一，或
如果 diag 不是 CUBLAS_DIAG_UNIT 和 CUBLAS_DIAG_NON_UNIT 之一 |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数在 GPU 上启动失败 |

有关参考文献，请参阅 NETLIB 文档：

[stpsv()](http://www.netlib.org/blas/stpsv.f), [dtpsv()](http://www.netlib.org/blas/dtpsv.f), [ctpsv()](http://www.netlib.org/blas/ctpsv.f), [ztpsv()](http://www.netlib.org/blas/ztpsv.f)