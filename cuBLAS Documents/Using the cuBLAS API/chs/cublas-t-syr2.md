### 2.6.10. cublas<t>syr2()

```c++
// 执行对称秩2更新
cublasStatus_t cublasSsyr2(cublasHandle_t handle, cublasFillMode_t uplo, int n,
                           const float           *alpha, const float           *x, int incx,
                           const float           *y, int incy, float           *A, int lda
cublasStatus_t cublasDsyr2(cublasHandle_t handle, cublasFillMode_t uplo, int n,
                           const double          *alpha, const double          *x, int incx,
                           const double          *y, int incy, double          *A, int lda
cublasStatus_t cublasCsyr2(cublasHandle_t handle, cublasFillMode_t uplo, int n,
                           const cuComplex       *alpha, const cuComplex       *x, int incx,
                           const cuComplex       *y, int incy, cuComplex       *A, int lda
cublasStatus_t cublasZsyr2(cublasHandle_t handle, cublasFillMode_t uplo, int n,
                           const cuDoubleComplex *alpha, const cuDoubleComplex *x, int incx,
                           const cuDoubleComplex *y, int incy, cuDoubleComplex *A, int lda
```

此函数支持64位整数接口。

此函数执行对称秩2更新

$A = \alpha\left( {\textbf{x}\textbf{y}^{T} + \textbf{y}\textbf{x}^{T}} \right) + A$

其中 $A$ 是一个以列主序格式存储的 $n \times n$ 对称矩阵，$\mathbf{x}$ 和 $\mathbf{y}$ 是向量，$\alpha$ 是标量。

| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | 输入 | cuBLAS 库上下文的句柄。 |
| uplo |  | 输入 | 指示矩阵 A 的下三角或上三角部分是否存储，另一对称部分未引用且从存储的元素推断。 |
| n |  | 输入 | 矩阵 A 的行数和列数。 |
| alpha | 主机或设备 | 输入 | 用于乘法的 <type> 标量。 |
| x | 设备 | 输入 | 包含 n 个元素的 <type> 向量。 |
| incx |  | 输入 | x 中连续元素之间的步长。 |
| y | 设备 | 输入 | 包含 n 个元素的 <type> 向量。 |
| incy |  | 输入 | y 中连续元素之间的步长。 |
| A | 设备 | 输入/输出 | 维度为 lda × n 的 <type> 数组，lda >= max(1,n)。 |
| lda |  | 输入 | 用于存储矩阵 A 的二维数组的主维度。 |

此函数返回的可能错误值及其含义如下所列。

| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | 如果 n < 0，或
如果 incx == 0 或 incy == 0，或
如果 uplo 不是 CUBLAS_FILL_MODE_LOWER 和 CUBLAS_FILL_MODE_UPPER 之一，或
如果 alpha 为 NULL，或
如果 lda < max(1, n) |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数在 GPU 上启动失败 |

有关参考信息，请参阅 NETLIB 文档：

[ssyr2()](http://www.netlib.org/lapack/explore-html/db/d99/ssyr2_8f_source.html)、[dsyr2()](http://www.netlib.org/lapack/explore-html/de/d41/dsyr2_8f_source.html)