### 2.5.4. cublas<t>axpy()

```c++

cublasStatus_t cublasSaxpy(cublasHandle_t handle, int n,
                           const float           *alpha,
                           const float           *x, int incx,
                           float                 *y, int incy)
cublasStatus_t cublasDaxpy(cublasHandle_t handle, int n,
                           const double          *alpha,
                           const double          *x, int incx,
                           double                *y, int incy)
cublasStatus_t cublasCaxpy(cublasHandle_t handle, int n,
                           const cuComplex       *alpha,
                           const cuComplex       *x, int incx,
                           cuComplex             *y, int incy)
cublasStatus_t cublasZaxpy(cublasHandle_t handle, int n,
                           const cuDoubleComplex *alpha,
                           const cuDoubleComplex *x, int incx,
                           cuDoubleComplex       *y, int incy)


```


此函数支持64位整数接口。

此函数将向量 `x` 乘以标量 $\alpha$ 并将其加到向量 `y` 上，用结果覆盖最新的向量。因此，执行的操作是对于 $i = 1,\ldots,n$、$k = 1 + \left( {i - 1} \right)*\text{incx}$ 和 $j = 1 + \left( {i - 1} \right)*\text{incy}$，有 $\mathbf{y}\lbrack j\rbrack = \alpha \times \mathbf{x}\lbrack k\rbrack + \mathbf{y}\lbrack j\rbrack$。请注意，最后两个公式反映了为与Fortran兼容而使用的1-based索引。

| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | 输入 | cuBLAS库上下文的句柄。 |
| alpha | 主机或设备 | 输入 | 用于乘法的 <type> 标量。 |
| n |  | 输入 | 向量 x 和 y 中的元素数量。 |
| x | 设备 | 输入 | 具有 n 个元素的 <type> 向量。 |
| incx |  | 输入 | x 中连续元素之间的步长。 |
| y | 设备 | 输入/输出 | 具有 n 个元素的 <type> 向量。 |
| incy |  | 输入 | y 中连续元素之间的步长。 |


此函数可能返回的错误值及其含义如下所列。


| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数在GPU上启动失败 |


参考文献请参阅NETLIB文档：


[saxpy()](http://www.netlib.org/blas/saxpy.f)、[daxpy()](http://www.netlib.org/blas/daxpy.f)、[caxpy()](http://www.netlib.org/blas/caxpy.f)、[zaxpy()](http://www.netlib.org/blas/zaxpy.f)