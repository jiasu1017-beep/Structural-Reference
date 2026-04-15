### 2.5.5. cublas<t>copy()



```c++

cublasStatus_t cublasScopy(cublasHandle_t handle, int n,
                           const float           *x, int incx,
                           float                 *y, int incy)
cublasStatus_t cublasDcopy(cublasHandle_t handle, int n,
                           const double          *x, int incx,
                           double                *y, int incy)
cublasStatus_t cublasCcopy(cublasHandle_t handle, int n,
                           const cuComplex       *x, int incx,
                           cuComplex             *y, int incy)
cublasStatus_t cublasZcopy(cublasHandle_t handle, int n,
                           const cuDoubleComplex *x, int incx,
                           cuDoubleComplex       *y, int incy)


```


此函数支持 64 位整数接口。


此函数将向量 `x` 复制到向量 `y` 中。因此，执行的操作是 $\mathbf{y}\lbrack j\rbrack = \mathbf{x}\lbrack k\rbrack$，其中 $i = 1,\ldots,n$，$k = 1 + \left( {i - 1} \right)*\text{incx}$，$j = 1 + \left( {i - 1} \right)*\text{incy}$。请注意，后两个等式反映的是 1 基于索引，用于与 Fortran 兼容。


| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | 输入 | cuBLAS 库上下文的句柄。 |
| n |  | 输入 | 向量 x 和 y 中的元素数量。 |
| x | 设备 | 输入 | 具有 n 个元素的 <type> 向量。 |
| incx |  | 输入 | x 中连续元素之间的步长。 |
| y | 设备 | 输入/输出 | 具有 n 个元素的 <type> 向量。 |
| incy |  | 输入 | y 中连续元素之间的步长。 |


此函数返回的可能错误值及其含义如下所列。


| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_EXECUTION_FAILED | 该函数无法在 GPU 上启动 |


参考文献请参阅 NETLIB 文档：


[scopy()](http://www.netlib.org/blas/scopy.f), [dcopy()](http://www.netlib.org/blas/dcopy.f), [ccopy()](http://www.netlib.org/blas/ccopy.f), [zcopy()](http://www.netlib.org/blas/zcopy.f)