### 2.6.8. cublas<t>symv()



```c++

cublasStatus_t cublasSsymv(cublasHandle_t handle, cublasFillMode_t uplo,
                           int n, const float           *alpha,
                           const float           *A, int lda,
                           const float           *x, int incx, const float           *beta,
                           float           *y, int incy)
cublasStatus_t cublasDsymv(cublasHandle_t handle, cublasFillMode_t uplo,
                           int n, const double          *alpha,
                           const double          *A, int lda,
                           const double          *x, int incx, const double          *beta,
                           double          *y, int incy)
cublasStatus_t cublasCsymv(cublasHandle_t handle, cublasFillMode_t uplo,
                           int n, const cuComplex       *alpha, /* 主机或设备指针 */
                           const cuComplex       *A, int lda,
                           const cuComplex       *x, int incx, const cuComplex       *beta,
                           cuComplex       *y, int incy)
cublasStatus_t cublasZsymv(cublasHandle_t handle, cublasFillMode_t uplo,
                           int n, const cuDoubleComplex *alpha,
                           const cuDoubleComplex *A, int lda,
                           const cuDoubleComplex *x, int incx, const cuDoubleComplex *beta,
                           cuDoubleComplex *y, int incy)


```


此函数支持64位整数接口。


此函数执行对称矩阵-向量乘法运算。


$\textbf{y} = \alpha A\textbf{x} + \beta\textbf{y}$
其中 $A$ 是一个以低位或高位模式存储的 $n \times n$ 对称矩阵，$\mathbf{x}$ 和 $\mathbf{y}$ 是向量，$\alpha$ 和 $\beta$ 是标量。


此函数有一个使用原子操作的可选更快实现，可以通过 cublasSetAtomicsMode() 启用。


有关原子操作使用的更多详细信息，请参阅 cublasSetAtomicsMode() 函数部分。


| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | 输入 | cuBLAS 库上下文的句柄。 |
| uplo |  | 输入 | 指示矩阵的下三角或上三角部分是否被存储，另一对称部分未被引用，且从存储的元素中推断。 |
| n |  | 输入 | 矩阵 A 的行数和列数。 |
| alpha | 主机或设备 | 输入 | 用于乘法的 <type> 标量。 |
| A | 设备 | 输入 | 维度为 lda x n 的 <type> 数组，其中 lda >= max(1, n)。 |
| lda |  | 输入 | 用于存储矩阵 A 的二维数组的主维度。 |
| x | 设备 | 输入 | 具有 n 个元素的 <type> 向量。 |
| incx |  | 输入 | x 中连续元素之间的步长。 |
| beta | 主机或设备 | 输入 | 用于乘法的 <type> 标量。如果 beta == 0，则 y 不必是有效输入。 |
| y | 设备 | 输入/输出 | 具有 n 个元素的 <type> 向量。 |
| incy |  | 输入 | y 中连续元素之间的步长。 |


此函数返回的可能错误值及其含义如下所列。


| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成。 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化。 |
| CUBLAS_STATUS_INVALID_VALUE | 如果 n < 0，或
如果 incx == 0 或 incy == 0，或
如果 uplo 不是 CUBLAS_FILL_MODE_LOWER 和 CUBLAS_FILL_MODE_UPPER 之一，或
如果 lda < n。 |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数未能在 GPU 上启动。 |


参考文献请参阅 NETLIB 文档：


[ssymv()](http://www.netlib.org/blas/ssymv.f), [dsymv()](http://www.netlib.org/blas/dsymv.f)