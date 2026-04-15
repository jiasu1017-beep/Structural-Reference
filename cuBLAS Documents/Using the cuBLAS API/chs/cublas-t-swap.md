### 2.5.13. cublas<t>swap()



```c++

cublasStatus_t cublasSswap(cublasHandle_t handle, int n, float           *x,
                           int incx, float           *y, int incy)
cublasStatus_t cublasDswap(cublasHandle_t handle, int n, double          *x,
                           int incx, double          *y, int incy)
cublasStatus_t cublasCswap(cublasHandle_t handle, int n, cuComplex       *x,
                           int incx, cuComplex       *y, int incy)
cublasStatus_t cublasZswap(cublasHandle_t handle, int n, cuDoubleComplex *x,
                           int incx, cuDoubleComplex *y, int incy)


```


此函数支持64位整数接口。


此函数用于交换向量 `x` 和 `y` 的元素。因此，执行的操作是 $\left. \mathbf{y}\lbrack j\rbrack\Leftrightarrow\mathbf{x}\lbrack k\rbrack \right.$，其中 $i = 1,\ldots,n$，$k = 1 + \left( {i - 1} \right)*\text{incx}$，$j = 1 + \left( {i - 1} \right)*\text{incy}$。请注意，最后两个等式反映了为与Fortran兼容而使用的一-based索引。


| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | 输入 | cuBLAS库上下文的句柄。 |
| n |  | 输入 | 向量x和y中的元素数量。 |
| x | 设备 | 输入/输出 | 包含n个元素的<类型>向量。 |
| incx |  | 输入 | x中连续元素之间的步长。 |
| y | 设备 | 输入/输出 | 包含n个元素的<类型>向量。 |
| incy |  | 输入 | y中连续元素之间的步长。 |


此函数可能返回的错误值及其含义如下所列。


| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数无法在GPU上启动 |


参考文献请参阅NETLIB文档：


[sswap()](http://www.netlib.org/blas/sswap.f), [dswap()](http://www.netlib.org/blas/dswap.f), [cswap()](http://www.netlib.org/blas/cswap.f), [zswap()](http://www.netlib.org/blas/zswap.f)