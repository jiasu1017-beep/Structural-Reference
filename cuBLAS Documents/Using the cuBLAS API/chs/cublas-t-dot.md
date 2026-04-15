### 2.5.6. cublas<t>dot()

```c++

cublasStatus_t cublasSdot (cublasHandle_t handle, int n,
                           const float           *x, int incx,
                           const float           *y, int incy,
                           float           *result)
cublasStatus_t cublasDdot (cublasHandle_t handle, int n,
                           const double          *x, int incx,
                           const double          *y, int incy,
                           double          *result)
cublasStatus_t cublasCdotu(cublasHandle_t handle, int n,
                           const cuComplex       *x, int incx,
                           const cuComplex       *y, int incy,
                           cuComplex       *result)
cublasStatus_t cublasCdotc(cublasHandle_t handle, int n,
                           const cuComplex       *x, int incx,
                           const cuComplex       *y, int incy,
                           cuComplex       *result)
cublasStatus_t cublasZdotu(cublasHandle_t handle, int n,
                           const cuDoubleComplex *x, int incx,
                           const cuDoubleComplex *y, int incy,
                           cuDoubleComplex *result)
cublasStatus_t cublasZdotc(cublasHandle_t handle, int n,
                           const cuDoubleComplex *x, int incx,
                           const cuDoubleComplex *y, int incy,
                           cuDoubleComplex       *result)


```

此函数支持64位整数接口。

此函数计算向量`x`和`y`的点积。因此，结果为 $\sum_{i = 1}^{n}\left( {\mathbf{x}\lbrack k\rbrack \times \mathbf{y}\lbrack j\rbrack} \right)$，其中 $k = 1 + \left( {i - 1} \right)*\text{incx}$ 且 $j = 1 + \left( {i - 1} \right)*\text{incy}$。注意，如果函数名以字符'c'结尾，则应在向量x的元素上使用共轭值；最后两个等式反映了为与Fortran兼容而使用的一-based索引。

| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | 输入 | cuBLAS库上下文的句柄。 |
| n |  | 输入 | 向量x和y中的元素数量。 |
| x | 设备 | 输入 | 具有n个元素的<type>向量。 |
| incx |  | 输入 | 向量x中连续元素之间的步长。 |
| y | 设备 | 输入 | 具有n个元素的<type>向量。 |
| incy |  | 输入 | 向量y中连续元素之间的步长。 |
| result | 主机或设备 | 输出 | 生成的点积，如果 n <= 0 则设置为 0。 |

此函数可能返回的错误值及其含义如下所列。

| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成。 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化。 |
| CUBLAS_STATUS_ALLOC_FAILED | 无法分配归约缓冲区。 |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数无法在GPU上启动。 |

有关参考，请参阅NETLIB文档：

[sdot()](http://www.netlib.org/blas/sdot.f), [ddot()](http://www.netlib.org/blas/ddot.f), [cdotu()](http://www.netlib.org/blas/cdotu.f), [cdotc()](http://www.netlib.org/blas/cdotc.f), [zdotu()](http://www.netlib.org/blas/zdotu.f), [zdotc()](http://www.netlib.org/blas/zdotc.f)