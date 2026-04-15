### 2.5.12. cublas<t>scal()



```c++

cublasStatus_t  cublasSscal(cublasHandle_t handle, int n,
                            const float           *alpha,
                            float           *x, int incx)
cublasStatus_t  cublasDscal(cublasHandle_t handle, int n,
                            const double          *alpha,
                            double          *x, int incx)
cublasStatus_t  cublasCscal(cublasHandle_t handle, int n,
                            const cuComplex       *alpha,
                            cuComplex       *x, int incx)
cublasStatus_t cublasCsscal(cublasHandle_t handle, int n,
                            const float           *alpha,
                            cuComplex       *x, int incx)
cublasStatus_t  cublasZscal(cublasHandle_t handle, int n,
                            const cuDoubleComplex *alpha,
                            cuDoubleComplex *x, int incx)
cublasStatus_t cublasZdscal(cublasHandle_t handle, int n,
                            const double          *alpha,
                            cuDoubleComplex *x, int incx)


```


此函数支持64位整数接口。


此函数用标量 $\alpha$ 缩放向量 `x`，并用结果覆盖原向量。因此，执行的操作是对于 $i = 1,\ldots,n$ 和 $j = 1 + \left( {i - 1} \right)*\text{incx}$，有 $\mathbf{x}\lbrack j\rbrack = \alpha \times \mathbf{x}\lbrack j\rbrack$。注意，上述等式反映了为与 Fortran 兼容而使用的从1开始的索引方式。


| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | 输入 | cuBLAS 库上下文的句柄。 |
| alpha | 主机或设备 | 输入 | 用于乘法的 <type> 标量。 |
| n |  | 输入 | 向量 x 中的元素个数。 |
| x | 设备 | 输入/输出 | 包含 n 个元素的 <type> 向量。 |
| incx |  | 输入 | 向量 x 中连续元素之间的步长。 |


此函数可能返回的错误值及其含义如下所示。


| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数在 GPU 上启动失败 |


相关参考请参阅 NETLIB 文档：


[sscal()](http://www.netlib.org/blas/sscal.f), [dscal()](http://www.netlib.org/blas/dscal.f), [csscal()](http://www.netlib.org/blas/csscal.f), [cscal()](http://www.netlib.org/blas/cscal.f), [zdscal()](http://www.netlib.org/blas/zdscal.f), [zscal()](http://www.netlib.org/blas/zscal.f)