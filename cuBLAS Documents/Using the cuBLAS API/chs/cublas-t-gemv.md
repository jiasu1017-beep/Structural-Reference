### 2.6.2. cublas<t>gemv()



```c++

cublasStatus_t cublasSgemv(cublasHandle_t handle, cublasOperation_t trans,
                           int m, int n,
                           const float           *alpha,
                           const float           *A, int lda,
                           const float           *x, int incx,
                           const float           *beta,
                           float           *y, int incy)
// 单精度实数矩阵向量乘法
cublasStatus_t cublasDgemv(cublasHandle_t handle, cublasOperation_t trans,
                           int m, int n,
                           const double          *alpha,
                           const double          *A, int lda,
                           const double          *x, int incx,
                           const double          *beta,
                           double          *y, int incy)
// 双精度实数矩阵向量乘法
cublasStatus_t cublasCgemv(cublasHandle_t handle, cublasOperation_t trans,
                           int m, int n,
                           const cuComplex       *alpha,
                           const cuComplex       *A, int lda,
                           const cuComplex       *x, int incx,
                           const cuComplex       *beta,
                           cuComplex       *y, int incy)
// 单精度复数矩阵向量乘法
cublasStatus_t cublasZgemv(cublasHandle_t handle, cublasOperation_t trans,
                           int m, int n,
                           const cuDoubleComplex *alpha,
                           const cuDoubleComplex *A, int lda,
                           const cuDoubleComplex *x, int incx,
                           const cuDoubleComplex *beta,
                           cuDoubleComplex *y, int incy)
// 双精度复数矩阵向量乘法


```


此函数支持64位整数接口。


此函数执行矩阵向量乘法


$\textbf{y} = \alpha\text{ op}(A)\textbf{x} + \beta\textbf{y}$


其中 $A$ 是以列主序格式存储的 $m \times n$ 矩阵，$\mathbf{x}$ 和 $\mathbf{y}$ 是向量，$\alpha$ 和 $\beta$ 是标量。此外，对于矩阵 $A$


$\text{ op}(A) = \begin{cases}
A & \text{ if trans == CUBLAS\_OP\_N} \\
A^{T} & \text{ if trans == CUBLAS\_OP\_T} \\
A^{H} & \text{ if trans == CUBLAS\_OP\_C} \\
\end{cases}$


| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | 输入 | cuBLAS库上下文的句柄。 |
| trans |  | 输入 | 运算 op(A)，可为非转置或（共轭）转置。 |
| m |  | 输入 | 矩阵 A 的行数。 |
| n |  | 输入 | 矩阵 A 的列数。 |
| alpha | 主机或设备 | 输入 | 用于乘法的 <type> 标量。 |
| A | 设备 | 输入 | 维度为 lda x n 的 <type> 数组，lda >= max(1, m)。在调用之前，数组 A 的前 m 行 n 列部分必须包含系数矩阵。退出时保持不变。 |
| lda |  | 输入 | 用于存储矩阵 A 的二维数组的主维。lda 至少为 max(1, m)。 |
| x | 设备 | 输入 | <type> 向量，当 trans == CUBLAS_OP_N 时至少包含 (1 + (n - 1) * abs(incx)) 个元素，否则至少包含 (1 + (m - 1) * abs(incx)) 个元素。 |
| incx |  | 输入 | x 中连续元素之间的步长。 |
| beta | 主机或设备 | 输入 | 用于乘法的 <type> 标量。如果 beta == 0，则 y 不必是有效的输入。 |
| y | 设备 | 输入/输出 | <type> 向量，当 trans == CUBLAS_OP_N 时至少包含 (1 + (m - 1) * abs(incy)) 个元素，否则至少包含 (1 + (n - 1) * abs(incy)) 个元素。 |
| incy |  | 输入 | y 中连续元素之间的步长。 |


此函数可能返回的错误值及其含义如下所述。


| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | 参数 m < 0 或 n < 0，或 incx == 0 或 incy == 0 |
| CUBLAS_STATUS_EXECUTION_FAILED | 该函数在GPU上启动失败 |


有关参考资料，请参阅 NETLIB 文档：


[sgemv()](http://www.netlib.org/blas/sgemv.f), [dgemv()](http://www.netlib.org/blas/dgemv.f), [cgemv()](http://www.netlib.org/blas/cgemv.f), [zgemv()](http://www.netlib.org/blas/zgemv.f)