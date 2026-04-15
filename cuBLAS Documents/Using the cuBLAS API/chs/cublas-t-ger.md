### 2.6.3. cublas<t>ger()

```c++

cublasStatus_t  cublasSger(cublasHandle_t handle, int m, int n,
                           const float           *alpha,
                           const float           *x, int incx,
                           const float           *y, int incy,
                           float           *A, int lda)
cublasStatus_t  cublasDger(cublasHandle_t handle, int m, int n,
                           const double          *alpha,
                           const double          *x, int incx,
                           const double          *y, int incy,
                           double          *A, int lda)
cublasStatus_t cublasCgeru(cublasHandle_t handle, int m, int n,
                           const cuComplex       *alpha,
                           const cuComplex       *x, int incx,
                           const cuComplex       *y, int incy,
                           cuComplex       *A, int lda)
cublasStatus_t cublasCgerc(cublasHandle_t handle, int m, int n,
                           const cuComplex       *alpha,
                           const cuComplex       *x, int incx,
                           const cuComplex       *y, int incy,
                           cuComplex       *A, int lda)
cublasStatus_t cublasZgeru(cublasHandle_t handle, int m, int n,
                           const cuDoubleComplex *alpha,
                           const cuDoubleComplex *x, int incx,
                           const cuDoubleComplex *y, int incy,
                           cuDoubleComplex *A, int lda)
cublasStatus_t cublasZgerc(cublasHandle_t handle, int m, int n,
                           const cuDoubleComplex *alpha,
                           const cuDoubleComplex *x, int incx,
                           const cuDoubleComplex *y, int incy,
                           cuDoubleComplex *A, int lda)


```

此函数支持64位整数接口。

此函数执行秩-1更新

$A = \begin{cases}
{\alpha\mathbf{xy}^{T} + A} & \text{if ger(),geru() is called} \\
{\alpha\mathbf{xy}^{H} + A} & \text{if gerc() is called} \\
\end{cases}$

其中，$A$是以列优先格式存储的$m \times n$矩阵，$\mathbf{x}$和$\mathbf{y}$是向量，$\alpha$是标量。


| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | input | cuBLAS库上下文的句柄。 |
| m |  | input | 矩阵A的行数。 |
| n |  | input | 矩阵A的列数。 |
| alpha | 主机或设备 | input | 用于乘法的<type>标量。 |
| x | 设备 | input | 包含m个元素的<type>向量。 |
| incx |  | input | x中连续元素之间的步长。 |
| y | 设备 | input | 包含n个元素的<type>向量。 |
| incy |  | input | y中连续元素之间的步长。 |
| A | 设备 | in/out | 维度为lda x n的<type>数组，其中lda >= max(1, m)。 |
| lda |  | input | 用于存储矩阵A的二维数组的主维度。 |


此函数返回的可能错误值及其含义如下所列。


| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | 如果m < 0或n < 0，或 |
| 如果incx == 0或incy == 0，或 |
| 如果alpha为NULL，或 |
| 如果lda < max(1, m) |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数在GPU上启动失败 |


参考资料请参阅NETLIB文档：


[sger()](http://www.netlib.org/blas/sger.f)、[dger()](http://www.netlib.org/blas/dger.f)、[cgeru()](http://www.netlib.org/blas/cgeru.f)、[cgerc()](http://www.netlib.org/blas/cgerc.f)、[zgeru()](http://www.netlib.org/blas/zgeru.f)、[zgerc()](http://www.netlib.org/blas/zgerc.f)