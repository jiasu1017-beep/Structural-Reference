### 2.6.17. cublas<t>hemv()

```c++

cublasStatus_t cublasChemv(cublasHandle_t handle, cublasFillMode_t uplo,
                           int n, const cuComplex       *alpha,
                           const cuComplex       *A, int lda,
                           const cuComplex       *x, int incx,
                           const cuComplex       *beta,
                           cuComplex       *y, int incy)
cublasStatus_t cublasZhemv(cublasHandle_t handle, cublasFillMode_t uplo,
                           int n, const cuDoubleComplex *alpha,
                           const cuDoubleComplex *A, int lda,
                           const cuDoubleComplex *x, int incx,
                           const cuDoubleComplex *beta,
                           cuDoubleComplex *y, int incy)


```

此函数支持 64 位整数接口。

此函数执行厄米特矩阵向量乘法运算：

$\textbf{y} = \alpha A\textbf{x} + \beta\textbf{y}$

其中，$A$ 是一个以低端或高端模式存储的 $n \times n$ 厄米特矩阵，$\mathbf{x}$ 和 $\mathbf{y}$ 是向量，$\alpha$ 和 $\beta$ 是标量。

此函数有一个使用原子操作的替代快速实现，可以通过以下方式启用：

请参阅关于原子操作使用详情的相关章节。

| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | 输入 | cuBLAS 库上下文的句柄。 |
| uplo |  | 输入 | 指定矩阵 A 的下三角或上三角部分是否存储，另一半厄米特部分未引用，由存储的元素推断。 |
| n |  | 输入 | 矩阵 A 的行数和列数。 |
| alpha | 主机或设备 | 输入 | 用于乘法的 <type> 标量。 |
| A | 设备 | 输入 | 维度为 lda x n 的 <type> 数组，lda >= max(1, n)。对角元素的虚部假定为零。 |
| lda |  | 输入 | 用于存储矩阵 A 的二维数组的主维度。 |
| x | 设备 | 输入 | 包含 n 个元素的 <type> 向量。 |
| incx |  | 输入 | x 中连续元素之间的步幅。 |
| beta | 主机或设备 | 输入 | 用于乘法的 <type> 标量。如果 beta == 0，则 y 不必是有效的输入。 |
| y | 设备 | 输入/输出 | 包含 n 个元素的 <type> 向量。 |
| incy |  | 输入 | y 中连续元素之间的步幅。 |

此函数返回的可能错误值及其含义如下所列。

| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | 如果 n < 0，或
如果 incx == 0 或 incy == 0，或
如果 uplo != CUBLAS_FILL_MODE_LOWER 且 uplo != CUBLAS_FILL_MODE_UPPER，或
如果 lda < n |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数在 GPU 上启动失败 |

有关参考资料，请参阅 NETLIB 文档：

[chemv()](http://www.netlib.org/blas/chemv.f), [zhemv()](http://www.netlib.org/blas/zhemv.f)