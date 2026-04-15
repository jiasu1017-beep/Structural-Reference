### 2.5.1. cublasI<t>amax()

```c++

cublasStatus_t cublasIsamax(cublasHandle_t handle, int n,
                            const float *x, int incx, int *result)
cublasStatus_t cublasIdamax(cublasHandle_t handle, int n,
                            const double *x, int incx, int *result)
cublasStatus_t cublasIcamax(cublasHandle_t handle, int n,
                            const cuComplex *x, int incx, int *result)
cublasStatus_t cublasIzamax(cublasHandle_t handle, int n,
                            const cuDoubleComplex *x, int incx, int *result)


```

此函数支持 64 位整数接口。

此函数用于查找最大绝对值元素的（最小）索引。因此，结果为第一个满足以下条件的 $i$：对于 $i = 1,\ldots,n$ 和 $j = 1 + \left( {i - 1} \right)*\text{ incx}$，使得 $\left| \mathbf{Im}\left( {x\lbrack j\rbrack} \right) \middle| + \middle| \mathbf{Re}\left( {x\lbrack j\rbrack} \right) \right|$ 最大。请注意，最后一个等式反映的是为与 Fortran 兼容而使用的 1-based 索引。

| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| handle |  | input | cuBLAS 库上下文的句柄。 |
| n |  | input | 向量 x 中的元素数量。 |
| x | device | input | 包含元素的 <type> 向量。 |
| incx |  | input | 向量 x 中连续元素之间的步长。 |
| result | host or device | output | 结果索引，如果 n <= 0 或 incx <= 0，则设置为 0。 |

此函数可能返回的错误值及其含义如下所列。


| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_ALLOC_FAILED | 无法分配归约缓冲区 |
| CUBLAS_STATUS_EXECUTION_FAILED | 函数无法在 GPU 上启动 |
| CUBLAS_STATUS_INVALID_VALUE | result 为 NULL |


相关参考请参阅 NETLIB 文档：


[isamax()](http://www.netlib.org/blas/isamax.f), [idamax()](http://www.netlib.org/blas/idamax.f), [icamax()](http://www.netlib.org/blas/icamax.f), [izamax()](http://www.netlib.org/blas/izamax.f)